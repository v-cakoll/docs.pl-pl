---
title: Rozszerzenie znaczników powiązania
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: 616e405e191cb264a002e903bed60cf04559a675
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964900"
---
# <a name="binding-markup-extension"></a>Rozszerzenie znaczników powiązania
Wprowadza wartość właściwości jako wartość powiązaną z danymi, tworząc obiekt wyrażenia pośredniego i interpretuje kontekst danych, który ma zastosowanie do elementu i jego powiązania w czasie wykonywania.  
  
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
 W tych składniach `[]` i `*` nie są literałami. Są one częścią notacji, aby wskazać, że `,` można użyć zero lub więcej par*wartości* *bindProp*`=`, z separatorem między nimi i poprzednimi parami*wartości* *bindProp*`=`.  
  
 Zamiast tego można ustawić wszystkie właściwości wymienione w sekcji "Właściwości powiązania, które można ustawić za pomocą rozszerzenia powiązania" przy użyciu atrybutów <xref:System.Windows.Data.Binding> elementu obiektu. Jednak to nie jest naprawdę użycie <xref:System.Windows.Data.Binding>rozszerzenia znacznika, jest tylko ogólnym przetwarzaniem kodu XAML atrybutów, które ustawiają właściwości klasy CLR. <xref:System.Windows.Data.Binding> Innymi słowy `<Binding` , *bindProp1*`="`*wartość1* <xref:System.Windows.Data.Binding> bindPropN valueN jest równoważną składnią dla atrybutów użycia elementu obiektu`"]*/>` `="``"[` zamiast użycia wyrażenia `Binding` . Aby dowiedzieć się więcej o używaniu atrybutów XAML dla <xref:System.Windows.Data.Binding>określonych właściwości, zobacz sekcję "użycie atrybutu języka XAML" odpowiedniej <xref:System.Windows.Data.Binding> właściwości w bibliotece klas .NET Framework.  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|Nazwa <xref:System.Windows.Data.Binding> właściwości lub <xref:System.Windows.Data.BindingBase> do ustawienia. Nie wszystkie <xref:System.Windows.Data.Binding> właściwości można ustawić `Binding` przy użyciu rozszerzenia, a niektóre właściwości `Binding` są ustawiane tylko w obrębie wyrażenia przy użyciu dalszych zagnieżdżonych rozszerzeń znaczników. Zobacz sekcję "Właściwości powiązania, które można ustawić za pomocą rozszerzenia powiązania".|  
|`value1, valueN`|Wartość, dla której ma zostać ustawiona właściwość. Obsługa wartości atrybutu jest ostatecznie specyficzna dla typu i logiki ustawionej określonej <xref:System.Windows.Data.Binding> właściwości.|  
|`path`|Ciąg ścieżki, który ustawia właściwość niejawną <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> . Zobacz również [PropertyPath SKŁADNI XAML](propertypath-xaml-syntax.md).|  
  
## <a name="unqualified-binding"></a>Niekwalifikowane {Binding}  
 Użycie pokazane w "użycie wyrażenia powiązania" <xref:System.Windows.Data.Binding> tworzy obiekt z wartościami domyślnymi, `null`które zawiera inicjał <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>. `{Binding}` Jest to nadal przydatne w wielu scenariuszach, ponieważ utworzony <xref:System.Windows.Data.Binding> może polegać na właściwościach powiązań danych kluczowych, takich jak <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> i <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> ustawionych w kontekście danych czasu wykonywania. Aby uzyskać więcej informacji na temat koncepcji kontekstu danych, zobacz [powiązanie danych](../data/data-binding-wpf.md).  
  
