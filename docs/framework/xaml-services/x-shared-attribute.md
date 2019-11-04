---
title: x:Shared — Atrybut
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: c820a9b1d9708e24b1460378199a6addc1e20899
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459926"
---
# <a name="xshared-attribute"></a>x:Shared — Atrybut
Po ustawieniu na `false`modyfikuje zachowanie pobierania zasobów WPF, tak aby żądania dla zasobu z atrybutami utworzyć nowe wystąpienie dla każdego żądania, zamiast udostępniać to samo wystąpienie dla wszystkich żądań.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a>Uwagi  
 `x:Shared` jest mapowany do przestrzeni nazw XAML języka XAML i jest rozpoznawany jako prawidłowy element języka XAML przez .NET Framework usług XAML i ich czytników XAML. Podane możliwości `x:Shared` są jednak odpowiednie dla aplikacji WPF i analizatora XAML WPF. W WPF `x:Shared` jest przydatny tylko jako atrybut, gdy jest stosowany do obiektu, który istnieje w <xref:System.Windows.ResourceDictionary>WPF. Inne użycia nie generują wyjątków analizy ani innych błędów, ale nie mają żadnego wpływu.  
  
 Znaczenia `x:Shared` nie określono w specyfikacji języka XAML. Inne implementacje języka XAML, takie jak te, które kompilują .NET Framework usług XAML, nie muszą zapewniać obsługi udostępniania zasobów. Takie implementacje języka XAML mogą zapewnić podobne zachowanie w strukturze pomocniczej, która również używa wartości `x:Shared`.  
  
 W programie WPF jest `true`domyślny warunek `x:Shared` dla zasobów. Ten stan oznacza, że każde żądanie zasobu zawsze zwraca to samo wystąpienie.  
  
 Modyfikowanie obiektu, który jest zwracany za pomocą interfejsu API zasobów, takiego jak <xref:System.Windows.FrameworkElement.FindResource%2A>, lub modyfikowanie obiektu bezpośrednio w ramach <xref:System.Windows.ResourceDictionary>, powoduje zmianę oryginalnego zasobu. Jeśli odwołania do tego zasobu były odwołaniami do zasobów dynamicznych, odbiorcy tego zasobu otrzymują zmieniony zasób.  
  
 Jeśli odwołania do zasobu były odwołaniami zasobów statycznych, zmiany w zasobie po czasie przetwarzania [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] są nieistotne. Aby uzyskać więcej informacji na temat odwołań do zasobów statycznych i dynamicznych, zobacz [zasoby XAML](../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 Jawne określanie `x:Shared="true"` jest rzadko wykonywane, ponieważ jest już wartością domyślną. Nie ma bezpośredniego odpowiednika kodu dla `x:Shared` w modelu obiektów WPF; może być określony tylko w użyciu języka XAML i musi być przetwarzany przy użyciu domyślnego zachowania WPF lub w pośrednim strumieniu węzła XAML na ścieżce ładowania, jeśli jest przetwarzany za pomocą .NET Framework usług XAML i ich czytników XAML.  
  
 Scenariusz dla `x:Shared="false"` polega na zdefiniowaniu <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> klasie pochodnej jako zasobu, a następnie wprowadzeniu zasobu elementu do modelu zawartości. `x:Shared="false"` umożliwia wprowadzanie zasobu elementu wiele razy w tej samej kolekcji (na przykład <xref:System.Windows.Controls.UIElementCollection>). Bez `x:Shared="false"` jest to nieprawidłowe, ponieważ kolekcja Wymusza unikatowość jego zawartości. Jednak zachowanie `x:Shared="false"` powoduje utworzenie innego identycznego wystąpienia zasobu, a nie zwrócenie tego samego wystąpienia.  
  
 Innym scenariuszem dla `x:Shared="false"` jest użycie zasobu <xref:System.Windows.Freezable> do wartości animacji, ale chcesz zmodyfikować zasób dla każdej animacji.  
  
 W obsłudze ciągów `false` nie jest rozróżniana wielkość liter.  
  
 W WPF `x:Shared` są prawidłowe tylko w następujących warunkach:  
  
- Należy skompilować <xref:System.Windows.ResourceDictionary>, który zawiera elementy z `x:Shared`. <xref:System.Windows.ResourceDictionary> nie może znajdować się w luźnym kodzie XAML ani używać dla motywów.  
  
- <xref:System.Windows.ResourceDictionary>, który zawiera elementy, nie może być zagnieżdżony w obrębie innego <xref:System.Windows.ResourceDictionary>. Na przykład nie można użyć `x:Shared` dla elementów w <xref:System.Windows.ResourceDictionary> znajdujących się w <xref:System.Windows.Style>, który jest już elementem <xref:System.Windows.ResourceDictionary>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.ResourceDictionary>
- [Zasoby XAML](../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Elementy podstawowe](../wpf/advanced/base-elements.md)
