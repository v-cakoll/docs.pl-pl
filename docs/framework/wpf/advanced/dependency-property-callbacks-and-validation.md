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
ms.openlocfilehash: 95a40b4a357b1a601eced6c8e5214871b95fcbd2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59219814"
---
# <a name="dependency-property-callbacks-and-validation"></a>Zależność wartości wywołania zwrotnego i walidacji
W tym temacie opisano sposób tworzenia właściwości zależności za pomocą alternatywnych implementacji niestandardowych dla powiązanych właściwości funkcji, takich jak sprawdzanie poprawności oznaczania, wywołania zwrotne, które są wywoływane po każdej zmianie od wartości właściwości i zastępowaniem możliwe, poza wpływa na określenie wartości. W tym temacie omówiono również scenariusze, w których rozwijając domyślną właściwość dla systemu zachowania przy użyciu tych metod jest właściwe.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że rozumiesz podstawowe scenariusze Implementowanie właściwości zależności i sposób stosowania metadanych właściwości zależności niestandardowej. Zobacz [niestandardowe właściwości zależności](custom-dependency-properties.md) i [metadane zależności właściwości](dependency-property-metadata.md) dla kontekstu.  
  
<a name="Validation_Callbacks"></a>   
## <a name="validation-callbacks"></a>Wywołania zwrotne weryfikacji  
 Wywołania zwrotne weryfikacji można przypisać do właściwości zależności, gdy najpierw zarejestrować. Wywołanie zwrotne weryfikacji nie jest częścią metadanych właściwości modelu; jest bezpośrednie wejście <xref:System.Windows.DependencyProperty.Register%2A> metody. W związku z tym po utworzeniu wywołanie zwrotne weryfikacji dla właściwości zależności nie może być zastąpiona przez nową metodę implementacji.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Wywołania zwrotne są implementowane w taki sposób, że są one udostępniane wartość obiektu. Zwracają `true` czy podana wartość jest nieprawidłowa dla właściwości; w przeciwnym razie zwracają `false`. Zakłada się, że właściwość jest poprawnego typu na typ zarejestrowany w systemie właściwości, sprawdzając typ w ramach wywołania zwrotne nie jest zazwyczaj wykonywane. Wywołania zwrotne są używane przez system właściwości w wielu różnych operacji. Obejmuje to inicjowania typu początkowej za pomocą wartości domyślnej, zmień programowy, wywołując <xref:System.Windows.DependencyObject.SetValue%2A>, lub próbuje przesłanianie metadanych z nową wartością domyślną, pod warunkiem. Jeśli wywołanie zwrotne weryfikacji jest wywoływane przez żaden z tych operacji, a następnie zwraca `false`, a następnie zostanie wygenerowany wyjątek. Autorzy aplikacji musi być przygotowana do obsługi tych wyjątków. Typowym zastosowaniem wywołania zwrotne sprawdzania poprawności jest sprawdzania poprawności wartości wyliczenia lub ograniczając wartości liczb całkowitych lub wartości podwójnej precyzji, gdy właściwość ustawia miar, które musi mieć wartość zero lub większą.  
  
 Wywołania zwrotne weryfikacji w szczególności powinny być klasy modułów sprawdzania poprawności, nie wystąpienia modułów sprawdzania poprawności. Parametry wywołania zwrotnego nie komunikują się określonym <xref:System.Windows.DependencyObject> na są ustawiane właściwości w celu weryfikacji. W związku z tym wywołania zwrotne weryfikacji nie są przydatne do wymuszania możliwe "dependencies", które mogą mieć wpływ na wartości właściwości, gdzie wartość danego wystąpienia właściwości jest zależne od czynników, takich jak wystąpienie określonej wartości innych właściwości, lub stan czasu wykonywania.  
  
 Poniżej przedstawiono przykładowy kod dla scenariusza wywołanie zwrotne weryfikacji bardzo prosty: Sprawdzanie poprawności, która właściwość, która jest <xref:System.Double> pierwotny nie jest <xref:System.Double.PositiveInfinity> lub <xref:System.Double.NegativeInfinity>.  
  
 [!code-csharp[DPCallbackOverride#ValidateValueCallback](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#validatevaluecallback)]
 [!code-vb[DPCallbackOverride#ValidateValueCallback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#validatevaluecallback)]  
  
<a name="Coerce_Value_Callbacks_and_Property_Changed_Events"></a>   
## <a name="coerce-value-callbacks-and-property-changed-events"></a>Coerce — wartość wywołania zwrotne i właściwości zmienione zdarzenia  
 Coerce — wartość wywołania zwrotne przekazywania konkretne <xref:System.Windows.DependencyObject> wystąpienia dla właściwości, tak jak <xref:System.Windows.PropertyChangedCallback> implementacji, które są wywoływane przez system właściwości, zawsze po zmianie wartości właściwości zależności. Przy użyciu tych dwóch wywołań zwrotnych w połączeniu, można utworzyć szereg właściwości elementów, których zmiany w jednej właściwości wymusi wymuszenia lub ponownej oceny innej właściwości.  
  
 Typowy scenariusz użycia za pomocą powiązania właściwości zależności jest, gdy właściwość interfejsu opartego na użytkownika, gdy element posiada jedną właściwość dla minimalnej i maksymalnej wartości, a trzeci właściwości dla wartości rzeczywistej lub bieżącego. W tym miejscu maksymalną została dostosowana w taki sposób, że bieżącą wartość przekracza maksymalną nowe, należy przekształcić bieżącą wartość nie może przekraczać nowe maksymalne i podobne relacji co do bieżącego.  
  
 Poniżej znajduje się bardzo krótki przykład kodu dla tylko jednej z właściwości trzy zależności, które ilustrują tę relację. W przykładzie pokazano sposób, w jaki `CurrentReading` właściwość minimalny/maksymalny/bieżący zestaw powiązanych * odczytywanie właściwości jest zarejestrowany. Korzysta ona weryfikacji, jak pokazano w poprzedniej sekcji.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Wywołanie zwrotne zmiany właściwości dla aktualnie jest używany do przekazywania zmian do innych właściwości zależne, za pomocą jawnego wywołania zwrotne wartości coerce, które są zarejestrowane dla tych innych właściwości:  
  
 [!code-csharp[DPCallbackOverride#OnPCCurrent](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#onpccurrent)]
 [!code-vb[DPCallbackOverride#OnPCCurrent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#onpccurrent)]  
  
 Wywołanie zwrotne wartość coerce sprawdza, czy wartości właściwości jest potencjalnie zależne od właściwości bieżącego i przekształca wynik dane bieżącą wartość, jeśli to konieczne:  
  
 [!code-csharp[DPCallbackOverride#CoerceCurrent](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#coercecurrent)]
 [!code-vb[DPCallbackOverride#CoerceCurrent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#coercecurrent)]  
  
> [!NOTE]
>  Domyślne wartości właściwości nie są zmuszone. Wartość właściwości jest równa wartości domyślnej może wystąpić, jeśli wartość właściwości nadal ma początkową domyślną lub za pośrednictwem usuwając innych wartości przy użyciu <xref:System.Windows.DependencyObject.ClearValue%2A>.  
  
 Zmieniać właściwości oraz wartości coerce wywołania zwrotne są częścią metadanych właściwości modelu. W związku z tym można zmienić wywołania zwrotne dla właściwości określonej zależności, zgodnie z jego lokalizacją w typie, który pochodzi z typu, który jest właścicielem właściwość zależności przez zastąpienie metadanych dla tej właściwości na danego typu.  
  
<a name="Advanced"></a>   
## <a name="advanced-coercion-and-callback-scenarios"></a>Scenariusze wywołania zwrotnego i wymuszenia zaawansowane  
  
### <a name="constraints-and-desired-values"></a>Ograniczenia i odpowiednie wartości  
 <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> Wywołań zwrotnych będą używane przez system właściwości konwersji wartości zgodnie z logiki możesz deklarować, ale wartość coerced lokalnie ustawiony właściwość zachowają "żądaną wartość" wewnętrznie. Jeżeli ograniczenia są oparte na wartości innych właściwości, które mogą zmieniać dynamicznie w okresie istnienia aplikacji, wymuszanie ograniczenia zostaną zmienione dynamicznie również i ograniczone właściwość można zmienić jego wartości, aby uzyskać jak najbliżej żądaną wartość jako możliwe nowe ograniczenia. Wartość będzie żądaną wartość, jeśli wszystkie ograniczenia są podniesione. Jeśli masz wiele właściwości, które są zależne od siebie nawzajem w sposób cykliczne, może potencjalnie wprowadzić sytuacje, w zależności dość skomplikowane. Na przykład w scenariuszu minimalny/maksymalny/bieżący można mieć minimalną i maksymalną dopuszczalną użytkownika do ustawienia. Jeśli tak, może być konieczne wymuszone, czy maksymalna zawsze jest większa niż wartość minimalna i na odwrót. Ale jeśli tego wymuszenia jest aktywny, a maksymalna przekształca wynik dane do Minimum, pozostawia bieżące w stanie unsettable, ponieważ zależy zarówno i jest ograniczone do zakresu od wartości, które ma wartość zero. Następnie jeśli są dostosowywane maksymalnej lub minimalnej bieżącego będą prezentowani jako działający "follow" jedną z wartości, ponieważ żądaną wartość bieżącą jest nadal przechowywane i próbuje nawiązać połączenie na żądaną wartość zgodnie z ograniczeniami są zmniejszyć.  
  
 Nie ma pod względem technicznym problem ze złożonych zależności, ale może być szkodą niewielkim wzroście wydajności, jeśli wymagają dużej liczby reevaluations, a także może być mylące dla użytkowników, jeśli mają one wpływ na Interfejsie bezpośrednio. Należy zachować ostrożność przy użyciu zmiany właściwości i wywołania zwrotne wartości wymuszonych i upewnij się, że może być traktowana jako sposób jednoznaczny wymuszenia próby, a nie "overconstrain".  
  
### <a name="using-coercevalue-to-cancel-value-changes"></a>Anuluj zmiany wartości przy użyciu CoerceValue  
 System właściwości będą traktować dowolny <xref:System.Windows.CoerceValueCallback> zwracającego wartość <xref:System.Windows.DependencyProperty.UnsetValue> w szczególnych przypadkach. Ten przypadek specjalny oznacza, że zmiana właściwości, które spowodowały <xref:System.Windows.CoerceValueCallback> wywołanego powinny zostać odrzucone przez system właściwości, a system właściwości zamiast tego powinien wysyłać raporty niezależnie od poprzedniej wartości, gdyby właściwość. Mechanizm ten może być przydatne do Sprawdź, czy zmiany właściwości, które były inicjowane asynchronicznie są ciągle ważny dla bieżącego stanu obiektu i pominąć zmiany, jeśli nie. Inny scenariusz możliwe polega na tym, że selektywnie można pominąć wartość, w zależności od tego, który składnik właściwości określenie wartości jest odpowiedzialny za raportowana. Aby to zrobić, można użyć <xref:System.Windows.DependencyProperty> przekazany jako dane wejściowe na potrzeby wywołania zwrotnego i identyfikator właściwości <xref:System.Windows.DependencyPropertyHelper.GetValueSource%2A>, a następnie przetwarzania <xref:System.Windows.ValueSource>.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [Metadane zależności właściwości](dependency-property-metadata.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