## <a name="implicit-path"></a>Ścieżka niejawna  
 Rozszerzenie znaczników używa <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> jako koncepcyjnej właściwości "default", gdzie `Path=` nie musi występować w wyrażeniu. `Binding` `Binding` Jeśli określisz wyrażenie z niejawną ścieżką, niejawna ścieżka musi znajdować się na początku wyrażenia, przed `bindProp` innymi = `value` parami, <xref:System.Windows.Data.Binding> w których właściwość jest określona przez nazwę. Na przykład: `{Binding PathString}`, gdzie `PathString` jest ciągiem, który jest analizowany jako wartość <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> w <xref:System.Windows.Data.Binding> elemencie utworzonym przez użycie rozszerzenia znacznika. Możesz dołączyć niejawną ścieżkę z innymi nazwanymi właściwościami po separatorze przecinka, `{Binding LastName, Mode=TwoWay}`na przykład.  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>Właściwości powiązania, które można ustawić za pomocą rozszerzenia powiązania  
 Składnia pokazana w tym temacie używa `bindProp` = `value` przybliżonego przybliżenia, ponieważ <xref:System.Windows.Data.BindingBase> istnieje wiele właściwości do odczytu/zapisu lub <xref:System.Windows.Data.Binding> które można ustawić za pomocą `Binding` rozszerzenia znacznika/ Składnia wyrażenia. Można je ustawić w dowolnej kolejności, z wyjątkiem niejawnego <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>. (Można określić `Path=`jawnie opcję, w której przypadku można ją ustawić w dowolnej kolejności). W zasadzie można ustawić zero lub więcej właściwości na poniższej liście, używając `bindProp` = `value` par oddzielonych przecinkami.  
  
 Niektóre z tych wartości właściwości wymagają typów obiektów, które nie obsługują konwersji typu natywnego z składni tekstu w języku XAML i w ten sposób wymagają rozszerzeń znaczników, aby można je było ustawić jako wartość atrybutu. Sprawdź sekcję użycie atrybutu XAML w bibliotece klas .NET Framework dla każdej właściwości, aby uzyskać więcej informacji. ciąg używany na potrzeby składni atrybutów XAML z lub bez użycia rozszerzenia znaczników jest zasadniczo taka sama jak wartość określona w `Binding` wyrażeniu, z wyjątkiem tego, że znaki cudzysłowu wokół każdego `bindProp` =wwyrażeniu. `value` `Binding`  
  
- <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: ciąg, który identyfikuje możliwą grupę powiązań. Jest to stosunkowo zaawansowane koncepcje powiązań. Zobacz stronę referencyjną <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>dla.  
  
- <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: Wartość logiczna może być albo `true`. `false` Wartość domyślna to `false`.  
  
- <xref:System.Windows.Data.Binding.Converter%2A>: można `bindProp` ustawić jako = `value` ciąg w wyrażeniu, ale w tym celu wymaga odwołania do obiektu dla wartości, takiej jak [StaticResource znacznika](staticresource-markup-extension.md). Wartość w tym przypadku jest wystąpieniem klasy niestandardowego konwertera.  
  
- <xref:System.Windows.Data.Binding.ConverterCulture%2A>: settable w wyrażeniu jako identyfikator oparty na standardach; Zapoznaj się z tematem <xref:System.Windows.Data.Binding.ConverterCulture%2A>referencyjnym.  
  
- <xref:System.Windows.Data.Binding.ConverterParameter%2A>: można ustawić jako `bindProp` = `value` ciąg w wyrażeniu, ale jest to zależne od typu przesyłanego parametru. W przypadku przekazywania typu odwołania dla wartości to użycie wymaga odwołania do obiektu, takiego jak zagnieżdżone [rozszerzenie znacznika StaticResource](staticresource-markup-extension.md).  
  
- <xref:System.Windows.Data.Binding.ElementName%2A>: wzajemnie <xref:System.Windows.Data.Binding.RelativeSource%2A> wykluczające <xref:System.Windows.Data.Binding.Source%2A>się i; każda z tych właściwości powiązań reprezentuje konkretną metodologię powiązania. Zobacz temat [powiązanie danych — omówienie](../data/data-binding-overview.md).  
  
