<template>
  <q-page class="q-pa-sm">
    <div class="row q-col-gutter-md">
      <div class="col-lg-8 col-md-8 col-xs-12 col-xs-12">
        <div class="row q-col-gutter-md">
          <div class="col-lg-6 col-md-6 col-xs-12 col-xs-12">
            <q-card class="col-lg-6 col-md-6 col-xs-12 no-shadow card_style fit">
              <q-card-section>
                <div class="text-h6 text-weight-bold">Your Orders</div>
                <div class="text-caption text-grey-8">
                  Introducing Our Dynamic Orders Dashboard for Seamless Management and Insightful Analysis.
                </div>
                <q-btn class="q-mt-lg" color="dark" text-white>
                  Create New Order
                </q-btn>
              </q-card-section>
            </q-card>
          </div>
          <div class="col-lg-3 col-md-3 col-xs-12 col-xs-12">
            <q-card class="col-lg-3 col-md-3 col-xs-12 no-shadow card_style fit">
              <q-card-section>
                <q-item clickable tag="label">
                  <q-item-section>
                    <q-item-label>This Week</q-item-label>
                    <q-item-label class="text-h6 text-weight-bolder" text-black>$1329</q-item-label>
                    <q-item-label class="text-grey-7">+25% from last week</q-item-label>
                    <q-linear-progress value="0.25" size="15px" color="black" rounded class="q-mt-lg" />
                  </q-item-section>
                </q-item>
              </q-card-section>
            </q-card>
          </div>
          <div class="col-lg-3 col-md-3 col-xs-12 col-xs-12">
            <q-card class="col-lg-3 col-md-3 col-xs-12 no-shadow card_style fit">
              <q-card-section>
                <q-item clickable tag="label">
                  <q-item-section>
                    <q-item-label>This Month</q-item-label>
                    <q-item-label class="text-h6 text-weight-bolder" text-black>$1329</q-item-label>
                    <q-item-label class="text-grey-7">+10% from last month</q-item-label>
                    <q-linear-progress value="0.5" size="15px" color="black" rounded class="q-mt-lg" />
                  </q-item-section>
                </q-item>
              </q-card-section>
            </q-card>
          </div>
          <div class="col-lg-12 col-md-12 col-xs-12 col-sm-12">
            <q-card bordered class="no-shadow card_style fit">
              <q-card-section>
                <div class="text-h6 text-weight-bold">Orders</div>
                <div class="text-caption text-grey-8">Recent orders from your store.</div>
              </q-card-section>
              <q-card-section class="q-pa-none q-ma-none overflow-hidden">
                <q-table :rows="orders" :columns="columns" hide-default-footer>
                  <template v-slot:body="props">
                    <q-tr :props="props" @click="onRowClick(props.row)">
                      <q-td key="customer" :props="props">
                        {{ props.row.customer }}
                      </q-td>
                      <q-td key="type" :props="props">
                        {{ props.row.type }}
                      </q-td>
                      <q-td key="status" :props="props">
                        <q-chip clickable :color="props.row.statusColor" text-color="white" :label="props.row.status" />
                      </q-td>
                      <q-td key="date" :props="props">
                        {{ props.row.date }}
                      </q-td>
                      <q-td key="amount" :props="props">
                        {{ props.row.amount }}
                      </q-td>
                    </q-tr>
                  </template>
                </q-table>
              </q-card-section>
            </q-card>
          </div>
        </div>
      </div>
      <div class="col-lg-4 col-md-4 col-xs-12 col-xs-12">
        <q-card class="no-shadow card_style fit">
          <q-card-section>
            <div class="text-h6 text-weight-bold">Order ID: Oe31b70H</div>
            <div class="text-caption text-grey-8">Date: November 23, 2023</div>
          </q-card-section>

          <q-card-section class="q-pt-none">
            <div class="text-body1 text-weight-bold">Order Details</div>
            <q-item dense>
              <q-item-section class="text-grey-8">Glimmer Lamps x 2</q-item-section>
              <q-item-section side class="text-grey-8">$250.00</q-item-section>
            </q-item>
            <q-item dense>
              <q-item-section class="text-grey-8">Aqua Filters x 1</q-item-section>
              <q-item-section side class="text-grey-8">$49.00</q-item-section>
            </q-item>
          </q-card-section>

          <q-separator spaced />

          <q-card-section>
            <div class="text-body1 text-weight-bold">Order Summary</div>
            <q-item dense>
              <q-item-section class="text-grey-8">Subtotal</q-item-section>
              <q-item-section side class="text-grey-8">$299.00</q-item-section>
            </q-item>
            <q-item dense>
              <q-item-section class="text-grey-8">Shipping</q-item-section>
              <q-item-section side class="text-grey-8">$5.00</q-item-section>
            </q-item>
            <q-item dense>
              <q-item-section class="text-grey-8">Tax</q-item-section>
              <q-item-section side class="text-grey-8">$25.00</q-item-section>
            </q-item>
            <q-item dense>
              <q-item-section class="text-grey-8">Total</q-item-section>
              <q-item-section side class="text-black text-weight-bold">$329.00</q-item-section>
            </q-item>
          </q-card-section>

          <q-separator spaced />

          <q-card-section>
            <div class="text-body1 text-weight-bold">Customer Information</div>
            <q-item dense>
              <q-item-section class="text-grey-8">Customer</q-item-section>
              <q-item-section side class="text-grey-8">Liam Johnson</q-item-section>
            </q-item>
            <q-item dense>
              <q-item-section class="text-grey-8">Email</q-item-section>
              <q-item-section side class="text-grey-8">liam@test.com</q-item-section>
            </q-item>
            <q-item dense>
              <q-item-section class="text-grey-8">Phone</q-item-section>
              <q-item-section side class="text-grey-8">+1 234 567 890</q-item-section>
            </q-item>
          </q-card-section>

          <q-separator spaced />

          <q-card-section>
            <div class="text-body1 text-weight-bold">Payment Information</div>
            <q-item dense>
              <q-item-section class="text-grey-8">
                <div>
                  <q-icon name="fa-solid fa-credit-card" class="q-mr-sm text-black" size="12px" />
                  Visa
                </div>
              </q-item-section>
              <q-item-section side class="text-grey-8">**** **** **** 4532</q-item-section>
            </q-item>
          </q-card-section>

          <q-card-section class="q-pa-md">
            <q-btn outline color="dark" class="card_style full-width" rounded>
              <q-icon left name="las la-print" />
              Print Invoice
            </q-btn>
          </q-card-section>
        </q-card>
      </div>
    </div>
  </q-page>
