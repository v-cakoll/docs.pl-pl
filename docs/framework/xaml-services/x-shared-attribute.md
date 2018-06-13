---
title: x:Shared — Atrybut
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: bee37735382249d2919ef870ca495e6096532352
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563800"
---
# <a name="xshared-attribute"></a>x:Shared — Atrybut
Jeśli wartość `false`, modyfikuje zachowanie pobieranie zasobu WPF, tak aby żądania dotyczące zasobów oparte na atrybutach Utwórz nowe wystąpienie dla każdego żądania i nie udostępniały tej samej wystąpienia dla wszystkich żądań.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a>Uwagi  
 `x:Shared` jest mapowany na przestrzeń nazw XAML dla języka XAML i został rozpoznany jako prawidłowy element języka XAML .NET Framework XAML Services i jego czytników XAML. Jednak podane możliwości `x:Shared` są dostępne tylko dla aplikacji WPF i dla analizatora WPF XAML. Na platformie WPF `x:Shared` przydaje się tylko jako atrybut po zastosowaniu do obiektu, który istnieje w ramach WPF <xref:System.Windows.ResourceDictionary>. Inne użycia nie zgłaszają wyjątki analizy lub inne błędy, ale nie działają.  
  
 Znaczenie `x:Shared` nie została określona w specyfikacji języka XAML. Inne implementacje XAML, takimi jak rozbudowywać usług .NET Framework XAML, nie zapewniają niekoniecznie udostępniania zasobów pomocy technicznej. Takie implementacje XAML może dostarczyć podobne zachowania w ramach obsługi, które również używane `x:Shared` wartości.  
  
 Na platformie WPF, domyślnie `x:Shared` warunek dla zasobów jest `true`. Ten stan oznacza, że każde żądanie zasobu zawsze zwraca to samo wystąpienie.  
  
 Modyfikowanie obiektu, który jest zwracany za pomocą zasobów interfejsu API, takich jak <xref:System.Windows.FrameworkElement.FindResource%2A>, lub modyfikowania obiektu bezpośrednio w <xref:System.Windows.ResourceDictionary>, zmiany pierwotnego zasobu. Odwołania do tego zasobu, gdyby odwołania do zasobów dynamicznych, korzystającym z tego zasobu Pobierz zmienione zasobów.  
  
 Odwołania do zasobu, gdyby odwołania do zasobu statycznych, zmiany zasobów po [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] czas przetwarzania nie mają znaczenia. Aby uzyskać więcej informacji o statyczne i odwołania do zasobów dynamicznej, zobacz [zasobów XAML](../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Jawne określenie `x:Shared="true"` rzadko się odbywa, ponieważ już jest ustawieniem domyślnym. Nie ma odpowiednika dla żadnego kodu bezpośrednio `x:Shared` w podsystemie WPF modelu obiektów; można określić tylko w przypadku użycia XAML i muszą zostać przetworzone przez domyślne zachowanie WPF lub pośredni strumień węzłów XAML w ścieżce obciążenia przetwarzanie przy użyciu programu .NET Framework XAML Se rvices i jego czytników XAML.  
  
 Scenariusz dla `x:Shared="false"` jest Jeśli zdefiniujesz <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> klasy jako zasób, a następnie wprowadzić zasobów element do modelu zawartości. `x:Shared="false"` Włącza zasób elementu można wprowadzać wiele razy w tej samej kolekcji (takie jak <xref:System.Windows.Controls.UIElementCollection>). Bez `x:Shared="false"` to jest nieprawidłowa, ponieważ kolekcja wymusza unikatowości jego zawartość. Jednak `x:Shared="false"` zachowanie tworzy inne wystąpienie identyczne zasobu zamiast zwracać tego samego wystąpienia.  
  
 Inny scenariusz `x:Shared="false"` jest użycie <xref:System.Windows.Freezable> zasobu dla wartości animacji, ale chcesz modyfikacja zasobu na podstawie na animacji.  
  
 Obsługa ciągu `false` nie jest uwzględniana wielkość liter.  
  
 Na platformie WPF `x:Shared` działa tylko w następujących warunkach:  
  
-   <xref:System.Windows.ResourceDictionary> Zawiera elementy z `x:Shared` muszą być skompilowane. <xref:System.Windows.ResourceDictionary> Nie może być w XAML utracić ani użyte dla motywów.  
  
-   <xref:System.Windows.ResourceDictionary> Zawiera elementy nie może być zagnieżdżony w innym <xref:System.Windows.ResourceDictionary>. Na przykład nie można użyć `x:Shared` dla elementów w <xref:System.Windows.ResourceDictionary> znajduje się w <xref:System.Windows.Style> jest już <xref:System.Windows.ResourceDictionary> elementu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.ResourceDictionary>  
 [Zasoby XAML](../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Elementy podstawowe](../../../docs/framework/wpf/advanced/base-elements.md)
