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
ms.openlocfilehash: 6b65d7e79e4eac30171eb0aad650f7c1e3880e30
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627273"
---
# <a name="built-in-reference-types-c-reference"></a>Wbudowane typy odwołań (C# odwołanie)

C#ma wiele wbudowanych typów odwołań. Mają słowa kluczowe lub operatory, które są synonimami dla typu w bibliotece .NET. 

## <a name="the-object-type"></a>Typ obiektu

Typ `object` jest aliasem dla <xref:System.Object?displayProperty=nameWithType> w programie .NET. W ujednoliconym systemie typów systemu C#, wszystkie typy, wstępnie zdefiniowane i zdefiniowane przez użytkownika, typy odwołań i typy wartości, dziedziczą bezpośrednio lub pośrednio z <xref:System.Object?displayProperty=nameWithType>. Wartości dowolnego typu można przypisać do zmiennych typu `object`. Dowolna zmienna `object` może być przypisana do jej wartości domyślnej przy użyciu `null`literału. Gdy zmienna typu wartości jest konwertowana na obiekt, jest określana jako *opakowana*. Gdy zmienna typu `object` jest konwertowana na typ wartości, jest ona określana jako *nieopakowana*. Aby uzyskać więcej informacji, zobacz [opakowanie i rozpakowywanie](../../programming-guide/types/boxing-and-unboxing.md). 

## <a name="the-string-type"></a>Typ ciągu

Typ `string` reprezentuje sekwencję zero lub więcej znaków Unicode. `string` jest alias <xref:System.String?displayProperty=nameWithType> na platformie .NET.

