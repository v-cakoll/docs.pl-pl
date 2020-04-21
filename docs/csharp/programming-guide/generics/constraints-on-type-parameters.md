---
title: Ograniczenia dotyczące parametrów typu — Przewodnik programowania języka C#
ms.date: 04/12/2018
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.openlocfilehash: 0035f7d8aa862b4bd1b09a6f122a89786a6e295b
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738250"
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>Ograniczenia dotyczące parametrów typu (Przewodnik programowania języka C#)

Ograniczenia informują kompilator o możliwościach, które musi mieć argument typu. Bez żadnych ograniczeń argument typu może być dowolnego typu. Kompilator może przyjąć tylko <xref:System.Object?displayProperty=nameWithType>członków , który jest ostateczną klasą podstawową dla dowolnego typu .NET. Aby uzyskać więcej informacji, zobacz [Dlaczego należy używać ograniczeń](#why-use-constraints). Jeśli kod klienta używa typu, który nie spełnia ograniczenia, kompilator generuje błąd. Ograniczenia są określone przy `where` użyciu kontekstowego słowa kluczowego. W poniższej tabeli wymieniono siedem typów ograniczeń:

|Ograniczenie|Opis|
|----------------|-----------------|
|`where T : struct`|Argument typu musi być typem wartości nienastępulnej. Aby uzyskać informacje o typach wartości, które można do wartości null, zobacz [Typy wartości możliwe do wartości null](../../language-reference/builtin-types/nullable-value-types.md). Ponieważ wszystkie typy wartości mają dostępne `struct` bez parametrów `new()` konstruktora, ograniczenie `new()` implikuje ograniczenie i nie można połączyć z ograniczeniem. Nie można połączyć `struct` ograniczenia `unmanaged` z ograniczeniem.|
|`where T : class`|Argument typu musi być typem odwołania. To ograniczenie dotyczy również dowolnej klasy, interfejsu, delegata lub typu tablicy. W kontekście nullable w języku C# 8.0 lub nowszym, `T` musi być typem odwołania niepodjętego do wartości null. |
|`where T : class?`|Argument typu musi być typem odwołania, można anulować lub nie można anulować. To ograniczenie dotyczy również dowolnej klasy, interfejsu, delegata lub typu tablicy.|
|`where T : notnull`|Argument typu musi być typem nienastępalnym. Argument może być typu odwołania niepodwymiernego w języku C# 8.0 lub nowszym lub typu wartości nienastępu. |
|`where T : unmanaged`|Argument typu musi być [typem niezarządzanym](../../language-reference/builtin-types/unmanaged-types.md)bez wartości null. Ograniczenie `unmanaged` implikuje `struct` ograniczenie i nie można ich `struct` łączyć z ograniczeniami lub ograniczeniami. `new()`|
|`where T : new()`|Argument typu musi mieć publiczny konstruktor bez parametrów. W połączeniu z innymi `new()` ograniczeniami, ograniczenie musi być określony jako ostatni. Ograniczenia `new()` nie można łączyć `struct` z `unmanaged` ograniczeniami i ograniczeniami.|
|`where T :`*nazwa klasy podstawowej>\<*|Argument typu musi być lub pochodzić z określonej klasy podstawowej. W kontekście nullable w języku C# 8.0 i nowszych, `T` musi być typu odwołania nienastępne null pochodną określonej klasy podstawowej. |
|`where T :`*nazwa klasy podstawowej>? \<*|Argument typu musi być lub pochodzić z określonej klasy podstawowej. W kontekście nullable w języku C# 8.0 i nowszych, `T` może być typu nullable lub niedopuszczania do null pochodzi od określonej klasy podstawowej. |
|`where T :`>nazwa interfejsu * \<*|Argument typu musi być lub implementować określony interfejs. Można określić wiele ograniczeń interfejsu. Interfejs ograniczający może być również ogólny. W kontekście nullable w języku C# 8.0 i nowszych, musi być typu niedopuszczania do wartości null, `T` który implementuje określony interfejs.|
|`where T :`nazwa interfejsu>? * \<*|Argument typu musi być lub implementować określony interfejs. Można określić wiele ograniczeń interfejsu. Interfejs ograniczający może być również ogólny. W kontekście nullable w języku C# `T` 8.0, może być typu odwołania nullable, typu odwołania niepodjętego do null lub typu wartości. `T`może nie być typem wartości możliwej do wartości null.|
|`where T : U`|Podany argument `T` typu musi być lub pochodzić `U`z argumentu dostarczonego dla . W kontekście nullable, jeśli `U` jest typem `T` odwołania niepodjętego do wartości null, musi być typem odwołania niepodjętego do null. Jeśli `U` jest typem odwołania `T` do nullable, może być nullable lub nie nullable. |

## <a name="why-use-constraints"></a>Dlaczego warto korzystać z ograniczeń

Ograniczenia określają możliwości i oczekiwania parametru typu. Deklarowanie tych ograniczeń oznacza, że można użyć operacji i wywołań metody typu ograniczającego. Jeśli klasa lub metoda rodzajowa używa dowolnej operacji na ogólne elementy członkowskie <xref:System.Object?displayProperty=nameWithType>poza proste przypisanie lub wywołanie żadnych metod nie jest obsługiwany przez , trzeba będzie zastosować ograniczenia do parametru typu. Na przykład ograniczenie klasy podstawowej informuje kompilator, że tylko obiekty tego typu lub pochodne tego typu będą używane jako argumenty typu. Gdy kompilator ma tę gwarancję, można zezwolić na metody tego typu, które mają być wywoływane w klasie rodzajowej. Poniższy przykład kodu pokazuje funkcje, które `GenericList<T>` można dodać do klasy (w [wprowadzenie do generics)](../../../standard/generics/index.md)stosując ograniczenie klasy podstawowej.

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#9)]

Ograniczenie umożliwia klasy ogólnej do `Employee.Name` korzystania z właściwości. Ograniczenie określa, że wszystkie `T` elementy typu są gwarantowane jako `Employee` obiekt lub `Employee`obiekt, który dziedziczy z .

Wiele ograniczeń można zastosować do tego samego parametru typu, a same ograniczenia mogą być typami ogólnymi w następujący sposób:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#10)]

Podczas stosowania `where T : class` ograniczenia, należy `==` `!=` unikać i operatorów na parametr typu, ponieważ te operatory będą testować tylko tożsamości odwołania, a nie dla równości wartości. To zachowanie występuje, nawet jeśli te operatory są przeciążone w typie, który jest używany jako argument. Poniższy kod ilustruje ten punkt; dane wyjściowe jest <xref:System.String> false, mimo `==` że klasa przeciąża operatora.

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#11)]

Kompilator wie `T` tylko, że jest typem odwołania w czasie kompilacji i musi używać domyślnych operatorów, które są prawidłowe dla wszystkich typów odwołań. Jeśli należy przetestować pod kątem równości wartości, `where T : IEquatable<T>` zalecanym sposobem jest również zastosowanie lub `where T : IComparable<T>` ograniczenie i zaimplementowanie interfejsu w dowolnej klasie, która będzie używana do konstruowania klasy ogólnej.

## <a name="constraining-multiple-parameters"></a>Ograniczanie wielu parametrów

Ograniczenia można zastosować do wielu parametrów i wielu ograniczeń do pojedynczego parametru, jak pokazano w poniższym przykładzie:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a>Parametry typu bez ograniczeń

 Parametry typu, które nie mają żadnych ograniczeń, takie jak T w klasie `SampleClass<T>{}`publicznej, są nazywane parametrami typu niezwiązanych. Parametry typu niezwiązany mają następujące reguły:

- I `!=` `==` operatorów nie można używać, ponieważ nie ma gwarancji, że argument typu betonu będzie obsługiwać tych operatorów.
- Mogą one być konwertowane do i z `System.Object` lub jawnie konwertowane na dowolny typ interfejsu.
- Można je porównać z [wartością null](../../language-reference/keywords/null.md). Jeśli parametr niezwiązany `null`jest porównywany do , porównanie zawsze zwróci false, jeśli argument typu jest typem wartości.

## <a name="type-parameters-as-constraints"></a>Parametry typu jako wiązania

Użycie parametru typu ogólnego jako ograniczenia jest przydatne, gdy funkcja elementu członkowskiego z własnym parametrem typu musi ograniczyć ten parametr do parametru typu typu zawierającego, jak pokazano w poniższym przykładzie:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#13)]

W poprzednim przykładzie `T` jest ograniczenie typu w `Add` kontekście metody i parametr typu nieograniczonego `List` w kontekście klasy.

Parametry typu mogą być również używane jako wiązania w definicjach klas ogólnych. Parametr typu musi być zadeklarowany w nawiasach kątowych wraz z innymi parametrami typu:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#14)]

Przydatność parametrów typu jako ograniczenia z klasami ogólnymi jest ograniczona, ponieważ kompilator `System.Object`nie może zakładać nic o parametrze typu, z wyjątkiem tego, że pochodzi on od . Użyj parametrów typu jako ograniczeń klas ogólnych w scenariuszach, w których chcesz wymusić relację dziedziczenia między dwoma parametrami typu.

## <a name="notnull-constraint"></a>Ograniczenie NotNull

Począwszy od języka C# 8.0 w kontekście nullable, można użyć `notnull` ograniczenia, aby określić, że argument typu musi być typu wartości nienastępujących do wartości null lub typu odwołania niepodjęwalnego. Ograniczenie `notnull` może być używane `nullable enable` tylko w kontekście. Kompilator generuje ostrzeżenie, jeśli `notnull` dodasz ograniczenie w kontekście nullable nieświadomy.

W przeciwieństwie do innych ograniczeń, gdy `notnull` argument typu narusza ograniczenie, kompilator generuje ostrzeżenie, gdy ten kod jest kompilowany w `nullable enable` kontekście. Jeśli kod jest kompilowany w kontekście nullable nieświadomy, kompilator nie generuje żadnych ostrzeżeń lub błędów.

Począwszy od języka C# 8.0 `class` w kontekście nullable, ograniczenie określa, że argument typu musi być typu odwołania nie można anulować. W kontekście nullable, gdy parametr typu jest typem odwołania do wartości null, kompilator generuje ostrzeżenie.

## <a name="unmanaged-constraint"></a>Ograniczenie niezarządzane

Począwszy od języka C# 7.3, można użyć `unmanaged` ograniczenia, aby określić, że parametr typu musi być [typem niezarządzanym bez](../../language-reference/builtin-types/unmanaged-types.md)wartości null. Ograniczenie `unmanaged` umożliwia pisanie procedur wielokrotnegoużytnia do pracy z typami, które mogą być manipulowane jako bloki pamięci, jak pokazano w poniższym przykładzie:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#15)]

Poprzednia metoda musi być skompilowana w `unsafe` `sizeof` kontekście, ponieważ używa operatora na typ nie wiadomo, że jest typem wbudowanym. Bez `unmanaged` ograniczenia `sizeof` operator jest niedostępny.

Ograniczenie `unmanaged` implikuje `struct` ograniczenie i nie można go połączyć. Ponieważ `struct` ograniczenie implikuje `new()` ograniczenie, `unmanaged` ograniczenia nie można `new()` również łączyć z ograniczeniem.

## <a name="delegate-constraints"></a>Delegować ograniczenia

Również począwszy od C# 7.3, można użyć <xref:System.Delegate?displayProperty=nameWithType> lub <xref:System.MulticastDelegate?displayProperty=nameWithType> jako ograniczenie klasy podstawowej. Clr zawsze dozwolone tego ograniczenia, ale język C# nie zezwala na to. Ograniczenie `System.Delegate` umożliwia pisanie kodu, który współpracuje z delegatów w sposób bezpieczny dla typu. Poniższy kod definiuje metodę rozszerzenia, która łączy dwóch delegatów, pod warunkiem, że są tego samego typu:

[!code-csharp[using the delegate constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#16)]

Powyższa metoda służy do łączenia delegatów, które są tego samego typu:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#17)]

Jeśli uncomment ostatni wiersz, nie będzie kompilować. Oba `first` `test` i są typy delegata, ale są one różne typy delegatów.

## <a name="enum-constraints"></a>Ograniczenia wyliczenia

Począwszy od C# 7.3, <xref:System.Enum?displayProperty=nameWithType> można również określić typ jako ograniczenie klasy podstawowej. Clr zawsze dozwolone tego ograniczenia, ale język C# nie zezwala na to. Ogólne przy `System.Enum` użyciu zapewnienia bezpiecznego dla typu programowania do `System.Enum`pamięci podręcznej wyniki przy użyciu metod statycznych w . Poniższy przykład znajduje wszystkie prawidłowe wartości dla typu wyliczenia, a następnie tworzy słownik, który mapuje te wartości do jego reprezentacji ciągu.

[!code-csharp[using the enum constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#18)]

Metody stosowane do korzystania z odbicia, co ma wpływ na wydajność. Można wywołać tę metodę, aby utworzyć kolekcję, która jest buforowana i ponownie, a nie powtarzanie wywołań, które wymagają odbicia.

Można go użyć, jak pokazano w poniższym przykładzie, aby utworzyć wyliczenie i utworzyć słownik jego wartości i nazw:

[!code-csharp[enum definition](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#19)]

[!code-csharp[using the enum constrained method](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#20)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Generic>
- [C# Przewodnik programowania](../index.md)
- [Wprowadzenie do typów ogólnych](./index.md)
- [Klasy ogólne](./generic-classes.md)
- [nowe ograniczenie](../../language-reference/keywords/new-constraint.md)
