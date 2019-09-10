---
title: Typy referencyjne dopuszczające wartość null
description: Ten artykuł zawiera omówienie typów referencyjnych dopuszczających wartość null C# , które dodano w 8. Dowiesz się, jak funkcja zapewnia bezpieczeństwo przed wyjątkami odwołania o wartości null dla nowych i istniejących projektów.
ms.date: 02/19/2019
ms.openlocfilehash: e66d74cdde3b3de9ec3f1b435cdbd3e3b24c2663
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851067"
---
# <a name="nullable-reference-types"></a>Typy referencyjne dopuszczające wartość null

C#8,0 wprowadza **typy odwołań do wartości null** i **typy odwołań niedopuszczających wartości null** , które umożliwiają wykonywanie ważnych instrukcji dotyczących właściwości dla zmiennych typu odwołania:

- **Odwołanie nie powinno mieć wartości null**. Gdy zmienne nie powinny mieć wartości null, kompilator wymusza reguły, które gwarantują, że można bezpiecznie odwoływać się do tych zmiennych bez uprzedniego sprawdzenia, czy nie ma ona wartości null:
  - Zmienna musi być zainicjowana do wartości innej niż null.
  - Do zmiennej nigdy nie można przypisać wartości `null`.
- **Odwołanie może mieć wartość null**. Gdy zmienne mogą mieć wartość null, kompilator wymusza różne reguły, aby upewnić się, że prawidłowo sprawdzono odwołanie o wartości null:
  - Zmienna może zostać wykorzystana tylko wtedy, gdy kompilator może zagwarantować, że wartość nie ma wartości null.
  - Te zmienne mogą być inicjowane z wartością `null` domyślną i mogą mieć przypisaną wartość `null` w innym kodzie.

Ta nowa funkcja zapewnia znaczne korzyści w porównaniu z obsługą zmiennych referencyjnych we wcześniejszych C# wersjach, w których nie można ustalić intencji projektu na podstawie deklaracji zmiennej. Kompilator nie zapewniał bezpieczeństwa przed wyjątkami odwołania o wartości null dla typów referencyjnych:

- **Odwołanie może mieć wartość null**. Żadne ostrzeżenia nie są wydawane, gdy typ odwołania jest zainicjowany do wartości null lub później przypisany do wartości null.
- **Przyjęto, że odwołanie nie ma wartości null**. Kompilator nie wystawia żadnych ostrzeżeń, gdy odwołania do typów odwołań. (Z odwołaniami do wartości null, kompilator emituje ostrzeżenia za każdym razem, gdy odwołujesz się do zmiennej, która może mieć wartość null).

Przy dodawaniu typów odwołań do wartości null można zadeklarować cel dokładniej. `null` Wartość jest poprawnym sposobem reprezentowania, że zmienna nie odwołuje się do wartości. Nie używaj tej funkcji, aby usunąć `null` wszystkie wartości z Twojego kodu. Zamiast tego należy zadeklarować intencję do kompilatora i innych deweloperów, które odczytują swój kod. Deklarując swój intencję, kompilator informuje, gdy piszesz kod, który jest niespójny z tym zamiarem.

**Typ referencyjny dopuszczający wartość null** jest zanotowany przy użyciu tej samej składni `?` co [typy wartości null](programming-guide/nullable-types/index.md): a jest dołączany do typu zmiennej. Na przykład następująca deklaracja zmiennej reprezentuje zmienną ciągu null, `name`:

```csharp
string? name;
```

Każda zmienna, w `?` której nie jest dołączana do nazwy typu, jest **typem referencyjnym, który nie dopuszcza wartości null**. Zawiera wszystkie zmienne typu odwołania w istniejącym kodzie po włączeniu tej funkcji.

Kompilator używa statycznej analizy do ustalenia, czy odwołanie dopuszczające wartość null jest znane jako inne niż null. Kompilator ostrzega o tym, jeśli odwołujesz się do odwołania do wartości null, jeśli może to mieć wartość null. Zachowanie to można zastąpić za pomocą operatora o **wartości null-łagodniejszej** (`!`) po nazwie zmiennej. Jeśli na przykład wiadomo, że `name` zmienna nie ma wartości null, ale kompilator generuje ostrzeżenie, można napisać następujący kod, aby zastąpić analizę kompilatora:

```csharp
name!.Length;
```

Szczegółowe informacje o tym operatorze można znaleźć w propozycji [dokumentacji specyfikacji dopuszczającej wartość null](../../_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) w witrynie GitHub.

