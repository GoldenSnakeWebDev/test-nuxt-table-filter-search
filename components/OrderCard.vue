    <!-- Please remove this file from your project -->
    <template>
        <div class="flex w-[calc((100%-72px)/4)] min-w-max py-6 pl-6 pr-4 flex-col shadow-custom jsutify-center items-start gap-12 rounded-xl bg-white">
            <div class="flex justify-between items-start self-stretch">
                <div class="flex items-start gap-4">
                    <div class="flex w-14 h-14 p-2 justify-center items-center gap-[10px] rounded-full bg-[#BFDFFF]" :style="{background:icon_color2}">
                        <div class="w-10 h-10 flex p-2 justify-center items-center gap-[10px] rounded-full"  :style="{background:icon_color1}">
                            <img :src="order_img_url" class="w-6 h-6"/>
                        </div>
                    </div>

                    <div class="flex items-start flex-col">
                        <p class="text-grey text-sm not-italic font-Poppins">
                            {{ title }}
                        </p>
                        
                        <p class="text-grey font-Poppins text-2xl not-italic">
                            {{ order_value.toLocaleString() }}
                        </p>
                    </div>
                </div>
                <div class="">
                    <img src="/img/more-vertical.svg" class="w-6 h-6"/>
                </div>
            </div>

            <div class="flex justify-between items-end self-stretch">
                <select v-model="selectedOption" id="selectOption" class="text-grey font-Poppins text-sm font-medium">
                    <option v-for="option in options" :key="option.value" :value="option.value">
                        {{ option.label }}
                    </option>
                </select>

                <div class="flex items-center gap-8">
                    <p class="text-grey font-Poppins text-sm font-medium">More</p>
                    <img src="/img/arrow-right.svg" class="w-4 h-4"/>
                </div>
            </div>
            
        </div>
    </template>
    
    <script>
    export default {
        data() {
            return {
                selectedOption: 'week',
                options: [
                    { value: 'week', label: 'This week' },
                    { value: 'month', label: 'This month' },
                    { value: 'year', label: 'This year' },
                ],
            };
        },

        props: {
            order_img_url: String,
            order_value: Number,
            title: String,
            icon_color1:String,
            icon_color2: String
        }
    }
    </script>
    