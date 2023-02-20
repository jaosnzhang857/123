import tkinter as tk
from tkinter import ttk
import netmiko
from netmiko import ConnectHandler

# 定义预设命令字典
PRESET_COMMANDS = {
    "display ip interface brief": "interface",
    "display vlan": "vlan",
    "display ip routing-table": "routing",
    "disp version": "version"
}

# 从文件中加载预设命令
with open("preset_commands.txt", "r") as f:
    for line in f:
        if line.strip():
            command, label = line.strip().split(": ")
            PRESET_COMMANDS[command] = label

# 保存预设命令到文件
def save_preset_commands():
    with open("preset_commands.txt", "w") as f:
        for command, label in PRESET_COMMANDS.items():
            f.write(f"{command}: {label}\n")

# 执行预设命令
def execute_command():
    selected_command = command_selector.get()
    device_ip = device_ip_entry.get()
    username = username_entry.get()
    password = password_entry.get()

    device = {
        'device_type': 'huawei',
        'ip': device_ip,
        'username': username,
        'password': password,
    }

    # 建立 SSH 连接
    try:
        with ConnectHandler(**device) as ssh:
            result = ssh.send_command(selected_command)
            result_text.delete("1.0", "end")
            result_text.insert("end", result)
    except netmiko.ssh_exception.NetMikoAuthenticationException:
        result_text.delete("1.0", "end")
        result_text.insert("end", "Authentication failed")
    except Exception as e:
        result_text.delete("1.0", "end")
        result_text.insert("end", str(e))

# 添加命令到预设命令列表和文件
def add_preset_command():
    command = new_command_entry.get()
    label = new_command_label_entry.get()
    PRESET_COMMANDS[command] = label
    save_preset_commands()
    command_selector['values'] = list(PRESET_COMMANDS.keys())
    new_command_entry.delete(0, 'end')
    new_command_label_entry.delete(0, 'end')

# 创建主窗口
window = tk.Tk()
window.title("命令执行器")

# 创建设备信息输入框
device_ip_label = ttk.Label(window, text="设备 IP 地址")
device_ip_entry = ttk.Entry(window)
device_ip_label.grid(row=0, column=0, padx=5, pady=5)
device_ip_entry.grid(row=0, column=1, padx=5, pady=5)

username_label = ttk.Label(window, text="用户名")
username_entry = ttk.Entry(window)
username_label.grid(row=1, column=0, padx=5, pady=5)
username_entry.grid(row=1, column=1, padx=5, pady=5)

password_label = ttk.Label(window, text="密码")
password_entry = ttk.Entry(window, show="*")
password_label.grid(row=2, column=0, padx=5, pady=5)
password_entry.grid(row=2, column=1, padx=5, pady=5)

# 创建命令选择下拉框
command_label = ttk.Label(window, text="选择要执行的命令")
command_selector = ttk

# 定义预设命令字典
PRESET_COMMANDS = {
    "display ip interface brief": "interface",
    "display vlan": "vlan",
    "display ip routing-table": "routing",
    "disp version": "version"
}

# 从文件中加载预设命令
with open("preset_commands.txt", "r") as f:
    for line in f:
        if line.strip():
            command, label = line.strip().split(": ")
            PRESET_COMMANDS[command] = label

# 保存预设命令到文件
def save_preset_commands():
    with open("preset_commands.txt", "w") as f:
        for command, label in PRESET_COMMANDS.items():
            f.write(f"{command}: {label}\n")

# 执行预设命令
def execute_command():
    selected_command = command_selector.get()
    device_ip = device_ip_entry.get()
    username = username_entry.get()
    password = password_entry.get()

    device = {
        'device_type': 'huawei',
        'ip': device_ip,
        'username': username,
        'password': password,
    }

    # 建立 SSH 连接
    try:
        with ConnectHandler(**device) as ssh:
            result = ssh.send_command(selected_command)
            result_text.delete("1.0", "end")
            result_text.insert("end", result)
    except netmiko.ssh_exception.NetMikoAuthenticationException:
        result_text.delete("1.0", "end")
        result_text.insert("end", "Authentication failed")
    except Exception as e:
        result_text.delete("1.0", "end")
        result_text.insert("end", str(e))

# 添加命令到预设命令列表和文件
def add_preset_command():
    command = new_command_entry.get()
    label = new_command_label_entry.get()
    PRESET_COMMANDS[command] = label
    save_preset_commands()
    command_selector['values'] = list(PRESET_COMMANDS.keys())
    new_command_entry.delete(0, 'end')
    new_command_label_entry.delete(0, 'end')

# 创建命令选择下拉框和执行按钮
command_selector = ttk.Combobox(window, values=list(PRESET_COMMANDS.keys()))
command_selector.grid(row=3, column=0, padx=5, pady=5)

execute_button = ttk.Button(window, text="执行", command=execute_command)
execute_button.grid(row=3, column=1, padx=5, pady=5)

# 创建结果显示框
result_text = tk.Text(window, height=10)
result_text.grid(row=4, column=0, columnspan=2, padx=5, pady=5)

# 创建添加预设命令输入框和按钮
new_command_label = ttk.Label(window, text="新命令标签")
new_command_label_entry = ttk.Entry(window)
new_command_label.grid(row=5, column=0, padx=5, pady=5)
new_command_label_entry.grid(row=5, column=1, padx=5, pady=5)

new_command = ttk.Label(window, text="新命令")
new_command_entry = ttk.Entry(window)
new_command.grid(row=6, column=0, padx=5, pady=5)
new_command_entry.grid(row=6, column=1, padx=5, pady=5)

add_command_button = ttk.Button(window, text="添加预设命令", command=add_preset_command)
add_command_button.grid(row=7, column=0, columnspan=2, padx=5, pady=5)

# 主循环
window.mainloop()
