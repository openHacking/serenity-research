# Serenity Research Skill

[English](README.md) | [中文](README.zh-CN.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Español](README.es.md)

Serenity Research es un skill de IA open source para convertir narrativas de mercado en investigación de inversión estructurada.

Está inspirado en patrones públicos de investigación estilo Serenity, pero es un marco original. El skill se enfoca en mapear una tendencia hacia shocks de demanda, capas de la cadena de valor, restricciones escasas, beneficiarios de segundo y tercer orden, calidad de evidencia, hipótesis de desajuste de precio y pruebas de falsación.

```text
trend -> demand shock -> value chain -> scarce layer -> second/third-order beneficiaries -> evidence -> mispricing hypothesis -> falsification
```

Solo ofrece apoyo de investigación. Este skill no proporciona asesoría financiera personalizada, ejecución de operaciones, retornos garantizados ni instrucciones de compra o venta.

## Inicio en 30 segundos

El CLI `skills` no requiere elegir un cliente de IA específico. Si tu entorno lo permite, instala con:

```bash
npx skills add https://github.com/openHacking/serenity-research --skill serenity-research
```

Si prefieres que un agente de IA lo instale por ti, usa el prompt que corresponda a tu cliente.

**Codex**

```text
Instala el skill serenity-research para Codex. Clona https://github.com/openHacking/serenity-research en ${CODEX_HOME:-$HOME/.codex}/skills/serenity-research y luego verifica que existan SKILL.md, README.md y agents/openai.yaml.
```

Para una instalación de Codex a nivel de proyecto, coloca el repositorio en `.codex/skills/serenity-research`.

**Claude Code u otro cliente con `skills` CLI**

```text
Instala el skill serenity-research desde https://github.com/openHacking/serenity-research usando el CLI skills. Después de instalarlo, verifica que el skill esté disponible como serenity-research.
```

**Otros agentes con shell**

```text
Instala serenity-research desde https://github.com/openHacking/serenity-research como un skill local de IA. Usa el CLI skills si está disponible. Si no, usa el directorio de skills requerido por este cliente y verifica que el cliente pueda descubrir SKILL.md.
```

Para actualizar una instalación existente de Codex:

```text
Actualiza serenity-research. Ve a ${CODEX_HOME:-$HOME/.codex}/skills/serenity-research, ejecuta git pull y reporta el commit más reciente.
```

Después de instalar, pregunta a tu agente:

```text
Usa serenity-research para mapear la cadena eléctrica de los centros de datos de IA y clasificar los beneficiarios de segundo orden más interesantes.
```

## Para qué ayuda

- Convertir un tema de mercado en un mapa de investigación.
- Encontrar cuellos de botella y capas escasas en la cadena industrial.
- Mirar más allá de los ganadores obvios hacia proveedores e infraestructura habilitadora.
- Cuestionar si una empresa realmente se beneficia de una tendencia.
- Ordenar candidatos por prioridad de investigación.
- Generar prompts de investigación profunda para temas de mercado y cadenas industriales.
- Construir listas de evidencia y condiciones de falsación.

## Estructura del repositorio

```text
serenity-research/
|-- SKILL.md
|-- README.md
|-- README.zh-CN.md
|-- README.ja.md
|-- README.ko.md
|-- README.es.md
|-- LICENSE
|-- agents/
|   `-- openai.yaml
|-- examples/
|   |-- theme-scan.md
`-- evals/
    `-- test-cases.md
```

## Prompts de ejemplo

Pide `serenity-research` directamente o describe la tarea con lenguaje estilo Serenity:

```text
Crea un prompt de investigación estilo Serenity para la cadena de suministro de infraestructura de IA.
```

```text
Cuestiona si Company X es realmente un cuello de botella en la cadena de suministro de robótica.
```

```text
Usa serenity-research para enseñarme el método con una pregunta a la vez.
```

## Salida predeterminada

El skill normalmente devuelve:

```text
1. Judgment first
2. Demand shock
3. Value-chain map
4. Scarce layers
5. Beneficiary layers
6. Candidate research list
7. Evidence checklist
8. What the market may be missing
9. Falsification conditions
10. Next verification steps
```

## Marco de puntuación

Al clasificar candidatos, el skill usa una puntuación de prioridad de investigación de 100 puntos:

| Dimension | Points |
| --- | ---: |
| Theme relevance | 20 |
| Earnings elasticity | 20 |
| Scarcity / bottleneck control | 20 |
| Evidence strength | 20 |
| Market recognition gap | 20 |

Las puntuaciones son prioridades de investigación, no pronósticos de retorno.

## Ejemplo: análisis de tema

En lugar de preguntar qué empresa popular está de moda, el skill pregunta:

- ¿Qué shock de demanda es observable?
- ¿Qué capas de la cadena de valor deben escalar?
- ¿Qué capas son difíciles de expandir rápidamente?
- ¿Qué proveedores de segundo y tercer orden pueden tener mayor elasticidad de ganancias?
- ¿Qué evidencia confirmaría o debilitaría la tesis?

Consulta [examples/theme-scan.md](examples/theme-scan.md) para un prompt reutilizable.

## Estándares de evidencia

Prioriza fuentes primarias y verificables:

- reportes y filings de empresas
- informes anuales e intermedios
- transcripciones de resultados
- presentaciones para inversores
- documentos de bolsa
- anuncios oficiales
- registros de compras
- registros regulatorios
- patentes y estándares
- contratos confirmados

Usa redes sociales y comentarios sin fuente solo como pistas de ideas. Las afirmaciones actuales de mercado deben verificarse con datos actuales antes de clasificar valores.

## Límites de investigación

Este skill está diseñado para investigación, priorización y prueba de tesis. No debe:

- prometer retornos
- decirle a un usuario qué comprar o vender
- inventar datos de mercado
- usar rumores como prueba
- tratar redes sociales como evidencia final
- ignorar riesgos de liquidez, valoración, regulación o gobierno corporativo

Las decisiones finales de inversión siguen siendo responsabilidad del usuario.

## License

MIT. See [LICENSE](LICENSE).
