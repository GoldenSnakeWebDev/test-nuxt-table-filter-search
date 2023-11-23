<!-- Please remove this file from your project -->
    <template>
        <div>
            <HeaderBar/>
            <div class="min-w-max min-h-screen lg:px-[5px] xl:px-[calc(100%/7)] xl:flex-wrap pt-[70px] pb-[400px] bg-[#F9F9F9] gap-6">
                <div class="flex gap-8 justify-between">
                        <order-card v-for="(data, index) in order_card_data" :key="index" :order_img_url="data.order_icon_url" :order_value="data.order_value" :title="data.title" :icon_color1="data.icon_color1" :icon_color2="data.icon_color2"/>
                </div>

                <div class="bg-white flex gap-1 items-center mt-9 p-2 rounded-lg shadow-custom">
                    <ul class="flex">
                        <li class="flex px-6 py-3 justify-center items-center">
                            <img :src="home_icon_url" alt="home"/>
                        </li>
                        <li class=" rounded-lg flex px-6 py-3 hover:bg-[#007FFF] justify-center items-center text-black font-Poppins text-sm font-medium">
                            <p>Orders</p>
                        </li>

                        <li class=" rounded-lg flex px-6 py-3 hover:bg-[#007FFF] justify-center items-center text-black font-Poppins text-sm font-medium">
                            <p>Favorites</p>
                        </li>

                        <li class=" rounded-lg flex px-6 py-3 hover:bg-[#007FFF] justify-center items-center text-black font-Poppins text-sm font-medium">
                            <p class="mr-4">Messages</p> <div class="w-5 h-5 bg-[#EBEBEB] rounded-full flex justify-center items-center"><p class="text-grey" v-if="messages>0">{{ messages }}</p></div>
                        </li>

                        <li class=" rounded-lg flex px-6 py-3 hover:bg-[#007FFF] justify-center items-center text-black font-Poppins text-sm font-medium">
                            <p>Organization</p>
                        </li>

                        <li class=" rounded-lg flex px-6 py-3 hover:bg-[#007FFF] justify-center items-center text-black font-Poppins text-sm font-medium">
                            <p class="mr-4">Users</p> <div class="w-5 h-5 bg-[#EBEBEB] rounded-full flex justify-center items-center"><p class="text-grey" v-if="users>0">{{ users }}</p></div>
                        </li>

                        <li class=" rounded-lg flex px-6 py-3 hover:bg-[#007FFF] justify-center items-center text-black font-Poppins text-sm font-medium">
                            <p>Shipping</p>
                        </li>

                        <li class=" rounded-lg flex px-6 py-3 hover:bg-[#007FFF] justify-center items-center text-black font-Poppins text-sm font-medium">
                            <p>Billing</p>
                        </li>

                        <li class=" rounded-lg flex px-6 py-3 hover:bg-[#007FFF] justify-center items-center text-black font-Poppins text-sm font-medium">
                            <p>Transaction History</p>
                        </li>

                        <li class=" rounded-lg flex px-6 py-3 hover:bg-[#007FFF] justify-center items-center text-black font-Poppins text-sm font-medium">
                            <p class="mr-4">Docs</p> <div class="w-5 h-5 bg-[#EBEBEB] rounded-full flex justify-center items-center"><p class="text-grey" v-if="docs>0">{{ docs }}</p></div>
                        </li>

                        <li class=" rounded-lg flex px-6 py-3 hover:bg-[#007FFF] justify-center items-center text-black font-Poppins text-sm font-medium">
                            <p>Settings</p>
                        </li>
                    </ul>
                </div>

                <div class="w-full flex gap-6 mt-8">
                    <!-- customer infromaition -->
                    <div class=" w-[calc((100%-24px)/2)] bg-white flex flex-col justify-center items-start p-6 rounded-xl">
                        <div class="flex flex-col gap-8 justify-center items-start self-stretch">
                            <div class="flex gap-8 items-center self-stretch">
                                <p class="w-full text-black font-Poppins font-semibold text-xl">Customer Information</p>
                                <img src="/img/more-vertical.svg" alt="more"/>
                            </div>

                            <div class="flex items-center gap-4 self-stretch">
                                <div class="w-16 h-16 flex justify-center items-center">
                                    <img :src="avatar" alt="avatar"/>
                                </div>
                                <div class="w-full flex flex-col gap-2">
                                    <div class="flex justify-between items-center self-stretch">
                                        <div class="flex items-center gap-3">
                                            <p class="text-grey font-Poppins font-semibold text-base">{{ first_name }} {{ surname }}</p>
                                            <img v-if="account_locked" src="/img/lock 01.svg" alt="lock"/>
                                            <img v-else src="/img/lock 02.svg" alt="unlock"/>
                                        </div>
                                        <div class="flex gap-2">
                                            <p class="text-grey font-Poppins text-sm font-normal">Last Active: </p>
                                            <p class="text-black font-Poppins text-sm font-medium">{{last_active}}</p>
                                        </div>
                                    </div>
                                    <div class="flex justify-between items-center self-stretch">
                                        <div class="flex gap-2">
                                            <p class="text-grey font-Poppins text-sm font-normal">Account Type: </p>
                                            <p class="text-black font-Poppins text-sm font-medium">{{account_type}}</p>
                                        </div>
                                        <p class="text-[#007FFF] font-Poppins text-sm font-medium">Nezo Global Development s.r.l.</p>
                                    </div>
                                </div>

                            </div>

                            <div class="flex flex-col gap-4 items-start pt-2 self-stretch">
                                <div class="flex items-center gap-3">
                                    <p class="text-grey font-Poppins text-sm font-semibold">Account Details</p>
                                    <div class="w-[44px] h-5 flex px-2 items-center gap-2.5 rounded-[50px] border-solid border border-[#007FFF]">
                                        <p class=" font-Poppins text-[#007FFF] text-center text-xs font-semibold">{{ account_detail }}</p>
                                    </div>
                                </div>
                                
                                <div class="w-full flex flex-col">
                                    <div class="w-full flex gap-3">
                                        <div class="w-[calc((100%-12px)/10*3)] font-Poppins font-normal text-sm text-grey">User Name</div>
                                        <div class="w-[calc((100%-12px)*7/10)] font-Poppins font-medium text-sm text-black">{{ username }}</div>
                                    </div>

                                    <div class="w-full flex gap-3">
                                        <div class="w-[calc((100%-12px)*3/10)] font-Poppins font-normal text-sm text-grey">Name</div>
                                        <div class="w-[calc((100%-12px)*7/10)] font-Poppins font-medium text-sm text-black">{{ first_name }}</div>
                                    </div>

                                    <div class="w-full flex gap-3">
                                        <div class="w-[calc((100%-12px)*3/10)] font-Poppins font-normal text-sm text-grey">Surname</div>
                                        <div class="w-[calc((100%-12px)*7/10)] font-Poppins font-medium text-sm text-black">{{ surname }}</div>
                                    </div>

                                    <div class="w-full flex gap-3">
                                        <div class="w-[calc((100%-12px)*3/10)] font-Poppins font-normal text-sm text-grey">Country</div>
                                        <div class="w-[calc((100%-12px)*7/10)] flex gap-2">
                                            <div class=" justify-start">
                                                <img :src="country_flag" alt="country flag"/>
                                            </div>
                                            <div class="font-Poppins font-medium text-sm text-black">{{ country }}</div>
                                            
                                        </div>
                                    </div>

                                    <div class="w-full flex gap-3">
                                        <div class="w-[calc((100%-12px)*3/10)] font-Poppins font-normal text-sm text-grey">Mobile Number</div>
                                        <div class="w-[calc((100%-12px)*7/10)] font-Poppins font-medium text-sm text-black">{{ mobile_number }}</div>
                                    </div>

                                    <div class="w-full flex gap-3">
                                        <div class="w-[calc((100%-12px)*3/10)] font-Poppins font-normal text-sm text-grey">Address</div>
                                        <div class="w-[calc((100%-12px)*7/10)] font-Poppins font-medium text-sm text-black">{{ address }}</div>
                                    </div>
                                </div>

                            </div>
                            <div class="flex flex-col gap-2.5 justify-center items-center py-2 self-strech">
                                <svg class="w-full" xmlns="http://www.w3.org/2000/svg" height="2" viewBox="0 0 638 2" fill="none">
                                    <path d="M1 1L637 1" stroke="#EBEBEB" stroke-linecap="round"/>
                                </svg>
                            </div>

                            <div class="flex justify-between items-center self-stretch">
                                <div class="flex gap-2 items-center">
                                    <div class="w-2 h-2 bg-[#00D395] rounded-full "></div>
                                    <div class=" font-Poppins font-medium text-grey text-sm">Registered</div>
                                    <div class=" font-Poppins font-medium text-black text-sm">{{ registed }}</div>

                                </div>

                                <div class="flex gap-2 items-center">
                                    <div class="w-2 h-2 bg-[#007FFF] rounded-full "></div>
                                    <div class=" font-Poppins font-medium text-grey text-sm">Email Marketing</div>
                                    <div class=" font-Poppins font-medium text-black text-sm">{{ registed }}</div>

                                </div>
                            </div>
                        </div>
                    </div>

                    <div class="w-[calc((100%-24px)/2)] flex flex-col gap-8">
                        <div class="flex gap-6">
                            <!-- net margin -->
                            <div class="w-[calc((100%-24px)/2)] bg-white flex flex-col justify-center items-start p-6 rounded-xl shadow-custom">
                                <div class="flex justify-between items-start self-stretch">
                                    <p class=" font-Poppins font-semibold text-black text-base">Net Margin</p>
                                    <div class="flex p-2 justify-center items-center gap-2.5 rounded-full bg-[#00D395]">
                                        <img src="/img/status-up.svg" alt="status">
                                    </div>
                                </div>

                                <div class="flex items-center self-stretch gap-[10px] font-Poppins font-semibold text-grey text-[28px]">
                                    {{ cur_price }}
                                </div>

                                <div class="flex flex-col justify-center items-center self-stretch gap-2">
                                    <p class="font-Poppins font-medium text-grey text-sm">View more</p>
                                    <img src="/img/arrow-right.svg" alt="arrow right">
                                </div>

                            </div>
                            <!-- recent transaction -->
                            <div class="w-[calc((100%-24px)/2)] flex p-6 flex-col justify-center items-center rounded-xl bg-white shadow-custom">
                                <div class="flex justify-center self-stretch gap-3">
                                    <p class=" font-Poppins font-semibold text-grey text-base">
                                        Recent Transactions
                                    </p>
                                </div>

                                <div class="flex pt-8 flex-col items-start self-stretch gap-2">
                                    <div class="w-full">
                                        <div class=" w-[50%] flex py-1 pl-2 items-start gap-[72px] rounded-s bg-[#F2F2F2]">
                                            <p class=" font-medium font-Poppins text-black text-sm">Amount</p>
                                        </div>

                                        <div class="w-[50%] flex py-1 pr-2 items-start gap-[72px] rounded-ee bg-[#F2F2F2]">
                                            <p class=" font-medium font-Poppins text-black text-sm">Status</p>

                                        </div>

                                    </div>

                                    <div class="w-full flex flex-col gap-2 px-2">
                                        <div class="flex items-start justify-between" v-for="(transaction, index) in recent_transaction" :key="index">
                                            <div class="flex">
                                                <div class=" w-[calc((100%-16px)/2)] flex flex-col justify-center items-start gap-2">
                                                    <p class=" font-Poppins font-normal text-black text-sm">$ {{ transaction.amount.toLocaleString() }} </p>
                                                </div>
                                                <div class="flex gap-2" v-if="transaction.status == 'Success'">
                                                    <div class="w-2 h-2 rounded-[100px] bg-[#00D395]"></div>
                                                    <div class="text-[#00D395] font-Poppins font-medium text-sm">Success</div>
                                                </div>
                                                <div class="flex gap-2" v-if="transaction.status == 'Declined'">
                                                    <div class="w-2 h-2 rounded-[100px] bg-[#Fa4B4B]"></div>
                                                    <div class="text-[#Fa4B4B] font-Poppins font-medium text-sm">Declined</div>
                                                </div>
                                                <div class="flex gap-2" v-if="transaction.status == 'Peding'">
                                                    <div class="w-2 h-2 rounded-[100px] bg-[#FF8A00]"></div>
                                                    <div class="text-[#FF8A00] font-Poppins font-medium text-sm">Pending</div>
                                                </div>
                                            </div>

                                            <div class="w-5 h-5 justify-center items-center flex">
                                                <img src="/img/arrow-square-right.svg" alt="arrow square right">
                                            </div>

                                        </div>
                                        <div class="flex flex-col justify-center items-center self-stretch gap-2 ">
                                            <p class="font-Poppins font-medium text-grey text-sm">View more</p>
                                            <img src="/img/arrow-right.svg" alt="arrow right">
                                        </div>
                                    </div>
                                </div>

                            </div>
                        </div>
                            <!-- default shipping address -->
                        <div class="w-full flex p-6 flex-col items-start gap-7 rounded-xl bg-white shadow-custom">
                            <div class="flex justify-between items-start self-stretch">
                                <p class=" font-semibold font-Poppins text-grey text-sm">Default Shipping Address</p>
                                <img src="/img/more-vertical.svg" alt="more">

                            </div>

                            <div class="w-full flex items-start gap-4 self-stretch">
                                <svg xmlns="http://www.w3.org/2000/svg" width="44" height="44" viewBox="0 0 44 44" fill="none">
                                    <path d="M23.8333 40.3333H9.16667C5.5 40.3333 3.66667 38.5 3.66667 34.8333V20.1667C3.66667 16.5 5.5 14.6667 9.16667 14.6667H18.3333V34.8333C18.3333 38.5 20.1667 40.3333 23.8333 40.3333Z" stroke="#00D395" stroke-width="2" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
                                    <path d="M18.535 7.33334C18.3883 7.88334 18.3333 8.48834 18.3333 9.16668V14.6667H9.16667V11C9.16667 8.98334 10.8167 7.33334 12.8333 7.33334H18.535Z" stroke="#00D395" stroke-width="2" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
                                    <path d="M25.6667 14.6667V23.8333" stroke="#00D395" stroke-width="2" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
                                    <path d="M33 14.6667V23.8333" stroke="#00D395" stroke-width="2" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
                                    <path d="M31.1667 31.1667H27.5C26.4917 31.1667 25.6667 31.9917 25.6667 33V40.3333H33V33C33 31.9917 32.175 31.1667 31.1667 31.1667Z" stroke="#00D395" stroke-width="2" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
                                    <path d="M11 23.8333V31.1667" stroke="#00D395" stroke-width="2" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
                                    <path d="M18.3333 34.8333V9.16666C18.3333 5.49999 20.1667 3.66666 23.8333 3.66666H34.8333C38.5 3.66666 40.3333 5.49999 40.3333 9.16666V34.8333C40.3333 38.5 38.5 40.3333 34.8333 40.3333H23.8333C20.1667 40.3333 18.3333 38.5 18.3333 34.8333Z" stroke="#00D395" stroke-width="2" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
                                </svg>

                                <div class="flex flex-col items-start gap-1">
                                    <p class=" font-semibold font-Poppins text-black text-sm">Address Alias 1</p>

                                    <p class=" font-normal font-Poppins text-black text-sm">{{ default_shipping_address }}</p>

                                </div>

                            </div>
                        </div>
                    </div>

                </div>

                <orders-table/>
            </div>

        </div>
    </template>       
    
    <script>
        import Apex from '../components/Apex.vue';
        import HeaderBar from '../components/HeaderBar.vue'
        import OrderCard from '../components/OrderCard.vue'
        
        export default {
            name: 'landingpage',
            components: { OrderCard, HeaderBar, Apex },
            async fetch() {
                this.order_card_data = await this.$axios.$get('/mock data/orderData.json');
                const customer_info = await this.$axios.$get('/mock data/customer_info.json');

                this.account_locked= customer_info.account_locked;
                this.avatar= customer_info.avatar;
                this.username = customer_info.username;
                this.last_active = customer_info.last_active;
                this.account_type = customer_info.account_type;
                this.first_name = customer_info.first_name;
                this.surname =  customer_info.surname;
                this.account_detail = customer_info.account_detail;
                this.country = customer_info.country;
                this.mobile_number = customer_info.mobile_number;
                this.address = customer_info.address;
                this.country_flag = customer_info.country_flag
                this.registed = customer_info.registed;
                this.email_marketing = customer_info.email_marketing
                this.cur_price = customer_info.cur_price;

                this.recent_transaction = await this.$axios.$get('/mock data/recent_transaction.json');

            },
            data() {
                return {
                    account_locked:true,
                    account_type:"",
                    account_detail:'',
                    address:'',
                    avatar:"",
                    country:'',
                    country_flag:'',
                    cur_price:'',
                    default_shipping_address: "5073 Mark Brown Rd, NE Dalton, Georgia (GA), 30721, United States",
                    docs: 8,
                    email_marketing:'',
                    first_name:'',
                    home_icon_url: "/img/home 03.svg",
                    last_active:"",
                    messages:130,
                    mobile_number:'',
                    order_card_data: this.order_card_data,
                    recent_transaction:[],
                    registed:'',
                    surname:'',
                    username:"",
                    users: 40,

                };
            },
        }
    </script>

  