## <a name="nullability-of-types"></a>Wartość zerowa typów

Każdy typ referencyjny może mieć jeden z czterech *nullabilities*, który opisuje, kiedy generowane są ostrzeżenia:

- Nie *ma wartości null*: Nie można przypisać wartości null do zmiennych tego typu. Przed usunięciem odwołania zmienne tego typu nie muszą mieć wartości null.
- *Wartość null*: Wartość null można przypisać do zmiennych tego typu. Odwołujące się do `null` zmiennych tego typu bez uprzedniego sprawdzenia powoduje ostrzeżenie.
- *Oblivious*: Jest to stan poprzedzającyC# 8. Zmienne tego typu mogą być wywoływane lub przypisane bez ostrzeżeń.
- *Nieznany*: Ogólnie rzecz biorąc, parametry typu, w których ograniczenia nie informują kompilatora, że typ musi *dopuszczać wartości null* lub nie dopuszczać *wartości null*.

Wartość null typu w deklaracji zmiennej jest kontrolowana przez *kontekst dopuszczający wartość* null, w którym zmienna jest zadeklarowana.

## <a name="nullable-contexts"></a>Konteksty dopuszczające wartość null

Konteksty dopuszczające wartość null umożliwiają precyzyjne kontrolowanie, w jaki sposób kompilator interpretuje zmienne typu odwołania. **Kontekst adnotacji dopuszczający wartość null** w dowolnym wierszu `enabled` źródłowym `disabled`to lub. Można traktować kompilator pre-C# 8 jako kompilując cały kod w `disabled` kontekście dopuszczającym wartość null: Dowolny typ odwołania może mieć wartość null. **Kontekst ostrzeżeń dopuszczających wartość null** może być `enabled` ustawiony `disabled`na lub. Kontekst ostrzeżeń dopuszczających wartość null określa ostrzeżenia generowane przez kompilator przy użyciu analizy przepływu.

Kontekst adnotacji dopuszczający wartość null i kontekst ostrzeżenia dopuszczający wartość null można ustawić `Nullable` dla projektu używającego elementu `csproj` w pliku. Ten element określa, w jaki sposób kompilator interpretuje wartość null typów i jakie ostrzeżenia są generowane. Prawidłowe ustawienia to:

- `enable`: Kontekst adnotacji z dopuszczaniem wartości null jest **włączony**. Kontekst ostrzegawczy dopuszczający wartość null jest **włączony**.
  - Zmienne typu referencyjnego, `string` na przykład, nie dopuszczają wartości null.  Wszystkie ostrzeżenia o wartości null są włączone.
- `warnings`: Kontekst adnotacji z dopuszczaniem wartości null jest **wyłączony**. Kontekst ostrzegawczy dopuszczający wartość null jest **włączony**.
  - Zmienne typu referencyjnego to Oblivious. Wszystkie ostrzeżenia o wartości null są włączone.
- `annotations`: Kontekst adnotacji z dopuszczaniem wartości null jest **włączony**. Kontekst ostrzegawczy dopuszczający wartość null jest **wyłączony**.
  - Zmienne typu referencyjnego to Oblivious. Wszystkie ostrzeżenia o wartości null są włączone.
- `disable`: Kontekst adnotacji z dopuszczaniem wartości null jest **wyłączony**. Kontekst ostrzegawczy dopuszczający wartość null jest **wyłączony**.
  - Zmienne typu referencyjnego to Oblivious, podobnie jak w przypadku wcześniejszych wersji C#programu. Wszystkie ostrzeżenia o wartości null są wyłączone.

> [!IMPORTANT]
> Element miał wcześniej nazwę `NullableContextOptions`. `Nullable` Zmiana nazwy jest dostarczana z programem Visual Studio 2019, 16,2-P1. Ta zmiana nie ma zestaw .NET Core SDK 3.0.100-preview5-011568. Jeśli używasz interfejs wiersza polecenia platformy .NET Core, musisz użyć `NullableContextOptions` do momentu udostępnienia kolejnej wersji zapoznawczej.

Możesz również użyć dyrektyw, aby ustawić te same konteksty w dowolnym miejscu w projekcie:

