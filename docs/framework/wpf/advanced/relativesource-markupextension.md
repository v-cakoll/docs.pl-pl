---
title: RelativeSource MarkupExtension
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 47117d684a981f31e22cf513fc78e1e2dda73f8a
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141265"
---
# <a name="relativesource-markupextension"></a>RelativeSource MarkupExtension

Określa właściwości źródła <xref:System.Windows.Data.RelativeSource> powiązania, które ma być używane w [rozszerzeniu Binding Markup](binding-markup-extension.md)lub podczas ustawiania <xref:System.Windows.Data.Binding.RelativeSource%2A> właściwości <xref:System.Windows.Data.Binding> elementu ustanowionego w języku XAML.

## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" ... />
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a>Użycie atrybutu języka XAML (zagnieżdżonego w rozszerzeniu Binding)

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" ... />
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
|`modeEnumValue`|Jeden z poniższych programów:<br /><br /> -Token `Self`ciągu; odnosi się do <xref:System.Windows.Data.RelativeSource> elementu as utworzonego z <xref:System.Windows.Data.RelativeSource.Mode%2A> właściwością ustawioną na <xref:System.Windows.Data.RelativeSourceMode.Self>.<br />-Token `TemplatedParent`ciągu; odnosi się do <xref:System.Windows.Data.RelativeSource> elementu as utworzonego z <xref:System.Windows.Data.RelativeSource.Mode%2A> właściwością ustawioną na <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.<br />-Token `PreviousData`ciągu; odnosi się do <xref:System.Windows.Data.RelativeSource> elementu as utworzonego z <xref:System.Windows.Data.RelativeSource.Mode%2A> właściwością ustawioną na <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.<br />-Zobacz poniżej, aby uzyskać `FindAncestor` informacje o trybie.|
|`FindAncestor`|Token `FindAncestor`ciągu. Użycie tego tokenu spowoduje przejście do trybu, `RelativeSource` w którym określa typ elementu nadrzędnego i opcjonalnie poziomu nadrzędnego. Odnosi się to <xref:System.Windows.Data.RelativeSource> tak, jakby został utworzony <xref:System.Windows.Data.RelativeSource.Mode%2A> z właściwością <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>ustawioną na.|
|`typeName`|Wymagane dla `FindAncestor` trybu. Nazwa typu, który wypełnia <xref:System.Windows.Data.RelativeSource.AncestorType%2A> właściwość.|
|`intLevel`|Opcjonalne dla `FindAncestor` trybu. Poziom elementu nadrzędnego (patrząc w kierunku nadrzędności w drzewie logicznym).|

## <a name="remarks"></a>Uwagi

`{RelativeSource TemplatedParent}`Użycie powiązań jest kluczową techniką, która eliminuje większą koncepcję rozdzielania interfejsu użytkownika kontrolki i logiki kontrolki. Umożliwia tworzenie powiązań z wewnątrz definicji szablonu do elementu nadrzędnego używającego szablonu (tzn. do wystąpienia obiektu, do którego w czasie wykonywania szablon jest stosowany). W takim przypadku rozszerzenie " [TemplateBinding Markup](templatebinding-markup-extension.md) " jest w istocie skrót dla następującego wyrażenia powiązania: `{Binding RelativeSource={RelativeSource TemplatedParent}}`. `TemplateBinding`lub `{RelativeSource TemplatedParent}` użycia są odpowiednie tylko w kodzie XAML, który definiuje szablon. Aby uzyskać więcej informacji, zobacz [TemplateBinding Markup Extension](templatebinding-markup-extension.md).

`{RelativeSource FindAncestor}`jest używany głównie w szablonach kontroli lub przewidywalnym samoobsługowym kompozycjom interfejsu użytkownika, w przypadkach, gdy kontrolka zawsze powinna znajdować się w drzewie wizualnym określonego typu elementu nadrzędnego. Na przykład elementy kontrolki elementów mogą używać `FindAncestor` użycia do powiązania z właściwościami elementów nadrzędnych elementu nadrzędnego. Lub elementy, które są częścią kompozycji formantu w szablonie, mogą używać `FindAncestor` powiązań z elementami nadrzędnymi w tej samej strukturze kompozycji.

