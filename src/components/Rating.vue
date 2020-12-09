<template>
    <div class="table">
        <div class="block-1">
            <div class="block">
                <div class="th-1">Скорость</div>
                <div class="rating-area">
                            <input type="radio" id="star-5" name="rating-1" value="5">
                            <label for="star-5" title="Оценка «5»"></label>	
                            <input type="radio" id="star-4" name="rating-1" value="4">
                            <label for="star-4" title="Оценка «4»"></label>    
                            <input type="radio" id="star-3" name="rating-1" value="3">
                            <label for="star-3" title="Оценка «3»"></label>  
                            <input type="radio" id="star-2" name="rating-1" value="2">
                            <label for="star-2" title="Оценка «2»"></label>    
                            <input type="radio" id="star-1" name="rating-1" value="1">
                            <label for="star-1" title="Оценка «1»"></label>
                </div>
            </div>
            <div class="block">
                <div class="th-1">Скорость отдачи видео</div>
                <div class="rating-area">
                            <input type="radio" id="star-10" name="rating-2" value="5">
                            <label for="star-10" title="Оценка «5»"></label>	
                            <input type="radio" id="star-9" name="rating-2" value="4">
                            <label for="star-9" title="Оценка «4»"></label>    
                            <input type="radio" id="star-8" name="rating-2" value="3">
                            <label for="star-8" title="Оценка «3»"></label>  
                            <input type="radio" id="star-7" name="rating-2" value="2">
                            <label for="star-7" title="Оценка «2»"></label>    
                            <input type="radio" id="star-6" name="rating-2" value="1">
                            <label for="star-6" title="Оценка «1»"></label>
                </div>
            </div>
        </div>
        <div class="block-2">
            <div class="block">
                <div class="th-1">Качество</div>
                <div class="rating-area">
                            <input type="radio" id="star-15" name="rating-3" value="5">
                            <label for="star-15" title="Оценка «5»"></label>	
                            <input type="radio" id="star-14" name="rating-3" value="4">
                            <label for="star-14" title="Оценка «4»"></label>    
                            <input type="radio" id="star-13" name="rating-3" value="3">
                            <label for="star-13" title="Оценка «3»"></label>  
                            <input type="radio" id="star-12" name="rating-3" value="2">
                            <label for="star-12" title="Оценка «2»"></label>    
                            <input type="radio" id="star-11" name="rating-3" value="1">
                            <label for="star-11" title="Оценка «1»"></label>
                </div>
            </div>
            <div class="block">
                <div class="th-1">Пунктуальность</div>
                <div class="rating-area">
                            <input type="radio" id="star-20" name="rating-4" value="5">
                            <label for="star-20" title="Оценка «5»"></label>	
                            <input type="radio" id="star-19" name="rating-4" value="4">
                            <label for="star-19" title="Оценка «4»"></label>    
                            <input type="radio" id="star-18" name="rating-4" value="3">
                            <label for="star-18" title="Оценка «3»"></label>  
                            <input type="radio" id="star-17" name="rating-4" value="2">
                            <label for="star-17" title="Оценка «2»"></label>    
                            <input type="radio" id="star-16" name="rating-4" value="1">
                            <label for="star-16" title="Оценка «1»"></label>
                </div>
            </div> 
        </div>
    </div>
</template>

<script>
export default {

}
</script>

<style scoped lang="sass">
.table
    display: flex
    .block
        display: flex
        flex-direction: column
        margin-bottom: 26px
        .th-1
            text-align: left
            font-family: Montserrat
            font-style: normal
            font-weight: 500
            font-size: 14px
            line-height: 20px
            color: #3C3C3C
        .rating-area 
            overflow: hidden
            width: 200px
            float: left

        .rating-area:not(:checked) > input 
            display: none

        .rating-area:not(:checked) > label 
            float: right
            width: 40px
            padding: 0
            cursor: pointer
            font-size: 30px
            line-height: 30px
            color: lightgrey
            text-shadow: 1px 1px #bbb

        .rating-area:not(:checked) > label:before 
            content: '★'

        .rating-area > input:checked ~ label 
            color: #53C6D1
            text-shadow: 1px 1px #c60

        .rating-area:not(:checked) > label:hover,
        .rating-area:not(:checked) > label:hover ~ label 
            color: #53C6D1

        .rating-area > input:checked + label:hover,
        .rating-area > input:checked + label:hover ~ label,
        .rating-area > input:checked ~ label:hover,
        .rating-area > input:checked ~ label:hover ~ label,
        .rating-area > label:hover ~ input:checked ~ label 
            color: #53C6D1
            text-shadow: 1px 1px goldenrod

        .rate-area > label:active 
            position: relative
.block-1
    margin-right: 57px
@media screen and ( max-width: 550px )
    .table
        flex-direction: column


</style>