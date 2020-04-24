---
title: RelativeSource MarkupExtension
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 6301299da966ade9b5cc7ccd105c8269a486744e
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646228"
---
# <a name="relativesource-markupextension"></a>RelativeSource MarkupExtension

Określa właściwości źródła <xref:System.Windows.Data.RelativeSource> powiązania, które mają być używane w [rozszerzeniu znaczników powiązania](binding-markup-extension.md)lub podczas ustawiania <xref:System.Windows.Data.Binding.RelativeSource%2A> właściwości <xref:System.Windows.Data.Binding> elementu ustanowionego w języku XAML.

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

— lub —

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
|`modeEnumValue`|Jeden z poniższych programów:<br /><br /> - Token `Self`ciągu; odpowiada utworzonej <xref:System.Windows.Data.RelativeSource> z jego <xref:System.Windows.Data.RelativeSource.Mode%2A> właściwością <xref:System.Windows.Data.RelativeSourceMode.Self>ustawioną na .<br />- Token `TemplatedParent`ciągu; odpowiada utworzonej <xref:System.Windows.Data.RelativeSource> z jego <xref:System.Windows.Data.RelativeSource.Mode%2A> właściwością <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>ustawioną na .<br />- Token `PreviousData`ciągu; odpowiada utworzonej <xref:System.Windows.Data.RelativeSource> z jego <xref:System.Windows.Data.RelativeSource.Mode%2A> właściwością <xref:System.Windows.Data.RelativeSourceMode.PreviousData>ustawioną na .<br />- Zobacz poniżej, aby uzyskać informacje na `FindAncestor` temat trybu.|
|`FindAncestor`|Token `FindAncestor`ciągu . Za pomocą tego tokenu wchodzi `RelativeSource` w tryb, w którym określa typ nadrzędny i opcjonalnie poziom nadrzędny. Odpowiada to utworzonej z jego właściwością ustawioną <xref:System.Windows.Data.RelativeSource> <xref:System.Windows.Data.RelativeSource.Mode%2A> na <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.|
|`typeName`|Wymagane w `FindAncestor` trybie. Nazwa typu, który wypełnia <xref:System.Windows.Data.RelativeSource.AncestorType%2A> właściwość.|
|`intLevel`|Opcjonalnie `FindAncestor` dla trybu. Poziom elementu nadrzędnego (patrząc w kierunku nadrzędności w drzewie logicznym).|

## <a name="remarks"></a>Uwagi

`{RelativeSource TemplatedParent}`użycie wiązania są kluczową techniką, która rozwiązuje się z większą koncepcją oddzielenia interfejsu użytkownika formantu i logiki formantu. Umożliwia tworzenie powiązań z wewnątrz definicji szablonu do elementu nadrzędnego używającego szablonu (tzn. do wystąpienia obiektu, do którego w czasie wykonywania szablon jest stosowany). W tym przypadku [rozszerzenie templatebinding znaczników](templatebinding-markup-extension.md) jest w rzeczywistości skrótem `{Binding RelativeSource={RelativeSource TemplatedParent}}`dla następującego wyrażenia wiązania: . `TemplateBinding`lub `{RelativeSource TemplatedParent}` użycia są istotne tylko w XAML, który definiuje szablon. Aby uzyskać więcej informacji, zobacz [Rozszerzenie znaczników powiązanie szablonu .](templatebinding-markup-extension.md)

`{RelativeSource FindAncestor}`jest używany głównie w szablonach kontroli lub przewidywalne kompozycje interfejsu użytkownika, w przypadkach, gdy formant jest zawsze oczekuje się w drzewie wizualnym określonego typu nadrzędnego. Na przykład elementy formantu `FindAncestor` elementów może używać użycia do powiązania z właściwości ich elementów nadrzędnego nadrzędnego. Lub elementy, które są częścią kompozycji `FindAncestor` kontroli w szablonie można użyć powiązań do elementów nadrzędnych w tej samej strukturze kompozycji.

