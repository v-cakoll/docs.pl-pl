---
title: x:Type — Rozszerzenie znaczników
ms.date: 03/30/2017
f1_keywords:
- x:TypeExtension
- Type
- x:Type
- xType
- TypeExtension
helpviewer_keywords:
- x:Type markup extension [XAML Services]
- XAML [XAML Services], x:Type markup extension
- XAML [XAML Services], TargetType attribute
- TargetType attribute [XAML Services]
- Type markup extension in XAML [XAML Services]
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
ms.openlocfilehash: f75d4e30dc41bbce995e466466c96c1a2830949b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071361"
---
# <a name="xtype-markup-extension"></a>x:Type — Rozszerzenie znaczników

Dostarcza obiekt CLR, <xref:System.Type> który jest typem podstawowym dla określonego typu XAML.

## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML

```xaml
<object property="{x:Type prefix:typeNameValue}" .../>
```

## <a name="xaml-object-element-usage"></a>Użycie elementu obiektu języka XAML

```xaml
<x:Type TypeName="prefix:typeNameValue"/>
```

## <a name="xaml-values"></a>Wartości XAML

|||
|-|-|
|`prefix`|Element opcjonalny. Prefiks, który mapuje nieobezwykaną przestrzeń nazw XAML. Określenie prefiksu często nie jest konieczne. Zobacz uwagi.|
|`typeNameValue`|Wymagany. Nazwa typu, którą można rozwiązać z bieżącą domyślną przestrzenią nazw XAML; lub określony zamapowany `prefix` prefiks, jeśli jest podany.|

## <a name="remarks"></a>Uwagi

Rozszerzenie `x:Type` znaczników ma podobną `typeof()` funkcję do operatora `GetType` w języku C# lub operatora w programie Microsoft Visual Basic.

Rozszerzenie `x:Type` znaczników dostarcza zachowanie konwersji od ciągu dla właściwości, które przyjmują typ <xref:System.Type>. Dane wejściowe są typem XAML. Relacja między wejściowym typem XAML <xref:System.Type> a wyjściowym <xref:System.Type> modułem CLR polega na <xref:System.Xaml.XamlType> tym, że dane wyjściowe <xref:System.Windows.Markup.IXamlTypeResolver> są danymi wejściowymi <xref:System.Xaml.XamlType.UnderlyingType%2A> <xref:System.Xaml.XamlType>, po wyszukinięciu niezbędnego kontekstu schematu XAML i usługi świadczonej przez kontekst.

W usługach .NET XAML obsługa tego rozszerzenia znaczników <xref:System.Windows.Markup.TypeExtension> jest definiowana przez klasę.

W określonych implementacjach framework niektóre <xref:System.Type> właściwości, które przyjmują jako wartość, mogą bezpośrednio akceptować nazwę typu (wartość ciągu typu). `Name` Jednak implementowanie tego zachowania jest złożonym scenariuszem. Na przykład zobacz sekcję "Uwagi dotyczące użycia WPF", która jest następująca.

Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu podany `x:Type` po ciągu identyfikatora jest <xref:System.Windows.Markup.TypeExtension.TypeName%2A> przypisany <xref:System.Windows.Markup.TypeExtension> jako wartość podstawowej klasy rozszerzenia. W domyślnym kontekście schematu XAML dla usług .NET XAML Services, który jest oparty <xref:System.Reflection.MemberInfo.Name%2A> na typach CLR, <xref:System.Reflection.MemberInfo.Name%2A> wartość tego atrybutu jest albo żądanym typem, albo zawiera poprzedzony prefiksem nieobezwymionego mapowania obszaru nazw XAML.

Rozszerzenie `x:Type` znaczników może być używane w składni elementu obiektu. W takim przypadku określenie wartości <xref:System.Windows.Markup.TypeExtension.TypeName%2A> właściwości jest wymagane do prawidłowego zainicjowania rozszerzenia.

Rozszerzenie `x:Type` znaczników może być również używane jako atrybut pełne; jednak to użycie nie jest typowe:`<object property="{x:Type TypeName=typeNameValue}" .../>`

## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF

### <a name="default-xaml-namespace-and-type-mapping"></a>Domyślny obszar nazw XAML i mapowanie typów

Domyślna przestrzeń nazw XAML dla programowania WPF zawiera większość typów XAML, których potrzebujesz w typowych scenariuszach XAML; w związku z tym często można uniknąć prefiksów podczas odwoływania się do wartości typu XAML. Może być konieczne zamapowanie prefiksu, jeśli odwołujesz się do typu z zestawu niestandardowego lub dla typów, które istnieją w zestawie WPF, ale pochodzą z obszaru nazw CLR, który nie został zamapowany na domyślny obszar nazw XAML. Aby uzyskać więcej informacji na temat prefiksów, obszarów nazw XAML i mapowania obszarów nazw CLR, zobacz [XAML Obszary nazw i Mapowanie obszaru nazw dla WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).

### <a name="type-properties-that-support-typename-as-string"></a>Właściwości typu obsługujące nazwa typu jako ciąg znaków

WPF WPF obsługuje techniki, które umożliwiają określanie <xref:System.Type> wartości niektórych właściwości typu bez konieczności użycia rozszerzenia znaczników. `x:Type` Zamiast tego można określić wartość jako ciąg, który nazywa typ. Przykładami tego <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> są <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>i . Obsługa tego zachowania nie jest świadczona za pośrednictwem konwerterów typu lub rozszerzeń znaczników. Zamiast tego jest to zachowanie odroczenia <xref:System.Windows.FrameworkElementFactory>zaimplementowane za pośrednictwem .

Silverlight obsługuje podobną konwencję. W rzeczywistości program Silverlight obecnie `{x:Type}` nie obsługuje obsługi języka XAML `{x:Type}` i nie akceptuje użycia poza kilkoma okolicznościami, które są przeznaczone do obsługi migracji XAML WPF-Silverlight. W związku z tym zachowanie typename-as-string jest wbudowany do <xref:System.Type> wszystkich silverlight natywnej oceny właściwości, gdzie jest wartością.

## <a name="xaml-2009"></a>XAML 2009

XAML 2009 zapewnia dodatkową obsługę typów ogólnych i `x:TypeArguments` `x:Type` modyfikuje zachowanie funkcji i zapewnić tę obsługę.

- `x:TypeArguments`i skojarzony element obiektu dla ogólnego wystąpienia obiektu może znajdować się na elementach innych niż katalog główny. Aby uzyskać więcej informacji, zobacz sekcję "XAML 2009" [x:TypeArguments Directive](xtypearguments-directive.md).

- XAML 2009 obsługuje składnię określania ograniczenia typu ogólnego w znacznikach. Może to być `x:TypeArguments`używane `x:Type`przez , przez , lub przez dwie funkcje w połączeniu.

- Implementacja WPF XAML podczas przetwarzania XAML 2009 dla obciążenia również dodaje tę funkcję do <xref:System.Type>zachowania konwersji typu niejawnego dla niektórych właściwości frameworku, które używają typu .

W WPF WPF można użyć XAML 2009 funkcje, ale tylko dla luźne XAML (XAML, który nie jest skompilowany znaczników). Markup-skompilowany XAML dla WPF i BAML formie XAML obecnie nie obsługują XAML 2009 słów kluczowych i funkcji.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Style>
- [Tworzenie szablonów i stylów](../fundamentals/styles-templates-overview.md)
- [Omówienie XAML (WPF)](../fundamentals/xaml.md)
- [Rozszerzenia znacznikowania i WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
