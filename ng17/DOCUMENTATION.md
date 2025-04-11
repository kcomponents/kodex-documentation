![Kruger Corp](https://img.shields.io/badge/Kruger_Corp_®-Copyright_2022-blue)

# kng-components-v3

## Documentación de Componentes Angular 17

Esta documentación describe los componentes y utilidades disponibles en la librería kng-components-v3 para Angular 17. La librería ofrece una colección de componentes predefinidos para construir aplicaciones web con un diseño y funcionalidad estandarizados.

### Índice de Componentes

1. [k-layout](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-layout.md) - Estructura principal de la aplicación, con cabecera, barra lateral y área de contenido.
2. [k-table](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-table.md) - Tabla de datos con paginación, ordenamiento y acciones.
3. [k-modal](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-modal.md) - Ventanas modales para formularios y contenido interactivo.
4. [k-search](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-search.md) - Componentes de búsqueda y filtrado avanzados.
5. [k-button](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-button.md) - Botones estilizados para diferentes acciones y contextos.
6. [k-component-filter](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-component-filter.md) - Componente completo para implementar filtros de búsqueda.
7. [k-component-panel-menu](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-component-panel-menu.md)
8. [k-confirm-dialog](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-confirm-dialog.md)
9. [k-footer](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-footer.md)
10. [k-message](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-message.md)
11. [k-panel-menu](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-panel-menu.md)
12. [k-scss](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17k-scss.md)
13. [k-tree](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-tree.md)
14. [k-user-service](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-user-service.md)
15. [k-validations](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-validations.md)
16. [k-viewer](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-viewer.md)
17. [typescript](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/typescript.md)


### Instalación

Para utilizar estos componentes, es necesario incluir las siguientes dependencias en su proyecto:

- Angular 17
- Bootstrap 4
- PrimeNG con tema Bootstrap
- Toastr
- Font Awesome

### Importación

Cada componente puede ser importado de forma individual o mediante módulos principales:

```typescript
// Importación individual de componentes
import { KLayoutComponent } from '@ec.com.kgr/kng-components-v3/k-layout';
import { KSearchModule } from '@ec.com.kgr/kng-components-v3/k-search';

// Ejemplo de uso en un componente standalone
@Component({
  selector: 'app-my-component',
  standalone: true,
  imports: [
    KLayoutComponent,
    KSearchModule
  ]
})
export class MyComponent { }
```

### Características Generales

- **Componentes Standalone**: Diseñados para Angular 17 con el enfoque standalone.
- **Diseño Responsivo**: Adaptables a diferentes tamaños de pantalla.
- **Estilo Consistente**: Aplicación de estilos uniformes a través de todos los componentes.
- **Integración con PrimeNG**: Utiliza y extiende componentes de PrimeNG.
- **Soporte para Formularios**: Integración con Angular Forms para validación y manejo de datos.
- **Internacionalización**: Preparados para soportar múltiples idiomas.

### Uso Recomendado

Para una experiencia óptima, se recomienda utilizar los componentes en conjunto para mantener la coherencia visual y funcional. El flujo típico de una aplicación incluiría:

1. Definir la estructura general con k-layout
2. Implementar filtros de búsqueda con k-component-filter
3. Mostrar datos en tablas con k-table
4. Gestionar formularios en modales con k-modal
5. Utilizar botones estandarizados con k-button

Consulte la documentación específica de cada componente para más detalles de implementación y ejemplos.
