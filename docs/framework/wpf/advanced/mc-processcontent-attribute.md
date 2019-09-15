---
title: mc:ProcessContent — Atrybut
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: e625d99cdb30368a798b4829d103f8f26b2c9274
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991856"
---
# <a name="mcprocesscontent-attribute"></a>mc:ProcessContent — Atrybut
Określa, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] które elementy powinny nadal mieć zawartość przetworzoną przez odpowiednie elementy nadrzędne, nawet jeśli bezpośredni element nadrzędny może być [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ignorowany przez procesor z powodu określenia [atrybutu MC:](mc-ignorable-attribute.md)Ignore. Ten `mc:ProcessContent` atrybut obsługuje zgodność znaczników zarówno dla niestandardowego mapowania przestrzeni nazw, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jak i do przechowywania wersji.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...  
  mc:ProcessContent="ignorablePrefix:ThisElementCanBeIgnored"  
>  
    <ignorablePrefix:ThisElementCanBeIgnored>  
        [content]  
    </ignorablePrefix:ThisElementCanBeIgnored>  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|*ignorablePrefix*|Dowolny prawidłowy ciąg prefiksu na specyfikację XML 1,0.|  
|*ignorableUri*|Dowolny prawidłowy identyfikator URI służący do wyznaczania przestrzeni nazw, zgodnie ze specyfikacją XML 1,0.|  
|*ThisElementCanBeIgnored*|Element, który może być ignorowany [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przez implementacje procesora, jeśli nie można rozpoznać typu podstawowego.|  
|*treści*|*ThisElementCanBeIgnored* jest oznaczony jako ignorowany. Jeśli procesor zignoruje ten element, *[zawartość]* jest przetwarzany przez *obiekt*.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor zignoruje zawartość w ignorowanym elemencie. Można określić konkretny element przez `mc:ProcessContent`, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a procesor będzie kontynuował przetwarzanie zawartości w zignorowanym elemencie. Zwykle jest to używane, jeśli zawartość jest zagnieżdżona w kilku tagach, co najmniej jeden z nich jest ignorowany i co najmniej jeden z nich nie jest ignorowany.  
  
 W atrybucie można określić wiele prefiksów, używając separatora spacji, na przykład: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.  
  
 `http://schemas.openxmlformats.org/markup-compatibility/2006` Przestrzeń nazw definiuje inne elementy i atrybuty, które nie są udokumentowane w tym obszarze zestawu SDK. Aby uzyskać więcej informacji, zobacz [Specyfikacja zgodności znaczników XML](https://go.microsoft.com/fwlink/?LinkId=73824).  
  
## <a name="see-also"></a>Zobacz także

- [mc:Ignorable, atrybut](mc-ignorable-attribute.md)
- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
