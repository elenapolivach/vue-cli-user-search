<template>
    <div class="btn-filtered-block">
            <a class="btn-filter" @click.prevent='$emit("filter-name")'>Name&nbsp;&darr;</a>
            <a class="btn-filter" @click.prevent='$emit("filter-star")'>Stars&nbsp;&darr;</a>
          </div>
</template>

