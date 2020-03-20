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
ms.openlocfilehash: c5f7439753037aeb5c2ff558da63e063ad65a5e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186436"
---
# <a name="dependency-property-callbacks-and-validation"></a>Zależność wartości wywołania zwrotnego i walidacji
W tym temacie opisano sposób tworzenia właściwości zależności przy użyciu alternatywnych implementacji niestandardowych dla funkcji związanych z właściwościami, takich jak określanie sprawdzania poprawności, wywołania zwrotne, które są wywoływane po zmianie efektywnej wartości właściwości i zastępowanie wpływ na ustalanie wartości. W tym temacie omówiono również scenariusze, w których rozszerzanie domyślnych zachowań systemowych właściwości przy użyciu tych technik jest odpowiednie.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie przyjęto założenie, że rozumiesz podstawowe scenariusze implementacji właściwości zależności i jak metadane są stosowane do właściwości zależności niestandardowej. Zobacz [Właściwości zależności niestandardowej](custom-dependency-properties.md) i [metadane właściwości zależności](dependency-property-metadata.md) dla kontekstu.  
  
<a name="Validation_Callbacks"></a>
## <a name="validation-callbacks"></a>Wywołania zwrotne sprawdzania poprawności  
 Wywołania zwrotne sprawdzania poprawności można przypisać do właściwości zależności przy pierwszym zarejestrowaniu go. Wywołanie zwrotne sprawdzania poprawności nie jest częścią metadanych właściwości; jest to bezpośrednie wejście <xref:System.Windows.DependencyProperty.Register%2A> metody. W związku z tym po wywołaniu zwrotnym sprawdzania poprawności jest tworzony dla właściwości zależności, nie można zastąpić przez nową implementację.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Wywołania zwrotne są implementowane w taki sposób, że są one dostarczane wartość obiektu. Zwracają, `true` jeśli podana wartość jest ważna dla właściwości; w przeciwnym `false`razie wrócą . Zakłada się, że właściwość jest odpowiedniego typu dla typu zarejestrowanego w systemie właściwości, więc sprawdzanie typu w wywołaniach zwrotnych zwykle nie jest wykonywane. Wywołania zwrotne są używane przez system właściwości w różnych operacjach. Obejmuje to początkową inicjację typu domyślną, <xref:System.Windows.DependencyObject.SetValue%2A>zmianę programową przez wywołanie lub próby zastąpienia metadanych nową wartością domyślną. Jeśli wywołanie zwrotne sprawdzania poprawności jest wywoływane `false`przez dowolną z tych operacji i zwraca , następnie zostanie zgłoszony wyjątek. Autorzy aplikacji muszą być przygotowani do obsługi tych wyjątków. Typowym zastosowaniem wywołań zwrotnych sprawdzania poprawności jest sprawdzanie poprawności wartości wyliczania lub ograniczanie wartości liczby całkowitej lub podwaja, gdy właściwość ustawia pomiary, które muszą być zerowe lub większe.  
  
 Wywołania zwrotne sprawdzania poprawności w szczególności są przeznaczone do sprawdzania poprawności klasy, a nie incewatory wystąpienia. Parametry wywołania zwrotnego nie komunikują się z określonymi <xref:System.Windows.DependencyObject> właściwościami do sprawdzenia poprawności. W związku z tym wywołania zwrotne sprawdzania poprawności nie są przydatne do wymuszania możliwych "zależności", które mogą mieć wpływ na wartość właściwości, gdzie wartość właściwości specyficzne dla wystąpienia jest zależna od czynników, takich jak wartości specyficzne dla wystąpienia innych właściwości lub stanu czasu wykonywania.  
  
 Poniżej przedstawiono przykładowy kod dla bardzo prostego scenariusza wywołania zwrotnego sprawdzania poprawności: sprawdzanie poprawności, że właściwość, która jest wpisywany jako <xref:System.Double> pierwotny nie <xref:System.Double.PositiveInfinity> jest lub <xref:System.Double.NegativeInfinity>.  
  
 [!code-csharp[DPCallbackOverride#ValidateValueCallback](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#validatevaluecallback)]
 [!code-vb[DPCallbackOverride#ValidateValueCallback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#validatevaluecallback)]  
  
<a name="Coerce_Value_Callbacks_and_Property_Changed_Events"></a>
## <a name="coerce-value-callbacks-and-property-changed-events"></a>Wywołanie zwrotne wartości wymuszonej i zdarzenia zmiany właściwości  
 Wywołania zwrotne wartości wymuszania przekazać określonego <xref:System.Windows.DependencyObject> <xref:System.Windows.PropertyChangedCallback> wystąpienia dla właściwości, podobnie jak implementacje, które są wywoływane przez system właściwości, gdy zmienia się wartość właściwości zależności. Za pomocą tych dwóch wywołań zwrotnych w połączeniu, można utworzyć serię właściwości na elementy, gdzie zmiany w jednej właściwości wymusi przymusu lub ponownej oceny innej właściwości.  
  
 Typowy scenariusz przy użyciu powiązania właściwości zależności jest, gdy masz właściwości oparte na interfejsie użytkownika, gdzie element posiada jedną właściwość dla wartości minimalnej i maksymalnej i trzeciej właściwości dla wartości rzeczywistej lub bieżącej. W tym miejscu, jeśli maksymalna została dostosowana w taki sposób, że bieżąca wartość przekroczyła nowe maksimum, należy wymuszać bieżącą wartość nie większą niż nowe maksimum i podobną relację dla minimalnej do bieżącej.  
  
 Poniżej przedstawiono bardzo krótki przykładowy kod tylko dla jednej z trzech właściwości zależności, które ilustrują tę relację. W przykładzie `CurrentReading` pokazano, jak jest rejestrowana właściwość zestawu Min/Max/Current powiązanych właściwości *Odczytu. Używa sprawdzania poprawności, jak pokazano w poprzedniej sekcji.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Właściwość zmieniona wywołania zwrotnego dla Current jest używany do przekazywania zmian do innych właściwości zależnych, jawnie wywołując wywołania zwrotne wartości wymuszania, które są zarejestrowane dla tych innych właściwości:  
  
 [!code-csharp[DPCallbackOverride#OnPCCurrent](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#onpccurrent)]
 [!code-vb[DPCallbackOverride#OnPCCurrent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#onpccurrent)]  
  
 Wywołanie zwrotne wartości wmusu sprawdza wartości właściwości, od których potencjalnie zależy bieżąca właściwość, i w razie potrzeby wymusza bieżącą wartość:  
  
 [!code-csharp[DPCallbackOverride#CoerceCurrent](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#coercecurrent)]
 [!code-vb[DPCallbackOverride#CoerceCurrent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#coercecurrent)]  
  
> [!NOTE]
> Domyślne wartości właściwości nie są wymuszane. Wartość właściwości równa wartości domyślnej może wystąpić, jeśli wartość właściwości nadal ma początkową wartość domyślną lub poprzez wyczyszczenie innych wartości za pomocą pliku <xref:System.Windows.DependencyObject.ClearValue%2A>.  
  
 Wartość wmusu i właściwości zmienione wywołania zwrotne są częścią metadanych właściwości. W związku z tym można zmienić wywołania zwrotne dla właściwości określonej zależności, ponieważ istnieje na typ, który pochodzi od typu, który jest właścicielem właściwości zależności, zastępując metadane dla tej właściwości na typ.  
  
<a name="Advanced"></a>
## <a name="advanced-coercion-and-callback-scenarios"></a>Zaawansowane scenariusze przymusu i wywołania zwrotnego  
  
### <a name="constraints-and-desired-values"></a>Wiązania i żądane wartości  
 Wywołania <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> zwrotne będą używane przez system właściwości do wymuszania wartości zgodnie z logiką, którą deklarujesz, ale wymuszona wartość właściwości ustawionej lokalnie nadal będzie zachowywać "żądaną wartość" wewnętrznie. Jeśli ograniczenia są oparte na innych wartościach właściwości, które mogą zmieniać się dynamicznie w okresie istnienia aplikacji, ograniczenia przymusu są również zmieniane dynamicznie, a właściwość ograniczona może zmienić jej wartość, aby zbliżyć się do żądanej wartości, jak możliwe, biorąc pod uwagę nowe ograniczenia. Wartość stanie się żądaną wartością, jeśli wszystkie ograniczenia zostaną zniesione. Potencjalnie można wprowadzić niektóre scenariusze zależności dość skomplikowane, jeśli masz wiele właściwości, które są zależne od siebie w sposób cykliczny. Na przykład w scenariuszu Min/Max/Current można wybrać opcję Ustawienia minimalnego i maksymalnego użytkownika. Jeśli tak, może być konieczne wymuszenia, że maksymalna jest zawsze większa niż minimalna i odwrotnie. Ale jeśli ten przymus jest aktywny, a Maksymalne wymusza do minimum, pozostawia Current w stanie unsettable, ponieważ jest zależny od obu i jest ograniczona do zakresu między wartościami, który jest zerowy. Następnie, jeśli maksymalna lub minimalna są dostosowane, Current wydaje się "śledzić" jedną z wartości, ponieważ żądana wartość Current jest nadal przechowywane i próbuje osiągnąć żądaną wartość, jak ograniczenia są poluzowane.  
  
 Nie ma nic technicznie nie tak ze złożonymi zależnościami, ale mogą one być niewielkie szkody wydajności, jeśli wymagają one dużej liczby ponownych wycen, a także może być mylące dla użytkowników, jeśli mają one wpływ na interfejs użytkownika bezpośrednio. Należy zachować ostrożność przy zmianie właściwości i wymuszać wartość wywołania zwrotnego i upewnij się, że przymus podejmowana próba może być traktowane tak jednoznacznie, jak to możliwe i nie "przepełnienie".  
  
### <a name="using-coercevalue-to-cancel-value-changes"></a>Używanie funkcji CoerceValue do anulowania zmian wartości  
 System właściwości będzie <xref:System.Windows.CoerceValueCallback> traktować każdy, <xref:System.Windows.DependencyProperty.UnsetValue> który zwraca wartość jako przypadek szczególny. Ten szczególny przypadek oznacza, że zmiana <xref:System.Windows.CoerceValueCallback> właściwości, która spowodowała wywołanie powinny zostać odrzucone przez system właściwości i że system właściwości powinien zamiast tego zgłosić niezależnie od poprzedniej wartości właściwości. Ten mechanizm może być przydatne, aby sprawdzić, czy zmiany do właściwości, które zostały zainicjowane asynchronicznie są nadal prawidłowe dla bieżącego stanu obiektu i pominąć zmiany, jeśli nie. Innym możliwym scenariuszem jest selektywne pomijanie wartości w zależności od tego, który składnik wartości właściwości jest odpowiedzialny za wartość zgłaszaną. Aby to zrobić, można <xref:System.Windows.DependencyProperty> użyć przekazanych w wywołaniu zwrotnym <xref:System.Windows.DependencyPropertyHelper.GetValueSource%2A>i identyfikatorze <xref:System.Windows.ValueSource>właściwości jako dane wejściowe dla , a następnie przetworzyć .  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd Właściwości zależności](dependency-properties-overview.md)
- [Metadane zależności właściwości](dependency-property-metadata.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
