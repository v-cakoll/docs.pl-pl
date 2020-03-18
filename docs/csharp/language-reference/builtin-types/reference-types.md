---
title: Wbudowane typy odwołań — odwołanie do języka C#
description: Dowiedz się więcej o typach odwołań, które mają słowa kluczowe języka C#, których możesz użyć do ich zadeklarowania.
ms.date: 06/25/2019
f1_keywords:
- object_CSharpKeyword
- object
- delegate_CSharpKeyword
- delegate
- dynamic_CSharpKeyword
- string
- string_CSharpKeyword
helpviewer_keywords:
- object keyword [C#]
- delegate keyword [C#]
- function pointers [C#]
- dynamic [C#]
- dynamic keyword [C#]
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.openlocfilehash: c2c03f47babd9ccf87eb60d33b9d65d1a9c82e2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399645"
---
# <a name="built-in-reference-types-c-reference"></a>Wbudowane typy odwołań (odwołanie do języka C#)

C# ma wiele wbudowanych typów odwołań. Mają słowa kluczowe lub operatory, które są synonimami dla typu w bibliotece .NET.

## <a name="the-object-type"></a>Typ obiektu

Typ `object` jest aliasem <xref:System.Object?displayProperty=nameWithType> w .NET. W ujednoliconym systemie typów Języka C#wszystkie typy, wstępnie zdefiniowane i zdefiniowane przez użytkownika, <xref:System.Object?displayProperty=nameWithType>typy odwołań i typy wartości dziedziczą bezpośrednio lub pośrednio z . Wartości dowolnego typu można przypisać do zmiennych typu `object`. Do `object` dowolnej zmiennej można przypisać wartość `null`domyślną za pomocą literału . Gdy zmienna typu wartości jest konwertowana na obiekt, mówi się, że *jest zapakowana*. Gdy zmienna `object` typu jest konwertowana na typ wartości, mówi się, że *jest rozpakowana*. Aby uzyskać więcej informacji, zobacz [Boks i Unboxing](../../programming-guide/types/boxing-and-unboxing.md).

## <a name="the-string-type"></a>Typ ciągu

Typ `string` reprezentuje sekwencję zero lub więcej znaków Unicode. `string`jest aliasem <xref:System.String?displayProperty=nameWithType> w .NET.

Mimo `string` że jest typem odwołania, [operatory `==` równości i `!=` ](../operators/equality-operators.md#string-equality) są zdefiniowane do porównywania `string` wartości obiektów, a nie odwołań. To sprawia, że testowanie równości ciągów bardziej intuicyjne. Przykład:

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

Spowoduje to wyświetlenie "True", a następnie "False", ponieważ `a` zawartość `b` ciągów są równoważne, ale i nie odnoszą się do tego samego wystąpienia ciągu.

Operator [+](../operators/addition-operator.md#string-concatenation) łączy ciągi:

```csharp
string a = "good " + "morning";
```

Spowoduje to utworzenie obiektu ciągu, który zawiera "dzień dobry".

Ciągi są *niezmienne*- zawartość obiektu ciągu nie można zmienić po utworzeniu obiektu, chociaż składnia sprawia, że wydaje się, jakby można to zrobić. Na przykład podczas pisania tego kodu kompilator faktycznie tworzy nowy obiekt ciągu do przechowywania nowej sekwencji znaków i że nowy obiekt jest przypisany do `b`. Pamięć, która została `b` przydzielona do (gdy zawierała ciąg "h") kwalifikuje się do wyrzucania elementów bezużytecznych.

```csharp
string b = "h";
b += "ello";
```

Operator `[]` [operator](../operators/member-access-operators.md#indexer-operator-) może służyć do odczytutylko dostęp do poszczególnych znaków ciągu. Prawidłowe wartości indeksu `0` zaczynają się od i muszą być mniejsze niż długość ciągu:

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

W podobny sposób `[]` operator może być również używany do iteracji nad każdym znakiem w ciągu:

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
```

Literały ciągów `string` są typu i mogą być `@`napisane w dwóch formach, cytowany i -quoted. Cytowane literały ciągów są ujęte w podwójne cudzysłowy ("):

```csharp
"good morning"  // a string literal
```

Literały ciągów mogą zawierać dowolne literały znaków. Sekwencje ucieczki są uwzględniane. W poniższym przykładzie `\\` użyto `\u0066` sekwencji ucieczki dla `\n` ukośnika odwrotnego, dla litery f i dla nowej linii.

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
// Output:
// \f
//  F
```

> [!NOTE]
> Kod `\udddd` ucieczki (gdzie `dddd` jest liczbą czterocyfrową) reprezentuje znak`dddd`Unicode U+ . Rozpoznawane są również ośmiocyfrowe kody `\Udddddddd`uchyłowane unicode: .

[Dosłowne literały ciągów](../tokens/verbatim.md) zaczynają się `@` od i są również ujęte w podwójne cudzysłowy. Przykład:

```csharp
@"good morning"  // a string literal
```

Zaletą ciągów dosłownych jest to, że sekwencje ucieczki *nie* są przetwarzane, co ułatwia pisanie, na przykład, w pełni kwalifikowanej nazwy pliku systemu Windows:

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

Aby dołączyć podwójny cudzysłów w @-quoted ciągu, podwoić go:

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a>Typ pełnomocnika

Deklaracja typu delegata jest podobna do podpisu metody. Ma wartość zwracaną i dowolną liczbę parametrów dowolnego typu:

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

W .NET `System.Action` `System.Func` i typy zawierają ogólne definicje dla wielu wspólnych delegatów. Prawdopodobnie nie trzeba definiować nowych typów delegatów niestandardowych. Zamiast tego można utworzyć wystąpienia typów ogólnych.

A `delegate` jest typem odwołania, który może służyć do hermetyzacji nazwie lub metody anonimowej. Delegaty są podobne do wskaźników funkcji w języku C++; jednak delegaci są bezpieczne typu i bezpieczne. Aby uzyskać aplikacje delegatów, zobacz [delegatów](../../programming-guide/delegates/index.md) i [delegatów ogólnych](../../programming-guide/generics/generic-delegates.md). Delegaci są podstawą [do zdarzeń](../../programming-guide/events/index.md). Pełnomocnika można utworzyć przez kojarzenie go z metodą o nazwie lub anonimowy.

Delegat musi być tworzone za pomocą metody lub wyrażenia lambda, który ma zgodny typ zwracany i parametry wejściowe. Aby uzyskać więcej informacji na temat stopnia wariancji dozwolonej w podpisie metody, zobacz [Wariancja w delegatach](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md). Do użytku z metodami anonimowymi delegat a kod, który ma być z nim skojarzony, są zadeklarowane razem.

## <a name="the-dynamic-type"></a>Typ dynamiczny

Typ `dynamic` wskazuje, że użycie zmiennej i odwołania do jej elementów członkowskich pomijają sprawdzanie typu kompilacji. Zamiast tego te operacje są rozwiązywane w czasie wykonywania. Typ `dynamic` ten upraszcza dostęp do interfejsów API COM, takich jak interfejsy API automatyzacji pakietu Office, do dynamicznych interfejsów API, takich jak biblioteki IronPython, oraz do modelu obiektu dokumentu HTML (DOM).

Typ `dynamic` zachowuje się `object` jak typ w większości przypadków. W szczególności każde wyrażenie inne niż null `dynamic` można przekonwertować na typ. Typ `dynamic` różni się `object` od tego, że operacje, które zawierają wyrażenia typu `dynamic` nie są rozpoznawane lub typu sprawdzane przez kompilator. Kompilator łączy informacje o operacji, a te informacje są później używane do oceny operacji w czasie wykonywania. W ramach procesu zmienne typu `dynamic` są kompilowane do zmiennych typu `object`. W związku `dynamic` z tym typ istnieje tylko w czasie kompilacji, a nie w czasie wykonywania.

Poniższy przykład kontrastuje zmienną `dynamic` typu ze `object`zmienną typu . Aby sprawdzić typ każdej zmiennej w czasie kompilacji, `obj` umieść `WriteLine` wskaźnik myszy nad `dyn` lub w instrukcjach. Skopiuj następujący kod do edytora, w którym dostępny jest program IntelliSense. IntelliSense **dynamic** pokazuje `dyn` dynamiczny dla `obj`i **obiekt** dla .

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

Instrukcje <xref:System.Console.WriteLine%2A> wyświetlają typy czasu `dyn` wykonywania i `obj`. W tym momencie oba mają tego samego typu, liczba całkowita. Zostaną wyświetlone następujące dane wyjściowe:

```console
System.Int32
System.Int32
```

Aby zobaczyć różnicę między `dyn` i `obj` w czasie kompilacji, dodaj następujące `WriteLine` dwa wiersze między deklaracjami i instrukcjami w poprzednim przykładzie.

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 Błąd kompilatora jest zgłaszany dla próby dodania `obj + 3`liczby całkowitej i obiektu w wyrażeniu . Jednak nie zgłaszano `dyn + 3`żadnego błędu dla . Wyrażenie, które `dyn` zawiera nie jest sprawdzana w `dyn` czasie `dynamic`kompilacji, ponieważ typem jest .

Poniższy przykład `dynamic` używa w kilku deklaracjach. Metoda `Main` kontrastuje również sprawdzanie typu kompilacji z sprawdzaniem typu wykonywania.

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Słowa kluczowe języka C#](../keywords/index.md)
- [Zdarzenia](../../programming-guide/events/index.md)
- [Używanie typu dynamicznego](../../programming-guide/types/using-type-dynamic.md)
- [Najlepsze rozwiązania dotyczące używania ciągów](../../../standard/base-types/best-practices-strings.md)
- [Podstawowe operacje na ciągach](../../../standard/base-types/basic-string-operations.md)
- [Tworzenie nowych ciągów](../../../standard/base-types/creating-new.md)
- [Operatory testowania typu i rzutowania](../operators/type-testing-and-cast.md)
- [Jak bezpiecznie oddać za pomocą dopasowania wzoru i jak i jest operatorzy](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [Instruktaż: tworzenie i używanie obiektów dynamicznych](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
