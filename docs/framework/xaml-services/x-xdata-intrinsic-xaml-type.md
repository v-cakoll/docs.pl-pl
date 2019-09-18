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
ms.openlocfilehash: c5f729837b9bb52ca7d232ca66b58e283a2bcefc
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053697"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData — Typ funkcji XAML
Umożliwia umieszczanie wysp danych XML w środowisku produkcyjnym XAML. Elementy XML w `x:XData` ramach nie powinny być traktowane przez procesory XAML tak, jakby były częścią działającej domyślnej przestrzeni nazw XAML lub dowolnej innej przestrzeni nazw XAML. `x:XData`może zawierać dowolny poprawnie sformułowany kod XML.  
  
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
|`elementDataRoot`|Pojedynczy element główny z podanej Wyspy danych. W przypadku większości odbiorców, XML, który nie ma jednego katalogu głównego, jest uznawany za nieprawidłowy. W szczególności, jeśli `x:XData` jest to źródło danych XML dla WPF lub wiele innych technologii, które używają źródeł danych XML do tworzenia powiązań z danymi, wymagany jest pojedynczy element główny.|  
|`[elementData]`|Opcjonalny. KOD XML, który reprezentuje dane XML. Dowolna liczba elementów może być zawarta jako dane elementu, a zagnieżdżone elementy mogą być zawarte w innych elementach. jednak ogólne reguły dotyczące języka XML mają zastosowanie.|  
  
## <a name="remarks"></a>Uwagi  
 Elementy XML w `x:XData` obiekcie mogą ponownie deklarować wszystkie możliwe przestrzenie nazw i prefiksy zawierające XMLDOM w danych.  
  
 Dostęp programistyczny do danych XML i `x:XData` wewnętrzny typ XAML jest możliwy w .NET Framework usługach XAML <xref:System.Windows.Markup.XData> za pomocą klasy.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF  
 Obiekt jest głównie używany jako obiekt <xref:System.Windows.Data.XmlDataProvider>podrzędny obiektu, lub alternatywnie, jako obiekt <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> podrzędny właściwości (w języku XAML jest zwykle wyrażona w składni elementu właściwości). `x:XData`  
  
 Dane powinny zwykle przedefiniować podstawową przestrzeń nazw XML w obrębie Wyspy danych, aby była nową domyślną przestrzenią nazw XML (ustawioną na pusty ciąg). Jest to najłatwiej w przypadku prostych wysp <xref:System.Windows.Data.Binding.XPath%2A> danych, ponieważ wyrażenia, które są używane do odwoływania się do danych i tworzenia powiązań z danymi, mogą uniknąć włączenia prefiksów. Bardziej złożone Wyspy danych mogą definiować wiele prefiksów danych i używać określonego prefiksu dla przestrzeni nazw XML w katalogu głównym. W takim przypadku wszystkie <xref:System.Windows.Data.Binding.XPath%2A> odwołania do wyrażeń powinny zawierać odpowiedni prefiks mapowany na przestrzeń nazw. Aby uzyskać więcej informacji, zobacz temat [powiązanie danych — omówienie](../wpf/data/data-binding-overview.md).  
  
 Technicznie `x:XData` , może być używany jako zawartość dowolnej właściwości typu <xref:System.Xml.Serialization.IXmlSerializable>. <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> Jest jednak jedyną wyrazistą implementacją.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Data.XmlDataProvider>
- [Powiązanie danych — omówienie](../wpf/data/data-binding-overview.md)
- [Rozszerzenie znaczników powiązania](../wpf/advanced/binding-markup-extension.md)
