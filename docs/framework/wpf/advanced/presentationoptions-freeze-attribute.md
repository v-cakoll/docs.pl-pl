---
title: PresentationOptions:Freeze — Atrybut
ms.date: 03/30/2017
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
ms.openlocfilehash: d3e0cee293a9585b972b0145da953976ed94b74c
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991427"
---
# <a name="presentationoptionsfreeze-attribute"></a>PresentationOptions:Freeze — Atrybut
<xref:System.Windows.Freezable.IsFrozen%2A> Ustawia <xref:System.Windows.Freezable> stan na `true` dla elementu zawierającego. Zachowanie domyślne dla a <xref:System.Windows.Freezable> `PresentationOptions:Freeze` bez określonego <xref:System.Windows.Freezable.IsFrozen%2A> <xref:System.Windows.Freezable> atrybutu jest w czasie ładowania i zależne od ogólnego zachowania w czasie wykonywania. `false`  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`PresentationOptions`|Prefiks przestrzeni nazw XML, który może być dowolnym prawidłowym ciągiem prefiksu na specyfikację XML 1,0. Prefiks `PresentationOptions` jest używany na potrzeby identyfikacji w tej dokumentacji.|  
|`freezableElement`|Element, który tworzy wystąpienie klasy <xref:System.Windows.Freezable>pochodnej.|  
  
## <a name="remarks"></a>Uwagi  
 Ten `Freeze` atrybut jest jedynym atrybutem lub innym elementem programistycznym zdefiniowanym `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` w przestrzeni nazw XML. Ten atrybut istnieje w tej specjalnej przestrzeni nazw, aby można było go wyznaczyć w sposób ignorowany, przy użyciu funkcji [MC: atrybut do ignorowania](mc-ignorable-attribute.md) jako część deklaracji elementu głównego. `Freeze` Przyczyną, że `Freeze` musi być możliwe ignorowanie, jest to, że nie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] wszystkie implementacje procesora <xref:System.Windows.Freezable> mogą zamrozić w czasie ładowania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ; ta funkcja nie jest częścią specyfikacji.  
  
 Możliwość przetwarzania `Freeze` atrybutu jest specjalnie wbudowana w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor, który przetwarza [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] skompilowane aplikacje. Atrybut nie jest obsługiwany przez żadną klasę, a składnia atrybutu nie jest rozszerzalna ani modyfikowalna. Jeśli wdrażasz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] własny procesor, możesz wybrać równoległe zachowanie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesora podczas przetwarzania `Freeze` atrybutu dla <xref:System.Windows.Freezable> elementów w czasie ładowania.  
  
 Dowolna wartość `Freeze` atrybutu innego niż `true` (bez uwzględniania wielkości liter) generuje błąd ładowania. (Określenie `Freeze` atrybutu jako `false` nie jest błędem, ale jest już ustawieniem `false` domyślnym, więc nie robi nic).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Freezable>
- [Przegląd obiektów Freezable](freezable-objects-overview.md)
- [mc:Ignorable, atrybut](mc-ignorable-attribute.md)
