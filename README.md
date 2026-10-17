<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/logo-dark.png">
  <img src="assets/logo-light.png" alt="Cactus Cibersegurança" width="260">
</picture>

# Avaliação de Segurança em Servidores Linux

**Cactus Cibersegurança** · Consultoria em segurança de infraestrutura Linux

![Modo](https://img.shields.io/badge/modo-read--only-8DA83A?style=flat-square)
![Duração](https://img.shields.io/badge/duração-7%20semanas-3D4A16?style=flat-square)
![Horas](https://img.shields.io/badge/esforço-116%20h-3D4A16?style=flat-square)
![Ferramentas](https://img.shields.io/badge/ferramentas-open--source-8DA83A?style=flat-square)
![Frameworks](https://img.shields.io/badge/CIS%20·%20ISO%2027001%20·%20NIST%20CSF-1C2118?style=flat-square)

</div>

---

## 📌 Sobre o projeto

Este repositório reúne o trabalho da Cactus Cibersegurança na **avaliação de segurança somente leitura (read-only)** do servidor Linux da **Academia Bamp**.

O objetivo é medir, com evidências, o risco do ambiente — **sem alterar nada em produção**. Ao final, a Academia Bamp recebe um relatório técnico com achados classificados por severidade, matriz de risco e um plano de remediação priorizado, **documentado, mas não aplicado**.

> [!IMPORTANT]
> Toda a coleta usa apenas comandos de leitura. O `sudo` é usado somente para **ler** configurações e logs protegidos, nunca para modificar arquivos, serviços ou pacotes.

---

## 🎯 Escopo

**Alvo:** 1 servidor Linux (VM em nuvem), acessado por contas individuais com sudo via SSH.
**Serviços expostos:** Apache/Nginx, MySQL, SSH, FTP e Samba.

| Pilar | O que é avaliado |
|---|---|
| **1. Hardening Linux** | Contas, senhas, permissões, binários SUID/SGID, serviços ativos, SSH, firewall e desvios do CIS Benchmark |
| **2. Proteção do SO** | SELinux/AppArmor, parâmetros de kernel (sysctl), versão do kernel e pacotes desatualizados |
| **3. Observabilidade** | Logs do sistema e dos serviços, rotação de logs, auditoria e monitoramento de integridade |
| **4. Conformidade** | OpenSCAP + SCAP Security Guide e aderência ao CIS, mapeada para ISO 27001 e NIST CSF |
| **5. Vulnerabilidades e CSIRT** | CVEs em pacotes e serviços, matriz de risco e recomendações de resposta a incidentes |

<table>
<tr>
<td width="50%" valign="top">

**✅ Inclui**
- Inventário e avaliação de *hardening* e configuração
- Análise de SELinux/AppArmor e de logs
- Varredura de vulnerabilidades (não intrusiva)
- Matriz de risco (probabilidade × impacto)
- Plano de remediação recomendado

</td>
<td width="50%" valign="top">

**🚫 Não inclui**
- Aplicar correções no servidor
- Exploração destrutiva ou PoC de *exploits*
- Alterar qualquer estado do ambiente
- *Pentest* intrusivo, DoS ou quebra de senhas

</td>
</tr>
</table>

---

## 🧭 Metodologia e cronograma

**Princípio:** avaliar, registrar evidências e recomendar — sem executar remediações.

| Fase | Atividades | S1 | S2 | S3 | S4 | S5 | S6 | S7 | Horas |
|---|---|:-:|:-:|:-:|:-:|:-:|:-:|:-:|--:|
| **1. Kickoff e contrato** | Abertura, regras de engajamento, aceite | 🟩 | | | | | | | 8 h |
| **2. Reconhecimento e inventário** | Portas, serviços, SO, pacotes, usuários | | 🟩 | 🟩 | | | | | 16 h |
| **3. Avaliação técnica** | Hardening, SELinux/AppArmor, kernel, logs | | | 🟩 | 🟩 | 🟩 | | | 40 h |
| **4. Conformidade** | OpenSCAP/CIS, CVEs, matriz de risco | | | | | 🟩 | 🟩 | | 28 h |
| **5. Entrega** | Relatório técnico e apresentação executiva | | | | | | | 🟩 | 24 h |
| | | | | | | | | | **116 h** |

> Kickoff com a entrega da proposta comercial em **20/10/2026**. A avaliação técnica só começa após o aceite formal.

---

## 🛠️ Ferramentas

Todas open-source, sem custo de licença.

| Finalidade | Ferramentas |
|---|---|
| Avaliação e conformidade | `Lynis` · `OpenSCAP` + `SCAP Security Guide` · `CIS-CAT Lite` |
| Reconhecimento externo | `Nmap` · `Nikto` · `ssh-audit` |
| Monitoramento e proteção *(avaliadas, não instaladas)* | `auditd` · `Wazuh` · `fail2ban` · `AIDE` |
| Coleta nativa | `ss` · `systemctl` · `find` · `getenforce` / `aa-status` · `sysctl` · `journalctl` |

---

## 📁 Estrutura do repositório

```text
cactus/
├── F1-kickoff-contrato/            # Proposta comercial, regras de engajamento, termo de aceite
├── F2-reconhecimento-inventario/   # Portas, serviços, versões, inventário do SO
├── F3-avaliacao-tecnica/           # Hardening, SELinux/AppArmor, kernel, logs e auditoria
├── F4-conformidade/                # OpenSCAP/CIS, CVEs, matriz de risco
├── F5-entrega/                     # Relatório técnico e apresentação executiva
├── assets/                         # Logo e imagens do README
└── README.md
```

---

## 🔐 Registro de evidências

Cada achado registra **identificador, comando executado, saída (ou captura de tela), data/hora e responsável**.

**Padrão de nome:**

```text
F<fase>-<frente>-<nº>_<descricao>.<ext>
```

Exemplo: `F3-HARD-001_ssh-config.txt`

**Integridade (SHA-256):** após adicionar evidências, gere e versione os hashes:

```bash
sha256sum F*/* > HASHES.sha256     # gerar
sha256sum -c HASHES.sha256         # conferir
```

---

## 📦 Entregáveis

| # | Entregável | Fase |
|:-:|---|:-:|
| 1 | Proposta comercial e termo de aceite | 1 |
| 2 | Inventário do ambiente | 2 |
| 3 | Pacote de evidências (com hashes SHA-256) | 3–4 |
| 4 | Matriz de risco (Crítica · Alta · Média · Baixa) | 4 |
| 5 | **Relatório técnico** — achados, matriz de risco e plano de remediação mapeado a CIS, ISO 27001 e NIST CSF | 5 |
| 6 | **Apresentação executiva** — 20 min para a gestão da Academia Bamp | 5 |

---

## 👥 Equipe

Cada consultor lidera uma frente e revisa o trabalho de outro — nenhum achado entra no relatório sem dupla checagem.

| Consultor | Papel | Frentes | Revisa |
|---|---|---|---|
| **Alexandre** | Interlocutor e gerente do projeto | Contato com o cliente, cronograma, consolidação do relatório | Pedro |
| **Bernardo** | Consultor de *hardening* | Pilares 1 e 2 | Miguel |
| **Miguel** | Consultor de observabilidade e conformidade | Pilares 3 e 4 | Bernardo |
| **Pedro** | Consultor de vulnerabilidades | Pilar 5, matriz de risco e resposta a incidentes | Alexandre |

**Como trabalhamos**
- Reunião semanal de 30 minutos para status e bloqueios.
- Pastas por fase e evidências nomeadas pelo padrão acima.
- Cada consultor usa apenas sua própria conta no servidor, para que os registros de acesso identifiquem quem executou cada comando.

---

## ⚠️ Limitações

- Nenhuma correção é aplicada — o plano de remediação é entregue para execução pela equipe do cliente.
- Os resultados refletem o estado do servidor nas datas da coleta.
- A identificação de CVEs depende das versões informadas pelos pacotes (pode haver falsos positivos e negativos).
- Se houver indício de risco iminente, a avaliação daquele item é interrompida e a Academia Bamp é comunicada imediatamente, sem agir no servidor.

---

<div align="center">

📄 [Proposta comercial completa (PDF)](F1-kickoff-contrato/Proposta_Comercial_Cactus_Ciberseguranca.pdf)

<sub>© 2026 Cactus Cibersegurança</sub>

</div>
