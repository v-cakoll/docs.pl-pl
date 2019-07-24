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
ms.openlocfilehash: dd268c0c132f4ecefe7b2336432442d9569ca38f
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401554"
---
# <a name="collection-type-dependency-properties"></a>Właściwości zależności typu kolekcji
Ten temat zawiera wskazówki i sugerowane wzorce dotyczące implementowania właściwości zależności, gdzie typ właściwości jest typem kolekcji.  

<a name="implementing"></a>   
## <a name="implementing-a-collection-type-dependency-property"></a>Implementowanie właściwości zależności typu kolekcji  
 Dla właściwości zależności ogólnie rzecz biorąc, wzorzec implementacji, który należy wykonać należy zdefiniować otokę właściwości CLR, gdzie ta właściwość jest obsługiwana przez <xref:System.Windows.DependencyProperty> identyfikator, a nie jako pole lub inną konstrukcję. Ten sam wzorzec należy wykonać podczas implementowania właściwości typu kolekcji. Jednak właściwość typu kolekcji wprowadza pewną złożoność do wzorca zawsze, gdy typ, który jest zawarty w kolekcji, jest samą <xref:System.Windows.DependencyObject> klasą lub <xref:System.Windows.Freezable> klasy pochodnej.  
  
<a name="initializing"></a>   
## <a name="initializing-the-collection-beyond-the-default-value"></a>Inicjowanie kolekcji poza wartością domyślną  
 Podczas tworzenia właściwości zależności nie należy określać wartości domyślnej właściwości jako początkowej wartości pola. Zamiast tego należy określić wartość domyślną za pomocą metadanych właściwości zależności. Jeśli właściwość jest typem referencyjnym, wartość domyślna określona w metadanych właściwości zależności nie jest wartością domyślną dla danego wystąpienia; Zamiast tego jest to wartość domyślna, która ma zastosowanie do wszystkich wystąpień tego typu. W związku z tym należy zachować ostrożność, aby nie używać pojedynczej kolekcji statycznej zdefiniowanej przez metadane właściwości kolekcji jako działającej wartości domyślnej dla nowo utworzonych wystąpień danego typu. Zamiast tego należy upewnić się, że w ramach logiki konstruktora klasy zacelowo ustawisz wartość kolekcji na unikatową kolekcję (wystąpienie). W przeciwnym razie zostanie utworzona niezamierzona Klasa singleton.  
  
 Rozważmy następujący przykład. W poniższej sekcji przykładu przedstawiono definicję klasy `Aquarium`. Klasa definiuje Właściwość `AquariumObjects`zależności typu kolekcji, która używa typu ogólnego <xref:System.Collections.Generic.List%601> z <xref:System.Windows.FrameworkElement> ograniczeniem typu. W wywołaniu właściwości zależności metadane są ustalane jako nowe ogólne <xref:System.Collections.Generic.List%601>. <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29>  
  
 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 Jeśli jednak po lewej stronie pozostało kod, ta wartość domyślna pojedynczej listy jest udostępniana dla wszystkich wystąpień `Aquarium`. W przypadku uruchomienia poniższego kodu testowego, który jest przeznaczony do pokazania, jak można utworzyć `Aquarium` wystąpienie dwóch oddzielnych wystąpień i dodać `Fish` jeden inny do każdego z nich, zobaczysz wynik zaskakujące:  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 Zamiast każdej kolekcji z liczbą jednego, każda kolekcja ma liczbę dwóch! Jest to spowodowane tym `Aquarium` , że `Fish` każdy z nich został dodany do kolekcji wartości domyślnych, co spowodowało wystąpienie pojedynczego konstruktora w metadanych i dlatego jest współużytkowany między wszystkimi wystąpieniami. Ta sytuacja jest niemal nigdy niepotrzebna.  
  
 Aby rozwiązać ten problem, należy zresetować wartość właściwości zależność kolekcji do unikatowego wystąpienia w ramach wywołania konstruktora klasy. Ponieważ właściwość jest właściwością zależności tylko do odczytu, należy użyć <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29> metody do jej ustawienia <xref:System.Windows.DependencyPropertyKey> przy użyciu, która jest dostępna tylko w obrębie klasy.  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 Teraz po ponownym uruchomieniu tego samego kodu testowego można zobaczyć więcej oczekiwanych wyników, gdzie każda z `Aquarium` nich obsługuje własną unikatową kolekcję.  
  
 W przypadku wybrania właściwości kolekcji do odczytu i zapisu powinna istnieć niewielka odmiana tego wzorca. W takim przypadku można wywołać metodę dostępu do zestawu publicznego z konstruktora, aby wykonać inicjalizację, która nadal wywoła sygnaturę <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29> nonkey w ramach otoki zestawu przy użyciu identyfikatora publicznego. <xref:System.Windows.DependencyProperty>  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a>Raportowanie zmian wartości powiązania z właściwości kolekcji  
 Właściwość kolekcji, która jest sama właściwością zależności, nie raportuje automatycznie zmian w jego właściwościach. Jeśli tworzysz powiązania do kolekcji, może to uniemożliwić powiązanie z raportowaniem, co spowoduje unieważnienie niektórych scenariuszy powiązań danych. Jeśli jednak typ <xref:System.Windows.FreezableCollection%601> kolekcji jest używany jako typ kolekcji, zmiany właściwości Subproperty w zawarte elementy w kolekcji są poprawnie zgłaszane, a powiązanie działa zgodnie z oczekiwaniami.  
  
 Aby włączyć powiązanie Subproperty w kolekcji obiektów zależności, należy utworzyć właściwość kolekcji jako typ <xref:System.Windows.FreezableCollection%601>z ograniczeniem typu dla tej kolekcji do dowolnej <xref:System.Windows.DependencyObject> klasy pochodnej.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FreezableCollection%601>
- [Klasy XAML i niestandardowe dla WPF](xaml-and-custom-classes-for-wpf.md)
- [Powiązanie danych — omówienie](../data/data-binding-overview.md)
- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
- [Metadane zależności właściwości](dependency-property-metadata.md)
