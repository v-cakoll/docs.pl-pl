---
title: "Zależność wartości wywołania zwrotnego i walidacji"
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
- dependency properties [WPF], validation
- coerce value callbacks [WPF]
- callbacks [WPF], validation
- dependency properties [WPF], callbacks
- validation of dependency properties [WPF]
ms.assetid: 48db5fb2-da7f-49a6-8e81-3540e7b25825
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0d1b62c7f49653627c626bce2583b2799df931dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="dependency-property-callbacks-and-validation"></a>Zależność wartości wywołania zwrotnego i walidacji
W tym temacie opisano sposób tworzenia właściwości zależności przy użyciu alternatywnych implementacji niestandardowych dla powiązanych właściwości funkcje, takie jak oznaczania sprawdzania poprawności, wywołania zwrotne wywoływane po każdej zmianie właściwości wartość efektywna i zastępowanie możliwe poza wpływ na określenie wartości. W tym temacie omówiono również zastosowaniach rozszerzając domyślne właściwości systemu zachowania przy użyciu tych metod odpowiednie.  
  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że rozumiesz podstawowe scenariusze wdrażania właściwości zależności i jak metadanych są stosowane do właściwości niestandardowych zależności. Zobacz [właściwości zależności niestandardowe](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) i [metadanych właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md) dla kontekstu.  
  
