---
title: Rozszerzenie znaczników powiązania
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: c6a424e085c7499db08d0a7e6b652f45fb2cdd70
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644082"
---
# <a name="binding-markup-extension"></a>Rozszerzenie znaczników powiązania
Defers wartość właściwości jest wartością powiązaną z danymi, tworząc obiekt wyrażenia pośredniego i interpretując kontekst danych, który ma zastosowanie do elementu i jego powiązania w czasie wykonywania.  
  
## <a name="binding-expression-usage"></a>Użycie wyrażenia wiązania  
  
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
 W tych składniach `[]` i `*` nie są literały. Są one częścią notacji, aby wskazać, że można użyć par*wartości* `,` zero lub więcej *bindProp,*`=`z separatorem między nimi i poprzednimi parami*wartości* *bindProp.*`=`  
  
 Każda z właściwości wymienionych w sekcji "Właściwości wiązania, które można ustawić za pomocą rozszerzenia wiązania", można zamiast tego ustawić przy użyciu atrybutów elementu <xref:System.Windows.Data.Binding> obiektu. Jednak to nie jest naprawdę użycie <xref:System.Windows.Data.Binding>rozszerzenia znaczników , jest to tylko ogólne przetwarzanie XAML <xref:System.Windows.Data.Binding> atrybutów, które ustawiają właściwości klasy CLR. Innymi słowy `<Binding` *bindProp1*`="`*wartość1* `"[` *bindPropN*`="`*valueN* `"]*/>` jest równoważną <xref:System.Windows.Data.Binding> składnią dla atrybutów użycia elementu obiektu zamiast użycia `Binding` wyrażenia. Aby dowiedzieć się więcej o użyciu atrybutu <xref:System.Windows.Data.Binding>XAML określonych właściwości , zobacz sekcję "Użycie atrybutu XAML" odpowiedniej właściwości <xref:System.Windows.Data.Binding> w bibliotece klas programu .NET Framework.  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|Nazwa <xref:System.Windows.Data.Binding> lub <xref:System.Windows.Data.BindingBase> właściwość do ustawionego. Nie <xref:System.Windows.Data.Binding> wszystkie właściwości można ustawić `Binding` za pomocą rozszerzenia, a niektóre `Binding` właściwości można ustawić w wyrażeniu tylko przy użyciu dalszych zagnieżdżonych rozszerzeń znaczników. Zobacz sekcję "Właściwości wiązania, które można ustawić z rozszerzeniem wiązania".|  
|`value1, valueN`|Wartość, aby ustawić właściwość. Obsługa wartości atrybutu jest ostatecznie specyficzne dla typu i <xref:System.Windows.Data.Binding> logiki określonej właściwości jest ustawiona.|  
|`path`|Ciąg ścieżki, który <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> ustawia niejawną właściwość. Zobacz też [Składnia XAML ścieżki właściwości](propertypath-xaml-syntax.md).|  
  
## <a name="unqualified-binding"></a>Niekwalifikowany {Powiązanie}  
 Użycie `{Binding}` pokazane w "Użycie wyrażenia <xref:System.Windows.Data.Binding> wiązania" tworzy obiekt z <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> wartościami domyślnymi, który zawiera inicjał `null`. Jest to nadal przydatne w wielu <xref:System.Windows.Data.Binding> scenariuszach, ponieważ utworzone może polegać <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> na właściwości powiązania danych klucza, takich jak i jest ustawiany w kontekście danych w czasie wykonywania. Aby uzyskać więcej informacji na temat pojęcia kontekstu danych, zobacz [Powiązanie danych](../../../desktop-wpf/data/data-binding-overview.md).  
  
