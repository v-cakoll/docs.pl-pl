---
title: Style i szablony wbudowane
ms.date: 03/30/2017
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
ms.openlocfilehash: b566e157e2d4a9e9be21a678541bf5d5341a898c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091437"
---
# <a name="inline-styles-and-templates"></a>Style i szablony wbudowane
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] udostępnia <xref:System.Windows.Style> obiekty i szablonu (<xref:System.Windows.FrameworkTemplate> podklasy) jako sposób zdefiniować wygląd elementu w zasobach, dzięki czemu będzie można ich użyć wiele razy. Z tego powodu atrybutów w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] typy, które wymagają <xref:System.Windows.Style> i <xref:System.Windows.FrameworkTemplate> prawie zawsze zasobów odwołuje się do istniejącego — style i szablony, a nie zdefiniować nowe wbudowane.  
  
## <a name="limitations-of-inline-styles-and-templates"></a>Ograniczenia style i Szablony wbudowane  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], z technicznego punktu widzenia można ustawić właściwości stylów i szablonów w jeden z dwóch sposobów. Można użyć składni atrybutów stylu, który został zdefiniowany w ramach zasobu, na przykład odwołanie do `<` *obiektu*`Style="{StaticResource`*myResourceKey*`}" .../>`. Lub składnia elementu właściwości umożliwia definiowanie w tekście stylu, na przykład:  
  
 `<` *obiekt* `>`  
  
 `<` *obiekt* `.Style>`  
  
 `<` `Style`  `.../>`  
  
 `</` *obiekt* `.Style>`  
  
 `</` *obiekt* `>`  
  
 Użycie atrybutu jest znacznie bardziej powszechne. Styl, który zdefiniowano w tekście i nie zdefiniowano w zasoby zawsze obejmuje tylko element zawierający i nie można ponownie użyć równie łatwo, ponieważ nie ma on zasobów klucza. Ogólnie rzecz biorąc zdefiniowany zasób stylu jest bardziej wszechstronna i przydatne i jest bardziej zgodne ogólne [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] oddzielenie logiki programu w kodzie, od projektowania w znacznikach zasady modelu programowania.  
  
 Zwykle nie ma powodu do wbudowanej stylu lub szablonu, nawet jeśli zamierzasz używać stylu lub szablonu w tej lokalizacji. Większość elementów, które mogą przejąć stylu lub szablonu obsługują również właściwość zawartości oraz model zawartości. Jeśli używane są tylko niezależnie od drzewo logiczne Utwórz za pomocą stylów i szablonów raz, byłoby jeszcze łatwiej Wypełnij tę właściwość zawartości z elementami podrzędnymi równoważne, w znacznikach bezpośrednie. Spowoduje to całkowicie pominąć mechanizmy stylów i szablonów.  
  
 Możliwe, style i szablony są również innych składni włączane przez rozszerzenia znaczników, które zwracają obiekt. Dwa rozszerzenia, które mają możliwe scenariusze obejmują [TemplateBinding](templatebinding-markup-extension.md) i <xref:System.Windows.Data.Binding>.  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonów i stylów](../controls/styling-and-templating.md)
