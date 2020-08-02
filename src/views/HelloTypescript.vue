<template>
  <div></div>
</template>

<script lang="ts">
import { defineComponent } from '@vue/composition-api'

// 2020/07/17 題目 初識 typescript
function helloWorld (params: string): void {
  console.log(params)
}

const msg: string = 'helloWorld'
helloWorld(msg)

// 2020/07/24 題目 基礎型別
// const a: number = 10
// const b: string = '10'
// const c: boolean = true
// const d: undefined = undefined
// const e: null = null
// const f: never
// const g: Array<number> = [1, 2]
// const h: Array<number|string> = [1, '2']
// const i: object = { x: 5, y: '6' }

// 2020/07/31 題目 interface
const a: A = { x: 5, y: '6' }
interface A {
    x: number,
    y: string
}

const b: B = { x: 5, y: '6' }
b.z = true
interface B {
    x: number,
    y: string,
    z?: boolean
}

const c: C = [1, '2'] // 此題類似I
interface C {
    [x: number]: number | string
}

const d: D = function (arg0) {
  return Number(arg0)
}
interface D {
    (arg0: string | number): number
}

const e: E = function (arg0, arg1): string {
  return arg0 + arg1
}
interface E {
    (arg0: string, arg1: string): string
}

const f: F = () => 'Hello'
interface F {
    (): string
}

const g: G = (x: number, y: number) => x + y
interface G {
    (x: number, y: number): number
}

const cb = function (x: number) {
  // eslint-disable-next-line standard/no-callback-literal
  cb(x + 1)
}

// eslint-disable-next-line @typescript-eslint/no-empty-function
const h: H = (cb) => {}
interface H {
    (cb: (x: number) => never): void
}

const i: I = {} // 這個 object 的 key 可以是任意整數，value為字串
interface I {
    [props: number]: string,
    [props: string]: string
}

export default defineComponent({})
</script>

<style scoped>

</style>
