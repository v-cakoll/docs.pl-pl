---
title: "PresentationOptions:Freeze — Atrybut"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d8f1a876f65941afb159d4c3d8904ab4426d9177
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="presentationoptionsfreeze-attribute"></a>PresentationOptions:Freeze — Atrybut
Ustawia <xref:System.Windows.Freezable.IsFrozen%2A> stan `true` na zawierający <xref:System.Windows.Freezable> elementu. Domyślne zachowanie dla <xref:System.Windows.Freezable> bez `PresentationOptions:Freeze` jest określony atrybut, który <xref:System.Windows.Freezable.IsFrozen%2A> jest `false` na czas ładowania, w zależności od ogólne <xref:System.Windows.Freezable> zachowania w czasie wykonywania.  
  
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
|`PresentationOptions`|Prefiks przestrzeni nazw XML, który może być dowolnym ciągiem prawidłowy prefiks na Specyfikacja XML 1.0. Prefiks `PresentationOptions` służy do identyfikacji w niniejszej dokumentacji.|  
|`freezableElement`|Element, który tworzy dowolne pochodnej klasy <xref:System.Windows.Freezable>.|  
  
## <a name="remarks"></a>Uwagi  
 `Freeze` Jest jedynym atrybutem lub innych elementów programowania zdefiniowana w `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` przestrzeni nazw XML. `Freeze` Atrybut istnieje w tym specjalnych przestrzeni nazw, w szczególności, aby może zostać wyznaczony jako ignorowalna, za pomocą [mc: atrybut Ignorable](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) jako część deklaracji elementu głównego. Powód który `Freeze` musi być w stanie się do pominięcia ponieważ nie jest wszystkich [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementacji procesora mogą zablokować <xref:System.Windows.Freezable> w czasie ładowania; ta funkcja nie jest częścią [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] specyfikacji.  
  
 Możliwość przetwarzania `Freeze` atrybutu w szczególności wbudowanej w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora, który przetwarza [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dla skompilowanych aplikacji. Ten atrybut nie jest obsługiwana przez wszystkie klasy i składnia atrybutu nie jest rozszerzony lub można modyfikować. W przypadku wdrażania własnych [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora można równoległe zamrożenia zachowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora podczas przetwarzania `Freeze` atrybutu <xref:System.Windows.Freezable> elementów w czasie ładowania.  
  
 Wszystkie wartości `Freeze` atrybutu innego niż `true` (bez rozróżniania wielkości liter) generuje błąd w czasie ładowania. (Określanie `Freeze` atrybutu jako `false` nie jest błąd, ale która jest już domyślnie, tak `false` nie działa).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Freezable>  
 [Obiekty obiektu freezable — omówienie](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [MC: atrybut do pominięcia](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)
