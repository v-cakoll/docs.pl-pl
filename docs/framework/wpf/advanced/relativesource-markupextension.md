---
title: RelativeSource MarkupExtension
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 6ede7bc8a6c2a45630c48417c7ab90eb8decdc39
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54029440"
---
# <a name="relativesource-markupextension"></a>RelativeSource MarkupExtension
Określa właściwości <xref:System.Windows.Data.RelativeSource> źródło powiązania, do użycia w [Binding Markup Extension](../../../../docs/framework/wpf/advanced/binding-markup-extension.md), lub podczas ustawiania <xref:System.Windows.Data.Binding.RelativeSource%2A> właściwość <xref:System.Windows.Data.Binding> elementu ustanowionych w XAML.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xml  
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>  
```  
  
## <a name="xaml-attribute-usage-nested-within-binding-extension"></a>Użycie atrybutu języka XAML (zagnieżdżonego w rozszerzeniu Binding)  
  
```xml  
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>Użycie elementu obiektu języka XAML  
  
```xml  
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource Mode="modeEnumValue"/>  
  </Binding.RelativeSource>  
</Binding>  
```
—lub—  
```xml
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource  
      Mode="FindAncestor"  
      AncestorType="{x:Type typeName}"  
      AncestorLevel="intLevel"  
    />  
  </Binding.RelativeSource>  
</Binding>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`modeEnumValue`|Jeden z poniższych:<br /><br /> -Token ciągu `Self`; odpowiada <xref:System.Windows.Data.RelativeSource> utworzonemu z jego <xref:System.Windows.Data.RelativeSource.Mode%2A> właściwością <xref:System.Windows.Data.RelativeSourceMode.Self>.<br />-Token ciągu `TemplatedParent`; odpowiada <xref:System.Windows.Data.RelativeSource> utworzonemu z jego <xref:System.Windows.Data.RelativeSource.Mode%2A> właściwością <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.<br />-Token ciągu `PreviousData`; odpowiada <xref:System.Windows.Data.RelativeSource> utworzonemu z jego <xref:System.Windows.Data.RelativeSource.Mode%2A> właściwością <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.<br />-Poniżej znajdują się informacje o `FindAncestor` trybu.|  
|`FindAncestor`|Token ciągu `FindAncestor`. Przy użyciu tego tokenu zgodnie z którą przechodzi w tryb `RelativeSource` Określa typ elementu nadrzędnego oraz opcjonalnie jego poziom. Odpowiada to <xref:System.Windows.Data.RelativeSource> utworzonemu z jego <xref:System.Windows.Data.RelativeSource.Mode%2A> właściwością <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.|  
|`typeName`|Wymagane dla `FindAncestor` trybu. Nazwa typu, która wypełnia <xref:System.Windows.Data.RelativeSource.AncestorType%2A> właściwości.|  
|`intLevel`|Opcjonalnie na potrzeby `FindAncestor` trybu. Poziom elementu nadrzędnego (patrząc w kierunku nadrzędności w drzewie logicznym).|  
  
## <a name="remarks"></a>Uwagi  
 `{RelativeSource TemplatedParent}` powiązań to technika odnoszący się do koncepcji oddzielania Interfejsu użytkownika formantu i od logiki formantu. Umożliwia tworzenie powiązań z wewnątrz definicji szablonu do elementu nadrzędnego używającego szablonu (tzn. do wystąpienia obiektu, do którego w czasie wykonywania szablon jest stosowany). Dla tego przypadku [TemplateBinding Markup Extension](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) jest w rzeczywistości skrótem następującego wyrażenia powiązania: `{Binding RelativeSource={RelativeSource TemplatedParent}}`. `TemplateBinding` lub `{RelativeSource TemplatedParent}` użycia są istotne tylko w ramach XAML, który definiuje szablonu. Aby uzyskać więcej informacji, zobacz [TemplateBinding Markup Extension](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)  
  
 `{RelativeSource FindAncestor}` jest głównie używane w szablonach formantów lub przewidywalnych samodzielnych kompozycjach interfejsu użytkownika, w przypadkach, w którym formantu zawsze oczekuje się, w drzewie wizualnym określonego typu elementu nadrzędnego. Na przykład, elementy z formantem elementów mogą używać `FindAncestor` elementu nadrzędnego formantu w celu utworzenia powiązania z właściwości ich pozycji. Ewentualnie elementy będące częścią kompozycji formantu w szablonie można użyć `FindAncestor` powiązania z elementami nadrzędnymi w tej samej strukturze kompozycji.  
  
 W składni obiektów `FindAncestor` wyświetlane w sekcjach XAML składnia drugiego składnia elementu obiektu jest używana specjalnie dla trybu `FindAncestor` trybu. `FindAncestor` tryb wymaga <xref:System.Windows.Data.RelativeSource.AncestorType%2A> wartość. Należy ustawić <xref:System.Windows.Data.RelativeSource.AncestorType%2A> jako atrybut poprzez [x: Type Markup Extension](../../../../docs/framework/xaml-services/x-type-markup-extension.md) odwołanie do typu szukanego elementu nadrzędnego do wyszukania. <xref:System.Windows.Data.RelativeSource.AncestorType%2A> Wartość jest używana podczas przetwarzania żądania powiązania w czasie wykonywania.  
  
 Dla `FindAncestor` tryb, opcjonalna właściwość <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> może pomóc odróżnić w przypadkach, gdzie prawdopodobnie jest więcej niż jednego elementu nadrzędnego tego typu w drzewie elementów.  
  
 Aby uzyskać więcej informacji na temat sposobu użycia `FindAncestor` tryb, zobacz <xref:System.Windows.Data.RelativeSource>.  
  
 `{RelativeSource Self}` jest przydatne w scenariuszach między właściwościami, gdzie jedna właściwość wystąpienia powinna zależeć od wartości innej właściwości tego samego wystąpienia, a nie ogólna Relacja zależności (np. przekształcenie) już istnieje. Chociaż rzadko, że dwie właściwości istnieje w obiekcie w taki sposób, że wartości są niemal identycznych (i takich samych typach), można także zastosować `Converter` parametr do powiązania mającego `{RelativeSource Self}`i używać konwertera do konwersji między źródłowymi i typy elementów docelowych. Inny scenariusz dla `{RelativeSource Self}` jest jako część <xref:System.Windows.MultiDataTrigger>.  
  
 Na przykład, poniższy XAML definiuje <xref:System.Windows.Shapes.Rectangle> element takich niezależnie od wartości wprowadzonej w <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.Shapes.Rectangle> jest zawsze kwadratem: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`  
  
 `{RelativeSource PreviousData}` jest przydatne w szablonach danych lub w sytuacjach, w którym powiązania korzystają z kolekcji jako źródło danych. Możesz użyć `{RelativeSource PreviousData}` może akcentować relacje między sąsiednimi elementami danych w kolekcji. Pokrewną techniką jest ustanowienie <xref:System.Windows.Data.MultiBinding> między elementami bieżącym i poprzednim w źródle danych i użyj powiązania konwertera w celu ustalenia różnic między dwoma elementami i ich właściwości.  
  
 W poniższym przykładzie pierwszy <xref:System.Windows.Controls.TextBlock> w elementach szablonów pokazuje bieżący numer. Drugi <xref:System.Windows.Controls.TextBlock> powiązanie jest <xref:System.Windows.Data.MultiBinding> nominalnie ma dwa <xref:System.Windows.Data.Binding> właściwości: bieżący rekord oraz powiązanie, które celowo używa poprzedniego rekordu danych przy użyciu `{RelativeSource PreviousData}`. Następnie konwerter <xref:System.Windows.Data.MultiBinding> oblicza różnicę i zwraca go do powiązania.  
  
