let user=document.getElementById("users");
let envelope=document.getElementById("envelope");
envelope.addEventListener("click",envelopefunction);
let background=document.getElementById("backgroundContainer");
let light=document.getElementById("light-theme");
light.addEventListener("click",lightTheme);
let dark=document.getElementById("dark-theme");
dark.addEventListener("click",darkTheme);
let homeContainer=document.getElementById("homeContainer");
let createContainer=document.getElementById("create-user");

let createbackground=document.getElementById("createbackground");



let sidehome=document.getElementById("sidehome");
let userslist=document.getElementById("users-list");
let list=document.getElementById("list");
let imagegallery=document.getElementById("imagegallery");
let images=document.getElementById("images");


function darkTheme()
{
    background.style.backgroundColor="black";
}
function lightTheme()
{   
    background.style.backgroundColor="#cbcaca";
}
function envelopefunction()
{
    alert("No Current Messages");
}
let updatedValue=null;
let users=0;
updatedValue=setInterval(function()
{
    users=users+10;
    user.textContent=users+"+";
    if(users===2500)
    {
        clearInterval(updatedValue);
    }
    
},10);
let average=document.getElementById("avg");
let updatedvalue1=null;
let avg=0.00;
updatedvalue1=setInterval(function()
{
    avg=avg+3;
    average.textContent=avg+" min";
    if(avg===123)
    {
       clearInterval(updatedvalue1);
    }
},100);
let download=document.getElementById("download");
let updated=null;
let down=0;
updated=setInterval(function(){
    down=down+100;
    download.textContent=down+"+";
    if(down===1700)
    {
        clearInterval(updated)
    }
},100);

let comment=document.getElementById("comment");
let update=null;
let comment1=0;
update=setInterval(function()
{
    comment1=comment1+1;
    comment.textContent=comment1+".5K+";
    if(comment1===5)
    {
        clearInterval(update);
    }
},500);
function createUser()
{  
   createbackground.style.backgroundColor="#42378F";
   sidehome.style.backgroundColor="transparent";
   list.style.backgroundColor="transparent";
   createContainer.classList.remove("d-none");
   sidehome.style.color="white";
   homeContainer.classList.add("d-none");
   userslist.classList.add("d-none");
   images.style.backgroundColor="transparent";
   sidecontact.style.backgroundColor="transparent";
   imagegallery.classList.add("d-none");
   contactbg.classList.add("d-none");
}
function home()
{    
    sidehome.style.backgroundColor=" #cbcaca";
    createbackground.style.backgroundColor="transparent";
    list.style.backgroundColor="transparent";
    sidehome.style.color="black";
    createContainer.classList.add("d-none");
    homeContainer.classList.remove("d-none");
    images.style.backgroundColor="transparent";
    sidecontact.style.backgroundColor="transparent";
    userslist.classList.add("d-none");
    imagegallery.classList.add("d-none");
    contactbg.classList.add("d-none");
}
function userlist()
{   
   list.style.backgroundColor="#42378F";
   images.style.backgroundColor="transparent";
   sidehome.style.color="white";
   createbackground.style.backgroundColor="transparent";
   sidehome.style.backgroundColor="transparent";
   sidecontact.style.backgroundColor="transparent";
   createContainer.classList.add("d-none");
   homeContainer.classList.add("d-none");
   userslist.classList.remove("d-none");
   imagegallery.classList.add("d-none");
   contactbg.classList.add("d-none");
}
function gallery()
{   
    images.style.backgroundColor="#42378F";
    list.style.backgroundColor="transparent";
   sidehome.style.color="white";
   createbackground.style.backgroundColor="transparent";
   sidecontact.style.backgroundColor="transparent";
   sidehome.style.backgroundColor="transparent";
    imagegallery.classList.remove("d-none");
    createContainer.classList.add("d-none");
    homeContainer.classList.add("d-none");
    userslist.classList.add("d-none");
    contactbg.classList.add("d-none");
}
let sidecontact=document.getElementById("side-contact");
let contactbg=document.getElementById("contactbg");
function contactus()
{
    sidecontact.style.backgroundColor="#42378F";
    images.style.backgroundColor="transparent";
    list.style.backgroundColor="transparent";
   sidehome.style.color="white";
   createbackground.style.backgroundColor="transparent";
   sidehome.style.backgroundColor="transparent";
    contactbg.classList.remove("d-none");
    createContainer.classList.add("d-none");
    homeContainer.classList.add("d-none");
    userslist.classList.add("d-none");
    imagegallery.classList.add("d-none");

}
/*let username=document.getElementById("username");
let email=document.getElementById("email");
let regdno=document.getElementById("regdno");
let submitbtn=document.getElementById("submitbtn");
let branch=document.getElementById("selectbranch");
let gender=document.getElementById("gender");
let ssccgpa=document.getElementById("ssccgpa");
let intercgpa=document.getElementById("intercgpa");
let btechcgpa=document.getElementById("btechcgpa");
let table=document.getElementById("table");*/

