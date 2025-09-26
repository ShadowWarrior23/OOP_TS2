# OOP_TS2

app.ts:
/* const h = document.querySelector('header') as HTMLDivElement;
h.style.color = ''; */

export class NumHandler{
    private _x: number
    protected _y: number

    constructor(a: number, b:number){
        this._x = a;
        this._y = b;
    }

    get x(){
        return this._x;
    }

    set x(v: number){
        if (v > 0) this._x = v;
    }

    get y(){
        return this._y;
    }

    set y(v: number){
        if (v > 0) this._y = v;
    }

    static help(){
        console.log('🦎🦎🦎...');
    }

    sum():number{
        return this._x + this._y;
    }

    sub():number{
        return this._x - this._y;
    }

    mult():number{
        return this._x * this._y;
    }

    div():number{
        return this._x / (this._y !== 0 ? this._y : 1);
    }
}

const numObj = new NumHandler(5, 9);
numObj.x = 100;
console.log(numObj.x);
console.log(numObj.sum(), numObj.sub(), numObj.mult(), numObj.div());
NumHandler.help();

child.ts:
import { NumHandler } from "./app.js";

export class Child extends NumHandler{
    private _s: number;
    private readonly _arr: number[];

    constructor(a:number, b:number, s:number){
        super(a, b);
        this._s = s;
        this._arr = Array.from({length: s}, (_, i) => i+1)
    }

    getArr = ()=> this._arr;

    override mult():number{
        if ((this.x) === 0) this.x = 1;
        if ((this.y) === 0) this._y = 1;
        return this.x * this.y;
    }
}

const numObj2 = new Child(5, 0, 10);
console.log(numObj2.mult(), numObj2.getArr(), numObj2.sub());
