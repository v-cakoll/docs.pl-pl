---
title: Wbudowane typy odwołań — C# odwołanie
description: Dowiedz się więcej na temat C# typów referencyjnych, które mają słowa kluczowe, których można użyć do deklarowania ich.
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
ms.openlocfilehash: fcfe2dafe588dce57628bff63e3519f70d7a7725
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566257"
---
# <a name="built-in-reference-types-c-reference"></a>Wbudowane typy odwołań (C# odwołanie)

C#ma wiele wbudowanych typów odwołań. Mają słowa kluczowe lub operatory, które są synonimami dla typu w bibliotece .NET. 

## <a name="the-object-type"></a>Typ obiektu

Typ jest aliasem dla <xref:System.Object?displayProperty=nameWithType> platformy .NET. `object` W ujednoliconym systemie typów systemu C#, wszystkie typy, wstępnie zdefiniowane i zdefiniowane przez użytkownika, typy odwołań i typy wartości, dziedziczą bezpośrednio lub <xref:System.Object?displayProperty=nameWithType>pośrednio z. Do zmiennych typu `object`można przypisać wartości dowolnego typu. Dowolna `object` zmienna może być przypisana do wartości domyślnej przy użyciu `null`literału. Gdy zmienna typu wartości jest konwertowana na obiekt, jest określana jako *opakowana*. Gdy zmienna typu Object jest konwertowana na typ wartości, jest ona określana jako nieopakowana. Aby uzyskać więcej informacji, zobacz [opakowanie i rozpakowywanie](../../programming-guide/types/boxing-and-unboxing.md). 

## <a name="the-string-type"></a>Typ ciągu

`string` Typ reprezentuje sekwencję składającą się z zero lub więcej znaków Unicode. `string`jest aliasem dla <xref:System.String?displayProperty=nameWithType> platformy .NET.