Chociaż `string` jest typem referencyjnym, [Operatory równości `==` i `!=`](../operators/equality-operators.md#string-equality) są zdefiniowane w celu porównania wartości obiektów `string`, a nie odwołań. Dzięki temu testowanie w celu zapewnienia bardziej intuicyjnego testowania. Na przykład:

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

Spowoduje to wyświetlenie wartości "true", a następnie wartości "false", ponieważ zawartość ciągów jest równoważna, ale `a` i `b` nie odwołują się do tego samego wystąpienia ciągu.

[Operator +](../operators/addition-operator.md#string-concatenation) łączy ciągi:

```csharp
string a = "good " + "morning";
```

Spowoduje to utworzenie obiektu ciągu zawierającego "dobry rano".

Ciągi są *niezmienne*— zawartość obiektu String nie może zostać zmieniona po utworzeniu obiektu, mimo że składnia wygląda tak, jakby to możliwe. Na przykład podczas pisania tego kodu kompilator tworzy nowy obiekt String, aby pomieścić nową sekwencję znaków i nowy obiekt został przypisany do `b`. Pamięć, która została przypisana do `b` (gdy zawiera ciąg "h"), kwalifikuje się do wyrzucania elementów bezużytecznych.

```csharp
string b = "h";
b += "ello";
```

[Operatora](../operators/member-access-operators.md#indexer-operator-) `[]` można używać do dostępu tylko do odczytu do poszczególnych znaków ciągu. Prawidłowe wartości indeksu zaczynają się o `0` i muszą być mniejsze niż długość ciągu:

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

W podobny sposób operator `[]` może być również używany do iteracji dla każdego znaku w ciągu:

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
``` 

Literały ciągu są typu `string` i mogą być zapisywane w dwóch postaciach, cytowane i `@`. Cudzysłowy ujęte w cudzysłów są ujęte w znaki podwójnego cudzysłowu ("):

```csharp
"good morning"  // a string literal
```

Literały ciągu mogą zawierać dowolny literał znakowy. Sekwencje ucieczki są uwzględniane. W poniższym przykładzie zastosowano sekwencję ucieczki `\\` dla ukośnika odwrotnego, `\u0066` dla litery f i `\n` dla nowego wiersza.

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
// Output:
// \f
//  F
```

> [!NOTE]
> Kod ucieczki `\udddd` (gdzie `dddd` jest liczbą czterocyfrową) reprezentuje znak Unicode U +`dddd`. Są również rozpoznawane osiem cyfrowych kodów ucieczki Unicode: `\Udddddddd`.

[Literały ciągu Verbatim](../tokens/verbatim.md) rozpoczynają się od `@` i są również ujęte w znaki podwójnego cudzysłowu. Na przykład:

```csharp
@"good morning"  // a string literal
```

Zaletą ciągów Verbatim jest to, że sekwencje unikowe *nie* są przetwarzane, co ułatwia pisanie, na przykład w pełni kwalifikowanej nazwy pliku systemu Windows:

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

Aby uwzględnić podwójny cudzysłów w ciągu @-quoted, należy go dwukrotnie:

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a>Typ delegata

Deklaracja typu delegata jest podobna do sygnatury metody. Ma ona wartość zwracaną i dowolną liczbę parametrów dowolnego typu:

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

W programie .NET typy `System.Action` i `System.Func` zapewniają definicje ogólne dla wielu typowych delegatów. Być może nie trzeba definiować nowych typów delegatów niestandardowych. Zamiast tego można tworzyć wystąpienia podanych typów ogólnych.

`delegate` jest typem referencyjnym, którego można użyć do hermetyzacji metody nazwanej lub anonimowej. Delegaty są podobne do wskaźników funkcji C++w; Delegaty są jednak bezpieczne i bezpieczne dla typów. W przypadku aplikacji delegatów zobacz [Delegaty](../../programming-guide/delegates/index.md) i [delegatów ogólnych](../../programming-guide/generics/generic-delegates.md). Delegaty są podstawą dla [zdarzeń](../../programming-guide/events/index.md). Można utworzyć wystąpienie delegata, kojarząc go z metodami nazwanymi lub anonimowymi.

Obiekt delegowany musi być skonkretyzowany przy użyciu metody lub wyrażenia lambda, które ma zgodny typ zwracany i parametry wejściowe. Aby uzyskać więcej informacji na temat stopnia wariancji, który jest dozwolony w sygnaturze metody, zobacz [Wariancja w delegatach](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md). Aby można było korzystać z metod anonimowych, delegat i kod, który ma być skojarzony z nim, są deklarowane razem. 

## <a name="the-dynamic-type"></a>Typ dynamiczny

Typ `dynamic` wskazuje, że użycie zmiennej i odwołań do jej elementów członkowskich obejście sprawdzania typu w czasie kompilacji. Zamiast tego te operacje są rozwiązywane w czasie wykonywania. Typ `dynamic` upraszcza dostęp do interfejsów API modelu COM, takich jak interfejsy API usługi Office Automation, do dynamicznych interfejsów API, takich jak biblioteki IronPython, oraz do Document Object Model HTML (DOM).

Typ `dynamic` zachowuje się jak typ `object` w większości sytuacji. W szczególności każde wyrażenie o wartości innej niż null można przekonwertować na typ `dynamic`. Typ `dynamic` różni się od `object` w tym, że operacje, które zawierają wyrażenia typu `dynamic` nie są rozpoznawane lub typem sprawdzonym przez kompilator. Kompilator pakuje razem informacje o operacji, a informacje te są później używane do szacowania operacji w czasie wykonywania. W ramach procesu zmienne typu `dynamic` są kompilowane do zmiennych typu `object`. W związku z tym, typ `dynamic` istnieje tylko w czasie kompilacji, a nie w czasie wykonywania.

Poniższy przykład kontrastuje zmienną typu `dynamic` do zmiennej typu `object`. Aby sprawdzić typ każdej zmiennej w czasie kompilacji, umieść wskaźnik myszy nad `dyn` lub `obj` w instrukcji `WriteLine`. Skopiuj poniższy kod do edytora, w którym jest dostępna funkcja IntelliSense. Funkcja IntelliSense wyświetla **dynamiczny** dla `dyn` i **obiektu** dla `obj`.

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

Instrukcje <xref:System.Console.WriteLine%2A> wyświetlają typy czasu wykonywania `dyn` i `obj`. W tym momencie oba mają ten sam typ, liczba całkowita. Generowane są następujące dane wyjściowe:

```console
System.Int32
System.Int32
```

Aby zobaczyć różnicę między `dyn` i `obj` w czasie kompilacji, Dodaj następujące dwa wiersze między deklaracjami i instrukcjami `WriteLine` w poprzednim przykładzie.

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 Zgłoszono błąd kompilatora dla próby dodania liczby całkowitej i obiektu w wyrażeniu `obj + 3`. Nie jest jednak zgłaszany żaden błąd dla `dyn + 3`. Wyrażenie zawierające `dyn` nie jest sprawdzane w czasie kompilacji, ponieważ typ `dyn` jest `dynamic`.

Poniższy przykład używa `dynamic` w kilku deklaracjach. Metoda `Main` również kontrastuje sprawdzanie typu w czasie kompilacji przy użyciu sprawdzania typu w czasie wykonywania.

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a>Zobacz też

- [C#Odwoła](../index.md)
- [Słowa kluczowe języka C#](../keywords/index.md)
- [Zdarzenia](../../programming-guide/events/index.md)
- [Używanie typu dynamicznego](../../programming-guide/types/using-type-dynamic.md)
- [Najlepsze rozwiązania dotyczące używania ciągów](../../../standard/base-types/best-practices-strings.md)
- [Podstawowe operacje na ciągach](../../../standard/base-types/basic-string-operations.md)
- [Tworzenie nowych ciągów](../../../standard/base-types/creating-new.md)
- [Operatory testowania typu i rzutowania](../operators/type-testing-and-cast.md)
- [Jak bezpiecznie rzutować przy użyciu dopasowania wzorca i operatorów AS i is](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [Przewodnik: Tworzenie obiektów dynamicznych i korzystanie z nich](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
