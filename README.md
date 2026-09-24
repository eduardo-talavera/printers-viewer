# printers-viewer
printers-viewer

```js
//PUT /api/printers/metrics
//Origin: http://localhost:5173
//Authorization: Bearer <TOKEN>

async function actualizarMetricas(token, impresoras) {
  const response = await fetch(
    "https://TU-DOMINIO.onrender.com/api/printers/metrics",
    {
      method: "PUT",
      headers: {
        "Content-Type": "application/json",
        Authorization: `Bearer ${token}`,
      },
      body: JSON.stringify(impresoras),
    }
  );

  const result = await response.json();

  if (!response.ok) {
    throw new Error(result.error?.message ?? "Error al actualizar métricas");
  }

  return result;
}

await actualizarMetricas(sessionToken, [
  {
    "serialNumber": "H7X4603511",
    "isColor": true,
    "pageCounters": {
      "color": 1250,
      "blackAndWhite": 750,
      "total": 2000
    },
    "tonerLevels": {
      "yellow": 81,
      "magenta": 64.5,
      "cyan": 72,
      "black": 58
    }
  },
  {
    "serialNumber": "1A24Y21847",
    "isColor": false,
    "pageCounters": {
      "blackAndWhite": 9500
    },
    "tonerLevels": {
      "black": 37
    }
  }
]);
```
