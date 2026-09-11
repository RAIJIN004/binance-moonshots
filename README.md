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

## Filtro INTRADIA (reemplaza al ATR diario)

El ATR diario miraba el pasado: una moneda podía moverse ayer y estar muerta hoy.
Ahora el filtro es **1h + 4h + spike de volumen** (velas 15m): solo pasa lo que se
mueve AHORA. El ATR quedó como dato informativo en `get_coin_analysis`.

## Tools

- `scan_smallcap_movers` — top smallcaps moviéndose ahora mismo
- `get_coin_analysis` — análisis + bloque `intraday_now` en vivo
- `list_smallcap_pairs` — universo smallcap en la banda de volumen

## Ejemplo

```python
scan_smallcap_movers(top_n=10)                        # defaults: 1h>=1.5%, 4h>=2%, spike>=1.0
scan_smallcap_movers(max_volume=10_000_000)           # micro-caps solamente
scan_smallcap_movers(min_1h_pct=3.0, min_vol_spike=2.0)  # solo pumps violentos con volumen
```

## Instalación / uso

```bash
pip install mcp requests
```

OpenCode (`opencode.json`) / Hermes (`config.yaml`): apunta el comando a
`C:\Users\jhonv\Downloads\binance-smallcaps\server.py` con `C:\Python313\python.exe`.

## License

MIT