```xml  
<ListBox Name="fibolist">  
    <ListBox.ItemTemplate>  
        <DataTemplate>  
            <StackPanel Orientation="Horizontal">  
            <TextBlock Text="{Binding}"/>  
            <TextBlock>, difference = </TextBlock>  
                <TextBlock>  
                    <TextBlock.Text>  
                        <MultiBinding Converter="{StaticResource DiffConverter}">  
                            <Binding/>  
                            <Binding RelativeSource="{RelativeSource PreviousData}"/>  
                        </MultiBinding>  
                    </TextBlock.Text>  
                </TextBlock>  
            </StackPanel>  
        </DataTemplate>  
    </ListBox.ItemTemplate>  
```  
  
 Nie omówiono w tym miejscu całej koncepcji powiązań danych. dokładniejsze zobacz [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacji procesora XAML, obsługa tego rozszerzenia znacznika jest definiowana przez <xref:System.Windows.Data.RelativeSource> klasy.  
  
 `RelativeSource` jest rozszerzeniem znacznika. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w XAML użyj `{` i `}` znaków w składni swoich atrybutów, które jest do Konwencja, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znacznika musi wykonać przetwarzanie atrybutu. Aby uzyskać więcej informacji, zobacz [rozszerzenia znacznikowania i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Data.Binding>  
 [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Powiązanie deklaracji — omówienie](../../../../docs/framework/wpf/data/binding-declarations-overview.md)  
 [x:Type, rozszerzenie znaczników](../../../../docs/framework/xaml-services/x-type-markup-extension.md)
