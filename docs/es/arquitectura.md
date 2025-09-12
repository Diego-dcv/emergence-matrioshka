# Arquitectura Técnica

## Vista General del Sistema

Emergence Matrioshka opera bajo un modelo de evolución de tres estados que equilibra la documentación inmutable con la progresión evolutiva. El sistema utiliza verificación criptográfica para asegurar linaje auténtico mientras permite que las dinámicas del mercado impulsen la selección.

## Modelo de Evolución de Tres Estados

### ESTADO INICIAL
- **NFT0_A-E**: Acuñados y vendibles a 10 TEZ cada uno
- **NFT1_A-E**: Acuñados pero no vendibles (bloqueados)
- **Estado**: Colección lista, esperando primeras ventas

### ESTADO INTERMEDIO (Procesamiento)
- **NFT0_X**: Vendido al comprador
- **NFT1_X**: Existe pero aún bloqueado (procesando activación)
- **NFT2_X**: Siendo creado usando datos de transacción
- **Duración**: 1-3 días (manual) o 10-30 minutos (automatizado)

### ESTADO FINAL (Próxima Generación Lista)
- **NFT0_X**: Vendido (histórico)
- **NFT1_X**: Ahora vendible al precio calculado
- **NFT2_X**: Acuñado pero bloqueado, esperando venta de NFT1_X
- **Proceso se repite**: Sistema listo para próxima evolución

## Mecánicas Económicas

### Evolución de Precios
