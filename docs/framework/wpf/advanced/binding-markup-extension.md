---
title: Rozszerzenie znaczników powiązania
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: 7a1bfde401722333181b3c057b3f58aebd7811a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713395"
---
# <a name="binding-markup-extension"></a>Rozszerzenie znaczników powiązania
Różni się wartość właściwości wartość powiązanych z danymi, tworzenie obiektu będącego wyrażeniem pośrednich i interpretowanie kontekst danych, która ma zastosowanie do elementu i jego powiązania w czasie wykonywania.  
  
## <a name="binding-expression-usage"></a>Użycie wyrażenia wiązania  
  
```  
<object property="{Binding}" .../>  
-or-  
<object property="{Binding  bindProp1=value1[, bindPropN=valueN]*}" ...  
/>  
-or-  
<object property="{Binding path}" .../>  
-or  
<object property="{Binding path[, bindPropN=valueN]*}" .../>  
```  
  
## <a name="syntax-notes"></a>Informacje o składni  
 W tych składni `[]` i `*` nie są literały. Są one częścią notacji, aby wskazać, że zero lub więcej *bindProp*`=`*wartość* pary mogą być używane, za pomocą `,` separator między nimi i poprzednim *bindProp*  `=` *wartość* pary.  
  
 Właściwości opisane w sekcji "Powiązanie, można można ustawić za pomocą powiązania rozszerzenie właściwości" można zamiast tego można ustawić za pomocą atrybutów <xref:System.Windows.Data.Binding> element obiektu. Jednak to nie naprawdę użycie rozszerzenia znaczników <xref:System.Windows.Data.Binding>, jest po prostu ogólnego przetwarzania XAML atrybutów, ustaw właściwości środowiska CLR, które <xref:System.Windows.Data.Binding> klasy. Innymi słowy `<Binding` *bindProp1*`="`*wartość1* `"[` *bindPropN*`="`*wartośćN* `"]*/>` jest równoważny składni w przypadku atrybutów elementów <xref:System.Windows.Data.Binding> obiektu użycie elementu zamiast `Binding` użycia wyrażenia. Aby dowiedzieć się o użycie atrybutu XAML konkretne właściwości <xref:System.Windows.Data.Binding>, zobacz sekcję "Użycia atrybutu XAML" odpowiednie właściwości <xref:System.Windows.Data.Binding> w bibliotece klas programu .NET Framework.  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|Nazwa <xref:System.Windows.Data.Binding> lub <xref:System.Windows.Data.BindingBase> właściwości do ustawienia. Nie wszystkie <xref:System.Windows.Data.Binding> właściwości można ustawić za pomocą `Binding` rozszerzenie i niektóre właściwości są można ustawić w ramach `Binding` wyrażenie tylko przy użyciu dalszych zagnieżdżone rozszerzenia znaczników. Zobacz sekcję "Powiązanie, można można ustawić za pomocą powiązania rozszerzenie właściwości".|  
|`value1, valueN`|Wartość do ustawienia właściwości. Obsługa wartość atrybutu jest ostatecznie określonego typu i logiki konkretne <xref:System.Windows.Data.Binding> ustawienia właściwości.|  
|`path`|Ciąg ścieżki, która ustawia niejawny <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> właściwości. Zobacz też [składnia elementu PropertyPath XAML](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).|  
  
## <a name="unqualified-binding"></a>Niekwalifikowane {powiązania}  
 `{Binding}` Użycia objętego "Powiązanie użycie wyrażenia" tworzy <xref:System.Windows.Data.Binding> obiektu z wartościami domyślnymi, co obejmuje początkowy <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> z `null`. To nadal jest użyteczne w wielu scenariuszach, ponieważ utworzony <xref:System.Windows.Data.Binding> może polegać na właściwości powiązania klucza danych takich jak <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> i <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> ustawiany w kontekście danych w czasie wykonywania. Aby uzyskać więcej informacji na temat koncepcji kontekst danych, zobacz [powiązanie danych](../../../../docs/framework/wpf/data/data-binding-wpf.md).  
  
