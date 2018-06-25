<template lang="pug">
  .home
    .container
      .row.mb-3
        .col-12.d-flex
          h4.font-weight-bold.mr-auto OVERVIEW
          .lh2.mr-4
            span.text-secondary {{ dateInterval.start }} 
            i.fas.fa-caret-right.text-dark.mx-1
            span.text-secondary  {{ dateInterval.end }}
          .lh2
            span.text-secondary  {{ dateInterval.type }} 
            i.fas.fa-caret-down.text-dark.mx-1

      .row
        .col-md-4
          .card.summary-card
            .card-body.text-center
              h6.card-title
                span.h4.mr-1: i.fas.fa-hand-holding-usd
                | TOTAL REVENUE
              .number.text-success
                | 54,540
        .col-md-4
          .card.summary-card
            .card-body.text-center
              h6.card-title 
                span.h4.mr-1: i.fas.fa-boxes
                |  TOTAL COST
              .number.text-danger
                | 12,660
        .col-md-4
          .card.summary-card
            .card-body.text-center
              h6.card-title
                span.h4.mr-1: i.fas.fa-money-bill
                |  NET INCOME
              .number.text-primary
                | 41,880

      .row
        .col-12
          .card
            .card-body
              h4.card-title Activity
              #linechart_material

      .row
        .col-md-6
          .card
            .card-body
              h4.card-title Transaction Website
              table.table.transaction-website-table.mb-0
                tbody
                  tr
                    td.h1
                      i.fab.fa-facebook
                    td.text-secondary
                      | Facebook.com
                    td.h5 45,836
                    td
                      .text-success
                        i.fas.fa-arrow-up
                        |  20%
                  tr
                    td.h1
                      i.fab.fa-google
                    td.text-secondary
                      | google.com
                    td.h5 23,582
                    td
                      .text-success
                        i.fas.fa-arrow-up
                        |  12%
                  tr
                    td.h1
                      i.fab.fa-slack
                    td.text-secondary
                      | slack.com
                    td.h5 2,489
                    td
                      .text-danger
                        i.fas.fa-arrow-down
                        |  15%
                  tr
                    td.h1
                      i.fab.fa-wordpress
                    td.text-secondary
                      | wordpress.com
                    td.h5 1,057
                    td
                      .text-danger
                        i.fas.fa-arrow-down
                        |  30%
        .col-md-6
          .card
            .card-body
              h4.card-title Latest Order
              table.table.latest-order-table
                tbody
                  tr(v-for="i in 3")
                    td
                      img(src="https://fakeimg.pl/100/")
                    td
                      h4 Vintage T-shirt
                      .d-flex.justify-content-between
                        .text-secondary
                          i.fas.fa-clock
                          |  2018/6/13 13:42
                          br
                          i.fas.fa-male
                          |  Belle Willis
                        .text-right
                          small Total
                          br
                          strong.h5 3,200

</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "home",
  components: {
    HelloWorld
  },
  data() {
    return {
      dateInterval: {
        start: "2018/6/6",
        end: "2018/6/13",
        type: "Weekly"
      }
    };
  },
  mounted() {
    this.drawChart();
  },
  methods: {
    drawChart() {
      google.charts.load("current", { packages: ["line"] });
      google.charts.setOnLoadCallback(drawChart);

      function drawChart() {
        var data = new google.visualization.DataTable();
        data.addColumn("number", "Day");
        data.addColumn("number", "Guardians of the Galaxy");
        data.addColumn("number", "The Avengers");
        data.addColumn("number", "Transformers: Age of Extinction");

        data.addRows([
          [1, 37.8, 80.8, 41.8],
          [2, 30.9, 69.5, 32.4],
          [3, 25.4, 57, 25.7],
          [4, 11.7, 18.8, 10.5],
          [5, 11.9, 17.6, 10.4],
          [6, 8.8, 13.6, 7.7],
          [7, 7.6, 12.3, 9.6],
          [8, 12.3, 29.2, 10.6],
          [9, 16.9, 42.9, 14.8],
          [10, 12.8, 30.9, 11.6],
          [11, 5.3, 7.9, 4.7],
          [12, 6.6, 8.4, 5.2],
          [13, 4.8, 6.3, 3.6],
          [14, 4.2, 6.2, 3.4]
        ]);

        var options = {
          chart: {
            // title: "Box Office Earnings in First Two Weeks of Opening",
            // subtitle: "in millions of dollars (USD)"
          },
          width: 900,
          height: 500
        };

        var chart = new google.charts.Line(
          document.getElementById("linechart_material")
        );

        chart.draw(data, google.charts.Line.convertOptions(options));
      }
    }
  }
};
</script>

<style lang="scss" scoped>
.card {
  margin-bottom: 18px;
}
.summary-card .number {
  font-size: 2.25rem;
  font-weight: bold;
}
table {
  td {
    vertical-align: middle;
  }
  tr:first-child td {
    border-top: 0;
  }
  &.transaction-website-table {
    tr td:first-child {
      font-size: 45px;
    }
    tr {
      height: 92px;
    }
  }
  &.latest-order-table {
    tr td:first-child {
      padding: 8px 20px 8px 0;
      width: 116px;
    }
  }
}
</style>