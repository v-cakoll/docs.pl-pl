---
title: x:Uid — dyrektywa
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
ms.openlocfilehash: b5b480016d2183268422dea861510c6a169ac27b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071340"
---
# <a name="xuid-directive"></a>x:Uid — dyrektywa

Udostępnia unikatowy identyfikator dla elementów znaczników. W wielu scenariuszach ten unikatowy identyfikator jest używany przez procesy i narzędzia lokalizacji XAML.

## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML

```xaml
<object x:Uid="identifier"... />
```

## <a name="xaml-values"></a>Wartości XAML

|||
|-|-|
|`identifier`|Ciąg utworzony ręcznie lub automatyczniegenerowany, który powinien być unikatowy w `x:Uid` pliku, gdy jest interpretowany przez konsumenta.|

## <a name="remarks"></a>Uwagi

W [MS-XAML] `x:Uid` jest zdefiniowany jako dyrektywa. Aby uzyskać więcej informacji, zobacz [ \[rozdział 5.3.6 ms-XAML\] ](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

`x:Uid`jest dyskretny `x:Name` zarówno ze względu na podany scenariusz lokalizacji XAML, jak i tak, że identyfikatory, `x:Name`które są używane do lokalizacji, nie mają zależności od implikacji modelu programowania . Ponadto, `x:Name` jest regulowany przez namescope XAML; jednak `x:Uid` nie podlega żadnemu językowi XAML zdefiniowanemu pojęciu wymuszania unikatowości. Procesory XAML w szerokim znaczeniu (procesory, które nie są częścią procesu lokalizacji) nie powinny wymuszać unikatowości `x:Uid` wartości. Odpowiedzialność ta spoczywa koncepcyjnie na twórcy wartości. Oczekiwanie unikatowości `x:Uid` wartości w ramach jednego źródła XAML jest uzasadnione dla konsumentów wartości, takich jak dedykowane procesy globalizacji lub narzędzia. Typowy model unikatowości `x:Uid` jest to, że wartości są unikatowe w pliku zakodowanym w formacie XML, który reprezentuje XAML.

Narzędzia, które mają znaczną wiedzę na temat określonego `x:Uid` schematu XAML można wybrać do zastosowania tylko dla ciągów true localizable, a nie dla wszystkich przypadkach, w których wartość ciągu tekstowego występuje w znacznikach.

Frameworks można określić określonej właściwości w modelu `x:Uid` obiektu, aby być <xref:System.Windows.Markup.UidPropertyAttribute> aliasem dla stosując atrybut do typu definiującego. Jeśli struktura określa określoną właściwość, nie jest `x:Uid` prawidłowa do określenia zarówno i aliasu elementu członkowskiego na tym samym obiekcie. Jeśli `x:Uid` określono zarówno i aliased element członkowski, .NET XAML Services API zazwyczaj zgłasza <xref:System.Xaml.XamlDuplicateMemberException> w tym przypadku.

## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF

Aby uzyskać więcej informacji `x:Uid` na temat roli w procesie lokalizacji WPF i w postaci BAML XAML, zobacz [Globalizacja dla WPF](../../framework/wpf/advanced/globalization-for-wpf.md) lub<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>
- <xref:Microsoft.Build.Tasks.Windows.UidManager>
- [Globalizacja dla WPF](../../framework/wpf/advanced/globalization-for-wpf.md)
