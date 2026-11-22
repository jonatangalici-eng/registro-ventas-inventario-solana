# Registro de Ventas con Inventario - Solana

Proyecto del Solana Engineer Track (Advance Bootcamp) de WayLearn.
Autor: JONATHAN GALICIA ROBLES

## Program ID (Devnet)
HbwMT5JUCi36kikH7hNHdz6DfKiExdt3vYbk4Kifp8wh

## Que hace
Programa en Rust y Anchor basado en el registro de ventas del bootcamp.
La informacion se reparte en cuentas PDA en lugar de una sola cuenta:
registro, cliente, venta y producto.

## Que agregue
1. Inventario de productos: cada producto es una cuenta PDA con SKU, categoria y stock.
2. Cada venta descuenta 1 unidad de stock. Si no hay stock, la venta se rechaza (error SinStock).
3. Cada devolucion regresa 1 unidad al stock.
4. Reposicion de stock (reponer_stock), que actualiza la cuenta del producto.
5. Cambio de nombre de cliente (cambiar_nombre_cliente).
6. Cierre condicionado de cuenta (cerrar_cliente): solo se puede cerrar si el cliente no tiene compras. La renta regresa al owner.
7. Validaciones y errores personalizados: nombre vacio o muy largo, monto 0, limite de 10 clientes y 10 ventas, SKU y categoria invalidos.
8. Correccion: el SKU de la venta permitia solo 5 caracteres; ahora permite 10.

## Permisos
Todas las instrucciones exigen que el firmante sea el owner del registro (has_one = owner).

## Como correrlo
1. Abrir beta.solpg.io y crear un proyecto Anchor.
2. Pegar lib.rs en src/lib.rs y presionar Build y luego Deploy (Devnet).
3. Pegar client.ts en client/client.ts y presionar Run.
El cliente ejecuta 19 pasos: crea registro, clientes y productos, hace ventas,
una venta rechazada por falta de stock, reposicion, devolucion, cambio de nombre,
un cierre rechazado por tener compras y un cierre exitoso.

## Pruebas y evidencias
Ver las capturas en este repositorio. Incluyen el despliegue exitoso, las
transacciones (tx), el rechazo por falta de stock (paso 9) y el rechazo al
cerrar un cliente con compras (paso 16).
