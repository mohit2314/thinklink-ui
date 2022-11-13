<template>
  <div class="inventory__section">
    <div class="section__heading-row">Inventory</div>
    <div class="inventory__table">
      <b-table :responsive="true" selected-variant="light" ref="selectableTable" :items="items" :fields="fields" selectable select-mode="multi" @row-selected="onRowSelected" label-sort-asc="" label-sort-desc="" :no-sort-reset="false" :sort-by.sync="sortBy" :sort-desc.sync="sortDesc" :sort-direction="sortDirection" stacked="md" show-empty small @filtered="onFiltered">
        <!-- <template #cell(name)="row"> {{ row.value.first }} {{ row.value.last }} </template> -->
        <!-- Example scoped slot for select state illustrative purposes -->
        <template #cell(select)="{ rowSelected }" style="height: 100%">
          <!-- <template v-if="rowSelected"> -->
          <div style="margin-top: 12px">
            <b-form-checkbox id="checkbox-1" style="accent-color: #ef4859" v-model="rowSelected" name="checkbox-1" value="true" unchecked-value="false"> </b-form-checkbox>
          </div>
          <!-- </template> -->
        </template>
        <template v-slot:cell(foto)="row">
          <div class="d-flex">
            <img width="48" height="48" class="img-fluid img-thumbnail" :src="require(`@/assets/${row.item.foto}.png`)" alt="..." />
            <div class="d-flex flex-column" style="margin-left: 8px">
              <div style="color: #262730; font-size: 16px; font-weight: 600">{{ row.item.name }}</div>

              <div style="color: #8c8ca1; font-size: 14px">{{ row.item.origin }}</div>
            </div>
          </div>
        </template>
        <!-- Rating -->
        <template #cell(rating)="row">
          <div class="d-flex">
            <div class="rating__tag">
              <p>{{ row.item.rating.code }}</p>
            </div>
            <div class="rating__tag">
              <p>{{ row.item.rating.value }}</p>
            </div>
          </div>
        </template>
        <!-- Vintage -->
        <template #cell(vintage)="row">
          <span class="col__common-style">{{ row.item.vintage }}</span>
        </template>
        <!-- Qty -->
        <template #cell(qty)="row">
          <span class="col__common-style">{{ row.item.qty }}</span>
        </template>
        <!-- Volume -->
        <template #cell(volume)="row">
          <span class="col__common-style"> {{ row.item.volume }}</span>
        </template>
        <!-- Cost -->
        <template #cell(cost)="row">
          <span class="col__common-style"> {{ row.item.cost }}</span>
        </template>
        <!-- Price -->
        <template #cell(price)="row">
          <span class="col__common-style price__style"> {{ row.item.price }}</span>
        </template>

        <template #cell(actions)="row">
          <b-icon v-if="!row.detailsShowing" icon="chevron-down" @click.stop="row.toggleDetails"></b-icon>
          <b-icon v-else icon="chevron-up" @click.stop="row.toggleDetails"></b-icon>

          <!-- <b-button size="sm" @click="row.toggleDetails"> {{ row.detailsShowing ? 'Hide' : 'Show' }} Details </b-button> -->
        </template>

        <template #row-details="row">
          <b-card>
            <div class="detailed__card-header">
              <div class="left__section">
                <div class="title">{{ row.item.name }}</div>
                <div class="d-flex">
                  <span class="region" style="margin-right: 42px"
                    ><p class="title" style="margin-right: 4px">Region:</p>
                    {{ row.item.origin }}</span
                  >
                  <span class="vintage"
                    ><p class="title" style="margin-right: 4px">Vintage :</p>
                    {{ row.item.vintage }}</span
                  >
                </div>
              </div>
              <div class="right__section">
                <a class="view__link" style="color: #ef4859; font-weight: 700">View wine</a>
                <span><b-icon icon="pencil-square"></b-icon></span>
                <span><b-icon icon="bag" style="color: #dadadb"></b-icon></span>
              </div>
            </div>
            <div class="details__section">
              <div class="rating__section">
                <div class="heading">Rating</div>
                <div class="rating__list">
                  <div class="list__item" v-for="(item, i) in ratingList" :key="i">
                    <span class="user">{{ item.user }}</span>
                    <span class="rating">{{ item.rating }}</span>
                  </div>
                </div>
              </div>
              <div class="stock__section">
                <div class="heading">Stock</div>
                <div class="stocks__list">
                  <div class="list__item" v-for="(item, i) in stockList" :key="i">
                    <span class="item">{{ item.item }}</span>
                    <span class="unit">{{ item.unit }}</span>
                  </div>
                </div>
              </div>
            </div>
            <!-- <ul>
              <li v-for="(value, key) in row.item" :key="key">{{ key }}: {{ value }}</li>
            </ul> -->
          </b-card>
        </template>
      </b-table>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        // { isActive: true, age: 40, name: { first: 'Dickerson', last: 'Macdonald' } },
        // { isActive: false, age: 21, name: { first: 'Larsen', last: 'Shaw' } },
        // {
        //   isActive: false,
        //   age: 9,
        //   name: { first: 'Mini', last: 'Navarro' },
        //   _rowVariant: 'success',
        // },
        // { isActive: false, age: 89, name: { first: 'Geneva', last: 'Wilson' } },
        // { isActive: true, age: 38, name: { first: 'Jami', last: 'Carney' } },
        // { isActive: false, age: 27, name: { first: 'Essie', last: 'Dunlap' } },
        // { isActive: true, age: 40, name: { first: 'Thor', last: 'Macdonald' } },
        // {
        //   isActive: true,
        //   age: 87,
        //   name: { first: 'Larsen', last: 'Shaw' },
        //   _cellVariants: { age: 'danger', isActive: 'warning' },
        // },
        // { isActive: false, age: 26, name: { first: 'Mitzi', last: 'Navarro' } },
        // { isActive: false, age: 22, name: { first: 'Genevieve', last: 'Wilson' } },
        // { isActive: true, age: 38, name: { first: 'John', last: 'Carney' } },
        // { isActive: false, age: 29, name: { first: 'Dick', last: 'Dunlap' } },
        // --
        // { isActive: false, product: 'Staglin Family Vineyard...', name: { first: 'Dick', last: 'Dunlap' } },
        { id: 1, name: 'Staglin Family Vineyard...', foto: 'inv1', origin: 'France · Sauternes ', rating: { code: 'RP 95', value: '+3' }, vintage: "1950's", qty: '04', volume: 'Standard (750 mL)', cost: '$56.95', price: '$59.95' },
        { id: 2, name: 'Bibi Graetz Testamatta Tos...', foto: 'inv2', origin: 'Chianti · Blends and Other', rating: { code: 'RP 95', value: '+3' }, vintage: '2015', qty: '32', volume: 'Magnum (1500 mL)', cost: '$71.95', price: '$72.95' },
        { id: 3, name: 'Cayuse Syrah en Chamber...', foto: 'inv3', origin: 'Syrah', rating: { code: 'RP 95', value: '+3' }, vintage: '2012', qty: '12', volume: 'Standard (750 mL)', cost: '$139.95', price: '$150.00' },
        // ---row details
        { id: 4, name: 'Staglin Family Vineyard...', foto: 'inv4', origin: 'United States · California · Blends', rating: { code: 'RP 95', value: '+3' }, vintage: '2010', qty: '04', volume: 'Odd Ball (5000 mL)', cost: '$56.95', price: '$59.95' },
        //  ---
        { id: 5, name: 'K Vintners Syrah Cattle king', foto: 'inv5', origin: 'France · Sauternes', rating: { code: 'RP 95', value: '+3' }, vintage: '2015', qty: '25', volume: 'Magnum (1500 mL)', cost: '$79.95', price: '$92.95' },
        { id: 6, name: "L'Ecole No. 41 Ferguson", foto: 'inv6', origin: 'United state · Celifornia · Blends', rating: { code: 'RP 95', value: '+3' }, vintage: '2004', qty: '04', volume: 'Odd Ball (5000 mL)', cost: '$54.95', price: '$59.95' },
        { id: 7, name: 'Staglin Family Vineyard...', foto: 'inv2', origin: 'France · Sauternes', rating: { code: 'RP 95', value: '+3' }, vintage: "1950's", qty: '22', volume: 'Regular (750 mL)', cost: '$56.95', price: '$59.95' },
      ],
      fields: [
        // { key: 'product', label: 'PRODUCT' },

        { key: 'select', label: '', class: 'text-center' },
        { key: 'foto', label: 'Product', sortable: false },
        { key: 'rating', label: 'RATING', sortable: true, class: 'text-center' },
        { key: 'vintage', label: 'VINTAGE', sortable: true, class: 'text-center' },
        { key: 'qty', label: 'QTY', sortable: true, class: 'text-center' },
        { key: 'volume', label: 'VOLUME', sortable: true, class: 'text-center' },
        { key: 'cost', label: 'COST', sortable: true, class: 'text-center' },
        { key: 'price', label: 'PRICE', sortable: true, class: 'text-center' },
        // {
        //   key: 'isActive',
        //   label: 'Is Active',
        //   formatter: (value, key, item) => {
        //     return value ? 'Yes' : 'No';
        //   },
        //   sortable: true,
        //   sortByFormatted: true,
        //   filterByFormatted: true,
        // },
        { key: 'actions', label: '' },
      ],
      totalRows: 1,
      currentPage: 1,
      perPage: 5,
      pageOptions: [5, 10, 15, { value: 100, text: 'Show a lot' }],
      sortBy: '',
      sortDesc: false,
      sortDirection: 'asc',
      filter: null,
      filterOn: [],
      infoModal: {
        id: 'info-modal',
        title: '',
        content: '',
      },

      ratingList: [
        { user: "James Suckling's", rating: 'JS 95' },
        { user: 'Robert Parker', rating: 'RP 80' },
        { user: 'Antonio Galloni’s', rating: '---' },
        { user: 'Wine Spectator Tasting', rating: 'WS 79' },
      ],
      stockList: [
        { item: 'Possimus', unit: '43 units' },
        { item: 'Downtown Condo', unit: '95 units' },
      ],
    };
  },
  computed: {
    sortOptions() {
      // Create an options list from our fields
      return this.fields
        .filter(f => f.sortable)
        .map(f => {
          return { text: f.label, value: f.key };
        });
    },
  },
  mounted() {
    // Set the initial number of items
    this.totalRows = this.items.length;
    this.$refs.selectableTable.selectRow(1);
    this.$refs.selectableTable.selectRow(2);
    this.$refs.selectableTable.toggleDetailsFactory('row-details', 2);
    console.log(this.$refs.selectableTable);
  },
  methods: {
    info(item, index, button) {
      this.infoModal.title = `Row index: ${index}`;
      this.infoModal.content = JSON.stringify(item, null, 2);
      this.$root.$emit('bv::show::modal', this.infoModal.id, button);
    },
    onRowSelected(items) {
      this.selected = items;
    },
    resetInfoModal() {
      this.infoModal.title = '';
      this.infoModal.content = '';
    },
    onFiltered(filteredItems) {
      // Trigger pagination to update the number of buttons/pages due to filtering
      this.totalRows = filteredItems.length;
      this.currentPage = 1;
    },
  },
};
</script>

