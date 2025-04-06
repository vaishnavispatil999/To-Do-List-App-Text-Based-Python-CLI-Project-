def load_tasks():
    try:
        with open("tasks.txt", "r") as f:
            tasks = [line.strip() for line in f.readlines()]
    except FileNotFoundError:
        tasks = []
    return tasks

def save_tasks(tasks):
    with open("tasks.txt", "w") as f:
        for task in tasks:
            f.write(task + "\n")

def show_tasks(tasks):
    if not tasks:
        print("✅ Task list is empty.")
    else:
        print("\n📋 Your To-Do List:")
        for idx, task in enumerate(tasks, 1):
            print(f"{idx}. {task}")

def add_task(tasks):
    task = input("➕ Enter new task: ")
    tasks.append(task)
    print("✅ Task added successfully!")

def delete_task(tasks):
    show_tasks(tasks)
    try:
        task_no = int(input("❌ Enter the task number to delete: "))
        if 1 <= task_no <= len(tasks):
            removed = tasks.pop(task_no - 1)
            print(f"🗑️ '{removed}' has been deleted.")
        else:
            print("⚠️ Please enter a valid task number.")
    except ValueError:
        print("⚠️ Please enter a number.")

def main():
    tasks = load_tasks()
    while True:
        print("\n🔹 To-Do Menu 🔹")
        print("1. Show Tasks")
        print("2. Add Task")
        print("3. Delete Task")
        print("4. Exit")
        choice = input("Enter your choice: ")

        if choice == "1":
            show_tasks(tasks)
        elif choice == "2":
            add_task(tasks)
        elif choice == "3":
            delete_task(tasks)
        elif choice == "4":
            save_tasks(tasks)
            print("💾 Tasks saved. Goodbye!")
            break
        else:
            print("⚠️ Invalid choice. Please try again.")

if __name__ == "__main__":
    main()

        
        
