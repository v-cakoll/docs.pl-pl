---
title: "Rozszerzenie znaczników powiązania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cc6a0616c6b462ffe6aca0a9adf27ac2ac7b7828
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="binding-markup-extension"></a>Rozszerzenie znaczników powiązania
Różni się wartość właściwości wartość powiązane z danymi, tworzenie obiektu będącego wyrażeniem pośrednie i interpretowanie kontekstu danych, która ma zastosowanie do elementu i jego powiązanie w czasie wykonywania.  
  
## <a name="binding-expression-usage"></a>Użycie wyrażenia powiązania  
  
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
  
## <a name="syntax-notes"></a>Uwagi dotyczące składni  
 W tych składni `[]` i `*` nie są literały. Są one częścią notacji, aby wskazać, że zero lub więcej *bindProp*`=`*wartość* pary mogą być używane, z `,` separatora między nimi i poprzedniego *bindProp*  `=` *wartość* pary.  
  
 Właściwości opisane w sekcji "Powiązanie właściwości czy można można ustawić z powiązania rozszerzenia" można zamiast tego można ustawić za pomocą atrybutów <xref:System.Windows.Data.Binding> object element. Jednak, który nie jest naprawdę użycie rozszerzenia znaczników <xref:System.Windows.Data.Binding>, jest tylko ogólne XAML przetwarzania atrybutów, które właściwości CLR <xref:System.Windows.Data.Binding> klasy. Innymi słowy `<Binding` *bindProp1*`="`*wartość1* `"[` *bindPropN*`="`*wartośćN* `"]*/>` jest równoważne składni dla atrybutów <xref:System.Windows.Data.Binding> obiekt użycie elementu zamiast `Binding` użycie wyrażenia. Aby dowiedzieć się więcej o użycie atrybutu XAML określonych właściwości <xref:System.Windows.Data.Binding>, zobacz sekcję "Użycia atrybutu XAML" odpowiednie właściwości <xref:System.Windows.Data.Binding> w bibliotece klas programu .NET Framework.  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|Nazwa <xref:System.Windows.Data.Binding> lub <xref:System.Windows.Data.BindingBase> właściwości do ustawienia. Nie wszystkie <xref:System.Windows.Data.Binding> właściwości można ustawić za pomocą `Binding` rozszerzenia, a niektóre właściwości są można ustawić w `Binding` wyrażenia tylko przy użyciu dalsze zagnieżdżone rozszerzenia znaczników. Zobacz sekcję "Powiązanie czy może być ustawić z powiązania rozszerzenie właściwości".|  
|`value1, valueN`|Wartość do ustawienia właściwości. Obsługa wartości atrybutu jest ostatecznie określonego typu i logiki konkretnym <xref:System.Windows.Data.Binding> ustawienia właściwości.|  
|`path`|Ciąg ścieżki, która ustawia niejawne <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> właściwości. Zobacz też [składnia PropertyPath XAML](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).|  
  
## <a name="unqualified-binding"></a>Niekwalifikowane {powiązanie}  
 `{Binding}` Tworzy użycia pokazano "Powiązanie użycie wyrażenia" <xref:System.Windows.Data.Binding> obiekt z wartościami domyślnymi, która obejmuje początkowy <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> z `null`. To nadal jest użyteczne w wielu scenariuszach, ponieważ utworzony <xref:System.Windows.Data.Binding> może polegania na właściwości powiązania danych klucza takich jak <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> i <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> ustawiany w kontekście danych w czasie wykonywania. Aby uzyskać więcej informacji na koncepcji kontekstu danych, zobacz [powiązania danych](../../../../docs/framework/wpf/data/data-binding-wpf.md).  
  
## <a name="implicit-path"></a>Niejawne ścieżki  
 `Binding` Używa rozszerzenia znaczników <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> jako koncepcyjnej "Właściwość domyślna", gdzie `Path=` nie musi występować w wyrażeniu. Jeśli określisz `Binding` wyrażenia ze ścieżką niejawne niejawne ścieżki muszą występować pierwsze w wyrażeniu, przed wszystkimi innymi `bindProp` = `value` pary where <xref:System.Windows.Data.Binding> określono właściwości według nazwy. Na przykład: `{Binding PathString}`, gdzie `PathString` jest ciągiem, który zostanie zidentyfikowane jako wartość <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> w <xref:System.Windows.Data.Binding> utworzone przez użycie rozszerzenia znaczników. Można je dołączyć niejawne ścieżki z innych właściwości o nazwie po przecinka jako separatora, na przykład `{Binding LastName, Mode=TwoWay}`.  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>Właściwości powiązania, które można ustawić za pomocą rozszerzenia powiązania  
 Składnia wyświetlane w tym temacie korzysta z ogólnego `bindProp` = `value` zbliżenia, ponieważ istnieje wiele właściwości odczytu/zapisu <xref:System.Windows.Data.BindingBase> lub <xref:System.Windows.Data.Binding> które można ustawić za pomocą `Binding` — rozszerzenie znaczników / Składnia wyrażeń. Może być ustawiona w dowolnej kolejności, z wyjątkiem niejawnej <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>. (Trzeba jawnie określić `Path=`, w którym to przypadku można ją ustawić w dowolnej kolejności). Zasadniczo, można ustawić zero lub więcej właściwości na liście poniżej, używając `bindProp` = `value` par oddzielonych przecinkami.  
  
 Niektóre z tych wartości właściwości wymagają typów obiektów, które nie obsługuje konwersji typu macierzystego składni tekstu w języku XAML i dlatego wymaga rozszerzenia znaczników można ustawić jako wartość atrybutu. Sprawdź sekcję użycie atrybutu XAML w bibliotece klas programu .NET Framework dla każdej właściwości, aby uzyskać więcej informacji; Ciąg używany do składnia atrybutu XAML z lub bez dalszego rozszerzenia znaczników użycia jest zasadniczo taki sam jak wartość określoną w `Binding` wyrażenia z powodu wyjątku nie umieszczaj znaki cudzysłowu wokół każdego `bindProp` = `value` w `Binding` wyrażenia.  
  
