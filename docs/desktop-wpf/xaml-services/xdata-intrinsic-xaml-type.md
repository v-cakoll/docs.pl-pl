---
title: x:XData — Typ funkcji XAML
ms.date: 03/30/2017
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
ms.openlocfilehash: b7f0954158988db107feb4a6c51ba81d5db11dcb
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071543"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData — Typ funkcji XAML
Umożliwia umieszczenie wysp danych XML w środowisku produkcyjnym XAML. Elementy XML `x:XData` wewnątrz nie powinny być traktowane przez procesory XAML tak, jakby były częścią działającej domyślnej przestrzeni nazw XAML lub innej przestrzeni nazw XAML. `x:XData`może zawierać dowolny dobrze uformowany kod XML.

## <a name="xaml-object-element-usage"></a>Użycie elementu obiektu języka XAML

```xaml
<x:XData>
  <elementDataRoot>
    [elementData]
  </elementDataRoot>
</x:XData>
```

## <a name="xaml-values"></a>Wartości XAML

|||
|-|-|
|`elementDataRoot`|Pojedynczy element główny zamkniętej wyspy danych. Dla większości potencjalnych konsumentów XML, który nie ma jednego katalogu głównego jest uważany za nieprawidłowy. W szczególności pojedynczy katalog główny jest `x:XData` wymagany, jeśli jest przeznaczony jako źródło danych XML dla WPF lub wiele innych technologii, które używają źródeł XML do wiązania danych.|
|`[elementData]`|Element opcjonalny. XML reprezentujący dane XML. Dowolna liczba elementów może być zawarta jako dane elementu i elementy zagnieżdżone mogą być zawarte w innych elementach; zastosowanie mają jednak ogólne zasady XML.|

## <a name="remarks"></a>Uwagi

Elementy XML w `x:XData` obiekcie można ponownie zadeklarować wszystkie możliwe przestrzenie nazw i prefiksy zawierające XMLDOM w danych.

Programowy dostęp do danych `x:XData` XML i wewnętrznego typu XAML jest możliwy w <xref:System.Windows.Markup.XData> usługach .NET XAML za pośrednictwem klasy.

## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF

Obiekt `x:XData` jest używany głównie jako obiekt <xref:System.Windows.Data.XmlDataProvider>podrzędny , lub alternatywnie, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> jako obiekt podrzędny właściwości (w XAML, jest to zazwyczaj wyrażone w składni elementu właściwości).

Dane powinny zazwyczaj przedefiniować podstawową przestrzeń nazw XML w obrębie wyspy danych jako nową domyślną przestrzeń nazw XML (ustawioną na pusty ciąg). Jest to najłatwiejsze dla <xref:System.Windows.Data.Binding.XPath%2A> prostych wysp danych, ponieważ wyrażenia, które są używane do odwoływania się i powiązania z danymi, mogą uniknąć dołączania prefiksów. Bardziej złożone wyspy danych mogą definiować wiele prefiksów danych i używać określonego prefiksu obszaru nazw XML w katalogu głównym. W takim przypadku <xref:System.Windows.Data.Binding.XPath%2A> wszystkie odwołania do wyrażeń powinny zawierać odpowiedni prefiks mapowany przez obszar nazw. Aby uzyskać więcej informacji, zobacz [Omówienie powiązania danych](../data/data-binding-overview.md).

Technicznie, `x:XData` może być używany jako zawartość dowolnej <xref:System.Xml.Serialization.IXmlSerializable>właściwości typu . Jest <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> to jednak jedyna znacząca implementacja.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Data.XmlDataProvider>
- [Omówienie powiązania danych](../data/data-binding-overview.md)
- [Rozszerzenie znaczników powiązania](../../framework/wpf/advanced/binding-markup-extension.md)
