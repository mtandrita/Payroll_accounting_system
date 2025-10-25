const employees = [];
const employeeSelect = document.getElementById('employee-select');
const employeeList = document.getElementById('employees');
const payslipDisplay = document.getElementById('payslip-display');
const modal = document.getElementById('payslip-modal');
const closeBtn = document.getElementsByClassName('close')[0];

// Add employee
document.getElementById('add-employee').addEventListener('submit', function(e) {
    e.preventDefault();
    const name = document.getElementById('name').value;
    const hourlyRate = parseFloat(document.getElementById('hourly-rate').value);
    employees.push({ name, hourlyRate });
    updateEmployeeSelect();
    updateEmployeeList();
    this.reset();
});

// Update employee dropdown
function updateEmployeeSelect() {
    employeeSelect.innerHTML = '<option value="">Choose an employee</option>';
    employees.forEach((emp, index) => {
        const option = document.createElement('option');
        option.value = index;
        option.textContent = emp.name;
        employeeSelect.appendChild(option);
    });
}

// Update employee list
function updateEmployeeList() {
    employeeList.innerHTML = '';
    employees.forEach(emp => {
        const li = document.createElement('li');
        li.textContent = `${emp.name} - $${emp.hourlyRate}/hr`;
        employeeList.appendChild(li);
    });
}

// Calculate payroll and show modal
document.getElementById('calculate-payroll').addEventListener('submit', function(e) {
    e.preventDefault();
    const empIndex = parseInt(employeeSelect.value);
    const hours = parseFloat(document.getElementById('hours').value);
    const emp = employees[empIndex];
    const grossPay = emp.hourlyRate * hours;
    const tax = grossPay * 0.20; // 20% tax
    const netPay = grossPay - tax;
    
    payslipDisplay.textContent = `
Employee: ${emp.name}
Hours Worked: ${hours}
Hourly Rate: $${emp.hourlyRate}
Gross Pay: $${grossPay.toFixed(2)}
Tax Deduction (20%): $${tax.toFixed(2)}
Net Pay: $${netPay.toFixed(2)}
    `;
    
    modal.style.display = 'block';
    this.reset();
});

// Close modal when clicking the X
closeBtn.onclick = function() {
    modal.style.display = 'none';
};

// Close modal when clicking outside the content
window.onclick = function(event) {
    if (event.target == modal) {
        modal.style.display = 'none';
    }
};
