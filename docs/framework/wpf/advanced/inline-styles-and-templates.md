---
title: Style i szablony wbudowane
ms.date: 03/30/2017
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
ms.openlocfilehash: b88ef444283f4e1e85009c59b39f3cc41965d300
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460006"
---
# <a name="inline-styles-and-templates"></a>Style i szablony wbudowane
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia <xref:System.Windows.Style> obiektów i obiektów szablonów (<xref:System.Windows.FrameworkTemplate> podklas) jako sposób definiowania wyglądu elementu w zasobach, dzięki czemu mogą być używane wiele razy. Z tego powodu atrybuty w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], które pobierają typy <xref:System.Windows.Style> i <xref:System.Windows.FrameworkTemplate> niemal zawsze tworzą odwołania do zasobów do istniejących stylów i szablonów zamiast definiować nowe.  
  
## <a name="limitations-of-inline-styles-and-templates"></a>Ograniczenia stylów i szablonów wbudowanych  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]właściwości stylu i szablonu można ustawić w jeden z dwóch sposobów. Można użyć składni atrybutu, aby odwołać się do stylu, który został zdefiniowany w ramach zasobu, na przykład `<`*obiektu* *`Style="{StaticResource``}" .../>`* . Lub można użyć składni elementu właściwości, aby zdefiniować styl wbudowany, na przykład:  
  
 `>` `<` *obiektu*  
  
 `.Style>` `<` *obiektu*  
  
 `<` `Style``.../>`  
  
 `.Style>` `</` *obiektu*  
  
 `>` `</` *obiektu*  
  
 Użycie atrybutu jest znacznie bardziej powszechne. Styl, który jest zdefiniowany w tekście i nie jest zdefiniowany w zasobach, jest koniecznie objęty zakresem zawierającym tylko element i nie można go ponownie użyć, ponieważ nie ma klucza zasobu. Ogólnie rzecz biorąc, styl zdefiniowany przez zasób jest bardziej uniwersalny i przydatny, co jest bardziej pomocne z ogólnym modelem programowania [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zasadą oddzielania logiki programu w kodzie od projektowania w znaczniku.  
  
 Zwykle nie istnieje powód, aby ustawić styl lub szablon w tekście, nawet jeśli zamierzasz użyć tego stylu lub szablonu w tej lokalizacji. Większość elementów, które mogą przyjmować styl lub szablon, obsługują również właściwość content i model zawartości. Jeśli używasz tylko dowolnego drzewa logicznego, które tworzysz za pośrednictwem stylu lub tworzenia szablonów raz, łatwiej jest wypełniać tę właściwość zawartości z odpowiednikami elementów podrzędnych w znacznikach bezpośrednich. Dzięki temu wszystkie mechanizmy stylu i szablonu zostaną całkowicie pominięte.  
  
 Inne składnie włączane przez rozszerzenia znaczników, które zwracają obiekt, są również dostępne dla stylów i szablonów. Dwa takie rozszerzenia, które mają możliwe scenariusze, obejmują [szablonbinding](templatebinding-markup-extension.md) i <xref:System.Windows.Data.Binding>.  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