W składni elementu obiektu dla `FindAncestor` trybu pokazanego w sekcjach SKŁADNI języka XAML, składnia drugiego elementu obiektu jest używana do `FindAncestor` trybu. `FindAncestor`tryb wymaga <xref:System.Windows.Data.RelativeSource.AncestorType%2A> wartości. Należy ustawić <xref:System.Windows.Data.RelativeSource.AncestorType%2A> jako atrybut, używając [x:Type — znacznika](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) odwołania do typu elementu nadrzędnego, który ma zostać wyszukany. Wartość <xref:System.Windows.Data.RelativeSource.AncestorType%2A> jest używana, gdy żądanie powiązania jest przetwarzane w czasie wykonywania.

W `FindAncestor` przypadku trybu Właściwość <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> opcjonalna może pomóc w odróżnieniu wyszukiwania nadrzędnego w przypadkach, gdy istnieje prawdopodobnie więcej niż jeden element nadrzędny tego typu istniejący w drzewie elementów.

Aby uzyskać więcej informacji na temat używania `FindAncestor` trybu, zobacz. <xref:System.Windows.Data.RelativeSource>

`{RelativeSource Self}`jest przydatne w scenariuszach, w których jedna Właściwość wystąpienia powinna zależeć od wartości innej właściwości tego samego wystąpienia, a żadna nie ogólna relacja między właściwościami zależności (na przykład przymusu) istnieje już między tymi dwiema właściwościami. Chociaż jest to rzadki, że dwie właściwości istnieją w obiekcie, tak że wartości są identyczne (i są identyczne), można również zastosować `Converter` parametr do powiązania, które ma `{RelativeSource Self}`, i użyć konwertera do konwersji między typami źródłowymi i docelowymi. Inny scenariusz dla `{RelativeSource Self}` jest jako część elementu <xref:System.Windows.MultiDataTrigger>.

Na przykład poniższy kod XAML definiuje <xref:System.Windows.Shapes.Rectangle> element <xref:System.Windows.FrameworkElement.Width%2A>, który nie ma znaczenia wartości, <xref:System.Windows.Shapes.Rectangle> jest zawsze kwadratem:`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`

`{RelativeSource PreviousData}`jest przydatne w szablonach danych lub w przypadkach, gdy powiązania używają kolekcji jako źródła danych. Możesz użyć `{RelativeSource PreviousData}` , aby wyróżnić relacje między sąsiednimi elementami danych w kolekcji. Pokrewna Technika polega na ustanowieniu <xref:System.Windows.Data.MultiBinding> między bieżącymi i poprzednimi elementami w źródle danych i wykorzystaniu konwertera dla tego powiązania, aby określić różnicę między dwoma elementami i ich właściwościami.

W poniższym przykładzie pierwszy <xref:System.Windows.Controls.TextBlock> w szablonie Items wyświetla bieżącą liczbę. Drugie <xref:System.Windows.Controls.TextBlock> powiązanie jest <xref:System.Windows.Data.MultiBinding> , które w sposób nominalny ma dwa <xref:System.Windows.Data.Binding> składniki: bieżący rekord i powiązanie, które w sposób celowy używa poprzedniego rekordu danych przy użyciu. `{RelativeSource PreviousData}` Następnie konwerter <xref:System.Windows.Data.MultiBinding> oblicza różnicę i zwraca go do powiązania.

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
</ListBox>
```

Opisywanie powiązania danych jako koncepcji nie jest tutaj omówione, zobacz temat [powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md).

W implementacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesora XAML obsługa tego rozszerzenia znacznika jest definiowana przez <xref:System.Windows.Data.RelativeSource> klasę.

`RelativeSource`jest rozszerzeniem znaczników. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w języku XAML używają `{` znaków `}` i w ich składni atrybutów, która jest konwencją, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybut. Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Data.Binding>
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Omówienie XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Przegląd powiązań danych](../../../desktop-wpf/data/data-binding-overview.md)
- [Przegląd Wiązanie deklaracji](../data/binding-declarations-overview.md)
- [x:Type — Rozszerzenie znaczników](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)
