---
title: Typy referencyjne dopuszczające wartość null
description: Ten artykuł zawiera omówienie typów referencyjnych dopuszczających wartość null C# , które dodano w 8,0. Dowiesz się, jak funkcja zapewnia bezpieczeństwo przed wyjątkami odwołania o wartości null dla nowych i istniejących projektów.
ms.date: 02/19/2019
ms.openlocfilehash: a108c73064b40171a58df0796d4a0b75eddebbff
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319055"
---
# <a name="nullable-reference-types"></a>Typy referencyjne dopuszczające wartość null

C#8,0 wprowadza **typy odwołań do wartości null** i **typy odwołań niedopuszczających wartości null** , które umożliwiają wykonywanie ważnych instrukcji dotyczących właściwości dla zmiennych typu odwołania:

- **Odwołanie nie powinno mieć wartości null**. Gdy zmienne nie powinny mieć wartości null, kompilator wymusza reguły, które gwarantują, że można bezpiecznie odwoływać się do tych zmiennych bez uprzedniego sprawdzenia, czy nie ma ona wartości null:
  - Zmienna musi być zainicjowana do wartości innej niż null.
  - Do zmiennej nigdy nie można przypisać wartości `null`.
- **Odwołanie może mieć wartość null**. Gdy zmienne mogą mieć wartość null, kompilator wymusza różne reguły, aby upewnić się, że prawidłowo sprawdzono odwołanie o wartości null:
  - Zmienna może zostać wykorzystana tylko wtedy, gdy kompilator może zagwarantować, że wartość nie ma wartości null.
  - Te zmienne mogą być inicjowane z wartością domyślną `null` i może być przypisana wartość `null` w innym kodzie.

Ta nowa funkcja zapewnia znaczne korzyści w porównaniu z obsługą zmiennych referencyjnych we wcześniejszych C# wersjach, w których nie można ustalić intencji projektu na podstawie deklaracji zmiennej. Kompilator nie zapewniał bezpieczeństwa przed wyjątkami odwołania o wartości null dla typów referencyjnych:

- **Odwołanie może mieć wartość null**. Żadne ostrzeżenia nie są wydawane, gdy typ odwołania jest zainicjowany do wartości null lub później przypisany do wartości null.
- **Przyjęto, że odwołanie nie ma wartości null**. Kompilator nie wystawia żadnych ostrzeżeń, gdy odwołania do typów odwołań. (Z odwołaniami do wartości null, kompilator emituje ostrzeżenia za każdym razem, gdy odwołujesz się do zmiennej, która może mieć wartość null).

Przy dodawaniu typów odwołań do wartości null można zadeklarować cel dokładniej. Wartość `null` jest prawidłowym sposobem reprezentowania, że zmienna nie odwołuje się do wartości. Nie używaj tej funkcji, aby usunąć wszystkie wartości `null` z kodu. Zamiast tego należy zadeklarować intencję do kompilatora i innych deweloperów, które odczytują swój kod. Deklarując swój intencję, kompilator informuje, gdy piszesz kod, który jest niespójny z tym zamiarem.

**Typ referencyjny dopuszczający wartość null** jest zanotowany przy użyciu tej samej składni co typ [wartości null](programming-guide/nullable-types/index.md): `?` jest dołączany do typu zmiennej. Na przykład następująca deklaracja zmiennej reprezentuje zmienną ciągu dopuszczającą wartość null, `name`:

```csharp
string? name;
```

Dowolna zmienna, w której `?` nie jest dołączana do nazwy typu, jest **typem referencyjnym, który nie dopuszcza wartości null**. Zawiera wszystkie zmienne typu odwołania w istniejącym kodzie po włączeniu tej funkcji.

Kompilator używa statycznej analizy do ustalenia, czy odwołanie dopuszczające wartość null jest znane jako inne niż null. Kompilator ostrzega o tym, jeśli odwołujesz się do odwołania do wartości null, jeśli może to mieć wartość null. Można zastąpić to zachowanie przy użyciu [operatora null-łagodniejszej](language-reference/operators/null-forgiving.md) `!` po nazwie zmiennej. Na przykład jeśli wiesz, że zmienna `name` nie ma wartości null, ale kompilator generuje ostrzeżenie, można napisać następujący kod, aby zastąpić analizę kompilatora:

