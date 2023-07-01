# GreenPi
以每天Pi个自动提交的速率为你的Github瓷砖墙增光添彩！

## 快速入门

1. 点按 `Use this template` 并创建一个仓库

2. 配置`/.github/workflows/pi.yml`
    * 配置自动提交
    
        取消注释`schedule`部分，以启用脚本的自动执行
        
        ```yml
        on:
            push:
                branches:
                - main
                schedule:
                - cron: "0 0 * * *"
        ```

    * 配置提交信息
        
        修改`Set up git data`部分中账号的信息，以实现提交人的显示

        ```yml
        - name: Set up git data
          run: |
          git config --local user.email "<你的邮件地址>"
          git config --local user.name "<你的用户名>"
          git remote set-url origin https://${{ github.actor }}:${{ secrets.GITHUB_TOKEN }}@github.com/${{ github.repository }}
          git pull --rebase
        ```
3. 配置`/main.py`
    * 设置 `ENABLE` 为 `True` 来启用提交
    * 设置 `START_DATE` 为 Pi 的计算的起始日期
    * 设置 `COMMIT_TIME` 为 Git中的提交时间，需要符合`HH:MM:SS+XX:YY`的格式，`XX:YY`为时区，例如`+08:00`为北京时间
    * 设置 `MESSAGE` 为需要提交的信息，为了安全起见没有使用`eval`进行解析，如果您对此做出贡献的话我将不胜感激。
    * 设置 `FAKE_COMMIT` 为 `False`来启用真实的提交，否则将只会输出待执行的指令。

4. 修改`Repo Settings`
    * 在`Actions permissions`中修改`Workflow permissions`为`Read and write permissions`

5. 完成了！现在你可以在每天的Pi个提交后，享受你的**有深有浅**的瓷砖墙了！

## 鸣谢

* [auto-green](https://github.com/justjavac/auto-green) 为此项目带来灵感
* [GitHub Actions](https://github.com/features/actions) 为此项目提供了自动化的支持

## License

This project is licensed under the terms of the MIT license. See the [LICENSE](LICENSE) file.
