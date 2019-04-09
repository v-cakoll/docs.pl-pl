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
ms.openlocfilehash: 9ce0b70bfdd70b47857167ff14e62ed2bbda569d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077462"
---
# <a name="collection-type-dependency-properties"></a>Właściwości zależności typu kolekcji
Ten temat zawiera wskazówki i sugerowane wzorce jak implementować właściwość zależności, gdzie typ właściwości jest typem kolekcji.  

<a name="implementing"></a>   
## <a name="implementing-a-collection-type-dependency-property"></a>Implementowanie właściwości zależności typu kolekcji  
 Dla właściwości zależności ogólnie rzecz biorąc, implementacja wzorzec stosowanej jest zdefiniowanie [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] otoki właściwości, w którym ta właściwość jest wspierana przez <xref:System.Windows.DependencyProperty> identyfikatora, a nie pola lub innej konstrukcji. Podczas implementacji właściwości typu kolekcji, stosować tego samego wzorca. Jednak właściwość typu kolekcji wprowadza złożoność wzorca zawsze wtedy, gdy typ, który znajduje się w tej kolekcji sam <xref:System.Windows.DependencyObject> lub <xref:System.Windows.Freezable> klasy pochodnej.  
  
<a name="initializing"></a>   
## <a name="initializing-the-collection-beyond-the-default-value"></a>Inicjowanie zbierania ponad wartość domyślną  
 Podczas tworzenia właściwości zależności nie określisz wartość domyślna właściwości jako wartość początkową pola. Zamiast tego należy określić wartość domyślną, za pośrednictwem metadane zależności właściwości. Jeśli Twoja własność jest typem referencyjnym, wartość domyślna określona w metadane zależności właściwości nie jest wartość domyślną dla każdego wystąpienia; Zamiast tego jest wartość domyślna, która ma zastosowanie do wszystkich wystąpień tego typu. W związku z tym należy uważać, aby nie korzystać z pojedynczej kolekcji statyczne, zdefiniowane przez kolekcję metadanych właściwości z wartością domyślną pracy dla nowo utworzonego wystąpienia tego typu. Zamiast tego należy się upewnić, celowo ustaw wartość kolekcji do kolekcji unikatowych (wystąpienie) jako część logiki konstruktora klasy. W przeciwnym razie zostaną utworzone klasy pojedynczej niezamierzone.  
  
 Rozważmy następujący przykład. Poniższa sekcja przykładzie przedstawiono definicję klasy `Aquarium`. Definiuje właściwości zależności typu kolekcji `AquariumObjects`, ogólny, który używa <xref:System.Collections.Generic.List%601> to typ <xref:System.Windows.FrameworkElement> typu ograniczenia. W <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29> wywołania dla właściwości zależności, metadane ustanawia wartość domyślna, która ma być nowy ogólny <xref:System.Collections.Generic.List%601>.  
  
 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 Jednak jeśli właśnie kod przedstawiony, tę wartość domyślną pojedynczej liście jest współdzielona przez wszystkie wystąpienia elementu `Aquarium`. Po uruchomieniu następujący kod testu, który jest przeznaczony do pokazania, jak można utworzyć dwa oddzielne `Aquarium` wystąpień, a następnie dodaj pojedynczy inny `Fish` do każdego z nich można zobaczyć Zaskakujące wyniki:  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 Zamiast poszczególnych kolekcji o liczenia jedengo Każda kolekcja ma liczbę dwa! Jest to spowodowane każdego `Aquarium` dodano jego `Fish` jako kolekcji wartości domyślnej korzystaniem przez wywołanie konstruktora pojedynczego w metadanych i dlatego jest współużytkowana przez wszystkie wystąpienia. Ta sytuacja jest prawie nigdy nie należy.  
  
 Aby rozwiązać ten problem, możesz zresetować wartość właściwości zależności kolekcji do unikatowego wystąpienia, jako część wywołania konstruktora klasy. Ponieważ właściwość ma wartość właściwości zależności tylko do odczytu, możesz użyć <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29> metodę, aby ustawić go przy użyciu <xref:System.Windows.DependencyPropertyKey> , jest dostępny tylko w klasie.  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 Teraz po uruchomieniu, że takie same ponownie przetestuj kod, zostanie wyświetlona więcej oczekiwanych wyników, gdzie każdy `Aquarium` obsługiwane swoją własną unikatową kolekcję.  
  
 Istniała nieznaczne modyfikacją tego wzorca, jeśli została wybrana opcja mają swoje właściwości kolekcji można odczytu i zapisu. W takim przypadku można wywołać metody dostępu publicznego zestawu z konstruktora, celu inicjowania, które nadal będą wywoływać nonkey podpis <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29> w ramach Twojej otoki zestawu przy użyciu publicznego <xref:System.Windows.DependencyProperty> identyfikatora.  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a>Raportowanie zmiany wartości powiązania z właściwościami kolekcji  
 Właściwość kolekcji, która sama jest właściwość zależności nie raportuje automatycznie zmiany do właściwości podrzędnych. W przypadku tworzenia powiązań do kolekcji, może to spowodować tworzenie powiązań z raportowania zmian, tym samym unieważniając Niektóre scenariusze powiązania danych. Jednak jeśli używasz typu kolekcji <xref:System.Windows.FreezableCollection%601> jako typ kolekcji, następnie zmiany właściwości podrzędnych elementów zawartych w kolekcji są prawidłowo raportowane, oraz powiązanie działa zgodnie z oczekiwaniami.  
  
 Aby włączyć powiązania właściwości podrzędnej w kolekcji obiektów zależności, Utwórz właściwość kolekcji jako typ <xref:System.Windows.FreezableCollection%601>, z ograniczeniem typu dla tej kolekcji do dowolnego <xref:System.Windows.DependencyObject> klasy pochodnej.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FreezableCollection%601>
- [Klasy XAML i niestandardowe dla WPF](xaml-and-custom-classes-for-wpf.md)
- [Przegląd Wiązanie danych](../data/data-binding-overview.md)
- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
- [Metadane zależności właściwości](dependency-property-metadata.md)
