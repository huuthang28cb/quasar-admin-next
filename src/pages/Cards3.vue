<template>
  <q-page class="q-pa-sm">
    <div class="row q-col-gutter-md">
      <div class="col-lg-4 col-sm-12 col-md-4 col-xs-12">
        <q-card flat bordered>
          <q-card-section>
            <div class="text-subtitle1">Create an account</div>
            <div class="text-caption text-grey-8">Enter your email below to create your account</div>
          </q-card-section>

          <q-card-section class="q-py-none">
            <div class="row q-col-gutter-sm">
              <div class="col-6">
                <q-btn outline class="full-width " type="button" rounded>
                  <q-icon name="fab fa-github" class="on-left" />
                  <span class="block">Github</span>
                </q-btn>
              </div>
              <div class="col-6">
                <q-btn outline class="full-width" type="button" rounded>
                  <q-icon name="fab fa-google" class="on-left" />
                  <span class="block">Google</span>
                </q-btn>
              </div>
            </div>
          </q-card-section>

          <q-card-section class="q-py-none">
            <q-item class="full-width q-px-none">
              <q-item-section class="column">
                <div class="q-mb-sm text-grey-7">Email</div>
                <q-field outlined dense class="float-right">

                </q-field>
              </q-item-section>
            </q-item>
            <q-item class="full-width q-px-none">
              <q-item-section class="column">
                <div class="q-mb-sm text-grey-7">Password</div>
                <q-field outlined dense class="float-right">

                </q-field>
              </q-item-section>
            </q-item>
          </q-card-section>

          <q-card-section>
            <q-btn class="bg-dark text-white full-width " type="button">
              <span class="block">Create account</span>
            </q-btn>
          </q-card-section>

        </q-card>
        <q-card flat bordered class=" q-mt-md no-shadow">
          <q-card-section>
            <div class="text-subtitle1">Team Members</div>
            <div class="text-caption text-grey-8">Invite your team members to collaborate.</div>
          </q-card-section>

          <q-card-section class="q-pa-none">
            <q-list>
              <q-item v-for="(member, index) in members" :key="index" class="row no-wrap full-width q-py-none q-pr-none"
                clickable>
                <q-item-section avatar>
                  <q-avatar round>
                    <img :src="member.avatar" :alt="member.name" />
                  </q-avatar>
                </q-item-section>

                <q-item-section class="column justify-center">
                  <q-item-label>{{ member.name }}</q-item-label>
                  <q-item-label class="text-grey-7"
                    style="overflow: hidden; display: -webkit-box; -webkit-box-orient: vertical; -webkit-line-clamp: 2;">
                    {{ member.email }}
                  </q-item-label>
                </q-item-section>

                <q-item-section class="q-card__section--vert">
                  <q-btn class="bg-dark text-white text-capitalize" type="button">
                    <span class="items-center justify-center row no-wrap text-no-wrap">
                      <span class="block">{{ member.role }}</span>
                      <q-icon name="arrow_drop_down" />
                    </span>
                  </q-btn>
                </q-item-section>
              </q-item>
            </q-list>
          </q-card-section>

        </q-card>
        <q-card flat bordered class=" q-mt-md no-shadow">
          <q-card-section>
            <div class="text-subtitle1">Payment Method</div>
            <div class="text-caption text-grey-8">Add a new payment method to your account.</div>
          </q-card-section>

          <q-card-section class="q-py-none">
            <div class="row q-gutter-lg">
              <q-btn v-for="(method, index) in paymentMethods" :key="index" class="col-3 text-center"
                :icon="method.icon" :label="method.label" outline @click="handlePaymentMethodClick(method)" />
            </div>
          </q-card-section>

          <q-card-section class="q-py-none">
            <div class="q-item q-item-type row no-wrap full-width q-px-none">
              <q-item-section class="column q-item__section--main justify-center">
                <div class="q-item__label q-mb-sm text-grey-7">Name</div>
                <q-field outlined dense class="float-right">
                </q-field>
              </q-item-section>
            </div>

            <div class="q-item q-item-type row no-wrap full-width q-px-none">
              <q-item-section class="column q-item__section--main justify-center">
                <div class="q-item__label q-mb-sm text-grey-7">Card number</div>
                <q-field outlined dense class="float-right">
                </q-field>
              </q-item-section>
            </div>

            <div class="row q-col-gutter-sm">
              <q-item v-for="(field, index) in dateFields" :key="index" class="col-4">
                <q-item-section class="column q-item__section--main justify-center">
                  <div class="q-item__label q-mb-sm text-grey-7">{{ field.label }}</div>
                  <q-field outlined dense class="float-right">

                  </q-field>
                </q-item-section>
              </q-item>
            </div>

            <div class="col-4">
              <q-item class="q-item-type row no-wrap full-width q-px-none">
                <q-item-section class="column q-item__section--main justify-center">
                  <div class="q-item__label q-mb-sm text-grey-7">CSV</div>
                  <q-field outlined dense class="float-right">

                  </q-field>
                </q-item-section>
              </q-item>
            </div>
          </q-card-section>

          <q-card-section>
            <q-btn class="full-width " color="dark" text-color="white" label="Continue" @click="handleContinueClick" />
          </q-card-section>
        </q-card>
      </div>
      <div class="col-lg-4 col-sm-12 col-md-4 col-xs-12">
        <q-card flat bordered>
          <q-card-section>
            <div class="text-subtitle1">Notifications</div>
            <div class="text-caption text-grey-8">Choose what you want to be notified about.</div>
          </q-card-section>

          <q-card-section class="q-pa-none">
            <q-list>
              <q-item clickable class="full-width q-pb-none">
                <q-item-section avatar>
                  <q-icon name="notifications" class="q-mr-sm" style="font-size: 24px;" />
                </q-item-section>
                <q-item-section>
                  <q-item-label class="text-grey-7">Everything</q-item-label>
                  <q-item-label>
                    Email digest, mentions &amp; all activity.
                  </q-item-label>
                </q-item-section>
              </q-item>

              <q-item clickable class="full-width q-pb-none">
                <q-item-section avatar>
                  <q-icon name="alternate_email" class="q-mr-sm" style="font-size: 24px;" />
                </q-item-section>
                <q-item-section>
                  <q-item-label class="text-grey-7">Available</q-item-label>
                  <q-item-label>
                    Only mentions and comments.
                  </q-item-label>
                </q-item-section>
              </q-item>

              <q-item clickable>
                <q-item-section avatar>
                  <q-icon name="notifications_off" class="q-mr-sm" style="font-size: 24px;" />
                </q-item-section>
                <q-item-section>
                  <q-item-label class="text-grey-7">Ignoring</q-item-label>
                  <q-item-label>
                    Turn off all notifications.
                  </q-item-label>
                </q-item-section>
              </q-item>
            </q-list>
          </q-card-section>
        </q-card>
        <q-card flat bordered class=" q-mt-md">
          <q-card-section>
            <div class="text-subtitle1">Share this document</div>
            <div class="text-caption text-grey-8">Anyone with the link can view this document.</div>
          </q-card-section>

          <q-separator class="q-mx-md q-my-md" />

          <q-card-section class="q-pa-none">
            <q-list>
              <q-item clickable class="full-width q-py-none q-pr-none">
                <q-item-section avatar>
                  <q-avatar round>
                    <img src="https://cdn.quasar.dev/img/avatar.png" alt="avatar.png" />
                  </q-avatar>
                </q-item-section>
                <q-item-section>
                  <q-item-label>Olivia Martin</q-item-label>
                  <q-item-label class="text-grey-7">m@example.com</q-item-label>
                </q-item-section>
                <q-item-section class="q-card__section--vert">
                  <q-btn class="bg-dark text-white text-capitalize" type="button">
                    <span class="items-center justify-center row no-wrap text-no-wrap">
                      <span class="block">Can Edit</span>
                      <q-icon name="arrow_drop_down" />
                    </span>
                  </q-btn>
                </q-item-section>
              </q-item>

              <q-item clickable class="full-width q-py-none q-pr-none">
                <q-item-section avatar>
                  <q-avatar round>
                    <img src="https://cdn.quasar.dev/img/boy-avatar.png" alt="boy-avatar.png" />
                  </q-avatar>
                </q-item-section>
                <q-item-section>
                  <q-item-label>Isabella Nguyen</q-item-label>
                  <q-item-label class="text-grey-7">b@example.com</q-item-label>
                </q-item-section>
                <q-item-section class="q-card__section--vert">
                  <q-btn class="bg-dark text-white text-capitalize" type="button">
                    <span class="items-center justify-center row no-wrap text-no-wrap">
                      <span class="block">Can Edit</span>
                      <q-icon name="arrow_drop_down" />
                    </span>
                  </q-btn>
                </q-item-section>
              </q-item>

              <q-item clickable class="full-width q-py-none q-pr-none">
                <q-item-section avatar>
                  <q-avatar round>
                    <img src="https://cdn.quasar.dev/img/avatar3.jpg" alt="avatar3.jpg" />
                  </q-avatar>
                </q-item-section>
                <q-item-section>
                  <q-item-label>Sofia Davis</q-item-label>
                  <q-item-label class="text-grey-7">p@example.com</q-item-label>
                </q-item-section>
                <q-item-section class="q-card__section--vert">
                  <q-btn class="bg-dark text-white text-capitalize" type="button">
                    <span class="items-center justify-center row no-wrap text-no-wrap">
                      <span class="block">Can Edit</span>
                      <q-icon name="arrow_drop_down" />
                    </span>
                  </q-btn>
                </q-item-section>
              </q-item>
            </q-list>
          </q-card-section>
        </q-card>
      </div>
      <div class="col-lg-4 col-sm-12 col-md-4 col-xs-12">
        <q-card flat bordered>
          <q-card-section>
            <div class="text-subtitle1">Cookie Settings</div>
            <div class="text-caption text-grey-8">Manage your cookie settings here.</div>
          </q-card-section>

          <q-separator class="q-mx-md q-my-md" />

          <q-card-section class="q-pa-none">
            <q-list>
              <q-item clickable class="full-width q-py-none q-pr-none q-mx-md q-my-md">
                <q-item-section>
                  <q-item-label>Strictly Necessary</q-item-label>
                  <q-item-label class="text-grey-7">
                    These cookies are essential in order to use the website and use its features.
                  </q-item-label>
                </q-item-section>
                <q-item-section side>
                  <q-toggle v-model="strictlyNecessary" />
                </q-item-section>
              </q-item>

              <q-item clickable class="full-width q-py-none q-pr-none q-mx-md q-my-md">
                <q-item-section>
                  <q-item-label>Functional Cookies</q-item-label>
                  <q-item-label class="text-grey-7">
                    These cookies allow the website to provide personalized functionality.
                  </q-item-label>
                </q-item-section>
                <q-item-section side>
                  <q-toggle v-model="functionalCookies" />
                </q-item-section>
              </q-item>

              <q-item clickable class="full-width q-py-none q-pr-none q-mx-md q-my-md">
                <q-item-section>
                  <q-item-label>Performance Cookies</q-item-label>
                  <q-item-label class="text-grey-7">
                    These cookies help to improve the performance of the website.
                  </q-item-label>
                </q-item-section>
                <q-item-section side>
                  <q-toggle v-model="performanceCookies" />
                </q-item-section>
              </q-item>
            </q-list>
          </q-card-section>
        </q-card>
        <q-card flat bordered class=" q-mt-md">
          <q-card-section class="q-px-none">
            <q-item class="row no-wrap" role="listitem">
              <q-item-section class="column q-item__section--main justify-center">
                <div class="text-subtitle1">Quasar Minimalist Design</div>
                <div class="text-caption text-grey-8">
                  Beautifully designed components built with Quasar Framework.
                </div>
              </q-item-section>
              <q-item-section class="column q-item__section--side justify-center">
                <q-btn-group outline>
                  <q-btn class="bg-dark text-white q-btn--rectangle q-btn--actionable q-btn--no-uppercase" type="button"
                    aria-expanded="false">
                    <q-icon name="star" class="q-mr-xs" />
                    Star
                  </q-btn>
                  <q-btn-dropdown class="bg-dark text-white q-btn--rectangle q-btn--actionable" aria-haspopup="true"
                    aria-controls="dropdown-menu" aria-label="Expand 'Star'">
                    <q-icon name="arrow_drop_down" />
                  </q-btn-dropdown>
                </q-btn-group>
              </q-item-section>
            </q-item>
          </q-card-section>
          <q-card-actions class="justify-start q-card__actions--horiz row">
            <q-btn flat round class="q-btn--actionable" type="button" aria-label="Event">
              <q-icon name="event" />
            </q-btn>
            <q-btn flat class="q-btn--actionable q-btn--no-uppercase" type="button" aria-label="Updated April 2023">
              Updated April 2023
            </q-btn>
            <q-btn flat class="text-dark q-btn--actionable" type="button" aria-label="10k">
              10k
            </q-btn>
          </q-card-actions>
        </q-card>
        <q-card flat bordered class=" q-mt-md no-shadow">
          <q-card-section>
            <div class="text-subtitle1">Report an issue</div>
            <div class="text-caption text-grey-8">What area are you having problems with?</div>
          </q-card-section>

          <q-card-section class="q-py-none">
            <div class="row q-col-gutter-sm">
              <div class="col-6">
                <q-item class="row no-wrap full-width q-px-none" role="listitem">
                  <q-item-section class="column q-item__section--main justify-center">
                    <div class="q-item__label q-mb-sm text-grey-7">Area</div>
                    <q-select outlined dense class="float-right" hide-dropdown-icon options-dense
                      placeholder="Select area" aria-label="Select area" />
                  </q-item-section>
                </q-item>
              </div>

              <div class="col-6">
                <q-item class="row no-wrap full-width q-px-none" role="listitem">
                  <q-item-section class="column q-item__section--main justify-center">
                    <div class="q-item__label q-mb-sm text-grey-7">Security Level</div>
                    <q-select outlined dense class="float-right" hide-dropdown-icon options-dense
                      placeholder="Select security level" aria-label="Select security level" />
                  </q-item-section>
                </q-item>
              </div>
            </div>

            <q-item class="row no-wrap full-width q-px-none" role="listitem">
              <q-item-section class="column q-item__section--main justify-center">
                <div class="q-item__label q-mb-sm text-grey-7">Subject</div>
                <q-input outlined dense class="float-right" placeholder="I need help with..." aria-label="Subject" />
              </q-item-section>
            </q-item>

            <q-item class="row no-wrap full-width q-px-none" role="listitem">
              <q-item-section class="column q-item__section--main justify-center">
                <div class="q-item__label q-mb-sm text-grey-7">Description</div>
                <q-input outlined dense type="textarea" rows="2" class="float-right"
                  placeholder="Please include all information relevant to your issue" aria-label="Description" />
              </q-item-section>
            </q-item>
          </q-card-section>

          <q-card-section>
            <q-btn class="full-width bg-dark text-white q-btn--rectangle q-btn--no-uppercase " type="button"
              aria-label="Submit">
              <q-icon name="send" />
              <span class="q-mx-xs">Submit</span>
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
      strictlyNecessary: false,
      functionalCookies: false,
      performanceCookies: false,
      members: [
        {
          name: 'Sofia Davis',
          email: 'sofiadavis@example.com',
          avatar: 'https://cdn.quasar.dev/img/avatar.png',
          role: 'Member',
        },
        {
          name: 'Jackson Lee',
          email: 'jacksonlee@example.com',
          avatar: 'https://cdn.quasar.dev/img/boy-avatar.png',
          role: 'Owner',
        },
      ],
      paymentMethods: [
        {
          label: 'Card',
          icon: 'fa-solid fa-credit-card',
        },
        {
          label: 'Paypal',
          icon: 'fa-brands fa-paypal',
        },
        {
          label: 'Apple',
          icon: 'fa-brands fa-apple',
        },
      ],
      dateFields: [
        {
          label: 'Month',
          model: null,
          options: ['01', '02', '03', '04', '05', '06', '07', '08', '09', '10', '11', '12'],
        },
        {
          label: 'Year',
          model: null,
          options: ['2023', '2024', '2025', '2026'],
        },
      ],
    }
  },
})
</script>

<style scoped></style>