## <a name="implicit-path"></a>Ścieżka niejawna  
 Rozszerzenie `Binding` znaczników <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> używa jako koncepcyjnej "właściwości domyślnej", gdzie `Path=` nie musi być wyświetlany w wyrażeniu. Jeśli określisz `Binding` wyrażenie ze ścieżką niejawną, ścieżka niejawna musi `bindProp` = `value` pojawić się <xref:System.Windows.Data.Binding> najpierw w wyrażeniu, przed innymi parami, w których właściwość jest określona przez nazwę. Na `{Binding PathString}`przykład: `PathString` , gdzie jest ciąg, który <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> jest <xref:System.Windows.Data.Binding> oceniany jako wartość w utworzone przez użycie rozszerzenia znaczników. Ścieżkę niejawną można dołączyć z innymi nazwanymi właściwościami po `{Binding LastName, Mode=TwoWay}`separatorze przecinków, na przykład .  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>Właściwości wiązania, które można ustawić za pomocą rozszerzenia wiązania  
 Składnia pokazana w tym temacie `bindProp` = `value` używa ogólnego przybliżenia, ponieważ istnieje wiele <xref:System.Windows.Data.BindingBase> właściwości <xref:System.Windows.Data.Binding> odczytu/zapisu `Binding` lub które można ustawić za pomocą rozszerzenia znacznika / składni wyrażenia. Można je ustawić w dowolnej kolejności, z <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>wyjątkiem niejawnego . (Masz możliwość jawnego określenia `Path=`, w którym to przypadku można go ustawić w dowolnej kolejności). Zasadniczo można ustawić zero lub więcej właściwości na poniższej `bindProp` = `value` liście, używając par oddzielonych przecinkami.  
  
 Kilka z tych wartości właściwości wymaga typów obiektów, które nie obsługują konwersji typu macierzystego ze składni tekstu w języku XAML, a zatem wymagają rozszerzeń znaczników w celu ustawionego jako wartość atrybutu. Sprawdź sekcję Użycie atrybutu XAML w bibliotece klas .NET Framework dla każdej właściwości, aby uzyskać więcej informacji; ciąg używany dla składni atrybutu XAML z lub bez użycia rozszerzenia znaczników jest zasadniczo `Binding` taki sam jak wartość określona w wyrażeniu, z wyjątkiem, że nie umieszczasz cudzysłowów wokół `bindProp` = `value` każdego w wyrażeniu. `Binding`  
  
- <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: ciąg identyfikujący możliwą grupę wiązania. Jest to stosunkowo zaawansowana koncepcja wiązania; patrz strona <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>referencyjna dla .  
  
- <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: Boolean, może `true` być `false`albo lub . Wartość domyślna to `false`.  
  
- <xref:System.Windows.Data.Binding.Converter%2A>: można ustawić `bindProp` = `value` jako ciąg w wyrażeniu, ale w tym celu wymaga odwołania do obiektu dla wartości, takich jak [StaticResource Markup Extension](staticresource-markup-extension.md). Wartość w tym przypadku jest wystąpieniem niestandardowej klasy konwertera.  
  
- <xref:System.Windows.Data.Binding.ConverterCulture%2A>: settable w wyrażeniu jako identyfikator oparty na standardach; zobacz temat referencyjny dla <xref:System.Windows.Data.Binding.ConverterCulture%2A>.  
  
- <xref:System.Windows.Data.Binding.ConverterParameter%2A>: można ustawić `bindProp` = `value` jako ciąg w wyrażeniu, ale zależy to od typu parametru, który jest przekazywany. W przypadku przekazywania typu odwołania dla wartości, to użycie wymaga odwołania do obiektu, takiego jak zagnieżdżone [rozszerzenie znaczników StaticResource](staticresource-markup-extension.md).  
  
- <xref:System.Windows.Data.Binding.ElementName%2A>: wzajemnie <xref:System.Windows.Data.Binding.RelativeSource%2A> się <xref:System.Windows.Data.Binding.Source%2A>wykluczają i ; każda z tych właściwości wiązania reprezentuje metodologię określonego wiązania. Zobacz [Omówienie powiązania danych](../../../desktop-wpf/data/data-binding-overview.md).  
  
