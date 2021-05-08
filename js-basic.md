# IMPORTANT JS CONCEPT
<hr>

## JS EVENT LOOP, CALLSTACK, EVENT TABLE, CALLBACK QUEUE, JOB/EVENT QUEUE, HEAP

1. **CALL STACK**
   <br>
   - Where all javascript code gets pushed in and executed one by one and gets popped out once the execution is done.
     <br><br>
2. **EVENT TABLE**
   <br>
    - Event table responsible for moving all asynchronous code to callback/event queue after specified time.
    <br><br>
3. **HEAP**
   <br>
    - HEAP is where memory allocation happens for all variable that is defined in program.
    <br><br>
4. **Callback queue** (Include Task Queue(also known as Macro Task) and Job Queue(Micro Task))
    <br>
    - Callback queue is where all asynchronous code gets pushed to and wait for the execution.
    - Task Queue
      - Task Queue where asynchronous code like: callback of an event, callback in setTimeout, setInterval, code from a console or `<script>` tag gets pushed to.
      - A new JavaScript program or subprogram is executed (such as from a console, or by running the code in a `<script>` element) directly.
      - An event fires, adding the event's callback function to the task queue.
      - A timeout or interval created with `setTimeout()` or `setInterval()` is reached, causing the corresponding callback to be added to the task queue.
    

