# To-Do List Application

**Live Demo:** [https://zumaralihassan-collab.github.io/Zumar-Should-Cost-Tool/todo.html](https://zumaralihassan-collab.github.io/Zumar-Should-Cost-Tool/todo.html)

A modern, fully-featured to-do list application with local storage functionality.

## Features

### Core Functionality
✅ **Add Tasks** - Create new tasks with a clean, intuitive interface  
✅ **Mark Complete** - Check off tasks as you complete them  
✅ **Delete Tasks** - Remove individual tasks or bulk delete completed items  
✅ **Local Storage** - All tasks are automatically saved to browser local storage  
✅ **Persistent Data** - Tasks remain even after closing and reopening the browser  

### Advanced Features
🎯 **Priority Levels** - Assign High, Medium, or Low priority to each task  
🔍 **Filter Tasks** - View All, Pending, Completed, or High Priority tasks  
📊 **Task Statistics** - Real-time display of Total, Completed, and Pending counts  
📥 **Export to JSON** - Download your tasks as a JSON file for backup  
🗑️ **Bulk Actions** - Clear all completed tasks at once  
⌨️ **Keyboard Support** - Press Enter to quickly add tasks  

### User Experience
- Clean, modern UI with gradient design
- Smooth animations and transitions
- Responsive design (works on mobile & desktop)
- Visual feedback on interactions
- Empty state messages
- XSS protection with HTML escaping

## How to Use

### Adding a Task
1. Type your task in the input field
2. Select a priority level (Low, Medium, High)
3. Click "Add" or press Enter

### Managing Tasks
- **Complete Task** - Click the checkbox next to the task
- **Delete Task** - Click the "Delete" button on the task
- **Filter Tasks** - Use the filter buttons to view specific task categories

### Bulk Operations
- **Clear Completed** - Click "🗑️ Clear Done" to remove all completed tasks
- **Export Tasks** - Click "📥 Export" to download tasks as a JSON file

## Technical Details

### Storage
- Uses browser **localStorage API**
- Tasks are stored as JSON in the key `tasks`
- Automatic saving after each operation
- Data persists across browser sessions

### Data Structure
```json
{
  "id": 1234567890,
  "text": "Task description",
  "completed": false,
  "priority": "high",
  "createdAt": "5/27/2026, 3:45:00 PM"
}
```

### Technologies Used
- **HTML5** - Structure
- **CSS3** - Styling with gradients and animations
- **JavaScript ES6** - Logic and local storage management
- **Tailwind CSS** - Utility classes

## Browser Compatibility
- ✅ Chrome/Edge 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Mobile browsers

## Keyboard Shortcuts
- **Enter** - Add new task from input field

## File Location
- `todo.html` - Complete self-contained application

## Future Enhancements
- Categories/tags for tasks
- Due dates and reminders
- Task notes/descriptions
- Dark mode
- Cloud sync
- Recurring tasks

---

**Built by:** Mohammed Zumar Ali Hassan  
**Last Updated:** May 27, 2026