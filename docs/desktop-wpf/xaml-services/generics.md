---
title: Typy ogólne w XAML
ms.date: 03/30/2017
helpviewer_keywords:
- generics [XAML Services]
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
ms.openlocfilehash: 9354f74b978652c36df28a91a6b9db5cfff4bb1e
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071739"
---
# <a name="generics-in-xaml"></a>Typy ogólne w XAML

Usługi .NET XAML zgodnie <xref:System.Xaml?displayProperty=fullName> z implementacji zapewnia obsługę przy użyciu typów ogólnego CLR. Ta obsługa obejmuje określanie ograniczeń generycznych jako argument typu i wymuszanie ograniczenia przez wywołanie odpowiedniej `Add` metody dla przypadków kolekcji rodzajowej. W tym temacie opisano aspekty używania typów ogólnych i odwoływania się do nich w języku XAML.

## <a name="xtypearguments"></a>x:Argumenty przed typem

`x:TypeArguments`jest dyrektywą zdefiniowaną przez język XAML. Gdy jest używany jako element członkowski typu XAML, który `x:TypeArguments` jest wspierany przez typ ogólny, przekazuje ograniczające argumenty typu ogólnego do konstruktora zapasowego. Aby uzyskać składnię odwołań, która odnosi się `x:TypeArguments`do korzystania z usług .NET XAML , która zawiera przykłady składni, zobacz [x:TypeArguments Directive](xtypearguments-directive.md).

Ponieważ `x:TypeArguments` przyjmuje ciąg i ma kopię zapasową konwertera typów, jest zazwyczaj zadeklarowany w użyciu XAML jako atrybut.

W strumieniu węzła XAML `x:TypeArguments` informacje zadeklarowane <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> przez `StartObject` można uzyskać z pozycji w strumieniu węzła. Zwracana <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> wartość jest listą <xref:System.Xaml.XamlType> wartości. Określenie, czy typ XAML reprezentuje typ ogólny, <xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>można dokonać, wywołując polecenie .

## <a name="rules-and-syntax-conventions-for-generics-in-xaml"></a>Reguły i konwencje składni dla generycznych w języku XAML

W języku XAML typ ogólny musi być zawsze reprezentowany jako ograniczony rodzajowy. Nieograniczony ogólny nigdy nie jest obecny w systemie typu XAML lub strumieniu węzła XAML i nie może być reprezentowany w znacznikach XAML. W składni atrybutu XAML można odwoływać się do ogólnego formatu w przypadkach, gdy `x:TypeArguments`jest to `x:Type` ograniczenie typu zagnieżdżonego ogólnego, do którego odwołuje się rodzajowy, lub w przypadkach, gdy dostarcza odwołanie do typu CLR dla typu ogólnego. Odwoływanie się do generycznych jest obsługiwane za pośrednictwem klasy zdefiniowanej <xref:System.Xaml.Schema.XamlTypeTypeConverter> przez usługi .NET XAML Services.

Formularz składni atrybutu XAML włączony <xref:System.Xaml.Schema.XamlTypeTypeConverter> przez zmianę typowej konwencji składni MSIL / CLR, która używa nawiasów kątowych dla typów i ograniczeń generycznych, a zamiast tego zastępuje nawiasy dla kontenera ograniczeń. Na przykład zobacz [x:Dyrektywa o typach.](xtypearguments-directive.md)

## <a name="generics-and-xaml-2009-features"></a>Funkcje ogólne i XAML 2009

Jeśli używasz XAML 2009 zamiast mapowania typów podstawowych CLR w celu uzyskania typów XAML dla pierwotnych języków wspólnych, można użyć `x:TypeArguments` [xaml 2009 wbudowanych typów](types-for-primitives.md) jako elementy informacji w . Na przykład można zadeklarować następujące (mapowania prefiksów nie są wyświetlane, ale `x` jest to obszar nazw XAML języka XAML dla XAML 2009):

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

## <a name="generics-support-in-wpf"></a>Obsługa leków generycznych w wyw.

Dla XAML 2006 użytkowania podczas specjalnie kierowania WPF [X:Class](xclass-directive.md) muszą być `x:TypeArguments`również dostępne na ten sam element co , a ten element musi być elementem głównym w dokumencie XAML. Element główny musi być mapowana do typu ogólnego z co najmniej jednym argumentem typu. Może to być na przykład <xref:System.Windows.Navigation.PageFunction%601>.

Możliwe obejścia do obsługi użycia ogólnego obejmują definiowanie niestandardowego rozszerzenia znaczników, które może zwracać typy ogólne lub dostarczanie definicji klasy zawijania, która pochodzi od typu ogólnego, ale spłaszcza ograniczenie ogólne w definicji własnej klasy.

W WPF można używać funkcji XAML 2009 wraz z `x:TypeArguments`, ale tylko dla luźnego XAML (XAML, który nie jest skompilowany znaczników). Markup-skompilowany XAML dla WPF i BAML formie XAML obecnie nie obsługują XAML 2009 słów kluczowych i funkcji.

Niestandardowe przepływy pracy w programie Windows Workflow Foundation for .NET Framework 3.5 nie obsługują ogólnego użycia XAML.

## <a name="see-also"></a>Zobacz też

- [x:TypeArguments — dyrektywa](xtypearguments-directive.md)
- [x:Class — dyrektywa](xclass-directive.md)
- [Typy wbudowane dla wspólnych elementów podstawowych języka XAML](types-for-primitives.md)