- <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: można ustawić jako `bindProp` = `value` ciąg w wyrażeniu, ale jest to zależne od typu przenoszonej wartości. W przypadku przekazywania typu referencyjnego wymagane jest odwołanie do obiektu, takie jak zagnieżdżone [rozszerzenie znacznika StaticResource](staticresource-markup-extension.md).  
  
- <xref:System.Windows.Data.Binding.IsAsync%2A>: Wartość logiczna może być albo `true`. `false` Wartość domyślna to `false`.  
  
- <xref:System.Windows.Data.Binding.Mode%2A>: *wartość* jest stałą nazwą z <xref:System.Windows.Data.BindingMode> wyliczenia. Na przykład `{Binding Mode=OneWay}`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: Wartość logiczna może być albo `true`. `false` Wartość domyślna to `false`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: Wartość logiczna może być albo `true`. `false` Wartość domyślna to `false`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: Wartość logiczna może być albo `true`. `false` Wartość domyślna to `false`.  
  
- <xref:System.Windows.Data.Binding.Path%2A>: ciąg opisujący ścieżkę do obiektu danych lub ogólnego modelu obiektów. Format zawiera kilka różnych konwencji do przechodzenia przez model obiektów, który nie może być odpowiednio opisany w tym temacie. Zobacz [składnię XAML PropertyPath](propertypath-xaml-syntax.md).  
  
- <xref:System.Windows.Data.Binding.RelativeSource%2A>: wzajemnie wykluczające <xref:System.Windows.Data.Binding.ElementName%2A> się <xref:System.Windows.Data.Binding.Source%2A>i z i; każda z tych właściwości powiązań reprezentuje konkretną metodologię powiązania. Zobacz temat [powiązanie danych — omówienie](../data/data-binding-overview.md). Wymaga zagnieżdżonego użycia [wyrażenia MarkupExtension RelativeSource](relativesource-markupextension.md) do określenia wartości.  
  
- <xref:System.Windows.Data.Binding.Source%2A>: wzajemnie <xref:System.Windows.Data.Binding.RelativeSource%2A> wykluczające <xref:System.Windows.Data.Binding.ElementName%2A>się i; każda z tych właściwości powiązań reprezentuje konkretną metodologię powiązania. Zobacz temat [powiązanie danych — omówienie](../data/data-binding-overview.md). Wymaga użycia rozszerzenia zagnieżdżonego, zazwyczaj [rozszerzenie znacznika StaticResource](staticresource-markup-extension.md) , które odwołuje się do źródła danych obiektu z poziomu utworzonego w słowniku zasobów.  
  
- <xref:System.Windows.Data.BindingBase.StringFormat%2A>: ciąg opisujący Konwencję formatu ciągu dla powiązanych danych. Jest to stosunkowo zaawansowane koncepcje powiązań. Zobacz stronę referencyjną <xref:System.Windows.Data.BindingBase.StringFormat%2A>dla.  
  
- <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: można ustawić jako `bindProp` = `value` ciąg w wyrażeniu, ale jest to zależne od typu przesyłanego parametru. W przypadku przekazywania typu odwołania dla wartości, wymagane jest odwołanie do obiektu, takie jak zagnieżdżone [rozszerzenie znacznika StaticResource](staticresource-markup-extension.md).  
  
- <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>: *wartość* jest stałą nazwą z <xref:System.Windows.Data.UpdateSourceTrigger> wyliczenia. Na przykład `{Binding UpdateSourceTrigger=LostFocus}`. Określone kontrolki mogą mieć różne wartości domyślne dla tej właściwości powiązania. Zobacz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: Wartość logiczna może być albo `true`. `false` Wartość domyślna to `false`. Zobacz uwagi.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: Wartość logiczna może być albo `true`. `false` Wartość domyślna to `false`. Zobacz uwagi.  
  
