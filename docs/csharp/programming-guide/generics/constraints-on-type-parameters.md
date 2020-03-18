---
title: Ograniczenia parametrów typu - Przewodnik programowania C#
ms.date: 04/12/2018
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.openlocfilehash: 76cd00b9c84f128d2a181115293df910d8deb6cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399799"
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>Ograniczenia parametrów typu (Przewodnik programowania C#)

Ograniczenia informują kompilator o możliwościach, które musi mieć argument typu. Bez żadnych ograniczeń argument typu może być dowolny typ. Kompilator może tylko <xref:System.Object?displayProperty=nameWithType>przyjąć członków , który jest ostateczną klasą podstawową dla dowolnego typu .NET. Aby uzyskać więcej informacji, zobacz [Dlaczego warto używać ograniczeń](#why-use-constraints). Jeśli kod klienta próbuje utworzyć wystąpienie klasy przy użyciu typu, który nie jest dozwolony przez ograniczenie, wynik jest błąd w czasie kompilacji. Ograniczenia są określane przy `where` użyciu kontekstowe słowo kluczowe. W poniższej tabeli wymieniono siedem typów ograniczeń:

|Ograniczenie|Opis|
|----------------|-----------------|
|`where T : struct`|Argument typu musi być typem wartości niepodlegających wartości null. Aby uzyskać informacje o typach wartości nullable, zobacz [Typy wartości nullable](../../language-reference/builtin-types/nullable-value-types.md). Ponieważ wszystkie typy wartości mają dostępny konstruktor bezparametrów, `struct` ograniczenie implikuje `new()` ograniczenie i `new()` nie można połączyć z ograniczeniem. Nie można również `struct` połączyć ograniczenia `unmanaged` z ograniczeniem.|
|`where T : class`|Argument typu musi być typem odwołania. To ograniczenie dotyczy również dowolnej klasy, interfejsu, delegata lub typu tablicy.|
|`where T : notnull`|Argument typu musi być typem niepodlegającym null. Argument może być typem odwołania niedopuszczającym do wartości null w języku C# 8.0 lub nowszym lub typem wartości niepodlegających zerwaniu. To ograniczenie dotyczy również dowolnej klasy, interfejsu, delegata lub typu tablicy.|
|`where T : unmanaged`|Argument typu musi być [typem niepodlegającym](../../language-reference/builtin-types/unmanaged-types.md)null. Ograniczenie `unmanaged` oznacza `struct` ograniczenie i nie można łączyć z `struct` lub `new()` ograniczenia.|
|`where T : new()`|Argument typu musi mieć konstruktora public parameterless. W połączeniu `new()` z innymi ograniczeniami ograniczenie musi być określone jako ostatnie. Ograniczenia `new()` nie można łączyć z ograniczeniami `struct` `unmanaged` i.|
|`where T :`*nazwa klasy podstawowej>\<*|Argument typu musi być lub pochodzić z określonej klasy podstawowej.|
|`where T :`nazwa interfejsu>* \<*|Argument typu musi być lub zaimplementować określony interfejs. Można określić wiele ograniczeń interfejsu. Interfejs ograniczający może być również ogólny.|
|`where T : U`|Argument typu podany dla T musi być lub pochodzić z argumentu dostarczonego dla U.|

## <a name="why-use-constraints"></a>Dlaczego warto używać ograniczeń

Ograniczając parametr type, można zwiększyć liczbę dozwolonych operacji i wywołań metody do tych obsługiwanych przez typ ograniczający i wszystkie typy w hierarchii dziedziczenia. Podczas projektowania ogólnych klas lub metod, jeśli będziesz wykonywać dowolną operację na członków ogólnych <xref:System.Object?displayProperty=nameWithType>poza proste przypisania lub wywołanie jakichkolwiek metod nie obsługiwane przez , należy zastosować ograniczenia do parametru typu. Na przykład ograniczenie klasy podstawowej informuje kompilator, że tylko obiekty tego typu lub pochodzące z tego typu będą używane jako argumenty typu. Gdy kompilator ma tę gwarancję, może zezwolić na metody tego typu, które mają być wywoływane w klasie ogólnej. W poniższym przykładzie kodu przedstawiono funkcje, `GenericList<T>` które można dodać do klasy (w [wprowadzenie do ogólnych)](../../../standard/generics/index.md)przez zastosowanie ograniczenia klasy podstawowej.

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#9)]

Ograniczenie umożliwia klasy ogólnej do `Employee.Name` korzystania z właściwości. Ograniczenie określa, że wszystkie elementy `T` typu są gwarantowane jako `Employee` obiekt lub obiekt, `Employee`który dziedziczy z .

Wiele ograniczeń można zastosować do tego samego parametru typu, a same ograniczenia mogą być typami ogólnymi w następujący sposób:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#10)]

Podczas stosowania `where T : class` ograniczenia, należy `==` unikać `!=` i operatorów na parametr typu, ponieważ te operatory będą testować tylko dla tożsamości odniesienia, a nie dla równości wartości. To zachowanie występuje, nawet jeśli te operatory są przeciążone w typie, który jest używany jako argument. Poniższy kod ilustruje ten punkt; dane wyjściowe jest false, mimo <xref:System.String> `==` że klasa przeciąża operatora.

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#11)]

Kompilator wie `T` tylko, że jest typem odwołania w czasie kompilacji i musi używać domyślnych operatorów, które są prawidłowe dla wszystkich typów odwołań. Jeśli należy przetestować równości wartości, zalecanym sposobem `where T : IEquatable<T>` jest `where T : IComparable<T>` również zastosowanie lub ograniczenie i zaimplementować interfejs w dowolnej klasie, która będzie używana do konstruowania klasy ogólnej.

## <a name="constraining-multiple-parameters"></a>Ograniczanie wielu parametrów

Ograniczenia do wielu parametrów i wiele wiązań można zastosować do jednego parametru, jak pokazano w poniższym przykładzie:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a>Parametry typu niezwiązanego

 Parametry typu, które nie mają żadnych ograniczeń, takie jak T w klasie `SampleClass<T>{}`publicznej, są nazywane parametrami typu niezwiązanego. Parametry typu niezwiązanego mają następujące reguły:

- `!=` Operatory `==` i nie mogą być używane, ponieważ nie ma gwarancji, że konkretny argument typu będzie obsługiwać te operatory.
- Można je konwertować na `System.Object` i z lub jawnie konwertowane na dowolny typ interfejsu.
- Można porównać je z [wartością null](../../language-reference/keywords/null.md). Jeśli parametr niezwiązany jest `null`porównywany do , porównanie zawsze zwraca false, jeśli argument typu jest typem wartości.

## <a name="type-parameters-as-constraints"></a>Wpisywanie parametrów jako ograniczeń

Użycie parametru typu ogólnego jako ograniczenia jest przydatne, gdy funkcja elementu członkowskiego z własnym parametrem type musi ograniczyć ten parametr do parametru typu typu zawierającego, jak pokazano w poniższym przykładzie:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#13)]

W poprzednim przykładzie `T` jest ograniczenie typu w kontekście `Add` metody i parametr typu nieograniczonego w `List` kontekście klasy.

Parametry typu mogą być również używane jako ograniczenia w ogólnych definicjach klas. Parametr typu musi być zadeklarowany w nawiasach kątowych wraz z innymi parametrami typu:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#14)]

Przydatność parametrów typu jako ograniczeń z klasami ogólnymi jest ograniczona, ponieważ kompilator nie może zakładać nic o parametrze typu, z wyjątkiem, że pochodzi z `System.Object`. Użyj parametrów typu jako ograniczeń dla klas ogólnych w scenariuszach, w których chcesz wymusić relację dziedziczenia między dwoma parametrami typu.

## <a name="notnull-constraint"></a>Ograniczenie NotNull

Począwszy od języka C# 8.0, można użyć `notnull` ograniczenia, aby określić, że argument typu musi być typem wartości niepodlegającym wartości null lub typem odwołania niepodlegającym zerowaniu. Ograniczenie `notnull` może być używane tylko `nullable enable` w kontekście. Kompilator generuje ostrzeżenie, jeśli `notnull` dodasz ograniczenie w kontekście nullable nieświadomych.

W przeciwieństwie do innych ograniczeń, `notnull` gdy argument typu narusza ograniczenie, kompilator generuje `nullable enable` ostrzeżenie, gdy ten kod jest kompilowany w kontekście. Jeśli kod jest kompilowany w kontekście nullable nieświadomych, kompilator nie generuje żadnych ostrzeżeń lub błędów.

## <a name="unmanaged-constraint"></a>Ograniczenie niezarządzane

Począwszy od języka C# 7.3, można użyć `unmanaged` ograniczenia, aby określić, że parametr type musi być [typem niepodlegającym](../../language-reference/builtin-types/unmanaged-types.md)null. Ograniczenie `unmanaged` umożliwia pisanie procedur wielokrotnego użytku do pracy z typami, które mogą być manipulowane jako bloki pamięci, jak pokazano w poniższym przykładzie:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#15)]

Powyższa metoda musi być skompilowana w `unsafe` `sizeof` kontekście, ponieważ używa operatora na typ nie wiadomo, że jest typem wbudowanym. Bez `unmanaged` ograniczenia `sizeof` operator jest niedostępny.

Ograniczenie `unmanaged` oznacza `struct` ograniczenie i nie można z nim łączyć. Ponieważ `struct` ograniczenie implikuje `new()` ograniczenie, `unmanaged` ograniczenia nie można również łączyć z `new()` ograniczeniem.

## <a name="delegate-constraints"></a>Delegowanie ograniczeń

Również począwszy od Języka C# <xref:System.Delegate?displayProperty=nameWithType> 7.3, można użyć lub <xref:System.MulticastDelegate?displayProperty=nameWithType> jako ograniczenie klasy podstawowej. CLR zawsze dozwolone to ograniczenie, ale język C# nie dozwolone. Ograniczenie `System.Delegate` umożliwia pisanie kodu, który działa z delegatów w sposób bezpieczny dla typu. Poniższy kod definiuje metodę rozszerzenia, która łączy dwóch delegatów, pod warunkiem, że są one tego samego typu:

[!code-csharp[using the delegate constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#16)]

Powyższa metoda służy do łączenia delegatów, które są tego samego typu:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#17)]

Jeśli odkomentujesz ostatni wiersz, nie zostanie on skompilowany. Oba `first` `test` typy i są delegowane, ale są to różne typy delegatów.

## <a name="enum-constraints"></a>Ograniczenia wyliczenia

Począwszy od C# 7.3, <xref:System.Enum?displayProperty=nameWithType> można również określić typ jako ograniczenie klasy podstawowej. CLR zawsze dozwolone to ograniczenie, ale język C# nie dozwolone. Rodzajowe `System.Enum` przy użyciu zapewniają programowanie bezpieczne dla typu `System.Enum`do buforowania wyników przy użyciu metod statycznych w programie . Poniższy przykład znajduje wszystkie prawidłowe wartości dla typu wyliczenia, a następnie tworzy słownik, który mapuje te wartości na jego reprezentację ciągu.

[!code-csharp[using the enum constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#18)]

Metody używane do korzystania z odbicia, co ma wpływ na wydajność. Można wywołać tę metodę do tworzenia kolekcji, która jest buforowana i ponownie używane, a nie powtarzanie wywołań, które wymagają odbicia.

Można go użyć, jak pokazano w poniższym przykładzie, aby utworzyć wyliczenie i utworzyć słownik jego wartości i nazw:

[!code-csharp[enum definition](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#19)]

[!code-csharp[using the enum constrained method](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#20)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Generic>
- [Przewodnik programowania języka C#](../index.md)
- [Wprowadzenie do typów ogólnych](./index.md)
- [Klasy ogólne](./generic-classes.md)
- [nowe ograniczenie](../../language-reference/keywords/new-constraint.md)
