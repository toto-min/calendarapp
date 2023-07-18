<template>
    <div>
        <p>
        커스텀 버튼 옵션
        </p>
        <div>
            <div class="btn-group" role="group">
                <button @click="pcCalendar" id="pc" class="btn btn-primary">pc</button>
                <button @click="andCalendar" id="android" class="btn btn-danger">안드로이드</button>
                <button @click="iosCalendar" id="ios" class="btn btn-warning">ios</button>
            </div>
        </div>
    </div>
</template>

<script setup>

import dayjs from 'dayjs'
import _ from 'lodash'
// 직접 만든 버튼에 캘린더 저장하기 기능 추가
import { atcb_action } from 'add-to-calendar-button'



const startDate = computed(() => {
    return dayjs().format('YYYY-MM-DD')
})

const endDate = computed(() => {
    return dayjs().format('YYYY-MM-DD')
})

const startTime = computed(() => {
    return dayjs().add(1, 'hour').format('hh:mm')
})

const endTime = computed(() => {
    return dayjs().add(2, 'hour').format('hh:mm')
})

// method

const pcCalendar = () => {
    let btn = document.getElementById('pc')
    config.options.splice(0, 1, 'Google')
    atcb_action(config, btn)
}

const andCalendar = () => {
    let btn = document.getElementById('android')
    config.options.splice(0, 1, 'Google')

    atcb_action(config, btn)
}

const iosCalendar = () => {
    let btn = document.getElementById('ios')
    config.options.splice(0, 1, 'iCal')

    atcb_action(config, btn)
}


// 버튼 설정
const config = {
    name: '캘린더 추가하기',
    description: '캘린더에 추가되었습니다.',
    startDate: startDate.value,
    startTime: startTime.value,
    endTime: endTime.value,
    options: [],
    timeZone: 'currentBrowser',
};


</script>