- <xref:System.Windows.Data.Binding.XPath%2A>: ciąg opisujący ścieżkę do XMLDOM źródła danych XML. Zobacz [powiąż z danymi XML przy użyciu XmlDataProvider i zapytań XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Poniżej znajdują się właściwości <xref:System.Windows.Data.Binding> , które nie mogą być ustawiane `Binding` przy użyciu`{Binding}` rozszerzenia znacznika/formularza wyrażenia.  
  
- <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: Ta właściwość oczekuje odwołania do implementacji wywołania zwrotnego. W składni XAML nie można odwoływać się do wywołań zwrotnych/metod innych niż procedury obsługi zdarzeń.  
  
- <xref:System.Windows.Data.Binding.ValidationRules%2A>: Właściwość przyjmuje ogólną kolekcję <xref:System.Windows.Controls.ValidationRule> obiektów. Może to być wyrażone jako element właściwości w <xref:System.Windows.Data.Binding> elemencie obiektu, ale nie ma łatwo dostępnej techniki analizy atrybutu do użycia `Binding` w wyrażeniu. Zobacz temat referencyjny <xref:System.Windows.Data.Binding.ValidationRules%2A>dla.  
  
- <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
> Zgodnie z pierwszeństwem `Binding` właściwości zależności wyrażenie jest równoważne wartości ustawionej lokalnie. `Binding` W`Binding` przypadku ustawienia wartości lokalnej dla właściwości, która wcześniej miała wyrażenie, zostaje całkowicie usunięty. Aby uzyskać szczegółowe informacje, zobacz [pierwszeństwo wartości właściwości zależności](dependency-property-value-precedence.md).  
  
 W tym temacie nie opisano opisu powiązania danych na poziomie podstawowym. Zobacz temat [powiązanie danych — omówienie](../data/data-binding-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Data.MultiBinding>i <xref:System.Windows.Data.PriorityBinding> nie[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsługują składni rozszerzenia. Zamiast tego należy użyć elementów właściwości. Zobacz tematy referencyjne <xref:System.Windows.Data.MultiBinding> dla <xref:System.Windows.Data.PriorityBinding>i.  
  
 W wartościach logicznych dla języka XAML jest rozróżniana wielkość liter. Na przykład można określić albo `{Binding NotifyOnValidationError=true}`. `{Binding NotifyOnValidationError=True}`  
  
 Powiązania obejmujące sprawdzanie poprawności danych są zwykle określane przez jawny `Binding` element, a nie `{Binding ...}` jako wyrażenie, a ustawienie <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> lub <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> w wyrażeniu jest nietypowe. Wynika to z faktu, <xref:System.Windows.Data.Binding.ValidationRules%2A> że właściwość pomocnika nie może być łatwo ustawiona w formularzu wyrażenia. Aby uzyskać więcej informacji, zobacz [implementowanie walidacji powiązania](../data/how-to-implement-binding-validation.md).  
  
 `Binding`jest rozszerzeniem znaczników. Rozszerzenia znaczników są zwykle implementowane, gdy istnieje wymóg, aby wartości atrybutów ucieczki były inne niż wartości literałów lub nazwy programów obsługi, a wymagania są bardziej globalne niż konwertery typów przypisane do określonych typów lub właściwości. Wszystkie rozszerzenia znaczników w języku XAML używają `{` znaków `}` i w ich składni atrybutów, która jest konwencją, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znacznika musi przetworzyć zawartość ciągu. Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
 `Binding`to nietypowe rozszerzenie znaczników w tym, <xref:System.Windows.Data.Binding> że Klasa implementująca funkcje rozszerzenia dla implementacji XAML WPF również implementuje kilka innych metod i właściwości, które nie są powiązane z XAML. Inne składowe mają na celu bardziej <xref:System.Windows.Data.Binding> uniwersalną i samodzielną klasę, która może zawierać wiele scenariuszy powiązań danych, a także działa jako rozszerzenie języka XAML.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Data.Binding>
- [Powiązanie danych — omówienie](../data/data-binding-overview.md)
- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
- [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md)