<style lang="scss">
.section__heading-row {
  font-weight: 700;
  font-size: 16px;
  line-height: 24px;
  /* identical to box height, or 150% */

  /* Dark color */

  color: #262730;
  margin: 24px 0 16px 0;
}

.inventory__table {
  border-top: 1px solid #dedede;
  .rating__tag {
    background: #f4f7ff;
    border-radius: 4px;
    width: 52px;
    max-height: 20px;
    // display: flex;
    // align-items: center;
    // justify-content: center;
    margin: 8px;
    p {
      color: #485572;
      font-size: 14px;
      font-weight: 600;
    }
  }
  .col__common-style {
    color: #8c8ca1;
    font-weight: 600;
  }
  .price__style {
    color: #262730;
  }
  .detailed__card-header {
    display: flex;
    justify-content: space-between;
    border-bottom: 1px solid #dedede;
    .left__section {
      display: flex;
      flex-direction: column;
      .title {
        color: #262730;
        font-size: 14px;
        font-weight: 600;
      }
      .region,
      .vintage {
        color: #8c8ca1;
        font-size: 14px;
        font-weight: 600;
        display: flex;
      }
    }
    .right__section {
      display: flex;
      gap: 12px;
    }
  }
  .details__section {
    display: flex;
    width: 100%;
    .heading {
      font-weight: 700;
      font-size: 12px;
      line-height: 16px;
      /* identical to box height, or 133% */

      letter-spacing: 0.06em;
      text-transform: uppercase;

      /* Subtle Text color */

      color: #8c8ca1;
      margin: 12px 0;
    }
    .rating__section {
      width: 50%;
      .rating__list {
        display: flex;
        flex-wrap: wrap;
        gap: 20px;
      }
    }
    .stock__section {
      width: 50%;
      .stocks__list {
        display: flex;
        flex-wrap: wrap;
        gap: 20px;
      }
    }
    .list__item {
      display: flex;
      flex-direction: column;
      width: 30%;
      .user,
      .item {
        font-family: 'Open Sans';
        font-style: normal;
        font-weight: 600;
        font-size: 14px;
        line-height: 20px;
        /* identical to box height, or 143% */

        /* Dark color */

        color: #262730;
      }
      .rating {
        background: #f4f7ff;
        border-radius: 4px;
        font-family: 'Open Sans';
        font-style: normal;
        font-weight: 600;
        font-size: 14px;
        line-height: 16px;
        /* identical to box height, or 114% */

        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        padding: 4px 7px;
        width: 64px;
        /* Body Text color */

        color: #485572;
      }
      .unit {
        background: #fff2ee;
        border-radius: 4px;
        font-family: 'Open Sans';
        font-style: normal;
        font-weight: 600;
        font-size: 14px;
        line-height: 16px;
        /* identical to box height, or 114% */

        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        padding: 4px 7px;
        width: 64px;
        /* Body Text color */
        font-weight: 600;
        font-size: 14px;
        line-height: 20px;
        /* identical to box height, or 143% */

        text-align: center;

        /* Primary color */

        color: #811434;
      }
    }
  }
}
</style>
