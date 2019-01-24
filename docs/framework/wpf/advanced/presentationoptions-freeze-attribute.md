---
title: PresentationOptions:Freeze — Atrybut
ms.date: 03/30/2017
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
ms.openlocfilehash: 9909a4170bdb217f91a1fc5713e89bb3a979a999
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512180"
---
# <a name="presentationoptionsfreeze-attribute"></a>PresentationOptions:Freeze — Atrybut
Zestawy <xref:System.Windows.Freezable.IsFrozen%2A> do stanu `true` na zawierający <xref:System.Windows.Freezable> elementu. Domyślne zachowanie dla <xref:System.Windows.Freezable> bez `PresentationOptions:Freeze` określony atrybut jest to, że <xref:System.Windows.Freezable.IsFrozen%2A> jest `false` na czas ładowania, w zależności od ogólnego <xref:System.Windows.Freezable> zachowanie w czasie wykonywania.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```  
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
|`PresentationOptions`|Prefiks przestrzeni nazw XML, który może być dowolnym ciągiem prawidłowy prefiks na Specyfikacja XML 1.0. Prefiks `PresentationOptions` jest używany w celach identyfikacyjnych w tej dokumentacji.|  
|`freezableElement`|Element, który tworzy dowolne pochodne klasy <xref:System.Windows.Freezable>.|  
  
## <a name="remarks"></a>Uwagi  
 `Freeze` Atrybut jest to jedyny atrybut lub innego elementu programowania zdefiniowanych w `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` przestrzeni nazw XML. `Freeze` Atrybut istnieje w tej przestrzeni nazw w specjalnych specjalnie tak, aby może zostać wyznaczony jako do pominięcia, za pomocą [mc: Ignorable — atrybut](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) jako część deklaracji elementu głównego. Przyczyna, `Freeze` musi być w stanie się ignorable jest, ponieważ nie wszystkie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementacji procesora będą mogli zablokować <xref:System.Windows.Freezable> w czasie ładowania; ta funkcja nie jest częścią [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] specyfikacji.  
  
 Możliwość przetwarzania `Freeze` atrybut specjalnie wbudowanej w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora, który przetwarza [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dla skompilowanych aplikacji. Ten atrybut nie jest obsługiwany przez wszystkie klasy i składnia atrybutu nie jest rozszerzalna lub jako do modyfikacji. W przypadku wdrażania własnych [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora, istnieje możliwość równoległego zamrożenia zachowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora podczas przetwarzania `Freeze` atrybutu na <xref:System.Windows.Freezable> elementy w czasie ładowania.  
  
 Wszystkie wartości `Freeze` atrybutu innego niż `true` (bez uwzględniania wielkości liter) generuje błąd w czasie ładowania. (Określanie `Freeze` atrybutu jako `false` nie jest to błąd, ale która jest już domyślnie to ustawienie `false` nic nie robi).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Freezable>
- [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
- [mc:Ignorable, atrybut](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)
