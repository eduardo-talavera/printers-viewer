# printers-viewer
printers-viewer

PUT /api/printers/metrics
Origin: http://localhost:5173
Authorization: Bearer <TOKEN>

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
    serialNumber: "SERIE-001",
    isColor: true,
    pageCounters: {
      color: 400,
      blackAndWhite: 600,
      total: 1000,
    },
    tonerLevels: {
      yellow: 80,
      magenta: 70,
      cyan: 60,
      black: 50,
    },
  },
]);
