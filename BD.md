1. **Usuarios**:
   
   - `id` (INT, clave primaria)
   - `nombre_usuario` (VARCHAR, único)
   - `correo_electronico` (VARCHAR)
   - `contrasenia` (VARCHAR, encriptada)
   - Otros datos de perfil (opcional)

2. **Partidas**:
   
   - `id` (INT, clave primaria)
   - `id_jugador_blanco` (INT, clave externa que hace referencia a la tabla de usuarios)
   - `id_jugador_negro` (INT, clave externa que hace referencia a la tabla de usuarios)
   - `estado_partida` (VARCHAR, por ejemplo: en curso, terminada)
   - `fecha_hora_inicio` (TIMESTAMP)
   - `fecha_hora_finalizacion` (TIMESTAMP, opcional)
   - Otros detalles de la partida (opcional)

3. **Movimientos**:
   
   - `id` (INT, clave primaria)
   - `id_partida` (INT, clave externa que hace referencia a la tabla de partidas)
   - `numero_movimiento` (INT)
   - `id_pieza_movida` (INT)
   - `coordenadas_origen` (VARCHAR, por ejemplo: "A2")
   - `coordenadas_destino` (VARCHAR, por ejemplo: "A4")
   - `tipo_movimiento` (VARCHAR, por ejemplo: normal, captura, jaque, jaque mate, etc.)