## <a name="implicit-path"></a>Niejawne ścieżki  
 `Binding` Używa rozszerzenia znaczników <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> jako koncepcji "Właściwość domyślna", gdzie `Path=` nie musi występować w wyrażeniu. Jeśli określisz `Binding` wyrażenia ze ścieżką niejawne, niejawne ścieżki musi występować jako pierwszy w wyrażeniu, przed inne `bindProp` = `value` par gdzie <xref:System.Windows.Data.Binding> określono właściwość według nazwy. Na przykład: `{Binding PathString}`, gdzie `PathString` jest ciągiem, który jest wynikiem obliczania wartości <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> w <xref:System.Windows.Data.Binding> utworzone przez użycie rozszerzenia znaczników. Można dołączyć niejawne ścieżkę z innych nazwane właściwości po przecinka jako separatora, na przykład `{Binding LastName, Mode=TwoWay}`.  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>Właściwości powiązania, które można ustawić za pomocą rozszerzenia wiązania  
 Składni przedstawione w tym temacie korzysta z ogólnego `bindProp` = `value` zbliżenia, ponieważ wiele właściwości odczytu/zapisu w programu <xref:System.Windows.Data.BindingBase> lub <xref:System.Windows.Data.Binding> , można ustawić przy użyciu `Binding` — rozszerzenie znaczników / Składnia wyrażeń. Można je skonfigurować w dowolnej kolejności, z wyjątkiem niejawnej <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>. (Istnieje możliwość jawnie określić `Path=`, w którym to przypadku może być ustawiona w dowolnej kolejności). Zasadniczo można ustawić zero lub więcej właściwości na liście poniżej, używając `bindProp` = `value` pary rozdzielonych przecinkami.  
  
 Niektóre z tych wartości właściwości wymagają typów obiektów, które nie obsługuje konwersji typu natywnego w składni tekstu w XAML i dlatego wymagają rozszerzenia znaczników do można ustawić jako wartość atrybutu. Sprawdź sekcję użycie atrybutu XAML w bibliotece klas programu .NET Framework, dla każdej właściwości, aby uzyskać więcej informacji; ciąg możesz użyć składni atrybutu XAML lub bez dalszego rozszerzenia znaczników użycia jest zasadniczo taka sama jak wartość określoną w `Binding` wyrażenia, z wyjątkiem nie należy umieszczać znaków cudzysłowu wokół każdej `bindProp` = `value` w `Binding` wyrażenia.  
  
-   <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: ciąg, który identyfikuje grupę możliwe powiązanie. Jest to pojęcie stosunkowo zaawansowane powiązanie; zobacz stronę odniesienia dla <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>.  
  
-   <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: Wartość logiczna, może być `true` lub `false`. Wartość domyślna to `false`.  
  
-   <xref:System.Windows.Data.Binding.Converter%2A>: można ustawić jako `bindProp` = `value` ciąg znaków w wyrażeniu, ale aby to zrobić wymaga odwołania do obiektu dla wartości, takich jak [staticresource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md). Wartość w tym przypadku jest wystąpienie klasy niestandardowej konwertera.  
  
-   <xref:System.Windows.Data.Binding.ConverterCulture%2A>: można ustawić w wyrażeniu jako identyfikatora oparte na standardach. zobacz temat referencyjny dotyczący <xref:System.Windows.Data.Binding.ConverterCulture%2A>.  
  