</template>

<script>
import { defineComponent, defineAsyncComponent } from 'vue'

export default defineComponent({
  name: "Cards",
  components: {},
  setup() {
    return {
      columns: [
        { name: 'customer', align: 'left', label: 'Customer', field: 'customer', sortable: true },
        { name: 'type', align: 'left', label: 'Type', field: 'type', sortable: true },
        { name: 'status', align: 'center', label: 'Status', field: 'status', sortable: true },
        { name: 'date', align: 'center', label: 'Date', field: 'date', sortable: true },
        { name: 'amount', align: 'right', label: 'Amount', field: 'amount', sortable: true }
      ],
      orders: [
        { customer: 'Liam Johnson', email: 'liam@example.com', type: 'Sale', status: 'Fulfilled', statusColor: 'teal', date: '2023-06-23', amount: '$250.00' },
        { customer: 'Olivia Smith', email: 'olivia@example.com', type: 'Refund', status: 'Declined', statusColor: 'red', date: '2023-06-24', amount: '$150.00' },
        { customer: 'Noah Williams', email: 'noah@example.com', type: 'Subscription', status: 'Fulfilled', statusColor: 'teal', date: '2023-06-25', amount: '$350.00' },
        { customer: 'Emma Brown', email: 'emma@example.com', type: 'Sale', status: 'Fulfilled', statusColor: 'teal', date: '2023-06-26', amount: '$450.00' },
        { customer: 'Liam Johnson', email: 'liam@example.com', type: 'Sale', status: 'Fulfilled', statusColor: 'teal', date: '2023-06-23', amount: '$250.00' },
        { customer: 'Olivia Smith', email: 'olivia@example.com', type: 'Refund', status: 'Declined', statusColor: 'red', date: '2023-06-24', amount: '$150.00' }
      ]
    }
  },
})
</script>

<style scoped></style>