-   <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: ciąg, który identyfikuje grupę możliwe powiązanie. Jest to pojęcie stosunkowo zaawansowane powiązanie; zobacz stronę odwołania <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>.  
  
-   <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: Wartość logiczna, mogą być `true` lub `false`. Wartość domyślna to `false`.  
  
-   <xref:System.Windows.Data.Binding.Converter%2A>: można ustawić jako `bindProp` = `value` ciąg w wyrażeniu, ale w tym celu wymaga odwołania do obiektu dla wartości, takich jak [StaticResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md). Wartość w tym przypadku jest wystąpienie klasy niestandardowej konwertera.  
  
-   <xref:System.Windows.Data.Binding.ConverterCulture%2A>: można ustawić w wyrażeniu jako identyfikatora opartych na standardach. zobacz temat informacje dla <xref:System.Windows.Data.Binding.ConverterCulture%2A>.  
  
-   <xref:System.Windows.Data.Binding.ConverterParameter%2A>: można ustawić jako `bindProp` = `value` ciąg w wyrażeniu, ale jest zależny od typu parametru przekazywana. Jeśli przekazywanie typu odwołania dla wartości, to użycie wymaga odwołania do obiektu, takie jak zagnieżdżoną [StaticResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
-   <xref:System.Windows.Data.Binding.ElementName%2A>: wykluczają się wzajemnie, a <xref:System.Windows.Data.Binding.RelativeSource%2A> i <xref:System.Windows.Data.Binding.Source%2A>; każdego z tych właściwości powiązań reprezentuje metodologii określonego powiązania. Zobacz [powiązanie przegląd danych](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
-   <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: można ustawić jako `bindProp` = `value` ciąg w wyrażeniu, ale zależy od rodzaju wartości były przekazywane. Jeśli przekazywanie typu odwołania wymaga odwołania do obiektu, takie jak zagnieżdżoną [StaticResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
-   <xref:System.Windows.Data.Binding.IsAsync%2A>: Wartość logiczna, mogą być `true` lub `false`. Wartość domyślna to `false`.  
  
-   <xref:System.Windows.Data.Binding.Mode%2A>: *wartość* jest nazwą stałej z <xref:System.Windows.Data.BindingMode> wyliczenia. Na przykład `{Binding Mode=OneWay}`.  
  
-   <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: Wartość logiczna, mogą być `true` lub `false`. Wartość domyślna to `false`.  
  
-   <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: Wartość logiczna, mogą być `true` lub `false`. Wartość domyślna to `false`.  
  
-   <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: Wartość logiczna, mogą być `true` lub `false`. Wartość domyślna to `false`.  
  
-   <xref:System.Windows.Data.Binding.Path%2A>: ciąg opisujący ścieżkę do obiektu danych lub modelu obiektu ogólne. Format zapewnia kilka różnych konwencji przechodzących przez model obiektów, które nie mogą być odpowiednio opisane w tym temacie. Zobacz [składnia PropertyPath XAML](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).  
  
-   <xref:System.Windows.Data.Binding.RelativeSource%2A>: wykluczają się wzajemnie w porównaniu z <xref:System.Windows.Data.Binding.ElementName%2A> i <xref:System.Windows.Data.Binding.Source%2A>; każdego z tych właściwości powiązań reprezentuje metodologii określonego powiązania. Zobacz [powiązanie przegląd danych](../../../../docs/framework/wpf/data/data-binding-overview.md). Wymaga zagnieżdżoną [RelativeSource MarkupExtension](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md) użycia w celu określenia wartości.  
  
-   <xref:System.Windows.Data.Binding.Source%2A>: wykluczają się wzajemnie, a <xref:System.Windows.Data.Binding.RelativeSource%2A> i <xref:System.Windows.Data.Binding.ElementName%2A>; każdego z tych właściwości powiązań reprezentuje metodologii określonego powiązania. Zobacz [powiązanie przegląd danych](../../../../docs/framework/wpf/data/data-binding-overview.md). Zwykle wymaga użycia zagnieżdżonego rozszerzenia, [StaticResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) odwołujący się do źródła danych obiektu ze słownika zasobów kluczem.  
  
-   <xref:System.Windows.Data.BindingBase.StringFormat%2A>: ciąg opisujący Konwencja formatu ciągu powiązania danych. Jest to pojęcie stosunkowo zaawansowane powiązanie; zobacz stronę odwołania <xref:System.Windows.Data.BindingBase.StringFormat%2A>.  
  
-   <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: można ustawić jako `bindProp` = `value` ciąg w wyrażeniu, ale jest zależny od typu parametru przekazywana. Jeśli przekazywanie typu odwołania dla wartości, wymaga odwołania do obiektu, takie jak zagnieżdżoną [StaticResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>: *wartość* jest nazwą stałej z <xref:System.Windows.Data.UpdateSourceTrigger> wyliczenia. Na przykład `{Binding UpdateSourceTrigger=LostFocus}`. Formanty określonej mogących mieć różne domyślne wartości dla tej właściwości powiązania. Zobacz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: Wartość logiczna, mogą być `true` lub `false`. Wartość domyślna to `false`. Zobacz uwagi.  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: Wartość logiczna, mogą być `true` lub `false`. Wartość domyślna to `false`. Zobacz uwagi.  
  
-   <xref:System.Windows.Data.Binding.XPath%2A>: ciąg opisujący ścieżkę do XMLDOM źródła danych XML. Zobacz [powiązania danych XML przy użyciu XMLDataProvider i kwerendy XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Poniżej przedstawiono właściwości <xref:System.Windows.Data.Binding> którego nie można ustawić za pomocą `Binding` — rozszerzenie znaczników /`{Binding}` wyrażenie w postaci.  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: Ta właściwość oczekuje odwołania do wykonania wywołania zwrotnego. Składnia języka XAML nie może odwoływać się do wywołania zwrotne/metod innych niż procedury obsługi zdarzeń.  
  
-   <xref:System.Windows.Data.Binding.ValidationRules%2A>: właściwość ma rodzajowy Kolekcja <xref:System.Windows.Controls.ValidationRule> obiektów. Może to być wyrażone jako elementu właściwości w <xref:System.Windows.Data.Binding> obiekt elementu, ale ma nie łatwo dostępne technika podczas analizowania atrybutu użycie `Binding` wyrażenia. Zobacz temat referencyjny dla <xref:System.Windows.Data.Binding.ValidationRules%2A>.  
  
-   <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
>  Pod względem pierwszeństwo właściwości zależności `Binding` wyrażenie jest odpowiednikiem lokalnie ustawione wartości. Jeśli ustawisz wartości lokalnej dla właściwości, która wcześniej była `Binding` wyrażenie `Binding` zostanie całkowicie usunięta. Aby uzyskać więcej informacji, zobacz [pierwszeństwo wartość właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).  
  
 W tym temacie nie opisano opisujący wiązanie danych na poziomie podstawowym. Zobacz [powiązanie przegląd danych](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Data.MultiBinding>i <xref:System.Windows.Data.PriorityBinding> nie obsługują [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] składni rozszerzenia. Zamiast tego użyj właściwości elementów. Zobacz tematy dokumentacji dla <xref:System.Windows.Data.MultiBinding> i <xref:System.Windows.Data.PriorityBinding>.  
  
 Wartości logiczna dla XAML są bez uwzględniania wielkości liter. Na przykład można określić albo `{Binding NotifyOnValidationError=true}` lub `{Binding NotifyOnValidationError=True}`.  
  
 Powiązania obejmujących sprawdzanie poprawności danych zazwyczaj są określane przez jawne `Binding` elementu, a nie jako `{Binding ...}` wyrażenie i ustawienie <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> lub <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> w wyrażeniu jest rzadko. Jest to spowodowane właściwości <xref:System.Windows.Data.Binding.ValidationRules%2A> nie można łatwo ustawić w postaci wyrażenia. Aby uzyskać więcej informacji, zobacz [weryfikacji powiązanie wdrożenie](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md).  
  
 `Binding`to rozszerzenie znacznika. Rozszerzenia znaczników zwykle są implementowane, gdy jest wymagany, aby wprowadzić wartości atrybutów, aby być inna niż wartości literału lub obsługi nazwy i wymagane jest bardziej globalnego niż konwertery typu na niektórych typów lub właściwości. Wszystkie rozszerzenia znaczników w XAML, użyj `{` i `}` znaków w ich składni atrybutu Konwencji, za pomocą którego procesora XAML rozpoznaje, że rozszerzenie znacznika musi przetworzyć zawartości ciągu. Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 `Binding`to rozszerzenie znacznika nietypowe w tym <xref:System.Windows.Data.Binding> klasy, która implementuje funkcje rozszerzenia dla implementacji XAML w WPF implementuje również kilka innych metod i właściwości, które nie są związane z XAML. O innych elementach członkowskich mają na celu upewnij <xref:System.Windows.Data.Binding> bardziej elastyczne i autonomiczną klasę, która może rozwiązać wiele scenariusze wiązania danych oprócz działa jako rozszerzenie znaczników w XAML.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Data.Binding>  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
