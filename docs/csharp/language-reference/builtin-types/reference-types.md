---
title: Wbudowane typy referencyjne - C# odwołania
description: Więcej informacji na temat typów odwołań, które mają C# słów kluczowych, można użyć, aby zadeklarować je.
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
ms.openlocfilehash: 4bc93216d74e2732870e08edd4bdb9570391cf5f
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2019
ms.locfileid: "67877196"
---
# <a name="built-in-reference-types-c-reference"></a>Wbudowane typy referencyjne (C# odwołania)

C#zawiera liczbę wbudowane typy referencyjne. Mają one słów kluczowych lub operatorów, które są synonimy dla typu w bibliotece programu .NET. 

## <a name="the-object-type"></a>Typ obiektu

`object` Typu jest aliasem dla <xref:System.Object?displayProperty=nameWithType> na platformie .NET. W systemie zunifikowany typ w języku C#, wszystkie typy, wstępnie zdefiniowanych i zdefiniowanych przez użytkownika typy odwołań i typy wartości dziedziczyć bezpośrednio lub pośrednio <xref:System.Object?displayProperty=nameWithType>. Można przypisać wartości dowolnego typu do zmiennych typu `object`. Wszelkie `object` zmiennej można przypisać do wartości domyślnej przy użyciu literału `null`. Kiedy zmienną typu wartości jest konwertowany na obiekt, jest określany jako *opakowany*. Zmienną obiektu typu jest konwertowany na typ wartości, jest określane jako *rozpakowany*. Aby uzyskać więcej informacji, zobacz [opakowywanie i rozpakowywanie](../../programming-guide/types/boxing-and-unboxing.md). 

## <a name="the-string-type"></a>Typ ciągu

`string` Typu reprezentuje sekwencję zero lub więcej znaków Unicode. `string` jest aliasem dla <xref:System.String?displayProperty=nameWithType> na platformie .NET.

