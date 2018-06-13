---
title: RelativeSource MarkupExtension
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 77caa7c84f63f90ae83df5685f93ba6d18f7436f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548269"
---
# <a name="relativesource-markupextension"></a>RelativeSource MarkupExtension
Określa właściwości <xref:System.Windows.Data.RelativeSource> źródle powiązania do użycia w [powiązania — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/binding-markup-extension.md), lub gdy ustawienie <xref:System.Windows.Data.Binding.RelativeSource%2A> właściwość <xref:System.Windows.Data.Binding> elementu w języku XAML.  
  
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
- or   
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
|`modeEnumValue`|Jeden z poniższych:<br /><br /> -Token ciągu `Self`; odpowiada <xref:System.Windows.Data.RelativeSource> utworzonego za jego <xref:System.Windows.Data.RelativeSource.Mode%2A> ustawioną właściwość <xref:System.Windows.Data.RelativeSourceMode.Self>.<br />-Token ciągu `TemplatedParent`; odpowiada <xref:System.Windows.Data.RelativeSource> utworzonego za jego <xref:System.Windows.Data.RelativeSource.Mode%2A> ustawioną właściwość <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.<br />-Token ciągu `PreviousData`; odpowiada <xref:System.Windows.Data.RelativeSource> utworzonego za jego <xref:System.Windows.Data.RelativeSource.Mode%2A> ustawioną właściwość <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.<br />-Poniżej zamieszczono informacje na `FindAncestor` tryb.|  
|`FindAncestor`|Token ciągu `FindAncestor`. Za pomocą tego tokenu zgodnie z którymi przechodzi w tryb `RelativeSource` Określa typ elementu nadrzędnego i opcjonalnie na poziomie nadrzędnym. Odpowiada to <xref:System.Windows.Data.RelativeSource> utworzonego za jego <xref:System.Windows.Data.RelativeSource.Mode%2A> ustawioną właściwość <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.|  
|`typeName`|Wymagany dla `FindAncestor` trybu. Nazwa typu, który wypełnia <xref:System.Windows.Data.RelativeSource.AncestorType%2A> właściwości.|  
|`intLevel`|Opcjonalny w przypadku `FindAncestor` tryb. Poziom elementu nadrzędnego (patrząc w kierunku nadrzędności w drzewie logicznym).|  
  