- <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: można ustawić `bindProp` = `value` jako ciąg w wyrażeniu, ale zależy to od typu przekazywana wartość. W przypadku przekazywania typu odwołania, wymaga odwołania do obiektu, takiego jak zagnieżdżone [rozszerzenie znaczników StaticResource](staticresource-markup-extension.md).  
  
- <xref:System.Windows.Data.Binding.IsAsync%2A>: Boolean, może `true` być `false`albo lub . Wartość domyślna to `false`.  
  
- <xref:System.Windows.Data.Binding.Mode%2A>: *wartość* jest stałą <xref:System.Windows.Data.BindingMode> nazwą z wyliczenia. Na przykład `{Binding Mode=OneWay}`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: Boolean, może `true` być `false`albo lub . Wartość domyślna to `false`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: Boolean, może `true` być `false`albo lub . Wartość domyślna to `false`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: Boolean, może `true` być `false`albo lub . Wartość domyślna to `false`.  
  
- <xref:System.Windows.Data.Binding.Path%2A>: ciąg opisujący ścieżkę do obiektu danych lub ogólnego modelu obiektu. Format zawiera kilka różnych konwencji przechodzenia przez model obiektu, które nie mogą być odpowiednio opisane w tym temacie. Zobacz [Składnia XAML ścieżki właściwości](propertypath-xaml-syntax.md).  
  
- <xref:System.Windows.Data.Binding.RelativeSource%2A>: wzajemnie się <xref:System.Windows.Data.Binding.ElementName%2A> <xref:System.Windows.Data.Binding.Source%2A>wykluczają w porównaniu z i ; każda z tych właściwości wiązania reprezentuje metodologię określonego wiązania. Zobacz [Omówienie powiązania danych](../../../desktop-wpf/data/data-binding-overview.md). Wymaga zagnieżdżonego [użycia RelativeSource MarkupExtension,](relativesource-markupextension.md) aby określić wartość.  
  
- <xref:System.Windows.Data.Binding.Source%2A>: wzajemnie <xref:System.Windows.Data.Binding.RelativeSource%2A> się <xref:System.Windows.Data.Binding.ElementName%2A>wykluczają i ; każda z tych właściwości wiązania reprezentuje metodologię określonego wiązania. Zobacz [Omówienie powiązania danych](../../../desktop-wpf/data/data-binding-overview.md). Wymaga użycia rozszerzenia zagnieżdżonego, zazwyczaj [StaticResource Markup Extension,](staticresource-markup-extension.md) który odwołuje się do źródła danych obiektu ze słownika zasobów kluczem.  
  
- <xref:System.Windows.Data.BindingBase.StringFormat%2A>: ciąg opisujący konwencję formatu ciągu dla danych powiązanych. Jest to stosunkowo zaawansowana koncepcja wiązania; patrz strona <xref:System.Windows.Data.BindingBase.StringFormat%2A>referencyjna dla .  
  
- <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: można ustawić `bindProp` = `value` jako ciąg w wyrażeniu, ale zależy to od typu parametru, który jest przekazywany. W przypadku przekazywania typu odwołania dla wartości, wymaga odwołania do obiektu, takiego jak zagnieżdżone [rozszerzenie znaczników StaticResource](staticresource-markup-extension.md).  
  
- <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>: *wartość* jest stałą <xref:System.Windows.Data.UpdateSourceTrigger> nazwą z wyliczenia. Na przykład `{Binding UpdateSourceTrigger=LostFocus}`. Określone formanty potencjalnie mają różne wartości domyślne dla tej właściwości wiązania. Zobacz: <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: Boolean, może `true` być `false`albo lub . Wartość domyślna to `false`. Zobacz uwagi.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: Boolean, może `true` być `false`albo lub . Wartość domyślna to `false`. Zobacz uwagi.  
  
