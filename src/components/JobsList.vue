<template>
    <div class="job-list">
        <p>Order by {{ order }}</p>
        <transition-group name="list" tag="ul">
            <li v-for="job in orderJobs" :key="job.id">
                <h1>{{  job.title}} in {{  job.location}}</h1>
                <div class="salary">
                    <p>{{  job.salary}} rupees</p>
                </div>
                <div class="description">
                    Lorem ipsum dolor sit amet, consectetur adipisicing elit. Velit eum fugit consequuntur veritatis reiciendis assumenda nisi. Culpa commodi eveniet voluptas tempore officiis, sed, debitis veniam maxime vero corporis eius sequi?
                </div>
            </li>
        </transition-group>

    </div>
</template>

<script lang="ts">
import { computed, defineComponent,PropType } from 'vue'
import job from '@/types/job';
import OrderTerm from '@/types/orderTerm';
export default defineComponent({
    props: {
       jobs: {
        required: true,
        type: Array as PropType<job[]>

        },
        order: {
            required: true,
            type: String as PropType<OrderTerm>
        }
    },
    setup (props) {
        
        const orderJobs = computed(() => {
            return [...props.jobs].sort((a: job,b: job) => {
                return a[props.order] > b[props.order] ? 1 : -1
            })
        })

        return {orderJobs}
    }   
})
</script>

<style scoped>
.list-move {
  transition: all 1s;
}
 .job-list {
    max-width: 960px;
    margin: 40px auto;
  }
  .job-list ul {
    padding: 0
  }
  .job-list li {
    list-style-type: none;
    background: white;
    padding: 16px;
    margin: 16px 0;
    border-radius: 4px;
  }
  .job-list h2 {
    margin: 0 0 10px;
    text-transform: capitalize;
  }
  .salary {
    display: flex;
  }
  .salary img {
    width: 30px;
  }
  .salary p {
    color: #17bf66;
    font-weight: bold;
    margin: 10px 4px;
  }
</style>