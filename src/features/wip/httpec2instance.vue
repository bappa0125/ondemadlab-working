<template >

  <div class="my-2 text-center" >
        <v-btn small @click="getResult()">Full Result</v-btn>
   
 <v-data-table
    :headers="headers"
    :items="desserts"
    class="text-center mytable"
  >
  
  <template v-slot:items="props">
   
      <td class="text-xs-left pruple"> <v-btn small color="primary" @click="getResult_perStep(props.item.eventname)">{{ props.item.steps_performed}}</v-btn></td>
     
      <td class="text-xs-left">{{ props.item.description }}</td>
      <td class="text-xs-left">{{ props.item.difficulty }}</td>
      <td class="text-xs-left">{{ props.item.area }}</td>
    </template>
</v-data-table>
  </div>
  
</template>

<script>
import axios from 'axios'
export default {
  name: 'Wip',

  data () {

    
    return {
      loading: false,
        data_to_show:{},
        pass_or_fail: "dark",
     headers: [
          {
            text: 'Steps to be Perfromed',
            align: 'left',
            sortable: false,
            value: 'steps_performed',
          },
          { text: 'Description', value: 'description' },
          { text: 'Difficulty', value: 'difficulty' },
          { text: 'Area', value: 'area' },
        ],
        desserts: [
          {
            steps_performed: 'VPC Creation',
            description: 'User need to create VPC , this should not be the default VPC',
            difficulty: 'Moderate',
            area: 'Networking',
            eventname:'CreateVpc',
          
          },
           {
            steps_performed: 'Route Table Creation',
            description: 'User need to create 4 subnets, two public and two private',
            difficulty: 'Moderate',
            area: 'Networking',
             eventname:'CreateRouteTable',
          
          },
           {
            steps_performed: 'NAT Gateway Creation',
            description: 'User need to create NAT gatway and configure the routes ',
            difficulty: 'Moderate',
            area: 'Networking',
             eventname:'CreateNatGateway',
          
          },
           {
            steps_performed: 'Internet Gateway Creation',
            description: 'User need to create Internet Gateway and configure the routes',
            difficulty: 'Moderate',
            area: 'Networking',
            eventname:'CreateInternetGateway',
          },
           {
            steps_performed: 'Ec2 instace creation',
            description: 'User will launch the EC2 instance and install httpd there and configure http server ofer there and then configure thte security group',
            difficulty: 'Moderate',
            area: 'infrastructure',
            eventname:'CreateEc2Intance',
          
          },
        
          ],
    }
  },
methods: {
getResult_perStep(eventname){
 this.$emit("callsteps",eventname)
},
},
  mounted () {
  },

  /////end of method list  
   
  
}
</script>

<style lang="stylus" scoped>
>>>.mytable thead {
    background-color: #CE93;
    border-bottom: none !important;
 }
.my-wip

  &__hero
    opacity 0.4

  &__cone
    width 100px
    .custom-loader {
    animation: loader 1s infinite;
    display: flex;
  }
  @-moz-keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  @-webkit-keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  @-o-keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  @keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }

</style>
