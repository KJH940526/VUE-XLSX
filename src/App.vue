<template>
  <div id="app">
    <div>
      <button @click="makeExcelFile5">Excel5</button>
    </div>
  </div>
</template>

<script>
import Xlsx from 'xlsx'

export default {
  name: 'App',
  data () {
    return {
      data1: [
        {
          관제사 : '김관제',
          모델 : "CCTV1",
          지역 : "성남시"
        },
        {
          관제사 : '이관제',
          모델 : "CCTV2",
          지역 : "서울특별시"
        },
        {
          관제사 : '다관제',
          모델 : "CCTV3",
          지역 : "중원구"
        },
        {
          관제사 : '라관제',
          모델 : "CCTV4",
          지역 : "중앙동"
        },
        
      ]
    }
  },
  methods: {
    makeExcelFile5 () {
      const workBook = Xlsx.utils.book_new() //book_new: workbook을 하나 만듭니다. 엑셀 파일을 하나 만듬
      const workSheet = Xlsx.utils.json_to_sheet(this.data1) //json_to_sheet: json 데이터를 worksheet 형태로 변환
      Xlsx.utils.book_append_sheet(workBook, workSheet, '시트이름') // sheet을 book에다 넣습니다. 이 때 sheet의 이름도 정합니다.
      Xlsx.writeFile(workBook, '파일이름.xlsx') // writeFile: 엑셀 파일을 다운로드
    }
  }
}
</script>

<style>
</style>