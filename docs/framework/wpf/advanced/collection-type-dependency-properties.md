---
title: Właściwości zależności typu kolekcji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [WPF], dependency
- properties [WPF], collection-type
- dependency properties [WPF]
- collection-type properties [WPF]
ms.assetid: 99f96a42-3ab7-4f64-a16b-2e10d654e97c
ms.openlocfilehash: e783ce4b95b52b86671181dfe4b316d4b91d8fc6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141540"
---
# <a name="collection-type-dependency-properties"></a>Właściwości zależności typu kolekcji
Ten temat zawiera wskazówki i sugerowane wzorce, jak zaimplementować właściwość zależności, gdzie typ właściwości jest typem kolekcji.  

<a name="implementing"></a>
## <a name="implementing-a-collection-type-dependency-property"></a>Implementowanie właściwości zależności typu kolekcji  
 Dla właściwości zależności w ogóle wzorzec implementacji, który należy wykonać jest zdefiniowanie otoki <xref:System.Windows.DependencyProperty> właściwości CLR, gdzie ta właściwość jest wspierany przez identyfikator, a nie pole lub inne konstrukcje. Postępuj zgodnie z tym samym wzorcem podczas implementowania właściwości typu kolekcji. Jednak właściwość typu kolekcji wprowadza pewną złożoność do wzorca, gdy typ, który <xref:System.Windows.DependencyObject> <xref:System.Windows.Freezable> jest zawarty w kolekcji jest sama lub klasa pochodna.  
  
<a name="initializing"></a>
## <a name="initializing-the-collection-beyond-the-default-value"></a>Inicjowanie kolekcji poza wartością domyślną  
 Podczas tworzenia właściwości zależności nie należy określać wartości domyślnej właściwości jako początkowej wartości pola. Zamiast tego należy określić wartość domyślną za pomocą metadanych właściwości zależności. Jeśli właściwość jest typem odwołania, wartość domyślna określona w metadanych właściwości zależności nie jest wartością domyślną na wystąpienie; zamiast tego jest to wartość domyślna, która ma zastosowanie do wszystkich wystąpień typu. W związku z tym należy uważać, aby nie używać pojedynczej kolekcji statycznej zdefiniowane przez metadane właściwości kolekcji jako wartość domyślną pracy dla nowo utworzonych wystąpień typu. Zamiast tego należy upewnić się, że celowo ustawić wartość kolekcji unikatowy (wystąpienie) kolekcji jako część logiki konstruktora klasy. W przeciwnym razie zostanie utworzona niezamierzona klasa singleton.  
  
 Rozważmy następujący przykład. W poniższej sekcji przykładu przedstawiono `Aquarium`definicję klasy , która zawiera wadę z wartością domyślną. Klasa definiuje właściwość `AquariumObjects`zależności typu kolekcji, która <xref:System.Collections.Generic.List%601> używa <xref:System.Windows.FrameworkElement> typu ogólnego z ograniczeniem typu. W <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29> wywołaniu właściwości zależności metadane ustanawia wartość domyślną jako <xref:System.Collections.Generic.List%601>nowy rodzajowy .

> [!WARNING]
> Poniższy kod nie działa poprawnie.

 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 Jeśli jednak kod został pominięty w sposób pokazany, ta domyślna `Aquarium`wartość pojedynczej listy jest współużytkowana dla wszystkich wystąpień pliku . Jeśli uruchomiono następujący kod testowy, który ma na celu `Aquarium` pokazanie, jak utworzyć `Fish` wystąpienia dwóch oddzielnych wystąpień i dodać jeden inny do każdego z nich, zobaczysz zaskakujący wynik:  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 Zamiast każdej kolekcji o liczbie po jednym, każda kolekcja ma liczbę dwóch! Jest tak, `Aquarium` ponieważ `Fish` każdy dodał jego do domyślnej kolekcji wartości, które powstały w wyniku wywołania konstruktora w metadanych i dlatego jest współużytkowany przez wszystkie wystąpienia. Ta sytuacja jest prawie nigdy, co chcesz.  
  
 Aby rozwiązać ten problem, należy zresetować wartość właściwości zależności kolekcji do unikatowego wystąpienia, jako część wywołania konstruktora klasy. Ponieważ właściwość jest właściwością zależności tylko do <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29> odczytu, należy <xref:System.Windows.DependencyPropertyKey> użyć metody, aby ją ustawić, przy użyciu, który jest dostępny tylko w klasie.  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 Teraz, jeśli uruchomiono ten sam kod testowy ponownie, `Aquarium` można zobaczyć więcej oczekiwanych wyników, gdzie każdy obsługiwane własnej kolekcji unikatowe.  
  
 Nie byłoby niewielkie różnice w tym wzorzec, jeśli zdecydujesz się, aby właściwość kolekcji być odczytu i zapisu. W takim przypadku można wywołać akcesor zestawu publicznego z konstruktora do inicjowania, który nadal będzie wywoływanie podpisu <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29> nonkey w obrębie otoki zestawu, przy użyciu identyfikatora publicznego. <xref:System.Windows.DependencyProperty>  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a>Raportowanie zmian wartości wiązania z właściwości kolekcji  
 Właściwość kolekcji, która sama jest właściwością zależności, nie zgłasza automatycznie zmian w jego właściwościach podrzędnych. Jeśli tworzysz powiązania w kolekcji, może to uniemożliwić powiązanie raportowania zmian, w ten sposób unieważnianie niektórych scenariuszy powiązania danych. Jednak jeśli używasz typu <xref:System.Windows.FreezableCollection%601> kolekcji jako typ kolekcji, a następnie zmiany podwładne do zawartych elementów w kolekcji są poprawnie zgłaszane i powiązania działa zgodnie z oczekiwaniami.  
  
 Aby włączyć powiązanie pododwładności w kolekcji obiektów <xref:System.Windows.FreezableCollection%601>zależności, utwórz właściwość <xref:System.Windows.DependencyObject> kolekcji jako typ, z ograniczeniem typu dla tej kolekcji do dowolnej klasy pochodnej.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.FreezableCollection%601>
- [Klasy XAML i niestandardowe dla WPF](xaml-and-custom-classes-for-wpf.md)
- [Przegląd Wiązanie danych](../../../desktop-wpf/data/data-binding-overview.md)
- [Przegląd Właściwości zależności](dependency-properties-overview.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
- [Metadane zależności właściwości](dependency-property-metadata.md)
