# Binance Moonshots (MCP Server)

Copia del **binance-trend-finder** enfocada en **moonshots**: micro/small caps para
**invertir poco a cambio de mucho retorno**. Monedas de bajo volumen que se mueven
fácil con poco capital. Misma lógica de momentum positivo (racha verde, ganancia
neta semanal, ATR), pero sobre un universo filtrado.

> ⚠️ Apuestas asimétricas: tamaño pequeño, stops definidos. El spread en <$500K es bravo.

## Diferencias vs trend-finder

| | trend-finder | smallcaps (este) |
|---|---|---|
| Volumen 24h | > $5M (sin techo) | Banda **$0.5M – $30M** |
| Gigantes (BTC/ETH/SOL...) | Incluidos | **Excluidos** por techo de volumen |
| Stablecoins/fiat | Parcial | **Excluidas siempre** (USDC, FDUSD, TUSD, DAI, EUR...) |
| Leverages (UP/DOWN/BULL/BEAR) | Excluidos | Excluidos |
| ATR mínimo | 2.0% | **3.0%** (vara más alta: se mueven fácil) |

## Tools

- `scan_smallcap_movers` — top smallcaps con momentum positivo sostenido
- `get_coin_analysis` — análisis detallado de un símbolo
- `list_smallcap_pairs` — universo smallcap en la banda de volumen

## Ejemplo

```python
scan_smallcap_movers(top_n=10)                        # defaults: banda 0.5M-30M, ATR>=3%
scan_smallcap_movers(max_volume=10_000_000)           # micro-caps solamente
scan_smallcap_movers(min_atr_pct=5.0)                 # solo las más violentas
```

## Instalación / uso

```bash
pip install mcp requests
```

OpenCode (`opencode.json`) / Hermes (`config.yaml`): apunta el comando a
`C:\Users\jhonv\Downloads\binance-smallcaps\server.py` con `C:\Python313\python.exe`.

## License

MIT