<a name="Validation_Callbacks"></a>   
## <a name="validation-callbacks"></a>Wywołania zwrotne walidacji  
 Wywołania zwrotne walidacji można przypisać do właściwości zależności, gdy najpierw zarejestrować. Wywołanie zwrotne weryfikacji nie jest częścią metadanych właściwości; jest bezpośrednie wejście <xref:System.Windows.DependencyProperty.Register%2A> metody. W związku z tym po utworzeniu wywołanie zwrotne weryfikacji dla właściwości zależności nie mogą zostać zastąpione przez nowej implementacji.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Wywołania zwrotne są wdrażane w taki sposób, że są one udostępniane na wartość obiektu. Zwracają `true` czy podana wartość jest nieprawidłowa dla właściwości; w przeciwnym razie zwracają `false`. Zakłada się, czy właściwość jest poprawnego typu na typ zarejestrowana z systemu właściwości tak Sprawdzanie typu wewnątrz wywołania zwrotne nie jest zazwyczaj określany. Wywołania zwrotne są używane przez system właściwości w wielu różnych operacji. Obejmuje to inicjowania typu początkowej przez wartość domyślną, programistyczny zmiany wywołując <xref:System.Windows.DependencyObject.SetValue%2A>, lub próbuje Zastępowanie metadanych z nowa wartość domyślna. Jeśli wywołanie zwrotne weryfikacji jest wywoływany przez żaden z tych operacji i zwraca `false`, a następnie zostanie zgłoszony wyjątek. Autorzy aplikacji musi być przygotowany do obsługi tych wyjątków. Sprawdzanie poprawności wartości wyliczenia typowym zastosowaniem wywołania zwrotne walidacji lub ograniczający wartości liczb całkowitych lub na symulacyjnych, gdy właściwość ustawia pomiarów, które musi mieć wartość zero lub większy.  
  
 Wywołania zwrotne walidacji w szczególności powinny być klasa modułów sprawdzania poprawności, nie wystąpienia modułów sprawdzania poprawności. Parametry wywołania zwrotnego nie komunikują się określony <xref:System.Windows.DependencyObject> na są ustawione właściwości do sprawdzania poprawności. W związku z tym wywołania zwrotne walidacji nie są przydatne do wymuszania możliwe "zależności", które mogłyby wpłynąć na wartość właściwości, gdy wartość właściwości danego wystąpienia jest zależny od czynników, takich jak wartości innych właściwości danego wystąpienia, lub stan czasu wykonywania.  
  
 Poniżej przedstawiono przykładowy kod służący do scenariusza wywołanie zwrotne weryfikacji bardzo proste: Sprawdzanie poprawności, która właściwość, która zostanie wpisany jako <xref:System.Double> pierwotny nie jest <xref:System.Double.PositiveInfinity> lub <xref:System.Double.NegativeInfinity>.  
  
 [!code-csharp[DPCallbackOverride#ValidateValueCallback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#validatevaluecallback)]
 [!code-vb[DPCallbackOverride#ValidateValueCallback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#validatevaluecallback)]  
  
<a name="Coerce_Value_Callbacks_and_Property_Changed_Events"></a>   
## <a name="coerce-value-callbacks-and-property-changed-events"></a>Coerce — wartość wywołania zwrotne i właściwości zmienione zdarzenia  
 Coerce — wartość wywołania zwrotne przekazywania konkretnym <xref:System.Windows.DependencyObject> wystąpienia dla właściwości, jak <xref:System.Windows.PropertyChangedCallback> implementacje, które są wywoływane przez system właściwości przy każdej zmianie wartości właściwości zależności. Przy użyciu tych dwóch wywołania zwrotne w połączeniu, można utworzyć szereg właściwości dla elementów, gdy zmiany w jedną właściwość wymusi koercja lub ponownej oceny innej właściwości.  
  
 Typowy scenariusz w za pomocą powiązania właściwości zależności jest w przypadku właściwości obsługiwanego interfejsu użytkownika, gdy element posiada jednej właściwości dla wartości minimalną i maksymalną, a trzeci właściwości dla wartości rzeczywistych lub bieżący. W tym miejscu Jeśli maksymalna została dostosowana w taki sposób, że bieżąca wartość przekracza maksimum nowe, należy przekształcić bieżącą wartość nie może przekraczać maksymalną nowy i podobne relacji dla co najmniej do bieżącego.  
  
 Poniżej znajduje się bardzo prosty przykład kodu dla tylko jednej z właściwości zależności trzy ilustrujące tej relacji. W przykładzie pokazano sposób `CurrentReading` minimalna/maksymalna/bieżącego zestawu właściwości powiązanych * odczytu właściwości jest zarejestrowany. Jak pokazano w poprzedniej sekcji użyto sprawdzania poprawności.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Zmiany właściwości wywołania zwrotnego dla bieżącego służy do przekazywania zmian do innych właściwości zależnych, wywołując jawnie wywołania zwrotne wartość coerce, które są zarejestrowane dla innych właściwości:  
  
 [!code-csharp[DPCallbackOverride#OnPCCurrent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#onpccurrent)]
 [!code-vb[DPCallbackOverride#OnPCCurrent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#onpccurrent)]  
  
 Wywołanie zwrotne wartość coerce sprawdza wartości właściwości jest potencjalnie zależne od bieżącej właściwości i przekształca wynik dane bieżącą wartość, w razie potrzeby:  
  
 [!code-csharp[DPCallbackOverride#CoerceCurrent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#coercecurrent)]
 [!code-vb[DPCallbackOverride#CoerceCurrent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#coercecurrent)]  
  
> [!NOTE]
>  Domyślne wartości właściwości nie są przekształcić. Wartość właściwości jest równa wartości domyślnej może wystąpić, gdy wartość właściwości nadal ma początkowej domyślnej lub za pośrednictwem wyczyszczenie innych wartości z <xref:System.Windows.DependencyObject.ClearValue%2A>.  
  
 Zmieniać właściwości oraz wartość coerce wywołań zwrotnych są częścią metadane właściwości. W związku z tym można zmienić wywołań zwrotnych dla właściwości zależności określonego istniejącego na typ, który pochodzi z typu, który jest właścicielem właściwości zależności przez zastępowanie metadanych dla tej właściwości w typie.  
  
<a name="Advanced"></a>   
## <a name="advanced-coercion-and-callback-scenarios"></a>Koercja zaawansowane i scenariusze wywołania zwrotnego  
  
### <a name="constraints-and-desired-values"></a>Ograniczenia i odpowiednie wartości  
 <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> Wywołania zwrotne będzie używany przez system właściwości konwersji wartości zgodnie z logiki deklarowaniu, ale wartość coerced lokalnie ustawionych właściwości nadal będą nadal "żądaną wartość" wewnętrznie. Jeśli ograniczenia są oparte na wartości innych właściwości, które może zmieniać dynamicznie okres istnienia aplikacji, ograniczenia koercja zostaną zmienione dynamicznie również i ograniczonego właściwość można zmienić jego wartości do pobrania maksymalnie zbliżony żądaną wartość jako możliwe nowych ograniczeń. Wartość będzie żądaną wartość unosiło są wszystkie ograniczenia. Jeśli masz wiele właściwości, które są zależne od siebie nawzajem w sposób cykliczne, może potencjalnie wprowadzić sytuacje, w zależności dość złożone. Na przykład w scenariuszu minimalna/maksymalna/bieżącym można wybrać do mieć minimalną i maksymalną się użytkownika można ustawić. Jeśli tak, może być konieczne wymuszone, czy maksymalna zawsze jest większa niż minimalna i na odwrót. Ale jeśli tego koercja jest aktywne, a maksymalna przekształca wynik dane do Minimum, pozostawia bieżącej w stanie unsettable, ponieważ jest zależny od obu i jest ograniczone do przedziału od wartości, które wynosi zero. Następnie jeśli zostaną skorygowane maksymalnej lub minimalnej bieżącego będzie prawdopodobnie "podążać" jedna z wartości, ponieważ żądaną wartość bieżącej nadal są przechowywane i próbuje nawiązać żądaną wartość, jak są zmniejszyć ograniczenia.  
  
 Nie ma nic technicznie problem ze złożonych zależności, ale może być szkody nieznaczne wydajności, jeśli wymaga dużej liczby reevaluations i również może być mylące dla użytkowników, jeśli ich wpływ na Interfejsie bezpośrednio. Należy zachować ostrożność przy zmianie właściwości i przekształcić wartość wywołania zwrotne i upewnij się, że wymuszenia próby może być traktowana jako jego jednoznacznej, a nie "overconstrain".  
  
### <a name="using-coercevalue-to-cancel-value-changes"></a>Anuluj zmiany wartości za pomocą element CoerceValue  
 Właściwości systemu traktują żadnego <xref:System.Windows.CoerceValueCallback> zwracającego wartość <xref:System.Windows.DependencyProperty.UnsetValue> w szczególnych przypadkach. Specjalny przypadek oznacza, że zmiany właściwości, które spowodowały <xref:System.Windows.CoerceValueCallback> wywoływana powinny zostać odrzucone przez system właściwości, oraz że systemu właściwość zamiast tego powinni zgłaszać niezależnie od poprzedniej wartości ma właściwość. Mechanizm ten może być przydatna, sprawdź, czy zmiany do właściwości, które są inicjowane asynchronicznie są nadal ważne dla bieżącego stanu obiektu i pominąć zmiany, jeśli nie. Inny możliwy scenariusz jest, że selektywnie można pominąć w zależności od tego, który składnik właściwości określenie wartości jest odpowiedzialny za wartość zgłaszana wartość. Aby to zrobić, można użyć <xref:System.Windows.DependencyProperty> przekazany jako dane wejściowe dla wywołania zwrotnego i identyfikator właściwości <xref:System.Windows.DependencyPropertyHelper.GetValueSource%2A>, a następnie przetwórz <xref:System.Windows.ValueSource>.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Metadane właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)  
 [Właściwości niestandardowe zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
