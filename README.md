<div align="center">

<img src="assets/logo.png" alt="Cactus Cibersegurança" width="260">

# Cactus · Avaliação de Segurança Linux

Repositório de evidências da avaliação de segurança **read-only** de um servidor Linux.

</div>

---

## Sobre

Aqui ficam as saídas de comandos, capturas de tela e relatórios produzidos durante a avaliação, organizados por fase. Nenhuma alteração é feita no servidor avaliado: o trabalho é apenas de coleta, análise e recomendação.

## Estrutura

```text
├── F1-kickoff-contrato/            # Proposta e regras de engajamento
├── F2-reconhecimento-inventario/   # Portas, serviços e inventário do SO
├── F3-avaliacao-tecnica/           # Hardening, SELinux/AppArmor, kernel e logs
├── F4-conformidade/                # OpenSCAP/CIS, CVEs e matriz de risco
├── F5-entrega/                     # Relatório técnico e apresentação
└── assets/                         # Logo da Cactus
```

## Padrão das evidências

```text
F<fase>-<frente>-<nº>_<descricao>.<ext>
```

Exemplo: `F3-HARD-001_ssh-config.txt`

Para garantir a integridade, gere os hashes após adicionar evidências:

```bash
sha256sum F*/* > HASHES.sha256    # gerar
sha256sum -c HASHES.sha256        # conferir
```

## Ferramentas

`Lynis` · `OpenSCAP` · `Nmap` · `Nikto` · `ssh-audit` · `journalctl` · `sysctl`

## Equipe

Alexandre · Bernardo · Miguel · Pedro

<div align="center">
<sub>© 2026 Cactus Cibersegurança</sub>
</div>
