---
title: Rozszerzenie znaczników powiązania
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: d0a437e756da16db978d8074c4355fd83d211b67
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453616"
---
# <a name="binding-markup-extension"></a>Rozszerzenie znaczników powiązania
Wprowadza wartość właściwości jako wartość powiązaną z danymi, tworząc obiekt wyrażenia pośredniego i interpretuje kontekst danych, który ma zastosowanie do elementu i jego powiązania w czasie wykonywania.  
  
## <a name="binding-expression-usage"></a>Użycie wyrażenia powiązania  
  
```xaml  
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
 W tych składni `[]` i `*` nie są literałami. Są one częścią notacji, aby wskazać, że można używać`=`*bindProp* par *wartości* zero lub więcej, z separatorem `,` między nimi i poprzednimi *bindProp*`=`*wartości* .  
  
 Zamiast tego można ustawić dowolne właściwości wymienione w sekcji "Właściwości powiązania, które można ustawić za pomocą rozszerzenia powiązania" przy użyciu atrybutów elementu <xref:System.Windows.Data.Binding> obiektu. Jednak nie jest to naprawdę użycie rozszerzenia znacznika <xref:System.Windows.Data.Binding>, to tylko ogólne przetwarzanie kodu XAML atrybutów, które ustawiają właściwości klasy CLR <xref:System.Windows.Data.Binding>. Innymi słowy `<Binding` *bindProp1*`="`*wartość1*`"[` *bindPropN*`="`*valueN*`"]*/>` jest równoważną składnią dla atrybutów użycia elementu obiektu <xref:System.Windows.Data.Binding> zamiast wyrażenia `Binding` użycie. Aby dowiedzieć się więcej o użyciu atrybutów XAML dla określonych właściwości <xref:System.Windows.Data.Binding>, zobacz sekcję "użycie atrybutu języka XAML" odpowiedniej właściwości <xref:System.Windows.Data.Binding> w bibliotece klas .NET Framework.  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|Nazwa właściwości <xref:System.Windows.Data.Binding> lub <xref:System.Windows.Data.BindingBase> do ustawienia. Nie wszystkie <xref:System.Windows.Data.Binding> właściwości można ustawić za pomocą rozszerzenia `Binding`, a niektóre właściwości są ustawiane w ramach wyrażenia `Binding` tylko przy użyciu dalszych zagnieżdżonych rozszerzeń znaczników. Zobacz sekcję "Właściwości powiązania, które można ustawić za pomocą rozszerzenia powiązania".|  
|`value1, valueN`|Wartość, dla której ma zostać ustawiona właściwość. Obsługa wartości atrybutu jest ostatecznie specyficzna dla typu i logiki ustawionej właściwości <xref:System.Windows.Data.Binding>.|  
|`path`|Ciąg ścieżki, który ustawia właściwość niejawną <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>. Zobacz również [PropertyPath SKŁADNI XAML](propertypath-xaml-syntax.md).|  
  
## <a name="unqualified-binding"></a>Niekwalifikowane {Binding}  
 Użycie `{Binding}` pokazane w "użycie wyrażenia powiązania" tworzy obiekt <xref:System.Windows.Data.Binding> z wartościami domyślnymi, które zawierają początkowy <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> `null`. Jest to nadal przydatne w wielu scenariuszach, ponieważ utworzone <xref:System.Windows.Data.Binding> mogą polegać na właściwościach powiązań danych kluczowych, takich jak <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> i <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> ustawionych w kontekście danych czasu wykonywania. Aby uzyskać więcej informacji na temat koncepcji kontekstu danych, zobacz [powiązanie danych](../data/data-binding-wpf.md).  
  
## <a name="implicit-path"></a>Ścieżka niejawna  
 Rozszerzenie `Binding` Markup używa <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> jako koncepcyjnej właściwości "default", gdzie `Path=` nie musi występować w wyrażeniu. Jeśli określisz wyrażenie `Binding` z niejawną ścieżką, niejawna ścieżka musi występować najpierw w wyrażeniu, przed innymi `bindProp`=`value` par, gdzie Właściwość <xref:System.Windows.Data.Binding> jest określona przez nazwę. Na przykład: `{Binding PathString}`, gdzie `PathString` jest ciągiem, który jest analizowany jako wartość <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> w <xref:System.Windows.Data.Binding> utworzonym przez użycie rozszerzenia znacznika. Można dołączyć niejawną ścieżkę z innymi nazwanymi właściwościami po separatorze przecinka, na przykład `{Binding LastName, Mode=TwoWay}`.  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>Właściwości powiązania, które można ustawić za pomocą rozszerzenia powiązania  
 Składnia pokazana w tym temacie używa ogólnych `bindProp`=`value` przybliżeniu, ponieważ istnieje wiele właściwości do odczytu/zapisu dla <xref:System.Windows.Data.BindingBase> lub <xref:System.Windows.Data.Binding>, które można ustawić za pomocą `Binding` składni rozszerzenia/wyrażenia znacznika. Można je ustawić w dowolnej kolejności, z wyjątkiem niejawnego <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>. (Można jawnie określić `Path=`, w którym to przypadku można ustawić w dowolnej kolejności). W zasadzie można ustawić zero lub więcej właściwości na poniższej liście przy użyciu `bindProp`=`value` par oddzielonych przecinkami.  
  
 Niektóre z tych wartości właściwości wymagają typów obiektów, które nie obsługują konwersji typu natywnego z składni tekstu w języku XAML i w ten sposób wymagają rozszerzeń znaczników, aby można je było ustawić jako wartość atrybutu. Sprawdź sekcję użycie atrybutu XAML w bibliotece klas .NET Framework dla każdej właściwości, aby uzyskać więcej informacji. ciąg używany na potrzeby składni atrybutów XAML z lub bez dalszych użycia rozszerzenia znaczników jest zasadniczo taki sam jak wartość określona w wyrażeniu `Binding`, z wyjątkiem tego, że znaki cudzysłowu wokół poszczególnych `bindProp`=`value` w wyrażenie `Binding`.  
  
- <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: ciąg, który identyfikuje możliwą grupę powiązań. Jest to stosunkowo zaawansowane koncepcje powiązań. Aby uzyskać <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>, zobacz stronę referencyjną.  
  
- <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: wartość logiczna może być albo `true` lub `false`. Wartość domyślna to `false`.  
  
- <xref:System.Windows.Data.Binding.Converter%2A>: można ustawić jako ciąg `bindProp`=`value` w wyrażeniu, ale w tym celu wymaga odwołania do obiektu dla wartości, takiej jak [StaticResource znacznika](staticresource-markup-extension.md). Wartość w tym przypadku jest wystąpieniem klasy niestandardowego konwertera.  
  
- <xref:System.Windows.Data.Binding.ConverterCulture%2A>: settable w wyrażeniu jako identyfikator oparty na standardach; Zapoznaj się z tematem referencyjnym <xref:System.Windows.Data.Binding.ConverterCulture%2A>.  
  
- <xref:System.Windows.Data.Binding.ConverterParameter%2A>: można ustawić jako ciąg `bindProp`=`value` w wyrażeniu, ale jest to zależne od typu przesyłanego parametru. W przypadku przekazywania typu odwołania dla wartości to użycie wymaga odwołania do obiektu, takiego jak zagnieżdżone [rozszerzenie znacznika StaticResource](staticresource-markup-extension.md).  
  
- <xref:System.Windows.Data.Binding.ElementName%2A>: wzajemnie wykluczające się w zależności od <xref:System.Windows.Data.Binding.RelativeSource%2A> i <xref:System.Windows.Data.Binding.Source%2A>; Każda z tych właściwości powiązań reprezentuje konkretną metodologię powiązania. Zobacz temat [powiązanie danych — omówienie](../data/data-binding-overview.md).  
  
- <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: można ustawić jako ciąg `bindProp`=`value` w wyrażeniu, ale jest to zależne od typu przenoszonej wartości. W przypadku przekazywania typu referencyjnego wymagane jest odwołanie do obiektu, takie jak zagnieżdżone [rozszerzenie znacznika StaticResource](staticresource-markup-extension.md).  
  
- <xref:System.Windows.Data.Binding.IsAsync%2A>: wartość logiczna może być albo `true` lub `false`. Wartość domyślna to `false`.  
  
- <xref:System.Windows.Data.Binding.Mode%2A>: *wartość* jest stałą nazwą z wyliczenia <xref:System.Windows.Data.BindingMode>. Na przykład `{Binding Mode=OneWay}`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: wartość logiczna może być albo `true` lub `false`. Wartość domyślna to `false`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: wartość logiczna może być albo `true` lub `false`. Wartość domyślna to `false`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: wartość logiczna może być albo `true` lub `false`. Wartość domyślna to `false`.  
  
- <xref:System.Windows.Data.Binding.Path%2A>: ciąg opisujący ścieżkę do obiektu danych lub ogólnego modelu obiektów. Format zawiera kilka różnych konwencji do przechodzenia przez model obiektów, który nie może być odpowiednio opisany w tym temacie. Zobacz [składnię XAML PropertyPath](propertypath-xaml-syntax.md).  
  
- <xref:System.Windows.Data.Binding.RelativeSource%2A>: wzajemnie wykluczające się w przeciwieństwie do <xref:System.Windows.Data.Binding.ElementName%2A> i <xref:System.Windows.Data.Binding.Source%2A>; Każda z tych właściwości powiązań reprezentuje konkretną metodologię powiązania. Zobacz temat [powiązanie danych — omówienie](../data/data-binding-overview.md). Wymaga zagnieżdżonego użycia [wyrażenia MarkupExtension RelativeSource](relativesource-markupextension.md) do określenia wartości.  
  
- <xref:System.Windows.Data.Binding.Source%2A>: wzajemnie wykluczające się w zależności od <xref:System.Windows.Data.Binding.RelativeSource%2A> i <xref:System.Windows.Data.Binding.ElementName%2A>; Każda z tych właściwości powiązań reprezentuje konkretną metodologię powiązania. Zobacz temat [powiązanie danych — omówienie](../data/data-binding-overview.md). Wymaga użycia rozszerzenia zagnieżdżonego, zazwyczaj [rozszerzenie znacznika StaticResource](staticresource-markup-extension.md) , które odwołuje się do źródła danych obiektu z poziomu utworzonego w słowniku zasobów.  
  
- <xref:System.Windows.Data.BindingBase.StringFormat%2A>: ciąg opisujący Konwencję formatu ciągu dla powiązanych danych. Jest to stosunkowo zaawansowane koncepcje powiązań. Aby uzyskać <xref:System.Windows.Data.BindingBase.StringFormat%2A>, zobacz stronę referencyjną.  
  
- <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: można ustawić jako ciąg `bindProp`=`value` w wyrażeniu, ale jest to zależne od typu przesyłanego parametru. W przypadku przekazywania typu odwołania dla wartości, wymagane jest odwołanie do obiektu, takie jak zagnieżdżone [rozszerzenie znacznika StaticResource](staticresource-markup-extension.md).  
  
- <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>: *wartość* jest stałą nazwą z wyliczenia <xref:System.Windows.Data.UpdateSourceTrigger>. Na przykład `{Binding UpdateSourceTrigger=LostFocus}`. Określone kontrolki mogą mieć różne wartości domyślne dla tej właściwości powiązania. Zobacz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: wartość logiczna może być albo `true` lub `false`. Wartość domyślna to `false`. Zobacz uwagi.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: wartość logiczna może być albo `true` lub `false`. Wartość domyślna to `false`. Zobacz uwagi.  
  
- <xref:System.Windows.Data.Binding.XPath%2A>: ciąg opisujący ścieżkę do XMLDOM źródła danych XML. Zobacz [powiąż z danymi XML przy użyciu XmlDataProvider i zapytań XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Poniżej znajdują się właściwości <xref:System.Windows.Data.Binding>, których nie można ustawić przy użyciu formularza wyrażenia `Binding` lub rozszerzenia znacznika`{Binding}`.  
  
- <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: Ta właściwość oczekuje odwołania do implementacji wywołania zwrotnego. W składni XAML nie można odwoływać się do wywołań zwrotnych/metod innych niż procedury obsługi zdarzeń.  
  
- <xref:System.Windows.Data.Binding.ValidationRules%2A>: Właściwość przyjmuje ogólną kolekcję obiektów <xref:System.Windows.Controls.ValidationRule>. Może to być wyrażone jako element właściwości w <xref:System.Windows.Data.Binding> elementu obiektu, ale nie ma łatwo dostępnej techniki analizy atrybutu do użycia w wyrażeniu `Binding`. Zapoznaj się z tematem referencyjnym <xref:System.Windows.Data.Binding.ValidationRules%2A>.  
  
- <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
> W zasadach pierwszeństwa właściwości zależności wyrażenie `Binding` jest równoważne wartości ustawionej lokalnie. Jeśli ustawisz wartość lokalną dla właściwości, która wcześniej zawierała wyrażenie `Binding`, `Binding` zostanie całkowicie usunięta. Aby uzyskać szczegółowe informacje, zobacz [pierwszeństwo wartości właściwości zależności](dependency-property-value-precedence.md).  
  
 W tym temacie nie opisano opisu powiązania danych na poziomie podstawowym. Zobacz temat [powiązanie danych — omówienie](../data/data-binding-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Data.MultiBinding> i <xref:System.Windows.Data.PriorityBinding> nie obsługują składni rozszerzenia [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Zamiast tego należy użyć elementów właściwości. Zobacz tematy referencyjne dla <xref:System.Windows.Data.MultiBinding> i <xref:System.Windows.Data.PriorityBinding>.  
  
 W wartościach logicznych dla języka XAML jest rozróżniana wielkość liter. Można na przykład określić wartość `{Binding NotifyOnValidationError=true}` lub `{Binding NotifyOnValidationError=True}`.  
  
 Powiązania, które obejmują sprawdzanie poprawności danych, są zwykle określane przez jawny element `Binding`, a nie jako wyrażenie `{Binding ...}` i ustawienie <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> lub <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> w wyrażeniu jest nietypowe. Wynika to z faktu, że właściwość pomocnika <xref:System.Windows.Data.Binding.ValidationRules%2A> nie może być łatwo ustawiona w formularzu wyrażenia. Aby uzyskać więcej informacji, zobacz [implementowanie walidacji powiązania](../data/how-to-implement-binding-validation.md).  
  
 `Binding` to rozszerzenie znaczników. Rozszerzenia znaczników są zwykle implementowane, gdy istnieje wymóg, aby wartości atrybutów ucieczki były inne niż wartości literałów lub nazwy programów obsługi, a wymagania są bardziej globalne niż konwertery typów przypisane do określonych typów lub właściwości. Wszystkie rozszerzenia znaczników w języku XAML używają znaków `{` i `}` w ich składni atrybutów, która jest konwencją, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znacznika musi przetwarzać zawartość ciągu. Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
 `Binding` jest nietypowym rozszerzeniem znaczników w tym, że Klasa <xref:System.Windows.Data.Binding> implementująca funkcje rozszerzenia dla implementacji XAML języka WPF również implementuje kilka innych metod i właściwości, które nie są powiązane z XAML. Inne składowe mają na celu <xref:System.Windows.Data.Binding> bardziej uniwersalną i samodzielną klasę, która może zawierać wiele scenariuszy powiązań danych, a także działa jako rozszerzenie znaczników XAML.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Data.Binding>
- [Powiązanie danych — omówienie](../data/data-binding-overview.md)
- [Przegląd XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md)
