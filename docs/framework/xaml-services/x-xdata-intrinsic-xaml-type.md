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
ms.openlocfilehash: 8496e7c87cf7e6eea996ca7af4f288b7495c7661
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459896"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData — Typ funkcji XAML
Umożliwia umieszczanie wysp danych XML w środowisku produkcyjnym XAML. Elementy XML w ramach `x:XData` nie powinny być traktowane przez procesory XAML tak, jakby były częścią działającej domyślnej przestrzeni nazw XAML lub dowolnej innej przestrzeni nazw XAML. `x:XData` może zawierać dowolny poprawnie sformułowany kod XML.  
  
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
|`elementDataRoot`|Pojedynczy element główny z podanej Wyspy danych. W przypadku większości odbiorców, XML, który nie ma jednego katalogu głównego, jest uznawany za nieprawidłowy. W szczególności jest wymagany pojedynczy katalog główny, jeśli `x:XData` jest to źródło danych XML dla WPF lub wiele innych technologii, które używają źródeł XML do powiązania danych.|  
|`[elementData]`|Opcjonalny. KOD XML, który reprezentuje dane XML. Dowolna liczba elementów może być zawarta jako dane elementu, a zagnieżdżone elementy mogą być zawarte w innych elementach. jednak ogólne reguły dotyczące języka XML mają zastosowanie.|  
  
## <a name="remarks"></a>Uwagi  
 Elementy XML w obiekcie `x:XData` mogą ponownie deklarować wszystkie możliwe przestrzenie nazw i prefiksy zawierające XMLDOM w danych.  
  
 Dostęp programistyczny do danych XML i `x:XData` wewnętrzny typ XAML jest możliwy w .NET Framework usług XAML za pomocą klasy <xref:System.Windows.Markup.XData>.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF  
 Obiekt `x:XData` jest używany głównie jako obiekt podrzędny <xref:System.Windows.Data.XmlDataProvider>lub alternatywnie, jako obiekt podrzędny właściwości <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> (w języku XAML jest zwykle wyrażona w składni elementu właściwości).  
  
 Dane powinny zwykle przedefiniować podstawową przestrzeń nazw XML w obrębie Wyspy danych, aby była nową domyślną przestrzenią nazw XML (ustawioną na pusty ciąg). Jest to najłatwiejsze w przypadku prostych wysp danych, ponieważ wyrażenia <xref:System.Windows.Data.Binding.XPath%2A>, które są używane do odwoływania się do danych i wiązania z nią, mogą uniknąć włączenia prefiksów. Bardziej złożone Wyspy danych mogą definiować wiele prefiksów danych i używać określonego prefiksu dla przestrzeni nazw XML w katalogu głównym. W takim przypadku wszystkie odwołania do wyrażenia <xref:System.Windows.Data.Binding.XPath%2A> powinny zawierać odpowiedni prefiks mapowany na przestrzeń nazw. Aby uzyskać więcej informacji, zobacz temat [powiązanie danych — omówienie](../../desktop-wpf/data/data-binding-overview.md).  
  
 Technicznie `x:XData` może służyć jako zawartość dowolnej właściwości typu <xref:System.Xml.Serialization.IXmlSerializable>. Jednak <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> jest jedyną wyrazistą implementacją.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Data.XmlDataProvider>
- [Powiązanie danych — omówienie](../../desktop-wpf/data/data-binding-overview.md)
- [Rozszerzenie znaczników powiązania](../wpf/advanced/binding-markup-extension.md)
