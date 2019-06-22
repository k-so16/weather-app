<template>
  <div>
    <!-- 地域を指定するメニュー -->
    <table class="area-selector">
      <tr>
        <td>都道府県</td>
        <td>
          <!-- 都道府県の選択肢が出るように属性を埋める -->
          <select>
            <option>
              <!-- 都道府県名を出力 -->
            </option>
          </select>
        </td>
      </tr>

      <!-- 都道府県が選択されたら表示する -->
      <tr>
        <td>地域</td>
          <!-- 地域の選択肢が出るように属性を埋める -->
        <td>
          <select>
            <option>
              <!-- 地域名を出力 -->
            </option>
          </select>
        </td>
      </tr>
    </table>

    <!-- 選択された地域の天気予報 -->
    <table class="forecast">
      <thead>
        <tr>
          <th>予報日</th>
          <th>天気</th>
          <th>最高気温</th>
          <th>最低気温</th>
        </tr>
      </thead>

      <tbody>
        <!-- 数日の天気予報のデータを出力するように属性を埋める -->
        <tr>
          <td>
            <!-- 日付を出力 -->
          </td>
          <td>
            <!-- 天気予報を出力 -->
            <figure>
              <!-- 画像が表示されるように属性を埋める -->
              <img>
              <figcaption>
                <!-- 文字の予報を出力 -->
              </figcaption>
            </figure>
          </td>
          <td>
            <!-- 最高気温を出力 -->
          </td>
          <td>
            <!-- 最低気温を出力 -->
          </td>
        </tr>
      </tbody>
    </table>
 </div>
</template>

<script>
import request from 'request-promise'

export default {
  props: [ /* 埋める */ ],

  data() {
    return {
      prefIndex: null,
      cityId: null,
      forecasts: [],
    }
  },

  watch: {
    cityId() {
      if (this.cityId === null) return

      request(`http://weather.livedoor.com/forecast/webservice/json/v1?city=${this.cityId}`)
        .then(body => {
          this.forecasts = JSON.parse(body).forecasts
        })
        .catch(err => {
          alert('データの取得に失敗しました')
          console.error(err)
        })
    },
  },
}
</script>

<style scoped>
/* お好みソースで召し上がれ */

table {
  margin: auto;
}

.forecast, .forecast th, .forecast td {
  border: solid 1px #888888;
  border-collapse: collapse;
}

.forecast th, .forecast td {
  text-align: center;
}
</style>
