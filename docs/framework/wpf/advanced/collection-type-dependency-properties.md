---
title: "Właściwości zależności typu kolekcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [WPF], dependency
- properties [WPF], collection-type
- dependency properties [WPF]
- collection-type properties [WPF]
ms.assetid: 99f96a42-3ab7-4f64-a16b-2e10d654e97c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 11927efee2b8375550767d119e6b4a95b3ef7bd8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="collection-type-dependency-properties"></a>Właściwości zależności typu kolekcji
Ten temat zawiera wskazówki i sugerowane wzorce dla implementowania właściwości zależności, których typ właściwości jest typem kolekcji.  
  
 
  
<a name="implementing"></a>   
## <a name="implementing-a-collection-type-dependency-property"></a>Implementowanie właściwości zależności typ kolekcji  
 Dla właściwości zależności ogólnie rzecz biorąc, można wzorzec implementacji jest zdefiniowanie [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] otoki właściwości, których tej właściwości nie jest obsługiwana przez <xref:System.Windows.DependencyProperty> identyfikator zamiast pola lub innych konstrukcji. W przypadku użycia tego samego wzorca po implementować właściwość typu kolekcji. Jednak właściwość typu kolekcji wprowadza pewne złożoności wzorzec zawsze, gdy typ, który jest zawarty w kolekcji jest <xref:System.Windows.DependencyObject> lub <xref:System.Windows.Freezable> klasy.  
  
<a name="initializing"></a>   
## <a name="initializing-the-collection-beyond-the-default-value"></a>Inicjowanie zbierania ponad wartość domyślną  
 Podczas tworzenia właściwości zależności nie określisz wartości domyślnej właściwości jako wartość początkowa pola. Zamiast tego można określić wartość domyślną, za pomocą metadanych właściwości zależności. Jeśli Twoje właściwości jest typem referencyjnym, wartość domyślna określona w metadanych właściwości zależności nie jest wartość domyślną dla każdego wystąpienia; Zamiast tego jest wartość domyślna, która ma zastosowanie do wszystkich wystąpień tego typu. W związku z tym należy zachować ostrożność, aby nie korzystać z pojedynczej kolekcji statycznych zdefiniowany przez metadane właściwości kolekcji pracy wartość domyślną dla nowo utworzonego wystąpienia danego typu. Zamiast tego należy się upewnić, celowo ustaw wartość kolekcji do kolekcji unikatowy (wystąpieniem) jako część logiki konstruktora klasy. W przeciwnym razie zostanie utworzony klasa pojedyncza przypadkowe.  
  
 Rozważmy następujący przykład. W poniższej sekcji przykładzie przedstawiono definicję klasy `Aquarium`. Klasa definiuje właściwość zależności typu kolekcji `AquariumObjects`, ogólnego, który używa <xref:System.Collections.Generic.List%601> to typ <xref:System.Windows.FrameworkElement> ograniczenie typu. W <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29> wywołania dla właściwości zależności metadanych ustanawia wartość domyślna ma być nowe ogólny <xref:System.Collections.Generic.List%601>.  
  
 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 Jednak jeśli kod pozostanie tak jak pokazano tej wartości domyślne jedną listę jest współdzielona przez wszystkie wystąpienia `Aquarium`. W przypadku uruchomienia następujący kod testu, który jest przeznaczony do wyświetlenia, jak może utworzyć wystąpienia dwa oddzielne `Aquarium` wystąpień i Dodaj jeden różnych `Fish` do każdego z nich, można zobaczyć zaskakująco wyników:  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 Zamiast każdej kolekcji o licznik równy jeden Każda kolekcja ma licznika dwóch! Jest to spowodowane każdego `Aquarium` dodana jego `Fish` do kolekcji wartości domyślne, wynika z jednego konstruktora wywołanie w metadanych i dlatego jest współużytkowana przez wszystkie wystąpienia. Ta sytuacja jest prawie nigdy nie chcesz.  
  
 Aby rozwiązać ten problem, należy zresetować wartość właściwości zależności kolekcji do unikatowego wystąpienia, jako część wywołania konstruktora klasy. Ponieważ ta właściwość jest właściwością tylko do odczytu zależności, użyj <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29> metodę, aby ustawić, za pomocą <xref:System.Windows.DependencyPropertyKey> który jest dostępny tylko w klasie.  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 Teraz, po przeprowadzeniu, że sama ponownie testowania kodu, można zobaczyć więcej oczekiwanych rezultatów, gdzie każdy `Aquarium` obsługiwane unikatowych pobrania.  
  
 Byłoby niewielkich zmian w tym wzorcu Jeśli zdecydujesz się na Twoje właściwości kolekcji można odczytu i zapisu. W takim przypadku należy wywołać metody dostępu publicznego zestawu z konstruktora w celu inicjowania, który będzie nadal wywoływania nonkey podpis <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29> w ramach Twojej otoki zestawu przy użyciu publicznego <xref:System.Windows.DependencyProperty> identyfikator.  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a>Raportowanie powiązanie zmiany wartości z właściwości kolekcji  
 Właściwości kolekcji, która jest elementem właściwości zależności nie raportuje automatycznie zmiany do właściwości podrzędnych. W przypadku tworzenia powiązania w kolekcji, może to spowodować powiązania z raportowania zmian, w związku z tym unieważnia niektóre scenariusze powiązania danych. Jednak jeśli używany jest typ kolekcji <xref:System.Windows.FreezableCollection%601> jako typ kolekcji, następnie zmiany podrzędnych zawartych w niej elementów w kolekcji są prawidłowo raportowane i powiązanie działa zgodnie z oczekiwaniami.  
  
 Aby włączyć podwłaściwości powiązania w kolekcji obiektów zależności, należy utworzyć jako typ właściwości kolekcji <xref:System.Windows.FreezableCollection%601>, z ograniczeniem typu dla tej kolekcji do dowolnego <xref:System.Windows.DependencyObject> klasy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.FreezableCollection%601>  
 [XAML oraz klas niestandardowych dla WPF](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [Omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Właściwości niestandardowe zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Metadane właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)