```csharp
name!.Length;
```

## <a name="nullability-of-types"></a>Wartość zerowa typów

Każdy typ referencyjny może mieć jeden z czterech *nullabilities*, który opisuje, kiedy generowane są ostrzeżenia:

- *Niedopuszczający wartości null*: nie można przypisać wartości null do zmiennych tego typu. Przed usunięciem odwołania zmienne tego typu nie muszą mieć wartości null.
- *Nullable*: wartość null może być przypisana do zmiennych tego typu. Wycofaj odwołania do zmiennych tego typu bez uprzedniego sprawdzenia dla `null` powoduje ostrzeżenie.
- *Oblivious*: to jest stan sprzedC# 8,0. Zmienne tego typu mogą być wywoływane lub przypisane bez ostrzeżeń.
- *Nieznane*: zwykle w przypadku parametrów typu, w których ograniczenia nie informują kompilatora, że typ musi *dopuszczać wartości null* lub nie dopuszczać *wartości null*.

Wartość null typu w deklaracji zmiennej jest kontrolowana przez *kontekst dopuszczający wartość* null, w którym zmienna jest zadeklarowana.

## <a name="nullable-contexts"></a>Konteksty dopuszczające wartość null

Konteksty dopuszczające wartość null umożliwiają precyzyjne kontrolowanie, w jaki sposób kompilator interpretuje zmienne typu odwołania. **Kontekst adnotacji dopuszczający wartość null** w dowolnym wierszu źródłowym jest włączony lub wyłączony. Można traktować kompilatorC# przed8,0 jako kompilując cały kod w wyłączonym kontekście dopuszczający wartość null: dowolny typ referencyjny może mieć wartość null. **Kontekst ostrzeżeń dopuszczających wartość null** może być również włączony lub wyłączony. Kontekst ostrzeżeń dopuszczających wartość null określa ostrzeżenia generowane przez kompilator przy użyciu analizy przepływu.

Kontekst adnotacji dopuszczający wartość null i kontekst ostrzeżenia dopuszczający wartość null można ustawić dla projektu przy użyciu elementu `Nullable` w pliku *. csproj* . Ten element określa, w jaki sposób kompilator interpretuje wartość null typów i jakie ostrzeżenia są generowane. Prawidłowe ustawienia to:

- `enable`: kontekst adnotacji dopuszczający wartość null jest **włączony**. Kontekst ostrzegawczy dopuszczający wartość null jest **włączony**.
  - Zmienne typu referencyjnego, `string` na przykład, nie dopuszczają wartości null.  Wszystkie ostrzeżenia o wartości null są włączone.
- `warnings`: kontekst adnotacji dopuszczający wartość null jest **wyłączony**. Kontekst ostrzegawczy dopuszczający wartość null jest **włączony**.
  - Zmienne typu referencyjnego to Oblivious. Wszystkie ostrzeżenia o wartości null są włączone.
- `annotations`: kontekst adnotacji dopuszczający wartość null jest **włączony**. Kontekst ostrzegawczy dopuszczający wartość null jest **wyłączony**.
  - Zmienne typu referencyjnego to Oblivious. Wszystkie ostrzeżenia o wartości null są wyłączone.
- `disable`: kontekst adnotacji dopuszczający wartość null jest **wyłączony**. Kontekst ostrzegawczy dopuszczający wartość null jest **wyłączony**.
  - Zmienne typu referencyjnego to Oblivious, podobnie jak w przypadku wcześniejszych wersji C#programu. Wszystkie ostrzeżenia o wartości null są wyłączone.

Możesz również użyć dyrektyw, aby ustawić te same konteksty w dowolnym miejscu w projekcie:

- `#nullable enable`: ustawia kontekst adnotacji dopuszczający wartość null i kontekst ostrzeżenia nullable do **włączenia**.
- `#nullable disable`: ustawia kontekst adnotacji dopuszczający wartość null i kontekst ostrzeżenia dopuszczający wartość **null.**
- `#nullable restore`: przywraca kontekst adnotacji dopuszczający wartość null i kontekst ostrzeżenia do wartości null w ustawieniach projektu.
- `#nullable disable warnings`: Ustaw wartość ustawienia kontekst ostrzeżenia o wartości null na **wyłączony**.
- `#nullable enable warnings`: Ustaw dla kontekstu ostrzeżenia nullable wartość **włączone**.
- `#nullable restore warnings`: przywraca kontekst ostrzegawczy dopuszczający wartość null do ustawień projektu.
- `#nullable disable annotations`: Ustaw wartość opcji kontekst adnotacji dopuszczającej wartość null na **wyłączony**.
- `#nullable enable annotations`: Ustaw kontekst adnotacji dopuszczający wartość **null.**
- `#nullable restore annotations`: przywraca kontekst ostrzeżenia adnotacji do ustawień projektu.

