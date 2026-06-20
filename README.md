class Ticket:
    def __init__(self, ticket_id, student_name, issue):
        self.ticket_id = ticket_id
        self.student_name = student_name
        self.issue = issue
        self.next = None


class TicketQueue:
    def __init__(self):
        self.head = None

  def enqueue(self, ticket_id, student_name, issue):
        """Add a new ticket to the end of the queue."""
        new_ticket = Ticket(ticket_id, student_name, issue)
        if not self.head:
            self.head = new_ticket
            return
        
current = self.head
        while current.next:
            current = current.next
        current.next = new_ticket

  def priority_insert(self, target_id, ticket_id, student_name, issue):
        """Insert a new ticket immediately after a specified ticket ID."""
        current = self.head
        while current:
            if current.ticket_id == target_id:
                new_ticket = Ticket(ticket_id, student_name, issue)
                new_ticket.next = current.next
                current.next = new_ticket
                return True
            current = current.next
        return False  # Target ID not found

  def resolve_ticket(self, ticket_id):
        """Delete a resolved ticket from the queue given its ticket ID."""
        if not self.head:
            return False

   if self.head.ticket_id == ticket_id:
            self.head = self.head.next
            return True

   current = self.head
        while current.next:
            if current.next.ticket_id == ticket_id:
                current.next = current.next.next
                return True
            current = current.next
        return False

  def find_middle(self):
        """Find the middle ticket using the fast/slow pointer method."""
        if not self.head:
            return None
        
  slow = self.head
        fast = self.head

   while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
            
  return slow

  def reverse_queue(self):
        """Reverse the queue in-place."""
        prev = None
        current = self.head
        
   while current:
            next_node = current.next
            current.next = prev
            prev = current
            current = next_node
            
   self.head = prev

def display_queue(self):
        """Traversal method to print all ticket IDs and details."""
        if not self.head:
            print("Queue is empty.")
            return
        
  current = self.head
        output = []
        while current:
            output.append(f"[ID: {current.ticket_id} | {current.student_name} | {current.issue}]")
            current = current.next
        print(" -> ".join(output))
        
    
  # 1. Enqueue
  queue.enqueue(101, "Alice", "WiFi issues")
    queue.enqueue(102, "Bob", "LMS login error")
    queue.enqueue(104, "Charlie", "ID Card replacement")
    
  print("Initial Queue:")
    queue.display_queue()

# 2. Priority Insert
  queue.priority_insert(102, 103, "David", "Urgent Exam Access Issue")
    print("\nAfter Priority Insertion of 103 after 102:")
    queue.display_queue()

# 3. Find Middle
  mid = queue.find_middle()
    if mid:
  print(f"\nMiddle Ticket: ID {mid.ticket_id} ({mid.student_name})")

# 4. Reverse Queue
  queue.reverse_queue()
    print("\nAfter Reversing Queue:")
    queue.display_queue()

# 5. Resolve Ticket
  queue.resolve_ticket(102)
    print("\nAfter Resolving Ticket 102:")
    queue.display_queue()


