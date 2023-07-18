<template>
    <div>
        <p>
            pc : 구글 캘린더
            <br />
            android: 구글 캘린더
            <br />
            ios: ios 캘린더
        </p>
        <add-to-calendar-button
            name="캘린더 추가"
            timeZone="Asia/Seoul"
            label="캘린더에 추가하기"
            description="캘린더에 추가하기 성공"
            :startDate="startDate"
            :endDate="endDate"
            :options="mobile"
            :startTime="startTime"
            :endTime="endTime"
        >
        </add-to-calendar-button>
    </div>
</template>
<script setup>
import 'add-to-calendar-button'
import UAParser from 'ua-parser-js'
import dayjs from 'dayjs'

// pc, 안드로이드, ios에 따라 열리는 캘린더가 다르게 적용 되도록
const mobile = computed(() => {

    if(process.client) {
        const parser = new UAParser(navigator.userAgent)

        if(parser.getDevice().type === 'mobile') {
            if(parser.getDevice().model === 'iPhone') {
                return 'Apple'
            } else {
                return 'Google'
            }
        } else {
            return 'Google'
        }
    }
})

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
</script>