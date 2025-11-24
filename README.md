🏥 Intelligent OR Scheduling & Optimization System
🌟 Project Overview: Solving the Hospital Bottleneck
Problem: Manual scheduling of Operating Rooms (ORs) and surgical teams is a critical bottleneck in healthcare, leading to lost revenue, resource waste, and unnecessary patient delays.

Our Solution: This project delivers an algorithmic engine built in Python that automatically generates highly efficient, conflict-free surgical schedules. We achieve true optimization by embedding a priority-driven triage system and specific resource constraints directly into the scheduling logic.

Result: A quantifiable reduction in resource waste and a smoother, more reliable patient flow, demonstrated through tangible performance metrics.

🎯 Key Features & Algorithmic Power
Feature	Description	Algorithmic Core
Surgical Triage	Surgeries are automatically sorted based on clinical urgency (Emergency > Urgent > Elective).	Min-Heap (Priority Queue)
Custom Seniority Tie-Breaker	Within the same clinical priority (e.g., two Urgent cases), the most senior surgeon's case is scheduled first to optimize senior resource usage.	Custom __lt__ comparison logic
Dynamic Conflict Detection	Prevents double-booking of surgeons and ensures all schedule windows respect unique, custom surgeon shifts (e.g., Dr. Lee's 14:00 cutoff).	Hash Maps for O(1) availability lookup
Maximized Efficiency	Greedy strategy attempts to fill the earliest feasible slot, maximizing case density.	Greedy Algorithm
Measurable Impact	Outputs clear metrics on OR Utilization Rate (CDI) and Total Idle Time.	Prefix Sum / Data Analysis
🚀 Core Algorithm Snippet
python
def __lt__(self, other):
    # Priority first, then seniority, then duration
    if self.priority != other.priority:
        return self.priority < other.priority
    elif self.seniority != other.seniority:
        return self.seniority < other.seniority
    else:
        return self.duration < other.duration
📊 Performance Results
OR Utilization Rate: 63.9% (OR-B)

Cases Scheduled: 12/13 (92.3% success rate)

Constraint Adherence: 100% (All surgeon limits respected)

Emergency Case Response: Immediate (07:30 AM start)

⚙️ How to Run the Project
Prerequisites
Python 3.x installed

Installation
Clone the repository:

bash
git clone https://github.com/soniyakuchekar71/Intelligent-OR-Scheduling-System
cd Intelligent-OR-Scheduling-System
Usage
The core logic is contained in main.py. You can modify the resource lists and surgical cases within the if __name__ == "__main__": block to test different scenarios.

Run the simulation from your terminal:

bash
python main.py
Sample Output Interpretation
The output displays the final schedule, followed by the metrics. Pay close attention to the unscheduled cases, as these directly highlight capacity and resource constraint limits (e.g., when Dr. Lee's custom shift time blocks a later assignment).

🛠️ Technical Architecture
Language: Python 3.x

Key Data Structures: Min-Heap, Hash Maps

Algorithm: Greedy Optimization

Complexity: O(n log n) for sorting, O(1) for resource lookup

🧠 Design & Custom Constraints (Crucial for Evaluation)
The success of this optimization lies in its ability to handle non-uniform, real-world constraints:

Unique Operating Hours: The OR day runs from 7:30 AM to 4:30 PM, deviating from a standard 8-hour window.

Surgeon-Specific Shifts: The scheduler respects custom availability (e.g., Dr. Lee is unavailable after 14:00 due to a mandatory training session).

Advanced Priority Triage (__lt__ function):

Level 1: Emergency

Level 2 (Tie-breaker): Seniority (Lower number = more senior)

Level 3 (Final Tie-breaker): Shortest Duration

📈 Future Enhancements
Web-based dashboard

Real-time schedule updates

Predictive case duration modeling

Multi-day scheduling capability

Buffer time optimization for room turnover

Machine learning for case duration prediction

👥 Contributing
We welcome contributions! Please feel free to submit pull requests or open issues for bugs and feature suggestions.

📄 License
This project is licensed under the MIT License - see the LICENSE file for details.

