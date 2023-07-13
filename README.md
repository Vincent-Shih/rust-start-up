# 使用方式

## 安裝步驟

已 `MacOS` 為例使用以下[官方網站](https://www.rust-lang.org/zh-TW/tools/install)提供的語法進行安裝

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

接著使用以下語法測試是否安裝成功

```bash
rustc --version
```

或者

```bash
rustc -V
```

一般來說按照預設的執行下去就會安裝好`cargo`，`carogo`是 rust的`建置系統`以及`套件管理器`以後會做越來越大的Project會越常使用到`cargo` 來處理你的`dependencies`

```bash
cargo --version
```

## Visual Code Debug

接下來我們最常做的事就是需要debug，所以參考以下做法，要使用`visual code`對rust debug前提是需要根據作異業桶安裝套件`codeLLDB`在`MacOS`中就是必須要裝的套件

1. [CodeLLDB](https://marketplace.visualstudio.com/items?itemName=vadimcn.vscode-lldb)
2. 建立一個 `src`目錄
3. 接下來移動目錄

    ```bash
    cd src
    ```

4. 建立一個`main.rs`
5. 裡面寫下

    ```bash
    fn main(){
        println!("Hello, world!");
    }
    ```

6. 再來我們移動到外面的資料夾

    ```bash
    cd ../
    ```

7. 建立一個`Cargo.toml`

   ```bash
    [package]

    name = "main"
    version = "0.0.1"
    authors= ["xxx@gmail"]
   ```

8. 接下來看一下你的目錄，是不是多了一個`target`的目錄以及一個`Cargo.lock`
9. 接下來執行以下指令

    ```bash
    cargo build
    ```

10. 你可以直接執行已下命令看看是否有辦法執行

    ```bash
    cargo run
    ```

11. 接下來在`visual code`按下左上角的`debug` 或按下 `fn`+`F5`編輯你的`launch.json`

    ```json
    {
        // Use IntelliSense to learn about possible attributes.
        // Hover to view descriptions of existing attributes.
        // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
        "version": "0.2.0",
        "configurations": [
            {
                "name": "(OSX) Launch",
                "type": "lldb",
                "request": "launch",
                "program": "${workspaceRoot}/target/debug/main",
                "args": [],
                "cwd": "${workspaceRoot}",
            }
        ]
    }
    ```

12. 在`configurations`的`program`中這個目錄的位子就是剛剛執行`cargo build`產生的檔案，再次執行`debug`就會停在有下中斷點的地方了。

## 套件安裝推薦

1. 安裝RLS

   ```bash
   rustup component add rls rust-analysis rust-src
   ```

2. MacOS Debug (codeLLDB)[https://marketplace.visualstudio.com/items?itemName=vadimcn.vscode-lldb]
3. TOML相關
   1. [Better TOML](https://marketplace.visualstudio.com/items?itemName=bungcip.better-toml)
   2. [crates](https://marketplace.visualstudio.com/items?itemName=serayuzgur.crates)
4. Test
   1. [Rust Test Explorer](https://marketplace.visualstudio.com/items?itemName=swellaby.vscode-rust-test-adapter)
5. 其他
   1. [Rust Doc Viewer](https://marketplace.visualstudio.com/items?itemName=JScearcy.rust-doc-viewer)