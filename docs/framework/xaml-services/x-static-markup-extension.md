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
ms.openlocfilehash: bf94f1d61ee3080c9d3582e55e0695b269801c80
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733361"
---
# <a name="xstatic-markup-extension"></a>x:Static — Rozszerzenie znaczników
Odwołuje się do dowolnej jednostki kodu statycznej przez wartość, która jest zdefiniowana w sposób zgodny z Common Language Specification (CLS). Właściwość statyczna, do której jest przywoływana, może służyć do podania wartości właściwości w języku XAML.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
| | |  
|-|-|  
|`prefix`|Opcjonalny. Prefiks, który odwołuje się do zamapowanej, innej niż domyślnej przestrzeni nazw XAML. `prefix` jest jawnie wyświetlana w użyciu, ponieważ rzadko odwołują się do właściwości statycznych, które pochodzą z domyślnej przestrzeni nazw XAML. Zobacz uwagi.|  
|`typeName`|Wymagany. Nazwa typu, który definiuje żądany statyczny element członkowski.|  
|`staticMemberName`|Wymagany. Nazwa żądanego statycznego elementu członkowskiego wartości (stałej, statycznej właściwości, pola lub wartości wyliczenia).|  
  
## <a name="remarks"></a>Uwagi  

Obiekt kodu, do którego istnieje odwołanie, musi mieć jedną z następujących wartości:  
  
- Stała  
- Właściwość statyczna  
- Pole  
- Wartość wyliczenia

Określenie innych jednostek kodu, takich jak niestatyczna właściwość, powoduje błąd czasu kompilacji, jeśli kod XAML jest kompilowany, lub wyjątek analizy czasu ładowania XAML.  

Można wprowadzić `x:Static` odwołań do pól statycznych lub właściwości, które nie znajdują się w domyślnej przestrzeni nazw XAML dla bieżącego dokumentu XAML; jednak wymaga to mapowania prefiksów. Przestrzenie nazw XAML są prawie zawsze definiowane w elemencie głównym dokumentu XAML.  

Operacje wyszukiwania dla właściwości statycznych mogą być wykonywane przez .NET Framework usług XAML i ich czytników XAML i autorów XAML, gdy są uruchamiane przy użyciu domyślnego kontekstu schematu języka XAML. Ten kontekst schematu XAML może używać odbicia środowiska CLR w celu dostarczenia wymaganych wartości statycznych dla konstruowania grafu obiektów. Określona `typeName` jest w rzeczywistości nazwą typu XAML, a nie nazwą typu CLR, chociaż są one zasadniczo takie same, jak w przypadku korzystania z domyślnego kontekstu schematu XAML lub w przypadku używania wszystkich istniejących platform implementujących język XAML opartych na środowisku CLR.  

Należy zachować ostrożność podczas wprowadzania `x:Static` odwołań, które nie są bezpośrednio typem wartości właściwości. W sekwencji przetwarzania XAML podane wartości z rozszerzenia znacznika nie wywołują dodatkowej konwersji wartości. Jest to prawdziwe nawet wtedy, gdy odwołanie `x:Static` tworzy ciąg tekstowy, a konwersja wartości dla wartości atrybutów na podstawie ciągu tekstowego zwykle występuje dla tego konkretnego elementu członkowskiego lub dla jakichkolwiek wartości elementów członkowskich zwracanego typu.  

Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu podany po ciągu identyfikatora `x:Static` jest przypisywany jako wartość <xref:System.Windows.Markup.StaticExtension.Member%2A> źródłowej klasy rozszerzenia <xref:System.Windows.Markup.StaticExtension>.  

Istnieją dwa inne użycia kodu XAML, które są technicznie możliwe. Jednak te użycia są mniej typowe, ponieważ nie są one niepotrzebnie pełne:  

1. Składnia elementu obiektu.

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

2. Składnia atrybutu z jawną właściwością elementu członkowskiego dla ciągu inicjującego.

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

W implementacji usług XAML .NET Framework obsługa tego rozszerzenia znacznika jest definiowana przez klasę <xref:System.Windows.Markup.StaticExtension>.  

`x:Static` to rozszerzenie znaczników. Wszystkie rozszerzenia znaczników w języku XAML używają znaków `{` i `}` w ich składni atrybutów, która jest konwencją, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znacznika musi zawierać wartość. Aby uzyskać więcej informacji na temat rozszerzeń znaczników, zobacz [znaczniki rozszerzeń dla języka XAML — Omówienie](markup-extensions-for-xaml-overview.md).  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF  
 Domyślna przestrzeń nazw języka XAML, która jest używana w programowaniu WPF, nie zawiera wielu użytecznych właściwości statycznych i większość przydatnych właściwości statycznych obsługuje takie jak konwertery typów, które ułatwiają użycie bez konieczności `{x:Static}`. W przypadku właściwości statycznych należy zmapować prefiks dla przestrzeni nazw XAML, jeśli jest spełniony jeden z następujących warunków:  
  
- Odwołujesz się do typu, który istnieje w WPF, ale nie jest częścią domyślnej przestrzeni nazw XAML dla WPF (`http://schemas.microsoft.com/winfx/2006/xaml/presentation`). Jest to dość typowy scenariusz korzystania z `x:Static`. Na przykład można użyć odwołania `x:Static` z mapowaniem przestrzeni nazw XAML do <xref:System> przestrzeni nazw środowiska CLR i zestawu Mscorlib, aby odwołać się do właściwości statycznych klasy <xref:System.Environment>.  
  
- Odwołujesz się do typu z niestandardowego zestawu.  
  
- Odwołujesz się do typu, który istnieje w zestawie WPF, ale ten typ znajduje się w przestrzeni nazw CLR, która nie została zmapowana do domyślnej przestrzeni nazw języka XAML WPF. Mapowanie przestrzeni nazw CLR do domyślnej przestrzeni nazw XAML dla WPF jest wykonywane przez definicje w różnych zestawach WPF (Aby uzyskać więcej informacji na temat tego pojęcia, zobacz [przestrzenie nazw XAML i mapowanie przestrzeni nazw dla WPF XAML](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)). Niemapowane przestrzenie nazw środowiska CLR mogą istnieć, jeśli przestrzeń nazw środowiska CLR składa się głównie z definicji klas, które nie są zwykle przeznaczone dla języka XAML, takich jak <xref:System.Windows.Threading>.  
  
 Aby uzyskać więcej informacji na temat używania prefiksów i przestrzeni nazw XAML dla WPF, zobacz [przestrzenie nazw XAML i mapowanie przestrzeni nazw dla języka XAML WPF](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz także

- [x:Type, rozszerzenie znaczników](x-type-markup-extension.md)
- [Typy migrowane z WPF do System.Xaml](types-migrated-from-wpf-to-system-xaml.md)
