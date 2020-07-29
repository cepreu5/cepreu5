<body style="text-align:left; font-family:Arial; font-size:14px; color: var(--LblColor);" 
	onload="init()">

	<fieldset ID="Main">

		<div ID="PwdFld">
				<input id="Password" type="password" class="inputMessage" placeholder="Парола"/>&nbsp;&nbsp;
				<img id="Suc2" style="width: 20px; height: 14px;" src="Suc.png" onclick='init2()'>
				<script>
				var input = document.getElementById("Password");
				input.addEventListener("keyup", function(event) {
					if (event.keyCode === 13) {
					 event.preventDefault();
					 document.getElementById("Suc2").click();
					}
				});
				</script>
		</div>

		<SELECT ID="Files" style="vertical-align: super;" onChange="SelFile()" class="inputMessage">
		</SELECT>
		&nbsp;&nbsp;&nbsp;&nbsp;
		<a><img src="Remove.png" width="20px" onclick="ClearTextArea()" title="Изтриване"></a>
		&nbsp;&nbsp;&nbsp;&nbsp;
		<a><img src="Copy.png" width="20px" onclick="doSelectAll()" title="Copy"></a>
		&nbsp;&nbsp;&nbsp;&nbsp;
		<a><img ID="ZoomBtn" src="zoom.png" width="20px" onclick="CZoom()" title="Увеличи"></a>
		&nbsp;&nbsp;&nbsp;
		<a><img src="Palette.png" width="15px" style="vertical-align: super" onclick="switchSheet()" title="Тема"></a>
		<br>
		<textarea ID="MsgText" rows="5" style="width: 320px" class="inputMessage"
			onInput="AutoTempl()" onFocus="AutoTempl()">
		</textarea>
		<br>
		Шаблони 
		<span ID="Sel"></span>&nbsp;Авто
		<a><img src="On.png" ID="Yes" style="width: 60px; height: 30px; display:none" align="center"
			onclick="NoAuto()" title="Авто"></a> 
		<a><img src="Off.png" ID="No" style="width: 60px; height: 30px; display:none" align="center" 
			onclick="NoAuto()" title="Авто"></a> 
		<a><img src="Space.png" width="20px" onclick="Normal()" ID="NormBtn"
			align="center" title="Нормализация"></a>
		<span ID="Info"><br></span>
		<br>
		<span ID="Sels"></span>
		<br>
		
		<!-- Calc -->
				<div style="margin-left: 1px; text-align: center;">
				<span ID="CalcSp"><br>
					<table border="0" width="90%"> 
						<tr> 
							<td colspan="3"><input type="text" id="result"/></td> 
							<!-- clr() function will call clr to clear all value -->
							<td><input type="button" class="cbutton" value="C" onclick="clr()"/> </td> 
						</tr> 
						<tr> 
							<!-- create button and assign value to each button -->
							<!-- dis("1") will call function dis to display value -->
							<td><input type="button" class="cbutton" value="1" onclick="dis('1')"/> </td> 
							<td><input type="button" class="cbutton" value="2" onclick="dis('2')"/> </td> 
							<td><input type="button" class="cbutton" value="3" onclick="dis('3')"/> </td> 
							<td><input type="button" class="cbutton" value="/" onclick="dis('/')"/> </td> 
						</tr> 
						<tr> 
							<td><input type="button" class="cbutton" value="4" onclick="dis('4')"/> </td> 
							<td><input type="button" class="cbutton" value="5" onclick="dis('5')"/> </td> 
							<td><input type="button" class="cbutton" value="6" onclick="dis('6')"/> </td> 
							<td><input type="button" class="cbutton" value="-" onclick="dis('-')"/> </td> 
						</tr> 
						<tr> 
							<td><input type="button" class="cbutton" value="7" onclick="dis('7')"/> </td> 
							<td><input type="button" class="cbutton" value="8" onclick="dis('8')"/> </td> 
							<td><input type="button" class="cbutton" value="9" onclick="dis('9')"/> </td> 
							<td><input type="button" class="cbutton" value="+" onclick="dis('+')"/> </td> 
						</tr> 
						<tr> 
							<td><input type="button" class="cbutton" value="." onclick="dis('.')"/> </td> 
							<td><input type="button" class="cbutton" value="0" onclick="dis('0')"/> </td> 
							<!-- solve function call function solve to evaluate value -->
							<td><input type="button" class="cbutton" value="=" onclick="solve()"/> </td> 
							<td><input type="button" class="cbutton" value="*" onclick="dis('*')"/> </td> 
						</tr> 
					</table>
					<br>
				</span>
				</div>

		<form name="submit-to-google-sheet" onsubmit="return false;">
			<input style="text-align:center; width: 9.5em" class="inputMessage" name="Field1" ID=res1 value="">
			<img src="Calendar.png" width="30px" align="center" title="Дата"
         onclick="if(event.ctrlKey) {ClearFld('res1'); return false;} else {InsDate();}">
			<input style="text-align:center; width: 9.5em" class="inputMessage" name="Field2" 
				ID=res2 value="">
			<img src="Calculator.png" width="30px" align="center" title="Калкулатор"
        onclick="if(event.ctrlKey) {ClearFld('res2'); return false;} else {Calc('res2');}">
			<input style="text-align:center; width: 9.5em" class="inputMessage" name="Field3" ID=res3 value=""
				list="acc-options">
				<datalist id="acc-options">
				</datalist>
			<img src="Remove.png" width="30px" onclick="ClearFld('res3')"
					align="center" title="Изтриване">
			<input style="text-align:center; width: 9.5em" class="inputMessage" name="Field4" ID=res4 value="">
				<img src="Remove.png" width="30px" onclick="ClearFld('res4')"
					align="center" title="Изтриване">
			<input style="text-align:center; width: 9.5em" class="inputMessage" name="Field5" ID=res5 
				value="">
				<img src="Remove.png" width="30px" onclick="ClearFld('res5')"
					align="center" title="Изтриване">
			<input style="text-align:center; width: 9.5em" class="inputMessage" name="Field6" ID=res6 
				value="">
				<img src="Remove.png" width="30px" onclick="ClearFld('res6')"
					align="center" title="Изтриване">
			<SELECT ID="Cats" class="inputMessage" style="width: 9.5em" name="Field7"
				onChange="createSubCat('SubCat'+this.selectedIndex)">
				<option value="" selected>Категория</option>
			</SELECT>&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp
			<SELECT ID="SubCats" class="inputMessage" style="width: 9.5em;" name="Field8">
				<option value="" selected>Подкатегория</option>
			</SELECT>
			<br>
			<span ID="NoteFld">
				Бележка: 
				<input style="text-align:left; width: 17em" ID="Note" class="inputMessage" name="Field9" 
					list="combo-options" value="">
				<datalist class="inputMessage" id="combo-options">
				</datalist>
				<a><img src="Remove.png" width="30px" onclick="ClearFld('Note')"
					align="center" title="Изтриване"></a>
			</span><br>
			<table><tr ID="TRow">
				<td ID="Cell1"><input type="image" name="submit" src="Send.png" style="width: 70px;" border="0" 
					title="Изпрати" onclick="showDiv()" alt="Изпрати"></td>
				<td ID="Cell2"><img style="width: 70px;" src="Extract.png" title="Екстракт" ID="ExtBtn"
					onclick="ExtClick()">
				</td>
				<td ID="Cell3"><img style="width: 70px;" src="Note.png" ID="NoteBtn" onclick="ShowNote()" 
					title="Бележка"></td>
				<td ID="Cell4"><img src="Template.png" style="width: 70px;" onclick="MakeTempl()" 
					title="Шаблон">
				</td>
				<td>
					<img id="loadingGif" style="width: 20px; display:none" src="Progress.gif"
						onclick='style="display: none"'>
					<img id="Suc" style="width: 20px; display:none" src="Suc.png"
						onclick='style="display: none"'>
					<a><img ID="ZoomBtn2" src="zoom2.png" onclick="CZoom()" 
						style="display:none" title="Намали"></a>
				</td></tr>
			</table>
		</form>

		<script>
			const form = document.forms['submit-to-google-sheet']
			form.addEventListener('submit', e => {
				e.preventDefault()
				fetch(
					scriptURL, {method: 'POST', body: new FormData(form)})
					.then(response => showSuc())
					.catch(error => alert('Грешка! ' + error.message))
				if (document.getElementById("Cats").selectedIndex==1) { // in case of transfer
					var WM=1, N;
					if (document.getElementById("res4").value.substr(3,1)=="/") {
						WM=document.getElementById("res5").value
					}
					var S=document.getElementById("res2").value
					N=parseFloat(S)*parseFloat(WM)
					if (document.getElementById("res4").value.substr(0,4)=="BGN/") {
							N=parseFloat(S)/parseFloat(WM)
					}
					if (!isNaN(N)) {
						S=N.toString()
						S=parseFloat(S).toFixed(2)
					}
					if (S.substr(0,1)=="-") {S=S.substr(1,S.length-1)}
					else {S="-"+S}
					document.getElementById("res2").value=S
					var AccSave=document.getElementById("res3").value
					document.getElementById("res3").value=
						document.getElementById("SubCats").value
					document.getElementById("SubCats").value=AccSave
					fetch(scriptURL, {method: 'POST', body: new FormData(form)})
						.then(res => {
							if(res.ok) {
							return res;
							} else {
							throw Error(`Request rejected with status ${res.status}`);
							}
						})
						.catch(error => alert('Грешка! ' + error.message))
				}
			})
		</script>
		
		<span ID="TemplFld">
			Шаблон: <input style="text-align:left; width: 18em" ID="res" class="inputMessage" value="">
			<a><img src="Remove.png" width="20px" onclick="ClearFld('res')"
				align="center" title="Изтриване"></a>
			<br>
			CSV: <input style="text-align:left; width: 19.8em" ID="CSV" class="inputMessage" value=""> 
			<a><img src="Copy.png" width="20px" align="top" onclick="CopyCSV()" title="Copy"></a>
		</span>
		<span ID="Author" style="font-family:Arial; font-size:10px; color: var(--LblColor, white);">
		&nbsp&nbsp
		<a><img src="Palette.png" width="15px" style="vertical-align: sub" onclick="ShowColors()" title="Цвят"></a>	
		&nbsp
			<input type="color" value="#FFFFFF" id="colorPicker" hidden>
			<SELECT ID="Colors" onChange="setColor()" class="inputMessage" hidden>&nbsp
				<option value="--FormBgrd">- Оцвети -</option>
				<option value="--FormBgrd">Фон</option>
				<option value="--FormColor">Форма</option>
				<option value="--BtnColor">Бутони</option>
				<option value="--InpBgrd">Полета</option>
				<option value="--LblColor">Етикети</option>
				<option value="--InpText">Текст</option>
			</SELECT>
			&nbsp&nbsp&nbsp
			© 2020 CX Extractor v. 4.09 /
		</span>
	</fieldset>
</body>

<!--
### Hi there 👋

**cepreu5/cepreu5** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