W składni elementu obiektu `FindAncestor` dla trybu pokazanego w sekcjach składni XAML składnia drugiego `FindAncestor` elementu obiektu jest używana specjalnie dla trybu. `FindAncestor`wymaga <xref:System.Windows.Data.RelativeSource.AncestorType%2A> wartości. Należy ustawić <xref:System.Windows.Data.RelativeSource.AncestorType%2A> jako atrybut przy użyciu [x:Type Markup Extension](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) odwołania do typu element nadrzędny, aby wyszukać. Wartość <xref:System.Windows.Data.RelativeSource.AncestorType%2A> jest używana, gdy żądanie powiązania jest przetwarzane w czasie wykonywania.

Dla `FindAncestor` trybu, opcjonalna właściwość <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> może pomóc rozróżniać wyszukiwanie nadrzędnego w przypadkach, gdy istnieje prawdopodobnie więcej niż jeden element nadrzędny tego typu istniejących w drzewie elementów.

Aby uzyskać więcej informacji `FindAncestor` na temat <xref:System.Windows.Data.RelativeSource>korzystania z tego trybu, zobacz .

`{RelativeSource Self}`jest przydatne w scenariuszach, w których jedna właściwość wystąpienia powinna zależeć od wartości innej właściwości tego samego wystąpienia, a nie ma już ogólnej relacji właściwości zależności (takiej jak przymus) między tymi dwiema właściwościami. Chociaż rzadko istnieją dwie właściwości obiektu, takie jak, że wartości są dosłownie identyczne (i `Converter` są identycznie wpisane), można również zastosować parametr do powiązania, które ma `{RelativeSource Self}`, i użyć konwertera do konwersji między typami źródłowymi i docelowymi. Innym scenariuszem `{RelativeSource Self}` jest jako <xref:System.Windows.MultiDataTrigger>część .

Na przykład następujący kod XAML <xref:System.Windows.Shapes.Rectangle> definiuje element w taki sposób, <xref:System.Windows.FrameworkElement.Width%2A>że <xref:System.Windows.Shapes.Rectangle> bez względu na to, dla jakiej wartości jest wprowadzona wartość, jest zawsze kwadratem:`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`

`{RelativeSource PreviousData}`jest przydatne w szablonach danych lub w przypadkach, gdy powiązania używają kolekcji jako źródła danych. Można użyć `{RelativeSource PreviousData}` do podświetlenia relacji między sąsiednimi elementami danych w kolekcji. Technika pokrewna <xref:System.Windows.Data.MultiBinding> jest ustanowienie między bieżącymi i poprzednimi elementami w źródle danych i użyć konwertera na tym wiązanie, aby określić różnicę między dwoma elementami i ich właściwości.

W poniższym przykładzie <xref:System.Windows.Controls.TextBlock> pierwszy w szablonie elementów wyświetla bieżący numer. Drugie <xref:System.Windows.Controls.TextBlock> powiązanie <xref:System.Windows.Data.MultiBinding> jest nominalnie <xref:System.Windows.Data.Binding> ma dwa składniki: bieżący rekord i powiązanie, które celowo `{RelativeSource PreviousData}`używa poprzedniego rekordu danych za pomocą . Następnie konwerter na <xref:System.Windows.Data.MultiBinding> oblicza różnicę i zwraca ją do powiązania.

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

Opisujące powiązanie danych jako pojęcie nie jest tutaj omówione, zobacz [Omówienie powiązania danych](../../../desktop-wpf/data/data-binding-overview.md).

W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacji procesora XAML obsługa tego rozszerzenia znaczników jest definiowana <xref:System.Windows.Data.RelativeSource> przez klasę.

`RelativeSource`jest rozszerzeniem znaczników. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w XAML używają `{` znaków i `}` w składni atrybutów, czyli konwencji, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znaczników musi przetworzyć atrybut. Aby uzyskać więcej informacji, zobacz [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md).

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Data.Binding>
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Omówienie XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Omówienie powiązania danych](../../../desktop-wpf/data/data-binding-overview.md)
- [Przegląd Wiązanie deklaracji](../data/binding-declarations-overview.md)
- [x:Type — Rozszerzenie znaczników](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)