- `#nullable enable`: Ustawia kontekst adnotacji dopuszczający wartość null i kontekst ostrzeżenia nullable do **włączenia**.
- `#nullable disable`: Ustawia kontekst adnotacji dopuszczający wartość null i kontekst ostrzeżenia dopuszczający wartość **null.**
- `#nullable restore`: Przywraca kontekst adnotacji dopuszczający wartość null i kontekst ostrzeżenia do wartości null w ustawieniach projektu.
- `#pragma warning disable nullable`: Ustaw dla kontekstu ostrzeżenia o wartości null wartość **wyłączone**.
- `#pragma warning enable nullable`: Ustaw kontekst ostrzeżenia wartości null na **włączone**.
- `#pragma warning restore nullable`: Przywraca kontekst ostrzegawczy dopuszczający wartość null do ustawień projektu.

Domyślne adnotacje dopuszczające wartość null i `disabled`konteksty ostrzeżenia są. Ta decyzja oznacza, że istniejący kod kompiluje się bez zmian i bez generowania nowych ostrzeżeń.

### <a name="nullable-annotation-context"></a>Kontekst adnotacji dopuszczający wartość null

Kompilator używa następujących reguł w wyłączonym kontekście adnotacji nullable:

- Nie można zadeklarować odwołań do wartości null w wyłączonym kontekście.
- Wszystkie zmienne odwołania mogą być przypisane do wartości null.
- Nie są generowane żadne ostrzeżenia, gdy zmienna typu odwołania jest wykorzystana.
- Operatora null-łagodniejszej nie można używać w wyłączonym kontekście.

Zachowanie jest takie samo jak w poprzednich wersjach programu C#.

Kompilator używa następujących reguł w włączonym kontekście adnotacji dopuszczających wartość null:

- Dowolna zmienna typu referencyjnego jest **odwołaniem niedopuszczanym do wartości null**.
- Wszystkie odwołania niedopuszczające wartości null mogą być bezpiecznie wywoływać.
- Dowolny typ referencyjny dopuszczający wartość `?` null (zanotowany przez po typie w deklaracji zmiennej) może mieć wartość null. Analiza statyczna określa, czy wartość jest znana jako inna niż null, gdy jest ona wywoływać. W przeciwnym razie kompilator wyświetli ostrzeżenie.
- Można użyć operatora null-łagodniejszej, aby zadeklarować, że odwołanie dopuszczające wartość null nie ma wartości null.

W włączonym kontekście dopuszczającym wartość `?` null, znak dołączony do typu referencyjnego deklaruje **typ referencyjny dopuszczający wartość null**. **Operator Forgiveness o wartości null** (`!`) może być dołączany do wyrażenia w celu stwierdzenia, że wyrażenie nie ma wartości null.

## <a name="nullable-warning-context"></a>Kontekst ostrzegawczy dopuszczający wartość null

Kontekst ostrzeżenia dopuszczający wartość null jest różny od kontekstu adnotacji dopuszczającej wartość null. Ostrzeżenia można włączyć nawet wtedy, gdy nowe adnotacje są wyłączone. Kompilator używa statycznej analizy przepływu do określenia **stanu null** dowolnych odwołań. Stan o wartości null **nie ma wartości null** lub **może mieć wartość null** , jeśli *kontekst ostrzeżenia o wartości null* nie jest **wyłączony**. Jeśli odwołujesz się do odwołania, gdy kompilator ustalił, że **może mieć wartość null**, kompilator wyświetli ostrzeżenie. Stan odwołania może **mieć wartość null** , chyba że kompilator może określić jeden z dwóch warunków:

1. Zmienna została ostatecznie przypisana do wartości innej niż null.
1. Zmienna lub wyrażenie zostało sprawdzone pod kątem wartości null przed usunięciem odwołania do niego.

Kompilator generuje ostrzeżenia za każdym razem, gdy użytkownik odwołuje się do zmiennej lub wyrażenia w stanie **null** , gdy jest `enabled`to wartość. Ponadto są generowane ostrzeżenia, gdy może istnieć zmienna **null** lub wyrażenie jest przypisywane do niezerowego typu odwołania w przypadku, gdy kontekst adnotacji ma `enabled`wartość null.

## <a name="learn-more"></a>Dowiedz się więcej

- [Specyfikacja referencyjna odwołania do wartości null](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-8.0/nullable-reference-types-specification.md)
- [Samouczek wprowadzający do odwołań do wartości null](tutorials/nullable-reference-types.md)
- [Migrowanie istniejącej bazy kodu do odwołań do wartości null](tutorials/upgrade-to-nullable-references.md)