## <a name="remarks"></a>Uwagi  
 `{RelativeSource TemplatedParent}` Powiązanie użycia to technika klucza, która dotyczy większych koncepcji oddzielenie logiki formantu i formantu interfejsu użytkownika. Umożliwia tworzenie powiązań z wewnątrz definicji szablonu do elementu nadrzędnego używającego szablonu (tzn. do wystąpienia obiektu, do którego w czasie wykonywania szablon jest stosowany). Dla tego przypadku [rozszerzenie znacznika TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) w rzeczywistości jest skróconą formą następującego wyrażenia powiązania: `{Binding RelativeSource={RelativeSource TemplatedParent}}`. `TemplateBinding` lub `{RelativeSource TemplatedParent}` użycia są tylko odpowiednie w języku XAML, który definiuje szablonu. Aby uzyskać więcej informacji, zobacz [rozszerzenie znacznika TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)  
  
 `{RelativeSource FindAncestor}` jest głównie używane w szablonów kontrolki lub przewidywalną niezależne kompozycji interfejsu użytkownika, w przypadkach, gdy formant zawsze powinien być w drzewie wizualnym określonego typu elementu nadrzędnego. Na przykład użyć elementów formantu elementów `FindAncestor` użycia w celu powiązania właściwości ich elementów kontroli nadrzędnego elementu nadrzędnego. Elementy, które są częścią kompozycji formantu w szablonie można także użyć `FindAncestor` powiązania z elementy nadrzędne w tej samej struktury kompozycji.  
  
 W składni elementu obiektu `FindAncestor` tryb opisane w sekcjach składni języka XAML, drugi obiekt elementu jest używana składnia specjalnie z myślą o `FindAncestor` tryb. `FindAncestor` tryb wymaga <xref:System.Windows.Data.RelativeSource.AncestorType%2A> wartość. Należy ustawić <xref:System.Windows.Data.RelativeSource.AncestorType%2A> jako przy użyciu atrybutu [x: Type — rozszerzenie znaczników](../../../../docs/framework/xaml-services/x-type-markup-extension.md) odwołanie do typu elementu nadrzędnego do wyszukania. <xref:System.Windows.Data.RelativeSource.AncestorType%2A> Wartość jest używana podczas przetwarzania żądania wiązania w czasie wykonywania.  
  
 Dla `FindAncestor` tryb, opcjonalna właściwość <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> może pomóc odróżniania wyszukiwania elementu nadrzędnego w przypadkach, w przypadku, gdy jest prawdopodobnie więcej niż jednego elementu nadrzędnego tego typu istniejącego w drzewie elementu.  
  
 Aby uzyskać więcej informacji na temat sposobu użycia `FindAncestor` tryb, zobacz <xref:System.Windows.Data.RelativeSource>.  
  
 `{RelativeSource Self}` jest przydatne w scenariuszach między te dwie właściwości gdzie jedną właściwość wystąpienia zależy od wartość inna właściwość w tym samym wystąpieniu i Brak relacji właściwości zależności ogólne (na przykład koercja) już istnieje. Mimo że rzadko, że dwie właściwości istnieje w obiekcie tak, aby wartości są identyczne dosłownie (i tak samo wpisywania), można także zastosować `Converter` parametr do powiązania, które ma `{RelativeSource Self}`i używania do konwersji między źródłem i typy elementów docelowych. Inny scenariusz `{RelativeSource Self}` jest częścią <xref:System.Windows.MultiDataTrigger>.  
  
 Na przykład definiuje następujące XAML <xref:System.Windows.Shapes.Rectangle> element takie wprowadzonym niezależnie od tego, jakie korzyści dla <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.Shapes.Rectangle> jest zawsze kwadrat: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`  
  
 `{RelativeSource PreviousData}` jest przydatne w szablonach danych lub w przypadkach, gdy powiązania użycia kolekcji jako źródła danych. Można użyć `{RelativeSource PreviousData}` aby wyróżnić relacji między elementami danych sąsiadujących ze sobą w kolekcji. Powiązane technika jest ustanowienie <xref:System.Windows.Data.MultiBinding> między elementami bieżącego i poprzedniego źródła danych i użycia konwertera dla tego powiązania w celu obliczenia różnicy między dwoma elementami i ich właściwości.  
  
 W poniższym przykładzie pierwszy <xref:System.Windows.Controls.TextBlock> w elementach szablonów wskazuje aktualną liczbę. Drugi <xref:System.Windows.Controls.TextBlock> powiązanie <xref:System.Windows.Data.MultiBinding> nominalnie zawierającego dwa <xref:System.Windows.Data.Binding> consistuents: bieżącego rekordu, a obiekt binding używający celowo poprzedniego rekordu danych przy użyciu `{RelativeSource PreviousData}`. Następnie konwertera na <xref:System.Windows.Data.MultiBinding> oblicza różnicę i zwraca go do powiązania.  
  
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
  
 Zobacz opisujący wiązanie danych koncepcji nie objętych w tym miejscu [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacji procesora XAML, obsługę tego rozszerzenia znacznika jest definiowana za pomocą <xref:System.Windows.Data.RelativeSource> klasy.  
  
 `RelativeSource` to rozszerzenie znacznika. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w XAML, użyj `{` i `}` znaków w ich składni atrybutu Konwencji, za pomocą którego procesora XAML rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybutu. Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Data.Binding>  
 [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Powiązanie deklaracji — omówienie](../../../../docs/framework/wpf/data/binding-declarations-overview.md)  
 [x:Type, rozszerzenie znaczników](../../../../docs/framework/xaml-services/x-type-markup-extension.md)
