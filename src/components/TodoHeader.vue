<template>
    <header>
        <h1>Todo App</h1>
        <div>최근추가아이템 :
            <span>
            {{ additem }}
            </span>
        </div>

    </header>
</template>

<script>
export default {
    props: ['additem'],
}
</script>