- <xref:System.Windows.Data.Binding.XPath%2A>: ciąg opisujący ścieżkę do pliku XMLDOM źródła danych XML. Zobacz [Powiązanie danych XML przy użyciu zapytań XMLDataProvider i XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Poniżej przedstawiono <xref:System.Windows.Data.Binding> właściwości, których nie `Binding` można ustawić`{Binding}` przy użyciu formularza rozszerzenia/wyrażenia znaczników.  
  
- <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: ta właściwość oczekuje odwołania do implementacji wywołania zwrotnego. Wywołania zwrotne/metody inne niż programy obsługi zdarzeń nie mogą odwoływać się w składni XAML.  
  
- <xref:System.Windows.Data.Binding.ValidationRules%2A>: właściwość przyjmuje ogólną kolekcję <xref:System.Windows.Controls.ValidationRule> obiektów. Może to być wyrażone jako <xref:System.Windows.Data.Binding> element właściwości w elemencie obiektu, ale nie ma `Binding` łatwo dostępnej techniki analizowania atrybutów dla użycia w wyrażeniu. Zobacz temat <xref:System.Windows.Data.Binding.ValidationRules%2A>referencyjny dla .  
  
- <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
> Pod względem pierwszeństwa właściwości zależności `Binding` wyrażenie jest równoważne wartości ustawionej lokalnie. Jeśli ustawisz wartość lokalną dla właściwości, `Binding` która `Binding` wcześniej miała wyrażenie, jest całkowicie usunięta. Aby uzyskać szczegółowe informacje, zobacz [Pierwszeństwo wartości właściwości zależności](dependency-property-value-precedence.md).  
  
 Opisujące powiązanie danych na poziomie podstawowym nie jest omówione w tym temacie. Zobacz [Omówienie powiązania danych](../../../desktop-wpf/data/data-binding-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Data.MultiBinding>i <xref:System.Windows.Data.PriorityBinding> nie obsługują [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] składni rozszerzenia. Zamiast tego należy użyć elementów właściwości. Zobacz tematy <xref:System.Windows.Data.MultiBinding> referencyjne dla i <xref:System.Windows.Data.PriorityBinding>.  
  
 Wartości logiczne dla XAML są niewrażliwe na wielkości liter. Na przykład można określić albo `{Binding NotifyOnValidationError=true}` lub `{Binding NotifyOnValidationError=True}`.  
  
 Powiązania, które obejmują sprawdzanie poprawności danych `Binding` są zazwyczaj określone `{Binding ...}` przez element <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> jawny, a nie jako wyrażenie, a ustawienie lub w wyrażeniu jest rzadkością. Jest tak, ponieważ <xref:System.Windows.Data.Binding.ValidationRules%2A> właściwość towarzysza nie można łatwo ustawić w formularzu wyrażenia. Aby uzyskać więcej informacji, zobacz [Implementowanie sprawdzania poprawności powiązania](../data/how-to-implement-binding-validation.md).  
  
 `Binding`jest rozszerzeniem znaczników. Rozszerzenia znaczników są zazwyczaj implementowane, gdy istnieje wymóg, aby uniknąć wartości atrybutów, które mają być inne niż wartości literału lub nazwy obsługi, a wymaganie jest bardziej globalne niż konwertery typów przypisane dla niektórych typów lub właściwości. Wszystkie rozszerzenia znaczników w XAML używają `{` znaków i `}` w składni atrybutów, czyli konwencji, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znaczników musi przetwarzać zawartość ciągu. Aby uzyskać więcej informacji, zobacz [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
 `Binding`jest nietypowe rozszerzenie znaczników w <xref:System.Windows.Data.Binding> tym klasy, która implementuje funkcje rozszerzenia dla implementacji XAML WPF WPF implementuje również kilka innych metod i właściwości, które nie są związane z XAML. Inne elementy członkowskie są <xref:System.Windows.Data.Binding> przeznaczone do bardziej wszechstronne i samodzielne klasy, które mogą rozwiązać wiele scenariuszy wiązania danych oprócz działania jako rozszerzenie znaczników XAML.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Data.Binding>
- [Omówienie powiązania danych](../../../desktop-wpf/data/data-binding-overview.md)
- [Omówienie XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md)
