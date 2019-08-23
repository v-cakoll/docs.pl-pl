---
title: Zależność wartości wywołania zwrotnego i walidacji
ms.date: 03/30/2017
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
ms.openlocfilehash: 7f00961ba100700c68936cc33facfdc758c77d3f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940823"
---
# <a name="dependency-property-callbacks-and-validation"></a>Zależność wartości wywołania zwrotnego i walidacji
W tym temacie opisano sposób tworzenia właściwości zależności przy użyciu alternatywnych implementacji niestandardowych dla funkcji związanych z właściwościami, takich jak sprawdzanie poprawności, wywołania zwrotne, które są wywoływane za każdym razem, gdy rzeczywista wartość właściwości jest zmieniana, i zastępowanie możliwa zewnętrzna wpływ na określanie wartości. W tym temacie omówiono również scenariusze, w których rozszerzane są domyślne zachowania systemu właściwości przy użyciu tych technik.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że rozumiesz podstawowe scenariusze implementowania właściwości zależności oraz sposób stosowania metadanych do niestandardowej właściwości zależności. Zapoznaj się z [właściwościami zależności niestandardowych](custom-dependency-properties.md) i [metadanych właściwości zależności](dependency-property-metadata.md) dla kontekstu.  
  
<a name="Validation_Callbacks"></a>   
## <a name="validation-callbacks"></a>Wywołania zwrotne weryfikacji  
 Wywołania zwrotne walidacji mogą być przypisywane do właściwości zależności przy pierwszym zarejestrowaniu. Wywołanie zwrotne walidacji nie jest częścią metadanych właściwości; jest to bezpośrednia wartość wejściowa <xref:System.Windows.DependencyProperty.Register%2A> metody. W związku z tym po utworzeniu wywołania zwrotnego walidacji dla właściwości zależności nie można go zastąpić nową implementacją.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Wywołania zwrotne są implementowane w taki sposób, że zapewniają wartość obiektu. Zwracają `true` one, jeśli podana wartość jest prawidłowa dla właściwości; w przeciwnym razie zwracają `false`. Przyjęto założenie, że właściwość jest poprawnego typu dla typu zarejestrowanego w systemie właściwości, więc sprawdzanie typu w ramach wywołania zwrotnego nie jest zwykle wykonywane. Wywołania zwrotne są używane przez system właściwości w różnych różnych operacjach. Obejmuje to początkową inicjalizację typu przez wartość domyślną, programistyczne zmiany przez <xref:System.Windows.DependencyObject.SetValue%2A>wywołanie lub prób przesłaniania metadanych przy użyciu nowej wartości domyślnej. Jeśli wywołanie zwrotne walidacji jest wywoływane przez jakąkolwiek z tych operacji i `false`zwraca, zostanie zgłoszony wyjątek. Aby można było obsłużyć te wyjątki, należy przygotować składniki zapisywania aplikacji. Typowym zastosowaniem wywołania zwrotnego walidacji jest sprawdzanie poprawności wartości wyliczenia lub ograniczanie wartości liczb całkowitych lub podwaja, gdy Właściwość ustawia pomiary, które muszą mieć wartość zero lub większą.  
  
 Wywołania zwrotne walidacji są przeznaczone wyłącznie do modułów walidacji klasy, a nie dla modułów walidacji wystąpień. Parametry wywołania zwrotnego nie komunikują się z konkretnym <xref:System.Windows.DependencyObject> ustawieniem, na którym są ustawione właściwości walidacji. W związku z tym wywołania zwrotne walidacji nie są przydatne do wymuszania możliwych "zależności", które mogą wpływać na wartość właściwości, gdzie wartość specyficzna dla wystąpienia właściwości zależy od czynników, takich jak wartości specyficzne dla wystąpienia innych właściwości lub stan czasu wykonywania.  
  
 Poniżej przedstawiono przykładowy kod dla bardzo prostego scenariusza wywołania zwrotnego walidacji: Sprawdzanie, czy właściwość, która jest wpisana <xref:System.Double> jako pierwotna <xref:System.Double.PositiveInfinity> nie <xref:System.Double.NegativeInfinity>jest ani.  
  
 [!code-csharp[DPCallbackOverride#ValidateValueCallback](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#validatevaluecallback)]
 [!code-vb[DPCallbackOverride#ValidateValueCallback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#validatevaluecallback)]  
  
<a name="Coerce_Value_Callbacks_and_Property_Changed_Events"></a>   
## <a name="coerce-value-callbacks-and-property-changed-events"></a>Wymuszanie wywołania zwrotnego wartości i zdarzeń zmian właściwości  
 Wywołania zwrotne wartości przekształcenie są przekazywane do <xref:System.Windows.DependencyObject> określonego wystąpienia właściwości, <xref:System.Windows.PropertyChangedCallback> tak jak w przypadku implementacji, które są wywoływane przez system właściwości przy każdej zmianie wartości właściwości zależności. Korzystając z tych dwóch wywołań zwrotnych w połączeniu, można utworzyć serię właściwości elementów, w których zmiany w jednej właściwości wymuszą przymus lub ponowną ocenę innej właściwości.  
  
 Typowym scenariuszem użycia powiązania właściwości zależności jest to, że istnieje właściwość oparta na interfejsie użytkownika, w której element zawiera jedną właściwość dla wartości minimalnej i maksymalnej oraz trzecią Właściwość wartości rzeczywistej lub bieżącej. W tym przypadku, jeśli maksimum zostało skorygowane w taki sposób, że bieżąca wartość przekroczyła nowe maksimum, można przekształcić bieżącą wartość nie większą niż nowa maksymalna i podobną relację dla minimum na bieżącą.  
  
 Poniżej znajduje się bardzo krótkie przykładowe kod dla tylko jednej z trzech właściwości zależności, które ilustrują tę relację. W przykładzie pokazano, `CurrentReading` jak jest zarejestrowana Właściwość min/max/Current z pokrewnych właściwości odczytu. Używa walidacji, jak pokazano w poprzedniej sekcji.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Wartość wywołania zwrotnego zmiany właściwości Current jest używana do przekazywania zmian do innych właściwości zależnych przez jawne wywołanie wywołania zwrotnego wartości wymuszonych zarejestrowanych dla tych innych właściwości:  
  
 [!code-csharp[DPCallbackOverride#OnPCCurrent](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#onpccurrent)]
 [!code-vb[DPCallbackOverride#OnPCCurrent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#onpccurrent)]  
  
 Wywołanie zwrotne wartości wymuszonej sprawdza wartości właściwości, od których jest zależna bieżąca właściwość, i w razie potrzeby wykonuje bieżącą wartość:  
  
 [!code-csharp[DPCallbackOverride#CoerceCurrent](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#coercecurrent)]
 [!code-vb[DPCallbackOverride#CoerceCurrent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#coercecurrent)]  
  
> [!NOTE]
> Domyślne wartości właściwości nie są wymuszone. Wartość właściwości równa wartości domyślnej może wystąpić, jeśli wartość właściwości nadal ma jej początkową domyślną lub przez wyczyszczenie innych wartości przy użyciu <xref:System.Windows.DependencyObject.ClearValue%2A>.  
  
 Wywołania zwrotne wartości i właściwości wymuszania są częścią metadanych właściwości. W związku z tym można zmienić wywołania zwrotne dla konkretnej właściwości zależności, ponieważ istnieje ona w typie, który pochodzi od typu będącego właścicielem właściwości zależności, zastępując metadane dla tej właściwości w typie.  
  
<a name="Advanced"></a>   
## <a name="advanced-coercion-and-callback-scenarios"></a>Zaawansowane scenariusze przymusu i wywołania zwrotnego  
  
### <a name="constraints-and-desired-values"></a>Ograniczenia i wymagane wartości  
 <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> Wywołania zwrotne będą używane przez system właściwości w celu wymuszenia wartości zgodnie z deklaracją zadeklarowaną przez użytkownika, ale zastosowana wartość właściwości Local Set nadal zachowa wartość "Żądana wartość" wewnętrznie. Jeśli ograniczenia są oparte na innych wartościach właściwości, które mogą być zmieniane dynamicznie w okresie istnienia aplikacji, ograniczenia przymusu są zmieniane dynamicznie, a właściwość ograniczona może zmienić wartość, aby uzyskać jak blisko żądanej wartości. możliwe jest uwzględnienie nowych ograniczeń. Wartość stanie się żądaną wartością, jeśli wszystkie ograniczenia zostaną zniesione. Możesz wprowadzić pewne dość skomplikowane scenariusze zależności, jeśli masz wiele właściwości, które są zależne od siebie w sposób cykliczny. Na przykład w scenariuszu min/max/Current można wybrać opcję minimalnej i maksymalnej wartości User settable. Jeśli tak, może być konieczne przekształcenie, że wartość maksymalna jest zawsze większa niż minimalna i odwrotnie. Ale jeśli to wymaganie jest aktywne, a maksymalne wartości wymuszone na minimum, pozostawia bieżące w stanie unsettable, ponieważ jest zależne od obu i są ograniczone do zakresu między wartościami, które są równe zero. Następnie, jeśli są dostosowywane wartości maksymalne lub minimalne, bieżąca będzie wyglądać "dalej" po jednej z wartości, ponieważ żądana wartość bieżąca jest nadal przechowywana i próbuje osiągnąć żądaną wartość, ponieważ ograniczenia są zmniejszane.  
  
 Nie ma żadnych technicznych problemów ze złożonymi zależnościami, ale mogą one stanowić niewielkie szkody związane z wydajnością, jeśli wymagają dużej liczby ocen, a także mogą być mylące dla użytkowników, jeśli wpływają one bezpośrednio na interfejs użytkownika. Należy zachować ostrożność ze zmianą właściwości i wymuszać wywołania zwrotne wartości oraz upewnić się, że podjęta próba wykonania może być traktowana jako niejednoznaczne, jak to możliwe, i nie jest "ograniczeniem".  
  
### <a name="using-coercevalue-to-cancel-value-changes"></a>Anulowanie zmian wartości przy użyciu CoerceValue  
 System właściwości będzie traktować wszystkie <xref:System.Windows.CoerceValueCallback> , które zwracają wartość <xref:System.Windows.DependencyProperty.UnsetValue> jako przypadek specjalny. W tym specjalnym przypadku zmiana właściwości, która spowodowała wywoływanie <xref:System.Windows.CoerceValueCallback> , powinna zostać odrzucona przez system właściwości, a system właściwości powinien zamiast tego zgłosić każdą poprzednią wartość właściwości. Mechanizm ten może być przydatny do sprawdzenia, czy zmiany właściwości, która została zainicjowana asynchronicznie, są nadal ważne dla bieżącego stanu obiektu i pomijania zmian, jeśli nie. Innym możliwym scenariuszem jest możliwość selektywnego pomijania wartości w zależności od tego, który składnik wyznaczania wartości właściwości jest odpowiedzialny za raportowaną wartość. W tym celu można użyć <xref:System.Windows.DependencyProperty> przekazywania wywołania zwrotnego i identyfikatora właściwości jako dane wejściowe dla <xref:System.Windows.DependencyPropertyHelper.GetValueSource%2A> <xref:System.Windows.ValueSource>, a następnie przetworzyć.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [Metadane zależności właściwości](dependency-property-metadata.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
