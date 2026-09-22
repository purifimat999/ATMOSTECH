[AtmosTech.js](https://github.com/user-attachments/files/32525699/AtmosTech.js)
function atualizarAlertaUmidade(dadosRecentes) {
	let alerta = document.getElementById("alertaUmidade");

	if (!alerta) {
		alerta = document.createElement("div");
		alerta.id = "alertaUmidade";
		alerta.setAttribute("role", "alert");
		alerta.textContent = "Atenção: Umidade Crítica! Risco à saúde.";

		alerta.style.cssText = `
			display: none;
			width: 100%;
			padding: 14px 18px;
			margin-bottom: 18px;
			border-radius: 8px;
			background-color: #d32f2f;
			color: #ffffff;
			font-weight: bold;
			text-align: center;
			box-shadow: 0 4px 12px rgba(0, 0, 0, 0.25);
		`;

		const topo = document.querySelector(".dashboard") || document.body;
		topo.prepend(alerta);
	}

	const umidadeNumerica = Number(dadosRecentes.umidade);
	alerta.style.display = umidadeNumerica < 30 ? "block" : "none";
}

// Use no callback do Firebase, depois de obter dadosRecentes.
atualizarAlertaUmidade(dadosRecentes);
