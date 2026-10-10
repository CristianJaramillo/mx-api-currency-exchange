# Bank Currency Exchange

**Versión:** 1.0.1  
**Contacto:** cristian_gerar@hotmail.com

`Currency Exchange` es un servicio de mostrador (Over-The-Counter) donde se realiza el intercambio de divisas. Cada transacción puede usar tipos de cambio preferenciales y puede incluir comisiones por transacción. En algunos casos, los cheques de viajero pueden manejarse como una pseudo-divisa dentro de esta capacidad.

---

## 🌐 Entornos disponibles

| Entorno     | URL base                                                                |
|-------------|-------------------------------------------------------------------------|
| Producción   | `https://api.bank.mx/customerServices/currencyExchange`               |
| Desarrollo  | `https://dev.bank.mx/customerServices/currencyExchange`                |

---

## 📃 Descripción general de operaciones

Esta API permite manejar el ciclo de vida de una transacción de cambio de divisas incluyendo:

- **Initiate:** Crear una nueva transacción.
- **Update:** Modificar una transacción en estado pendiente.
- **Execute:** Ejecutar una transacción previamente iniciada.
- **Retrieve:** Consultar detalles completos de una transacción.
- **Control:** Cancelar una transacción para evitar que se procese.

Cada operación está alineada al modelo BIAN y refleja una acción específica sobre la entidad de `CurrencyExchangeTransaction`.

---

## 📄 Recursos disponibles

| Método | Path                                           | Descripción |
|--------|--------------------------------------------------|-------------|
| POST   | `/v1/transaction/initiate`                       | Crea una nueva solicitud de cambio de divisa para un cliente. Define moneda de origen, destino, monto, tipo de cambio, comisiones y método de pago. |
| PUT    | `/v1/transaction/update`                         | Permite ajustar información de una transacción si aún está en estado pendiente o en proceso. Modifica valores como monto, tipo de cambio, etc. |
| PUT    | `/v1/transaction/execute`                        | Ejecuta la transacción previamente iniciada. Representa la ejecución efectiva del intercambio de divisas, aplicando el tipo de cambio acordado. |
| GET    | `/v1/transaction/{transactionId}/retrieve`       | Obtiene toda la información relacionada a una transacción previamente registrada. ÚTil para validaciones, reportes o presentación al cliente. |
| PUT    | `/v1/transaction/control`                        | Cambia el estado de una transacción para indicar su cancelación. Evita que avance o afecte saldos. |

---

## ⛔️ Códigos de error comunes

| Código | Descripción |
|--------|-------------|
| `400`  | Solicitud mal formada |
| `401`  | No autenticado |
| `403`  | Acceso denegado |
| `404`  | Transacción no encontrada |
| `409`  | Conflicto en el estado actual |
| `500`  | Error interno del servidor |

---

## 🔐 Seguridad

Esta API utiliza **Bearer Authentication (JWT)** para proteger los endpoints.

```http
Authorization: Bearer <token>
```

---

## ✏️ Contacto

Para soporte, dudas o mejoras, contactar a: cristian_gerar@hotmail.com
