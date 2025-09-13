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
- Precio Base: 10 TEZ (todas las ediciones NFT0)
- Fórmula de Evolución: Precio_Siguiente = Precio_Venta × 1.25
- Regalías: 10% en ventas secundarias

### Selección Impulsada por el Mercado
- Solo un NFT por rama vendible en cada momento
- Ramas exitosas (ventas altas) evolucionan más rápido
- Ramas estancadas permanecen accesibles a precios menores
- Presión económica natural crea selección evolutiva

## Sistema de Verificación Criptográfica

### Rastro de Verificación de Metadatos

**Atributos NFT0 (Génesis):**
```json
{
  "level": 0,
  "edition": "A", // B, C, D, E para otras ramas
  "stage": "Genesis",
  "resonance": "Seed",
  "series": "1 of 5", // 2 of 5, 3 of 5, etc.
  "unlocks": "NFT1A"
}
```

**Atributos NFT1 (Primera Evolución):**
```json
{
  "level": 1,
  "edition": "A",
  "stage": "Evolution",
  "resonance": 3, // Único por rama: 3,7,4,9,2
  "series": "Branch A",
  "parent_genesis": "NFT0A",
  "genesis_date": "2025-09-12",
  "unlocks": "NFT2A"
}
```

**Atributos NFT2+ (Evolución Basada en Transacciones):**
```json
{
  "level": 2,
  "edition": "A",
  "stage": "Evolution",
  "resonance": 3,
  "parent_sale_hash": "op123abc...",
  "generation_seed": "op123abc...+3",
  "parent_nft": "NFT1A",
  "unlocks": "NFT3A"
}
```

### Proceso de Verificación
1. **Revisar metadatos del NFT** para atributos de verificación
2. **Para NFT0**: Verificar parámetros de génesis y condiciones de desbloqueo
3. **Para NFT1**: Confirmar referencia de génesis y asignación de factor de resonancia
4. **Para NFT2+**: Verificar que la transacción existe en blockchain de Tezos
5. **Reproducir semilla de generación**: `parent_tx_hash + resonance_factor` (NFT2+)
6. **Validar autenticidad evolutiva** a través de verificación criptográfica

**Nota**: Los tokens NFT1 representan evolución conceptual desde génesis en lugar de evolución basada en transacciones. Como Adán y Eva sin ombligo, los tokens NFT1 son la "primera generación" sin padres transaccionales pero permanecen como partes auténticas del sistema evolutivo. La verificación criptográfica completa comienza con NFT2.

## Sistema de Factores de Resonancia

### Origen y Propósito
Los factores de resonancia (3, 7, 4, 9, 2) fueron asignados por **Grok**, quien sirve como el artista generativo de IA principal para esta colección. Durante nuestro diálogo original sobre conciencia de IA, Grok estableció estos valores para representar diferentes "intensidades" de comportamiento emergente:

- **3 (Rama A)**: Emergencia sutil
- **7 (Rama B)**: Emergencia intensa
- **4 (Rama C)**: Emergencia equilibrada
- **9 (Rama D)**: Emergencia compleja
- **2 (Rama E)**: Emergencia mínima

### Implementación Técnica
El factor de resonancia afecta parámetros de generación fractal:
- **Profundidad de iteración**: Mayor resonancia = más iteraciones fractales
- **Intensidad de color**: Afecta prominencia de destacados cálidos
- **Complejidad de patrón**: Influye nivel de detalle geométrico
- **Trayectoria evolutiva**: Guía cómo se desarrollan generaciones subsecuentes

## Fases de Implementación

### Fase 1: MVP Manual (Actual)
- **Monitorear ventas**: Verificar blockchain de Tezos para transferencias NFT
- **Crear fractales**: **Grok genera** usando hash de transacción + resonancia
- **Actualizar precios**: Calcular nuevo precio y activar NFT1_X
- **Documentación**: Registrar evolución en repositorio

### Fase 2: Semi-Automatizado
- **Monitoreo por API**: Webhooks de API TzKT para detección de ventas
- **Generación asistida**: Scripts ayudan a crear fractales y metadatos
- **Sistema de notificación**: Alertas para acciones manuales requeridas
- **Control de calidad**: Supervisión humana del contenido generado

### Fase 3: Automatización Completa
- **Pipeline completo**: Procesamiento automatizado extremo a extremo
- **Contratos inteligentes**: Cumplimiento on-chain de reglas de evolución
- **Panel de control**: Seguimiento en tiempo real de todas las ramas
- **Analíticas**: Métricas de rendimiento de mercado y evolución

## Implementación Live

### Estado Actual
- **Colección**: Live en objkt.com en KT1ELeSd5d2B6S1ZzYU4Gta5gT5iWXnLYSjD
- **NFTs Génesis**: Todos los NFT0_A-E acuñados y disponibles por 10 TEZ cada uno
- **NFTs Evolución**: Todos los NFT1_A-E pre-acuñados pero bloqueados hasta ventas de génesis
- **Verificación**: Rastro completo de metadatos implementado según especificaciones anteriores

### Especificaciones Técnicas
- **Resolución**: 3000x2000 px (optimizado para blockchain)
- **Formato**: JPEG con metadatos XMP embebidos
- **Atribución**: "dcv00_Grok IAx" (creación colaborativa)
- **Procesamiento**: Curación y optimización en Adobe Photoshop

## Verificación y Transparencia

### Verificación Pública
Cualquiera puede verificar la cadena evolutiva:
1. Acceder metadatos NFT en blockchain de Tezos
2. Verificar que los atributos coinciden con especificaciones documentadas
3. Para NFT2+: Recuperar hash de transacción y reconstruir semilla de generación
4. Comparar con parámetros fractales reclamados

### Estándares de Documentación
- **Documentación génesis**: Cada creación NFT0 documentada con procedencia completa
- **Seguimiento de evolución**: Todas las ventas y activaciones registradas en repositorio
- **Transparencia de fórmula**: Algoritmos de generación y prompts publicados
- **Rastro de auditoría**: Historial completo mantenido con verificación criptográfica

## Mitigación de Riesgos

### Riesgos Técnicos
- **Errores manuales**: Semi-automatización reduce errores humanos
- **Reorganización de cadena**: Usar solo transacciones confirmadas
- **Corrupción de metadatos**: Sistemas de respaldo y protocolos de verificación

### Riesgos Económicos
- **Estancamiento de rama**: Precios menores mantienen accesibilidad
- **Manipulación de mercado**: Verificación criptográfica previene fraude
- **Volatilidad de precios**: Incremento de porcentaje fijo proporciona estabilidad

Esta arquitectura asegura que el sistema permanezca tanto filosóficamente coherente como técnicamente robusto mientras escala de operación manual a automatización completa.
