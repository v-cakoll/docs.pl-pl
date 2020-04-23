---
title: xml:lang — Obsługa w XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: b5a06adbb7cb874bc09899118f13b91fbec7a85e
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071445"
---
# <a name="xmllang-handling-in-xaml"></a>xml:lang — Obsługa w XAML

Atrybut `xml:lang` jest atrybutem zdefiniowanym przez XML, który deklaruje informacje o języku i kulturze dla elementu w języku XML. To samo znaczenie atrybutu utrzymuje się w XAML; istnieją jednak pewne dodatkowe kwestie.

## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML

```xaml
<object xml:lang="rfc3066lang" />
```

## <a name="xaml-values"></a>Wartości XAML

|||
|-|-|
|*rfc3066lang*|Ciąg, który jest pochodną standardu [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) i identyfikuje język lub region języka. Gdy jest to ostatni, język i region są oddzielone pojedynczym łącznikiem. Zobacz <xref:System.Windows.Markup.XmlLanguage> więcej informacji na temat wartości i formatu.|

## <a name="remarks"></a>Uwagi

Definicja atrybutu `xml:lang` w [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] pochodzi od `xml:lang` zdefiniowane jako "atrybut specjalny" przez Konsorcjum Sieci World Wide Web (W3C) dla XML. Informacje o języku i kulturze są potencjalnie przetwarzane na różne sposoby przez elementy, w zależności od ich implementacji; jednak nie ma [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] domyślnego `xml:lang` przetwarzania atrybutu.

Domyślną wartością `xml:lang` atrybutu jest pusty ciąg na poziomie atrybutu.

Efekty `xml:lang` atrybutów i wartość atrybutu są zazwyczaj utrwalane do elementów podrzędnych, podczas `xml:lang` gdy są interpretowane przez systemy, które działają na wartości.

Podczas interpretowania przez moduły zapisu xaml `xml:lang` usług .NET XAML Services, wartość może tworzyć <xref:System.Windows.Markup.XmlLanguage> lub <xref:System.Globalization.CultureInfo> obiekty w reprezentacji obiektu źródłowego; jednak to zachowanie zależy od tego, czy wartość określona dla `xml:lang` jest prawidłową konstrukcją dla tych klas.

Frameworks można utworzyć skojarzenia między właściwości zdefiniowane `xml:lang` przez ramy i <xref:System.Windows.Markup.XmlLangPropertyAttribute> znaczenie w XML, stosując do właściwości.

## <a name="wpf-usage-nodes"></a>Węzły użycia WPF

Dla elementów, które <xref:System.Windows.FrameworkElement> są <xref:System.Windows.FrameworkContentElement>klasy pochodne <xref:System.Windows.FrameworkElement.Language%2A> lub , można użyć `xml:lang` właściwości równoważne zależności zamiast atrybutu. Domyślnie <xref:System.Windows.FrameworkElement.Language%2A> właściwość używa "en-US", jeśli nie jest w inny sposób ustawiona, za pośrednictwem właściwości lub poprzez przetwarzanie atrybutu. `xml:lang`

## <a name="see-also"></a>Zobacz też

- [Globalizacja dla WPF](../../framework/wpf/advanced/globalization-for-wpf.md)