Domyślnie w przypadku adnotacji z dopuszczaniem wartości null i kontekstów ostrzeżeń są **wyłączone**. Oznacza to, że istniejący kod kompiluje się bez zmian i nie generuje żadnych nowych ostrzeżeń.

## <a name="nullable-annotation-context"></a>Kontekst adnotacji dopuszczający wartość null

Kompilator używa następujących reguł w wyłączonym kontekście adnotacji nullable:

- Nie można zadeklarować odwołań do wartości null w wyłączonym kontekście.
- Wszystkie zmienne odwołania mogą być przypisane do wartości null.
- Nie są generowane żadne ostrzeżenia, gdy zmienna typu odwołania jest wykorzystana.
- Operatora null-łagodniejszej nie można używać w wyłączonym kontekście.

Zachowanie jest takie samo jak w poprzednich wersjach programu C#.

Kompilator używa następujących reguł w włączonym kontekście adnotacji dopuszczających wartość null:

- Dowolna zmienna typu referencyjnego jest **odwołaniem niedopuszczanym do wartości null**.
- Wszystkie odwołania niedopuszczające wartości null mogą być bezpiecznie wywoływać.
- Dowolny typ referencyjny dopuszczający wartość null (zanotowany przez `?` po typie w deklaracji zmiennej) może mieć wartość null. Analiza statyczna określa, czy wartość jest znana jako inna niż null, gdy jest ona wywoływać. W przeciwnym razie kompilator wyświetli ostrzeżenie.
- Można użyć operatora null-łagodniejszej, aby zadeklarować, że odwołanie dopuszczające wartość null nie ma wartości null.

W włączonym kontekście dopuszczającym wartość null, znak `?` dołączany do typu referencyjnego deklaruje **typ referencyjny dopuszczający wartość null**. @No__t **operator łagodniejszej o wartości null** -1 może być dołączany do wyrażenia w celu stwierdzenia, że wyrażenie nie ma wartości null.

## <a name="nullable-warning-context"></a>Kontekst ostrzegawczy dopuszczający wartość null

Kontekst ostrzeżenia dopuszczający wartość null jest różny od kontekstu adnotacji dopuszczającej wartość null. Ostrzeżenia można włączyć nawet wtedy, gdy nowe adnotacje są wyłączone. Kompilator używa statycznej analizy przepływu do określenia **stanu null** dowolnych odwołań. Stan o wartości null **nie ma wartości null** lub **może mieć wartość null** , jeśli *kontekst ostrzeżenia o wartości null* nie jest **wyłączony**. Jeśli odwołujesz się do odwołania, gdy kompilator ustalił, że **może mieć wartość null**, kompilator wyświetli ostrzeżenie. Stan odwołania może **mieć wartość null** , chyba że kompilator może określić jeden z dwóch warunków:

1. Zmienna została ostatecznie przypisana do wartości innej niż null.
1. Zmienna lub wyrażenie zostało sprawdzone pod kątem wartości null przed usunięciem odwołania do niego.

Kompilator generuje ostrzeżenia za każdym razem, gdy użytkownik odwołuje się do zmiennej lub wyrażenia w stanie null, gdy jest włączony kontekst ostrzeżenia z **wartością** null. Ponadto są generowane ostrzeżenia, gdy możliwa jest zmienna **null** lub wyrażenie jest przypisywane do niezerowego typu odwołania w włączonym kontekście adnotacji dopuszczających wartość null.

## <a name="see-also"></a>Zobacz także

- [Specyfikacja typu referencyjnego dopuszczająca wartość null](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)
- [Samouczek wprowadzający do odwołań do wartości null](tutorials/nullable-reference-types.md)
- [Migrowanie istniejącej bazy kodu do odwołań do wartości null](tutorials/upgrade-to-nullable-references.md)