-   <xref:System.Windows.Data.Binding.ConverterParameter%2A>: można ustawić jako `bindProp` = `value` ciąg znaków w wyrażeniu, ale jest zależna od typu parametru przekazywana. W przypadku przekazywania typu odwołania dla wartości, to użycie wymaga odwołania do obiektu takich jak zagnieżdżoną [staticresource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
-   <xref:System.Windows.Data.Binding.ElementName%2A>: wzajemnie się wykluczają i <xref:System.Windows.Data.Binding.RelativeSource%2A> i <xref:System.Windows.Data.Binding.Source%2A>; każdy z tych właściwości powiązań reprezentuje metodologii określonego powiązania. Zobacz [Przegląd wiązanie danych](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
-   <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: można ustawić jako `bindProp` = `value` ciąg znaków w wyrażeniu, ale zależy od rodzaju wartość przekazywana. Jeśli przekazywanie typu odwołania wymaga odwołania do obiektu takich jak zagnieżdżoną [staticresource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
-   <xref:System.Windows.Data.Binding.IsAsync%2A>: Wartość logiczna, może być `true` lub `false`. Wartość domyślna to `false`.  
  
-   <xref:System.Windows.Data.Binding.Mode%2A>: *wartość* jest stałe nazwą z <xref:System.Windows.Data.BindingMode> wyliczenia. Na przykład `{Binding Mode=OneWay}`.  
  
-   <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: Wartość logiczna, może być `true` lub `false`. Wartość domyślna to `false`.  
  
-   <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: Wartość logiczna, może być `true` lub `false`. Wartość domyślna to `false`.  
  
-   <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: Wartość logiczna, może być `true` lub `false`. Wartość domyślna to `false`.  
  
-   <xref:System.Windows.Data.Binding.Path%2A>: ciąg opisujący ścieżkę do obiektu danych lub modelu obiektu ogólne. Format oferuje kilka różnych konwencji przechodzenie przez model obiektowy, który nie może być odpowiednio opisane w tym temacie. Zobacz [składnia elementu PropertyPath XAML](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).  
  
-   <xref:System.Windows.Data.Binding.RelativeSource%2A>: wzajemnie się wykluczają w porównaniu z <xref:System.Windows.Data.Binding.ElementName%2A> i <xref:System.Windows.Data.Binding.Source%2A>; każdy z tych właściwości powiązań reprezentuje metodologii określonego powiązania. Zobacz [Przegląd wiązanie danych](../../../../docs/framework/wpf/data/data-binding-overview.md). Wymaga zagnieżdżoną [RelativeSource, rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md) użycia, aby określić wartość.  
  
-   <xref:System.Windows.Data.Binding.Source%2A>: wzajemnie się wykluczają i <xref:System.Windows.Data.Binding.RelativeSource%2A> i <xref:System.Windows.Data.Binding.ElementName%2A>; każdy z tych właściwości powiązań reprezentuje metodologii określonego powiązania. Zobacz [Przegląd wiązanie danych](../../../../docs/framework/wpf/data/data-binding-overview.md). Zwykle wymaga użycia rozszerzenia zagnieżdżonego [staticresource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) odwołujący się do źródła danych obiektu ze słownika zasobów kluczem.  
  
-   <xref:System.Windows.Data.BindingBase.StringFormat%2A>: ciąg, który opisuje ciąg formatu Konwencję dotyczącą powiązane dane. Jest to pojęcie stosunkowo zaawansowane powiązanie; zobacz stronę odniesienia dla <xref:System.Windows.Data.BindingBase.StringFormat%2A>.  
  
-   <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: można ustawić jako `bindProp` = `value` ciąg znaków w wyrażeniu, ale jest zależna od typu parametru przekazywana. Jeśli przekazywanie typu odwołania dla wartości, wymaga odwołania do obiektu takich jak zagnieżdżoną [staticresource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>: *wartość* jest stałe nazwą z <xref:System.Windows.Data.UpdateSourceTrigger> wyliczenia. Na przykład `{Binding UpdateSourceTrigger=LostFocus}`. Określonych kontrolek potencjalnie mieć różne domyślne wartości dla tej właściwości powiązania. Zobacz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: Wartość logiczna, może być `true` lub `false`. Wartość domyślna to `false`. Zobacz uwagi.  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: Wartość logiczna, może być `true` lub `false`. Wartość domyślna to `false`. Zobacz uwagi.  
  
-   <xref:System.Windows.Data.Binding.XPath%2A>: ciąg opisujący ścieżkę do XMLDOM źródła danych XML. Zobacz [Powiąż z danymi XML przy użyciu XMLDataProvider i zapytań XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Poniżej przedstawiono właściwości <xref:System.Windows.Data.Binding> , nie można ustawić za pomocą `Binding` — rozszerzenie znaczników /`{Binding}` forma wyrażenia.  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: Ta właściwość oczekuje odwołania do wykonania wywołania zwrotnego. Składnia XAML nie może odwoływać się do wywołania zwrotne/metod innych niż procedury obsługi zdarzeń.  
  
-   <xref:System.Windows.Data.Binding.ValidationRules%2A>: właściwość przyjmuje ogólnego zbiór <xref:System.Windows.Controls.ValidationRule> obiektów. Może to być wyrażone jako prvek Vlastnosti w <xref:System.Windows.Data.Binding> obiekt elementu, ale nie ma żadnych łatwości technika podczas analizowania atrybutu do użycia w `Binding` wyrażenia. Zobacz temat referencyjny dotyczący <xref:System.Windows.Data.Binding.ValidationRules%2A>.  
  
-   <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
>  Pod względem następstwo właściwości `Binding` wyrażenie jest odpowiednikiem lokalnie ustawiony wartość. Jeśli ustawisz wartości lokalnej dla właściwości, która miała wcześniej `Binding` wyrażenie `Binding` zostało całkowicie usunięte. Aby uzyskać więcej informacji, zobacz [następstwo wartości właściwości](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).  
  
 W tym temacie nie obejmuje opisujący wiązanie danych na poziomie podstawowym. Zobacz [Przegląd wiązanie danych](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Data.MultiBinding> i <xref:System.Windows.Data.PriorityBinding> nie obsługują [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] składni rozszerzenia. Zamiast tego należy użyć właściwości elementów. Zobacz Tematy referencyjne dotyczące <xref:System.Windows.Data.MultiBinding> i <xref:System.Windows.Data.PriorityBinding>.  
  
 Wartości logiczne dla XAML są bez uwzględniania wielkości liter. Na przykład można określić albo `{Binding NotifyOnValidationError=true}` lub `{Binding NotifyOnValidationError=True}`.  
  
 Powiązania, które obejmują sprawdzanie poprawności danych zazwyczaj są określane przez jawną `Binding` elementu, a nie jako `{Binding ...}` wyrażenie i ustawienie <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> lub <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> w wyrażeniu jest mało prawdopodobna. Jest to spowodowane właściwości <xref:System.Windows.Data.Binding.ValidationRules%2A> nie łatwo można ustawić w postaci wyrażenia. Aby uzyskać więcej informacji, zobacz [Walidacja powiązania Implementowanie](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md).  
  
 `Binding` jest rozszerzeniem znacznika. Rozszerzenia znaczników są zazwyczaj implementowane, gdy istnieje wymóg, aby wprowadzić wartości atrybutów były inne niż wartości literałów lub obsługi nazw, a wymóg ma charakter bardziej globalny niż konwertery typu opartego na atrybutach na niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w XAML użyj `{` i `}` znaków w składni swoich atrybutów, które jest do Konwencja, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znacznika musi przetworzyć zawartości ciągu. Aby uzyskać więcej informacji, zobacz [rozszerzenia znacznikowania i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 `Binding` to rozszerzenie znaczników nietypowe, w tym <xref:System.Windows.Data.Binding> klasę, która implementuje funkcje rozszerzenia dla implementacji XAML w WPF implementuje również kilka innych metod i właściwości, które nie są związane z XAML. Inni członkowie mają na celu wprowadzić <xref:System.Windows.Data.Binding> bardziej wszechstronna, niezależna klasę, która może rozwiązać wiele scenariusze powiązania danych oprócz działa jako rozszerzenie znaczników XAML.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Data.Binding>
- [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [Rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