Chociaż `string` jest typem referencyjnym, [Operatory `==` równości i są `!=` ](../operators/equality-operators.md#string-equality) zdefiniowane do porównywania wartości `string` obiektów, a nie odwołań. Dzięki temu testowanie w celu zapewnienia bardziej intuicyjnego testowania. Przykład:

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

Spowoduje to wyświetlenie wartości "true", a następnie wartości "false", ponieważ zawartość ciągów jest `a` równoważna, ale i `b` nie odwołuje się do tego samego wystąpienia ciągu.

[Operator +](../operators/addition-operator.md#string-concatenation) łączy ciągi:

```csharp
string a = "good " + "morning";
```

Spowoduje to utworzenie obiektu ciągu zawierającego "dobry rano".

Ciągi są *niezmienne*— zawartość obiektu String nie może zostać zmieniona po utworzeniu obiektu, mimo że składnia wygląda tak, jakby to możliwe. Na przykład podczas pisania tego kodu kompilator w rzeczywistości tworzy nowy obiekt ciągu do przechowywania nowej sekwencji znaków, a nowy obiekt jest przypisany do `b`. Pamięć, która została przypisana dla `b` (gdy zawiera ciąg "h"), kwalifikuje się do wyrzucania elementów bezużytecznych.

```csharp
string b = "h";
b += "ello";
```

Operatora można używać do dostępu tylko do odczytu do [](../operators/member-access-operators.md#indexer-operator-) `string`poszczególnych znaków. `[]` Prawidłowe wartości zaczynają `0` się od i muszą być mniejsze niż długość: `string`

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

W podobny sposób `[]` operator może być również używany do iteracji dla każdego znaku `string`w:

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
``` 

Literały ciągu są typu `string` i mogą być zapisywane w dwóch postaciach, cytowane i `@`ujęte w cudzysłów. Cudzysłowy ujęte w cudzysłów są ujęte w znaki podwójnego cudzysłowu ("):

```csharp
"good morning"  // a string literal
```

Literały ciągu mogą zawierać dowolny literał znakowy. Sekwencje ucieczki są uwzględniane. Poniższy przykład używa sekwencji `\\` unikowej dla ukośnika odwrotnego, `\u0066` dla litery f i `\n` dla nowego wiersza.

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
\\ Output:
\\ \f
\\  F
```

> [!NOTE]
> Kod `\udddd` ucieczki (gdzie `dddd` jest liczbą czterocyfrową) reprezentuje znak Unicode U +`dddd`. Są również rozpoznawane osiem cyfrowych kodów ucieczki `\Udddddddd`Unicode:.

[Literały ciągu Verbatim](../tokens/verbatim.md) zaczynają `@` się od i są również ujęte w znaki podwójnego cudzysłowu. Przykład:

```csharp
@"good morning"  // a string literal
```

Zaletą ciągów Verbatim jest to, że sekwencje unikowe *nie* są przetwarzane, co ułatwia pisanie, na przykład w pełni kwalifikowanej nazwy pliku systemu Windows:

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

Aby uwzględnić podwójny cudzysłów w @-quoted ciągu, należy go dwukrotnie:

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a>Typ delegata

Deklaracja typu delegata jest podobna do sygnatury metody. Ma ona wartość zwracaną i dowolną liczbę parametrów dowolnego typu:

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

W programie .NET `System.Action` i `System.Func` typy zapewniają definicje ogólne dla wielu typowych delegatów. Być może nie trzeba definiować nowych typów delegatów niestandardowych. Zamiast tego można tworzyć wystąpienia podanych typów ogólnych.

A `delegate` to typ referencyjny, który może służyć do hermetyzacji metody nazwanej lub anonimowej. Delegaty są podobne do wskaźników funkcji C++w; Delegaty są jednak bezpieczne i bezpieczne dla typów. W przypadku aplikacji delegatów zobacz [Delegaty](../../programming-guide/delegates/index.md) i [delegatów ogólnych](../../programming-guide/generics/generic-delegates.md). Delegaty są podstawą dla [zdarzeń](../../programming-guide/events/index.md). Można utworzyć wystąpienie delegata, kojarząc go z metodami nazwanymi lub anonimowymi.

Obiekt delegowany musi być skonkretyzowany przy użyciu metody lub wyrażenia lambda, które ma zgodny typ zwracany i parametry wejściowe. Aby uzyskać więcej informacji na temat stopnia wariancji, który jest dozwolony w sygnaturze metody, zobacz [Wariancja w delegatach](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md). Aby można było korzystać z metod anonimowych, delegat i kod, który ma być skojarzony z nim, są deklarowane razem. 

## <a name="the-dynamic-type"></a>Typ dynamiczny

`dynamic` Typ wskazuje, że użycie zmiennej i odwołań do jej elementów członkowskich obejście sprawdzania typu w czasie kompilacji. Zamiast tego te operacje są rozwiązywane w czasie wykonywania. `dynamic` Typ upraszcza dostęp do interfejsów API modelu COM, takich jak interfejsy API usługi Office Automation, do dynamicznych interfejsów API, takich jak biblioteki IronPython, oraz do Document Object Model HTML (dom).

Typ `dynamic` zachowuje się jak typ `object` w większości sytuacji. W szczególności każde wyrażenie o wartości innej niż null można przekonwertować na `dynamic` typ. Typ różni się od `object` w tym, że operacje zawierające wyrażenia typu `dynamic` nie są rozpoznawane lub typem sprawdzonym przez kompilator. `dynamic` Kompilator pakuje razem informacje o operacji, a informacje te są później używane do szacowania operacji w czasie wykonywania. W ramach procesu zmienne typu `dynamic` są kompilowane do zmiennych typu. `object` W związku z `dynamic` tym, typ istnieje tylko w czasie kompilacji, a nie w czasie wykonywania.

Poniższy przykład kontrastuje zmienną typu `dynamic` do zmiennej typu. `object` Aby sprawdzić typ każdej zmiennej w czasie kompilacji, umieść wskaźnik myszy nad `dyn` lub `obj` w `WriteLine` instrukcjach. Skopiuj poniższy kod do edytora, w którym jest dostępna funkcja IntelliSense. Funkcja IntelliSense wyświetla dynamiczne `dyn` dla **obiektów** `obj`i.

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

Instrukcje wyświetlają `dyn` typy czasu wykonywania i `obj`. <xref:System.Console.WriteLine%2A> W tym momencie oba mają ten sam typ, liczba całkowita. Generowane są następujące dane wyjściowe:

```console
System.Int32
System.Int32
```

Aby wyświetlić różnicę między `dyn` i `obj` w czasie kompilacji, Dodaj następujące dwa wiersze `WriteLine` między deklaracjami i instrukcjami w poprzednim przykładzie.

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 Zgłoszono błąd kompilatora dla próby dodania liczby całkowitej i obiektu w wyrażeniu `obj + 3`. Nie jest jednak zgłaszany `dyn + 3`żaden błąd. Wyrażenie, które zawiera `dyn` nie jest sprawdzane w czasie kompilacji, ponieważ `dyn` jest `dynamic`typem.

Poniższy przykład używa `dynamic` w kilku deklaracjach. Metoda `Main` ta również kontrastuje sprawdzanie typu czasu kompilacji z sprawdzaniem typu w czasie wykonywania.

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Słowa kluczowe języka C#](../keywords/index.md)
- [Zdarzenia](../../../csharp/programming-guide/events/index.md)
- [Używanie typu dynamicznego](../../programming-guide/types/using-type-dynamic.md)
- [Najlepsze rozwiązania dotyczące używania ciągów](../../../standard/base-types/best-practices-strings.md)
- [Podstawowe operacje na ciągach](../../../standard/base-types/basic-string-operations.md)
- [Tworzenie nowych ciągów](../../../standard/base-types/creating-new.md)
- [Operatory testowania typu i rzutowania](../operators/type-testing-and-cast.md)
- [Instrukcje: bezpieczne rzutowanie przy użyciu dopasowania wzorca i operatorów AS i is](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [Przewodnik: Tworzenie obiektów dynamicznych i korzystanie z nich](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
