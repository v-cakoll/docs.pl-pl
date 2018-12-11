---
title: Typy dopuszczające wartości null odwołań
description: Ten artykuł zawiera omówienie typów referencyjnych dopuszczającego wartość null, dodane w C# 8. Dowiesz się, jak ta funkcja zapewnia zabezpieczenie przed wyjątków odwołanie o wartości null dla nowych i istniejących projektów.
ms.date: 12/03/2018
ms.openlocfilehash: f18fc9dbce2f934b216b3eb0b80658fec6b44c46
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53156487"
---
# <a name="nullable-reference-types"></a>Typy dopuszczające wartości null odwołań

C#wprowadza 8.0 **typy dopuszczające wartości null odwołań** i **typów referencyjnych dopuszcza** , umożliwiają wykonywanie instrukcji ważne informacje o właściwościach dla zmiennych typu odwołania:

- **Odwołanie nie może mieć wartości null**. Gdy zmienne nie powinien mieć wartość null, kompilator wymusza reguły, które upewnij się, można bezpiecznie wyłuskania te zmienne bez uprzedniego sprawdzenia, czy nie ma wartości null:
  - Zmienna musi zostać zainicjowany do wartości innej niż null.
  - Zmienna może być nigdy przypisywana wartość `null`.
- **Odwołanie może mieć wartości null**. Gdy zmienne mogą mieć wartości null, kompilator wymuszają różne reguły, aby upewnić się, że poprawnie sprawdzeniu odwołania zerowego:
  - Zmienna może zostać wyłuskany tylko, gdy kompilator może zagwarantować, że wartość nie jest null.
  - Te zmienne mogą być inicjowane przy użyciu domyślnego `null` wartości i mieć przypisaną taką wartość `null` w innym kodzie.

Ta nowa funkcja zapewnia znaczące korzyści związane nad obsługą zmienne odwołujące się do we wcześniejszych wersjach programu C# gdzie celem projektu nie można określić w deklaracji zmiennej. Kompilator nie udostępnia zabezpieczenie przed wyjątki odwołanie o wartości null dla typów odwołań:

- **Odwołanie może mieć wartości null**. Są wyświetlane nie ostrzeżenia, gdy typ odwołania jest inicjowane na wartość null lub później przypisane do wartości null.
- **Przyjęto, że odwołanie nie może być null**. Kompilator nie generuje żadnych ostrzeżeń podczas wyłuskiwany są typami odwołań. (Z odwołaniami dopuszczającego wartość null, kompilator generuje ostrzeżenia zawsze wtedy, gdy użytkownik cofnie odwołanie zmienna, która może mieć wartości null).

A **typu dopuszczającego wartość null odwołania** podano przy użyciu takiej samej składni jak [typy o wartości zerowalnej](programming-guide/nullable-types/index.md): `?` jest dołączany do typu zmiennej. Na przykład następującą deklarację zmiennej reprezentuje zmienną ciągu nullable `name`:

```csharp
string? name;
```

Jakakolwiek zmienna gdzie `?` nie jest dołączany do typu nazwa jest **typ niedopuszczający odwołania**. Obejmuje to wszystkich zmiennych typu odwołania w istniejącym kodzie włączenie tej funkcji.

Kompilator używa analizy statycznej, aby określić, czy odwołanie dopuszczającego wartość null jest znane z innych niż null. Kompilator wyświetla ostrzeżenie, jeśli użytkownik cofnie odwołanie odwołaniem dopuszczającego wartość null podczas może mieć wartości null. To zachowanie można zastąpić za pomocą **null forgiving operator** (`!`) po nazwie zmiennej. Na przykład, jeśli znasz `name` zmiennej nie jest null, ale kompilator generuje ostrzeżenie, można napisać następujący kod, aby zastąpić kompilatora analizy:

```csharp
name!.Length;
```

