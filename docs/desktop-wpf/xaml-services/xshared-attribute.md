---
title: x:Shared — Atrybut
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: e1cd1d9db5c19decd840b433f986e0ba53557a8b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071375"
---
# <a name="xshared-attribute"></a>x:Shared — Atrybut

Po ustawieniu, modyfikuje zachowanie pobierania zasobów WPF, tak aby `false`żądania przypisanego zasobu utworzyć nowe wystąpienie dla każdego żądania zamiast udostępniania tego samego wystąpienia dla wszystkich żądań.

## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML

```xaml
<ResourceDictionary>
  <object x:Shared="false".../>
</ResourceDictionary>
```

## <a name="remarks"></a>Uwagi

`x:Shared`jest mapowany do przestrzeni nazw XAML języka XAML i jest rozpoznawany jako prawidłowy element języka XAML przez usługi .NET XAML Services i jego czytniki XAML. Jednak podane możliwości `x:Shared` są istotne tylko dla aplikacji WPF i analizatora WPF XAML. W WPF, jest przydatne tylko jako atrybut, `x:Shared` gdy jest stosowany do obiektu, który istnieje w ramach WPF. <xref:System.Windows.ResourceDictionary> Inne użycia nie zgłaszają wyjątków analizy lub innych błędów, ale nie mają wpływu.

Znaczenie nie `x:Shared` jest określone w specyfikacji języka XAML. Inne implementacje XAML, takie jak te, które opierają się na usługach .NET XAML, niekoniecznie zapewniają obsługę udostępniania zasobów. Takie implementacje XAML może zapewnić podobne zachowanie `x:Shared` w ramach obsługi, który również używane wartości.

W WPF WPF `x:Shared` domyślnym `true`warunkiem dla zasobów jest . Ten warunek oznacza, że każde żądanie zasobu zawsze zwraca to samo wystąpienie.

Modyfikowanie obiektu zwracanego za pośrednictwem interfejsu <xref:System.Windows.FrameworkElement.FindResource%2A>API zasobów, takiego jak , <xref:System.Windows.ResourceDictionary>lub modyfikowanie obiektu bezpośrednio w obrębie programu , zmienia oryginalny zasób. Jeśli odwołania do tego zasobu były dynamiczne odwołania do zasobów, konsumenci tego zasobu uzyskać zmieniony zasób.

Jeśli odwołania do zasobu były statyczne odwołania do [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] zasobów, zmiany w zasobie po czasie przetwarzania są nieistotne. Aby uzyskać więcej informacji na temat odwołań do zasobów statycznych i dynamicznych, zobacz [Zasoby XAML](../fundamentals/xaml-resources-define.md).

Jawne określanie `x:Shared="true"` jest rzadko wykonywane, ponieważ jest to już wartość domyślna. Nie ma odpowiednika `x:Shared` kodu bezpośredniego w modelu obiektu WPF; można go określić tylko w użyciu XAML i muszą być przetwarzane przez domyślne zachowanie WPF lub w pośrednim strumieniu węzła XAML na ścieżce obciążenia, jeśli są przetwarzane przy użyciu usług .NET XAML i jego czytników XAML.

Scenariusz jest, `x:Shared="false"` jeśli zdefiniować <xref:System.Windows.FrameworkContentElement> lub pochodną <xref:System.Windows.FrameworkElement> klasy jako zasób, a następnie wprowadzić zasób elementu do modelu zawartości. `x:Shared="false"`umożliwia wielokrotne wprowadzanie zasobu elementu w tej <xref:System.Windows.Controls.UIElementCollection>samej kolekcji (np. ). Bez `x:Shared="false"` tego jest nieprawidłowe, ponieważ kolekcja wymusza unikatowość jego zawartości. Jednak `x:Shared="false"` zachowanie tworzy inne identyczne wystąpienie zasobu zamiast zwracania tego samego wystąpienia.

Innym scenariuszem `x:Shared="false"` jest użycie <xref:System.Windows.Freezable> zasobu dla wartości animacji, ale chcesz zmodyfikować zasób na podstawie animacji.

Obsługa ciągów `false` nie jest rozróżniana wielkość liter.

W `x:Shared` WPF, jest ważny tylko pod następującymi warunkami:

- Ten, <xref:System.Windows.ResourceDictionary> który zawiera `x:Shared` elementy z muszą być skompilowane. Nie <xref:System.Windows.ResourceDictionary> może znajdować się w luźnym kodzie XAML ani używać go do motywów.

- Elementy, <xref:System.Windows.ResourceDictionary> które zawierają elementy, nie <xref:System.Windows.ResourceDictionary>mogą być zagnieżdżone w innym pliku . Na przykład nie `x:Shared` można użyć <xref:System.Windows.ResourceDictionary> dla elementów <xref:System.Windows.Style> w, <xref:System.Windows.ResourceDictionary> który znajduje się w obrębie, który jest już elementem.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.ResourceDictionary>
- [Zasoby XAML](../fundamentals/xaml-resources-define.md)
- [Elementy bazy](../../framework/wpf/advanced/base-elements.md)