document.addEventListener("DOMContentLoaded", function() {
    const registrationForm = document.getElementById("registrationForm");
    const studentTable = document.getElementById("studentTable");
    
    registrationForm.addEventListener("submit", function(event) {
        event.preventDefault();
        const student = getStudentFromForm();
        addStudentToTable(student);
        saveStudentToLocalstorage(student);
        registrationForm.reset();
    });
function getStudentFromForm() {
    const student = {};
    student.name = document.getElementById("name").value;
    student.regdno = document.getElementById("regdno").value;
    student.email = document.getElementById("email").value;
    student.branch = document.getElementById("branch").value;
    student.gender = getSelectedGender();
    student.ssccgpa = document.getElementById("ssccgpa").value;
    student.intercgpa = document.getElementById("intercgpa").value;
    student.btechcgpa = document.getElementById("btechcgpa").value;
    return student;
}

function getSelectedGender() {
    const genderRadios = document.getElementsByName("gender");
        for (let i = 0; i < genderRadios.length; i++) {
            if (genderRadios[i].checked) {
                return genderRadios[i].value;
            }
        }
    return "";
}
    
function addStudentToTable(student) {
    const row = document.createElement("tr");

    appendCell(row, student.name);
    appendCell(row, student.regdno);
    appendCell(row, student.email);
    appendCell(row, student.branch);
    appendCell(row, student.gender);
    appendCell(row, student.ssccgpa);
    appendCell(row, student.intercgpa);
    appendCell(row, student.btechcgpa);

    studentTable.appendChild(row);
}

function appendCell(row, value) {
    const cell = document.createElement("td");
    cell.textContent = value;
    row.appendChild(cell);
}
    
function saveStudentToLocalstorage(student) {
    let students = JSON.parse(localStorage.getItem("students")) || [];
    students.push(student);
    localStorage.setItem("students", JSON.stringify(students));
}
    
function loadStudentsFromLocalstorage() {
    let students = JSON.parse(localStorage.getItem("students")) || [];
    students.forEach(function(student) {
        addStudentToTable(student);
    });
}
    
loadStudentsFromLocalstorage();
});


/*
let details={
    "branch":"CSE",
    "gender":"Male"
};
gender.addEventListener('change',genderchange);
function genderchange(event)
{
    details.gender=event.target.value;
}
branch.addEventListener('change',branchchange);

function branchchange(event)
{
    details.branch=event.target.value;
}
let details={
    "name":username.value,
    "email":email.value,
    "regdno":regdno.value,
    "branch":"CSE",
    "gender":"Male",
    "ssccgpa":ssccgpa.value,
    "intercgpa":intercgpa.value,
    "btechcgpa":btechcgpa.value
};
submitbtn.onclick=function()
{   
    localStorage.setItem("details",JSON.stringify(details));
    tabledata(details);  
}
if(details===null)
{
    let details1=localStorage.getItem("details");
    details1=JSON.parse(details1);
    tabledata(details1);
}
let counter=0;  
function tabledata(details)
{   
    let tablerow=document.createElement('tr');
    table.appendChild(tablerow);
    counter=counter+1;
    let tabledata=document.createElement('td');
    tabledata.textContent=counter;
    tablerow.appendChild(tabledata);
    
    let tabledata0=document.createElement('td');
    tabledata0.textContent=details.name;
    tablerow.appendChild(tabledata0);

    let tabledata1=document.createElement('td');
    tabledata1.textContent=details.email;
    tablerow.appendChild(tabledata1);

    let tabledata2=document.createElement('td');
    tabledata2.textContent=details.regdno;
    tablerow.appendChild(tabledata2);

    let tabledata3=document.createElement('td');
    tabledata3.textContent=details.branch;
    tablerow.appendChild(tabledata3);

    let tabledata4=document.createElement('td');
    tabledata4.textContent=details.gender;
    tablerow.appendChild(tabledata4);

    let tabledata5=document.createElement('td');
    tabledata5.textContent=details.ssccgpa;
    tablerow.appendChild(tabledata5);

    let tabledata6=document.createElement('td');
    tabledata6.textContent=details.intercgpa;
    tablerow.appendChild(tabledata6);

    let tabledata7=document.createElement('td');
    tabledata7.textContent=details.btechcgpa;
    tablerow.appendChild(tabledata7);


}*/