Można znaleźć szczegółowe informacje dotyczące tego operatora w [wersję roboczą typy dopuszczające wartości null odwołań](https://github.com/dotnet/csharplang/blob/master/proposals/nullable-reference-types-specification.md#the-null-forgiving-operator) propozycji specyfikację w witrynie GitHub.

## <a name="nullable-contexts"></a>Konteksty dopuszczającego wartość null

Konteksty dopuszczającego wartość null, Włącz szczegółową kontrolę dla jak kompilator interpretuje zmiennych typu odwołania. Dopuszcza wartości null kontekst wiersza danego źródła jest `enabled` lub `disabled`. Można potraktować przedC# 8 kompilatora jako kompilowania kodu w `disabled` nullable kontekstu: Dowolny typ odwołania może mieć wartości null. Ostrzeżenia nie są generowane, gdy zmienne typu referencyjnego jest wyłuskiwany.

Kontekst dopuszczającego wartość null jest kontrolowany za pomocą nowej dyrektywy pragma:

- `#nullable enable` Ustawia kontekst dopuszcza wartości null na włączony.
- `#nullable disable` Ustawia kontekst dopuszcza wartości null na wyłączone.

Domyślny kontekst dopuszczającego wartość null jest `disabled`. Tej decyzji oznacza, że istniejący kod kompiluje bez zmian i wygenerowanie nowego ostrzeżenia.

Kompilator używa następujących reguł w kontekście nullable wyłączone:

- Nie można zadeklarować odwołania dopuszczającego wartość null w kontekście wyłączone.
- Wszystkie zmienne odwołania można przypisać wartość null.
- Żadne ostrzeżenia nie są generowane, gdy zmienna typu odwołania jest wyłuskiwany.
- Operator forgiving o wartości null nie może służyć w kontekście wyłączone.

To zachowanie jest taka sama jak poprzednie wersje C#.

Kompilator używa następujących reguł w kontekście nullable włączone:

- Jakakolwiek zmienna typu odwołania jest **dopuszcza odwołanie**.
- Bezpiecznie może zostać wyłuskany dowolnego odwołania do wartości null.
- Dowolny typ dopuszczający wartość null odwołanie (oznaczone przez `?` po typie w deklaracji zmiennej) może mieć wartości null. Analiza statyczna decyduje o tym, jeśli wartość jest znane jako inna niż null, po wyłuskaniu. W przeciwnym razie kompilator wyświetla ostrzeżenie.
- Aby zadeklarować, że odwołaniem dopuszczającego wartość null nie jest null, można użyć operatora forgiving o wartości null.

Bardziej rozbudowane gramatyki proponuje się wprowadzenie dla kontekstów dopuszcza wartości null i będzie dostępna w przyszłych wersjach zapoznawczych. Aby uzyskać więcej informacji na temat kontekstów dopuszczającego wartość null, zobacz [Specyfikacja odwołania nullable](https://github.com/dotnet/csharplang/blob/master/proposals/nullable-reference-types-specification.md#nullable-contexts) projektu.

## <a name="null-states-of-nullable-references"></a>Stany null odwołań dopuszczającego wartość null

Kompilator używa analizy statycznej, aby określić **wartość null, stan** jakiegokolwiek odniesienia dopuszczającego wartość null. Stan o wartości null jest **nie null** lub **może być null**. Jeśli użytkownik cofnie odwołanie odwołaniem dopuszczającego wartość null podczas kompilator stwierdził, ma ona **może być null**, kompilator wyświetla ostrzeżenie. Stan odwołania dopuszczającego wartość null jest **może być null** chyba, że kompilator może określić jeden z warunków:

1. Zmienna zdecydowanie przypisany do wartości innej niż null.
1. Przed usuwając odwołanie do zmiennej został sprawdzony o wartości null.

Kompilator wymusza, że nigdy nie można ustawić odwołania niedopuszczającej wartości null. Należy zainicjować je na wartość inną niż null. Jeśli nie, kompilator wyświetla ostrzeżenie, że odwołanie do wartości null nie zainicjowano. Kompilator również ostrzega, gdy przypisać wartości null odwołanie do odwołania dopuszczającego wartość null **może mieć wartości null**. Oznacza to, innych niż null odwołanie do odwołania dopuszczającego wartość NULL można przypisywać tylko, jeśli odniesienie dopuszczającego wartość null nie jest **nie null**.

## <a name="learn-more"></a>Dowiedz się więcej

- [Specyfikacja Nullable odwołania do projektu](https://github.com/dotnet/csharplang/blob/master/proposals/nullable-reference-types-specification.md)
- [Wprowadzenie do samouczka odwołania dopuszczającego wartość null](tutorials/nullable-reference-types.md)
