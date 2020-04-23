---
title: x:Static — Rozszerzenie znaczników
ms.date: 03/30/2017
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
ms.openlocfilehash: fb9ee6807135f17fd9e0c799533bba28b369ebe2
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072026"
---
# <a name="xstatic-markup-extension"></a>x:Static — Rozszerzenie znaczników

Odwołuje się do każdej statycznej jednostki kodu według wartości, która jest zdefiniowana w sposób zgodny ze specyfikacją języka wspólnego (CLS). Właściwość statyczna, do którego się odwołuje, może służyć do podania wartości właściwości w języku XAML.

## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML

```xaml
<object property="{x:Static prefix:typeName.staticMemberName}" .../>
```

## <a name="xaml-values"></a>Wartości XAML

| | |
|-|-|
|`prefix`|Element opcjonalny. Prefiks, który odwołuje się do zamapowane, nie-domyślny obszar nazw XAML. `prefix`jest jawnie wyświetlany w użyciu, ponieważ rzadko odwołuje się do właściwości statycznych, które pochodzą z domyślnej przestrzeni nazw XAML. Zobacz uwagi.|
|`typeName`|Wymagany. Nazwa typu, który definiuje żądany element członkowski statyczny.|
|`staticMemberName`|Wymagany. Nazwa żądanego elementu członkowskiego wartości statycznej (stała, właściwość statyczna, pole lub wartość wyliczenia).|

## <a name="remarks"></a>Uwagi

Encja kodu, do której się odwołuje, musi być jedną z następujących czynności:

- Stała
- Właściwość statyczna
- Pole
- Wartość wyliczenia

Określanie innej jednostki kodu, takiej jak właściwość niestatyczna, powoduje błąd w czasie kompilacji, jeśli znaczniki XAML są skompilowane lub wyjątek analizy czasu ładowania XAML.

Można wprowadzać odwołania do pól statycznych lub właściwości, które nie znajdują się `x:Static` w domyślnej przestrzeni nazw XAML dla bieżącego dokumentu XAML; Jednak wymaga to mapowania prefiksu. Przestrzenie nazw XAML są prawie zawsze zdefiniowane w elemencie głównym dokumentu XAML.

Operacje wyszukiwania właściwości statycznych mogą być wykonywane przez usługi .NET XAML Services i ich czytniki XAML i moduły zapisujących XAML, gdy są uruchomione z domyślnym kontekstem schematu XAML. Ten kontekst schematu XAML można użyć odbicia CLR, aby zapewnić niezbędne wartości statyczne dla konstrukcji wykresu obiektu. Określony `typeName` jest w rzeczywistości nazwa typu XAML, a nie nazwa typu CLR, chociaż są one zasadniczo taką samą nazwę podczas korzystania z domyślnego kontekstu schematu XAML lub podczas korzystania z wszystkich istniejących platform implementujących XAML oparte na programie CLR.

Należy zachować `x:Static` ostrożność podczas dokonywania odwołań, które nie są bezpośrednio typu wartości właściwości. W sekwencji przetwarzania XAML podane wartości z rozszerzenia znaczników nie wywołać konwersji wartości dodatkowych. Jest to prawdą, `x:Static` nawet jeśli odwołanie tworzy ciąg tekstowy, a konwersja wartości dla wartości atrybutów na podstawie ciągu tekstowego zazwyczaj występuje dla tego określonego elementu członkowskiego lub dla dowolnych wartości członkowskich typu zwracanego.

Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu podany `x:Static` po ciągu identyfikatora jest <xref:System.Windows.Markup.StaticExtension.Member%2A> przypisany <xref:System.Windows.Markup.StaticExtension> jako wartość podstawowej klasy rozszerzenia.

Istnieją dwa inne użycia XAML, które są technicznie możliwe. Jednak te użycia są mniej powszechne, ponieważ są one niepotrzebnie pełne:

01. Składnia elementu obiektu.

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

02. Składnia atrybutu z jawną właściwością Member dla ciągu inicjowania.

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

W implementacji usług .NET XAML obsługa tego rozszerzenia <xref:System.Windows.Markup.StaticExtension> znaczników jest definiowana przez klasę.

`x:Static`jest rozszerzeniem znaczników. Wszystkie rozszerzenia znaczników w XAML używają `{` znaków i `}` w składni atrybutów, czyli konwencji, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znaczników musi zawierać wartość. Aby uzyskać więcej informacji na temat rozszerzeń znaczników, zobacz [Rozszerzenia znaczników dla XAML Overview](markup-extensions-overview.md).

## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF

Domyślna przestrzeń nazw XAML używana do programowania WPF nie zawiera wielu przydatnych właściwości statycznych, a większość przydatnych właściwości statycznych `{x:Static}` ma obsługę, taką jak konwertery typów, które ułatwiają użycie bez konieczności. W przypadku właściwości statycznych należy zamapować prefiks obszaru nazw XAML, jeśli spełniony jest jeden z następujących elementów:

- Odwołujesz się do typu, który istnieje w WPF, ale nie jest częścią`http://schemas.microsoft.com/winfx/2006/xaml/presentation`domyślnej przestrzeni nazw XAML dla WPF ( ). Jest to dość typowy scenariusz `x:Static`użycia programu . Na przykład można użyć `x:Static` odwołania z mapowania przestrzeni nazw <xref:System> XAML do obszaru nazw CLR i zestawu mscorlib w celu odwołania się do właściwości statycznych <xref:System.Environment> klasy.

- Odwołujesz się do typu z zestawu niestandardowego.

- Odwołujesz się do typu, który istnieje w WPF zestawu, ale ten typ znajduje się w obszarze nazw CLR, który nie został zamapowany do części domyślnej przestrzeni nazw XAML WPF. Mapowanie obszarów nazw CLR do domyślnej przestrzeni nazw XAML dla WPF jest wykonywane przez definicje w różnych zestawach WPF (aby uzyskać więcej informacji na temat tej koncepcji, zobacz [XAML obszary nazw i Mapowanie obszaru nazw dla WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)). Niemapowane przestrzenie nazw CLR mogą istnieć, jeśli obszar nazw CLR składa się głównie z definicji <xref:System.Windows.Threading>klas, które zazwyczaj nie są przeznaczone dla XAML, takich jak .

Aby uzyskać więcej informacji na temat używania prefiksów i obszarów nazw XAML dla WPF, zobacz [XAML Obszary nazw i Mapowanie obszaru nazw dla WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).

## <a name="see-also"></a>Zobacz też

- [x:Type — Rozszerzenie znaczników](xtype-markup-extension.md)
- [Typy migrowane z WPF do System.Xaml](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
