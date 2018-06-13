---
title: Style i szablony wbudowane
ms.date: 03/30/2017
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
ms.openlocfilehash: 9c06f61bce1e17770fa0a9b9ed7a0e20625a79ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545892"
---
# <a name="inline-styles-and-templates"></a>Style i szablony wbudowane
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] udostępnia <xref:System.Windows.Style> obiekty i szablonu (<xref:System.Windows.FrameworkTemplate> podklasy) jako sposób definiowania wygląd elementu w zasobach, dzięki czemu mogą być używane wiele razy. Z tego powodu atrybutów w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] typy, które wymagają <xref:System.Windows.Style> i <xref:System.Windows.FrameworkTemplate> prawie zawsze zasobów odwołuje się do istniejącego style i szablony, zamiast definiować nowych wbudowanego.  
  
## <a name="limitations-of-inline-styles-and-templates"></a>Ograniczenia style wbudowane i szablony  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], technicznie można ustawić właściwości stylu i szablonu w jeden z dwóch sposobów. Za pomocą składni atrybutów ma dotyczyć odwołanie styl, który został zdefiniowany w ramach zasobu, na przykład `<` *obiektu*`Style="{StaticResource`*myResourceKey*`}" .../>`. Lub składni elementu właściwości umożliwia definiowanie w tekście stylu, na przykład:  
  
 `<` *Obiekt* `>`  
  
 `<` *Obiekt* `.Style>`  
  
 `<` `Style`  `.../>`  
  
 `</` *Obiekt* `.Style>`  
  
 `</` *Obiekt* `>`  
  
 Użycie atrybutu jest znacznie bardziej powszechne. Styl, który zdefiniowano w tekście i zasoby nie są zdefiniowane w niekoniecznie obejmuje tylko zawierającego element i nie można ponownie użyć równie łatwo, ponieważ nie ma on zasobów klucza. Ogólnie rzecz biorąc jest bardziej elastyczne i przydatne zasób zdefiniowany styl i jest bardziej zgodne ogólne [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programowania modelu Zasada oddzielenia logice programu w kodzie z projektu w znaczniku.  
  
 Zwykle to nie nie powodu można ustawić stylu lub szablonie wbudowany, nawet jeśli zamierzasz używać tego stylu lub szablonie w tej lokalizacji. Większość elementów, które można wykonać w stylu lub szablonie obsługują także właściwością zawartości i modelu zawartości. Jeśli używane są tylko niezależnie od drzewa logicznego można tworzyć za pomocą stylów lub tworzenia szablonów raz, będzie jeszcze lepiej tylko elementy podrzędne odpowiednik w znaczniku bezpośredniego wypełnienie tej właściwości zawartości. Czy to całkowicie pominąć szablon i stylu mechanizmów.  
  
 Możliwe, style i szablony są również innych składni, aby włączyć rozszerzenia znaczników, które zwracają obiekt. Dwa rozszerzenia, które mają możliwe scenariusze obejmują [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) i <xref:System.Windows.Data.Binding>.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)