Mimo że `string` jest typem referencyjnym [Operatory równości `==` i `!=` ](../operators/equality-operators.md#string-equality) są zdefiniowane w celu porównania wartości `string` obiektów, nie odwołuje się. To sprawia, że testowanie dla równości ciągu bardziej intuicyjne. Przykład:

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

Spowoduje to wyświetlenie "True" i następnie "False", ponieważ zawartość ciągi są równoważne, ale `a` i `b` odwołuje się do tego samego wystąpienia ciągu.

[+ — Operator](../operators/addition-operator.md#string-concatenation) łączy ciągi:

```csharp
string a = "good " + "morning";
```

Spowoduje to utworzenie obiekt ciągu zawierający "good morning".

Ciągi są *niezmienne*— nie można zmienić zawartość obiekt ciągu, po utworzeniu obiektu, mimo że składnia sprawia, że wyświetlane tak, jakby można to zrobić. Na przykład podczas pisania tego kodu, kompilator tworzy obiekt ciągu do przechowywania nową sekwencję znaków, a nowy obiekt jest przypisany do `b`. Pamięć, która zostały przydzielone dla `b` (gdy zawiera ciąg "h") jest uprawniona do wyrzucania elementów bezużytecznych.

```csharp
string b = "h";
b += "ello";
```

`[]` [Operator](../operators/member-access-operators.md#indexer-operator-) umożliwia dostęp tylko do odczytu do pojedynczych znaków z `string`. Prawidłowe wartości rozpoczynają się od `0` i musi być mniejsza niż długość `string`:

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

W podobny sposób `[]` operator może również służyć do Iterowanie po każdego znaku w `string`:

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
``` 

Literały ciągów są typu `string` i mogą być zapisywane w dwóch formach, w cudzysłowach i `@`— w cudzysłowach. Jako ciąg, który literały są ujęte w podwójny cudzysłów ("):

```csharp
"good morning"  // a string literal
```

Literały ciągu może zawierać dowolny znak literału. Sekwencje unikowe są uwzględniane. W poniższym przykładzie użyto sekwencja unikowa `\\` dla ukośnikiem, po którym `\u0066` literę f, i `\n` dla nowego wiersza.

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
\\ Output:
\\ \f
\\  F
```

> [!NOTE]
> Kod escape `\udddd` (gdzie `dddd` jest liczbę czterocyfrową) reprezentuje znak Unicode U +`dddd`. Kodów wyjścia Unicode ośmiu cyfr, również są rozpoznawane: `\Udddddddd`.

[Ciąg Verbatim literały](../tokens/verbatim.md) rozpoczynać `@` i również są ujęte w podwójny cudzysłów. Na przykład:

```csharp
@"good morning"  // a string literal
```

Zaletą ciągi verbatim jest, że sekwencje ucieczki to *nie* przetwarzany, która ułatwia zapisu, na przykład w pełni kwalifikowanej nazwy pliku Windows:

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

Aby uwzględnić znak podwójnego cudzysłowu w @-quoted ciąg, podwój go:

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a>Typ delegata

Deklaracja typu delegata jest podobny do podpisu metody. Ma wartość zwracaną i dowolną liczbę parametrów, dowolnego typu:

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

Na platformie .NET `System.Action` i `System.Func` typy zapewniają ogólne definicji dla wielu typowych obiektów delegowanych. Prawdopodobnie nie trzeba definiować nowe typy niestandardową klasę delegatów. Zamiast tego można tworzyć wystąpień typów ogólnych podana.

Element `delegate` jest typem referencyjnym, który może służyć do hermetyzacji nazwane lub metodę anonimową. Delegaty są podobne do wskaźników funkcji języka C++; Jednak obiekty delegowane są bezpieczne i bezpieczny typowo. W przypadku aplikacji delegatów, zobacz [delegatów](../../programming-guide/delegates/index.md) i [delegatów ogólnych](../../programming-guide/generics/generic-delegates.md). Obiekty delegowane są podstawą [zdarzenia](../../programming-guide/events/index.md). Pełnomocnik może być utworzone przez skojarzenie przy użyciu metody nazwane i anonimowe.

Za pomocą metody lub wyrażenia lambda zgodne zwracany typ i parametry wejściowe, można utworzyć wystąpienia obiektu delegowanego. Aby uzyskać więcej informacji na temat stopień odchylenia, jaki jest dozwolony w podpisie metody, zobacz [wariancje w Delegatach](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md). Do użytku z metod anonimowych delegat i kodu, które ma zostać skojarzony z nim są zadeklarowane jednocześnie. 

## <a name="the-dynamic-type"></a>Typ dynamiczny

`dynamic` Typu wskazuje, które używają zmiennej i odwołuje się do jego elementów członkowskich pomijanie typów w czasie kompilacji sprawdzania. Zamiast tego te operacje są rozwiązywane w czasie wykonywania. `dynamic` Typu upraszcza dostęp do interfejsów API modelu COM, takich jak interfejsy API usługi Automation pakietu Office, aby dynamicznych interfejsów API, takich jak biblioteki IronPython i aby HTML Document Object Model (DOM).

Typ `dynamic` zachowuje się jak typ `object` w większości przypadków. W szczególności dowolne wyrażenie, inną niż null można przekonwertować na `dynamic` typu. `dynamic` Typ różni się od `object` w tej operacji, które zawierają wyrażenia typu `dynamic` nie są rozpoznawane lub typ sprawdzana przez kompilator. Pakiety kompilatora, które razem informacje na temat operacji, a te informacje później użyte do oceny operacji w czasie wykonywania. W ramach procesu, a zmienne typu `dynamic` są kompilowane do zmiennych typu `object`. W związku z tym, wpisz `dynamic` istnieje tylko w czasie kompilacji, nie w czasie wykonywania.

Poniższy przykład zachowanie różni się od zmiennej typu `dynamic` do zmiennej typu `object`. Aby sprawdzić typ każdej zmiennej w czasie kompilacji, umieść wskaźnik myszy nad `dyn` lub `obj` w `WriteLine` instrukcji. Skopiuj następujący kod do edytora, w których jest dostępna funkcja IntelliSense. Funkcja IntelliSense pokazuje **dynamiczne** dla `dyn` i **obiektu** dla `obj`.

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<xref:System.Console.WriteLine%2A> Instrukcji prezentuje typy środowiska wykonawczego `dyn` i `obj`. W tym momencie mają ten sam typ, liczbę całkowitą. Są następujące wyniki:

```console
System.Int32
System.Int32
```

Aby zobaczyć różnicę między `dyn` i `obj` w czasie kompilacji, Dodaj następujące dwa wiersze między deklaracjami i `WriteLine` instrukcji w poprzednim przykładzie.

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 Błąd kompilatora jest zgłaszany, próba dodanie całkowitą, a obiekt w wyrażeniu `obj + 3`. Jednak błąd nie jest zgłaszany, `dyn + 3`. Wyrażenie, które zawiera `dyn` nie jest sprawdzana w czasie kompilacji, ponieważ typ `dyn` jest `dynamic`.

W poniższym przykładzie użyto `dynamic` w kilka deklaracji. `Main` Metoda również zachowanie różni się od typu w czasie kompilacji sprawdzania ze sprawdzaniem typu run-time.

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Słowa kluczowe języka C#](../keywords/index.md)
- [Zdarzenia](../../../csharp/programming-guide/events/index.md)
- [Używanie typu dynamicznego](../../programming-guide/types/using-type-dynamic.md)
- [Najlepsze rozwiązania dotyczące używania ciągów](../../../standard/base-types/best-practices-strings.md)
- [Podstawowe operacje na ciągach](../../../standard/base-types/basic-string-operations.md)
- [Tworzenie nowych ciągów](../../../standard/base-types/creating-new.md)
- [Operatory badania typu i konwersji](../operators/type-testing-and-conversion-operators.md)
- [Porady: bezpieczne rzutowanie za pomocą dopasowywania do wzorca i as operatorów i is](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [Wskazówki: Tworzenie obiektów dynamicznych i posługiwanie](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
