<template>
  <div></div>
</template>

<script lang="ts">

/**
 * #1
 * 宣告一個 function funcA讓參數與回傳型態一致，並能夠通過編譯
 * */

function funcA<T> (arg: T): T {
  return arg
}

funcA('helloGeneric').toLowerCase()
funcA(1234).toFixed()

/**
 * #2
 * 宣告一個 function funcB讓參數是一個 Array 並回傳它的長度
 * */

function funcB<T> (arg: T[]): number {
  return arg.length
}

console.log(funcB(['a', 2, new Date()]))

/**
 * #3
 * 宣告一個 interface C 讓下面的函數通過編譯
 * */

interface C<T> {
    (arg0: string, arg1: T): T
}

function funC1 (arg0: string, arg1: number): number {
  return arg1
}

function funC2 (arg0: string, arg1: string): string {
  return arg1
}

const c1: C<number> = funC1
const c2: C<string> = funC2

/**
 * #4
 * 修改 funcD 讓它只接受 type D 的三種字串
 * */
type D = 'x' | 'y' | 'z'

function funcD<T extends D> (arg0: T) {
  console.log(arg0)
}

funcD('x')
funcD('123') // Argument of type '"123"' is not assignable to parameter of type 'D'

/**
 * #5
 * 設計一個 interface E 可同時作為 e1 及 e2 的型態，並替 e1 及 e2 加上型別註解可編譯通過 題示：<T, K>逗號帶多個泛型
 */

interface E<T, K> {
    (arg0: T, arg1: K): [T, K]
}

const e1: E<number, string> = function funcE1 (arg0: number, arg1: string) {
  return [arg0, arg1]
}

const e2: E<Date, boolean> = function funcE2 (arg0: Date, arg1: boolean) {
  return [arg0, arg1]
}

/**
 * #6
 * 設計一個函數 funcF，參數為1為一個obj，參數2為key回傳值為 obj[key]，
 * 且能夠編譯通過 題示：extends keyof
 * (不能有 Parameter 'obj' implicitly has an 'any' type.)
 */

function funcF<T, K extends keyof T> (obj: T, key: K): T[K] {
  return obj[key]
}

const a = {
  a: 'a',
  b: 'b',
  c: 'c'
}

funcF(a, 'a')
funcF(a, 'd')

export default {
  name: 'Generic',
  methods: {

  }
}
</script>

<style scoped>

</style>
