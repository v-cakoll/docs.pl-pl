---
title: x:Shared — Atrybut
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: da35f209b632bdf9e4ab2298239a505df69d6048
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125746"
---
# <a name="xshared-attribute"></a>x:Shared — Atrybut
Po ustawieniu `false`, modyfikuje zachowanie pobierania zasobów WPF żądania zasobu atrybutami Utwórz nowe wystąpienie dla każdego żądania zamiast udostępnianie tego samego wystąpienia dla wszystkich żądań.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a>Uwagi  
 `x:Shared` jest zamapowana na przestrzeń nazw XAML dla języka XAML oraz został rozpoznany jako prawidłowy element języka XAML usług programu .NET Framework XAML i jego czytelnicy XAML. Jednak podane możliwości `x:Shared` są dostępne tylko dla aplikacji WPF i analizatora WPF XAML. W środowisku WPF `x:Shared` przydaje się tylko jako atrybut stosowania do obiektu, który istnieje w technologii WPF <xref:System.Windows.ResourceDictionary>. Inne sposoby użycia nie zgłaszają wyjątków analizy lub inne błędy, ale nie mają wpływu.  
  
 Znaczenie `x:Shared` nie została określona w specyfikacji języka XAML. Inne implementacje XAML, takich jak te, które są kompilowane na usług .NET Framework XAML, niekoniecznie nie oferuje udostępnianie zasobów pomocy technicznej. Takie implementacje XAML może dostarczyć podobne zachowanie w ramach obsługi, które również używane `x:Shared` wartości.  
  
 W środowisku WPF domyślnie `x:Shared` warunku dla zasobów jest `true`. Ten warunek oznacza, że każde żądanie danego zasobu zawsze zwraca to samo wystąpienie.  
  
 Obiekt, który jest zwracany za pośrednictwem zasobów interfejsu API, takich jak modyfikowanie <xref:System.Windows.FrameworkElement.FindResource%2A>, lub zmodyfikowanie obiektu bezpośrednio w ramach <xref:System.Windows.ResourceDictionary>, zmienia oryginalny zasób. Odwołania do tego zasobu, gdyby odwołania do zasobów dynamicznych, użytkowników tego zasobu Pobieranie zmienionych zasobów.  
  
 Odwołania do zasobu, gdyby odwołania do zasobów statycznych, zmienia się do zasobu po [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] czas przetwarzania są nieistotne. Aby uzyskać więcej informacji o statycznej i odwołania do zasobów dynamicznej, zobacz [zasoby XAML](../wpf/advanced/xaml-resources.md).  
  
 Jawne określenie `x:Shared="true"` rzadko odbywa się, ponieważ już jest ustawieniem domyślnym. Brak przeznaczony do bezpośredniego kodu `x:Shared` modelu obiektów WPF; można określić tylko w przypadku użycia XAML i muszą zostać przetworzone przez domyślne zachowanie WPF lub pośredniego strumień węzłów XAML w ścieżce obciążenia przetwarzanie za pomocą programu .NET Framework XAML Se rvices i jego czytelnicy XAML.  
  
 Scenariusz dotyczący `x:Shared="false"` jest, jeśli zdefiniujesz <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> klasy jako zasób, a następnie zasobów elementu jest wprowadzenie do modelu zawartości. `x:Shared="false"` Włącza zasób elementu, należy wprowadzić wiele razy w tej samej kolekcji (takie jak <xref:System.Windows.Controls.UIElementCollection>). Bez `x:Shared="false"` to ustawienie jest nieprawidłowe, ponieważ kolekcja wymusza unikatowości jego zawartość. Jednak `x:Shared="false"` zachowanie tworzy inne wystąpienie identyczne zasobu, zamiast zwracać tego samego wystąpienia.  
  
 Inny scenariusz dla `x:Shared="false"` jest użycie <xref:System.Windows.Freezable> zasobu dla wartości animacji, ale chcesz zmodyfikować zasobów na podstawie poszczególnych animacji.  
  
 Obsługa ciągu `false` nie jest uwzględniana wielkość liter.  
  
 W środowisku WPF `x:Shared` obowiązuje tylko w następujących warunkach:  
  
-   <xref:System.Windows.ResourceDictionary> Zawiera elementy z `x:Shared` muszą być skompilowane. <xref:System.Windows.ResourceDictionary> Nie może być w ramach luźne XAML lub używany dla motywów.  
  
-   <xref:System.Windows.ResourceDictionary> Zawiera elementy nie może być zagnieżdżony w innym <xref:System.Windows.ResourceDictionary>. Na przykład nie można użyć `x:Shared` dla elementów w <xref:System.Windows.ResourceDictionary> znajduje się w <xref:System.Windows.Style> jest już <xref:System.Windows.ResourceDictionary> elementu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.ResourceDictionary>
- [Zasoby XAML](../wpf/advanced/xaml-resources.md)
- [Elementy bazy](../wpf/advanced/base-elements.md)
