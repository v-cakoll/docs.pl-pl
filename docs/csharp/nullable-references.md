---
title: Typy dopuszczające wartości null odwołań
description: Ten artykuł zawiera omówienie typów referencyjnych dopuszczającego wartość null, dodane w C# 8. Dowiesz się, jak ta funkcja zapewnia zabezpieczenie przed wyjątków odwołanie o wartości null dla nowych i istniejących projektów.
ms.date: 02/19/2019
ms.openlocfilehash: 9ce9efb890f0eff5a6c6747f96c143a4d093dbfb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61684045"
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

Z dodatkiem typy dopuszczające wartości null odwołań można zadeklarować zgodne z zamiarami użytkownika wyraźniej. `null` Wartość jest prawidłowym sposobem, aby reprezentować, że zmienna nie odwołuje się do wartości. Nie używaj tej funkcji, aby usunąć wszystkie `null` wartości w kodzie. Przeciwnie należy zadeklarować zgodne z zamiarami użytkownika do kompilatora i innymi deweloperami, które odczytują swój kod. DEKLARUJĄC zgodne z zamiarami użytkownika, kompilator informuje użytkownika, kiedy piszesz kod, który jest niezgodny z tym przeznaczeniem.

A **typu dopuszczającego wartość null odwołania** podano przy użyciu takiej samej składni jak [typy o wartości zerowalnej](programming-guide/nullable-types/index.md): `?` jest dołączany do typu zmiennej. Na przykład następującą deklarację zmiennej reprezentuje zmienną ciągu nullable `name`:

```csharp
string? name;
```

Jakakolwiek zmienna gdzie `?` nie jest dołączany do typu nazwa jest **typ niedopuszczający odwołania**. Obejmuje to wszystkich zmiennych typu odwołania w istniejącym kodzie włączenie tej funkcji.

Kompilator używa analizy statycznej, aby określić, czy odwołanie dopuszczającego wartość null jest znane z innych niż null. Kompilator wyświetla ostrzeżenie, jeśli użytkownik cofnie odwołanie odwołaniem dopuszczającego wartość null podczas może mieć wartości null. To zachowanie można zastąpić za pomocą **null forgiving operator** (`!`) po nazwie zmiennej. Na przykład, jeśli znasz `name` zmiennej nie jest null, ale kompilator generuje ostrzeżenie, można napisać następujący kod, aby zastąpić kompilatora analizy:

```csharp
name!.Length;
```

Można znaleźć szczegółowe informacje dotyczące tego operatora w [wersję roboczą typy dopuszczające wartości null odwołań](../../_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) propozycji specyfikację w witrynie GitHub.

## <a name="nullability-of-types"></a>Dopuszczanie wartości null dla typów

Dowolny typ odwołania może mieć jedną z czterech *nullabilities*, która opisuje, kiedy są generowane, ostrzeżenia:

- *Kolumną*: Nie można przypisać wartości null do zmiennych tego typu. Zmienne tego typu nie muszą być sprawdzone o wartości null, przed usunięciem odwołania.
- *Dopuszcza wartości null*: Wartość NULL można przypisać do zmiennych tego typu. Wyłuskanie zmiennych tego typu bez wcześniejszego sprawdzenia dla `null` powoduje, że ostrzeżenie.
- *Oblivious*: Jest to wstępneC# 8 stanu. Zmienne tego typu można wyłuskiwany lub bez ostrzeżenia.
- *Nieznany*: Zwykle jest to dla parametrów typu gdzie ograniczenia nie poinformować kompilator, że typ musi być *nullable* lub *niedopuszczające wartości null*.

Dopuszczanie wartości null typu w deklaracji zmiennej jest kontrolowana przez *nullable kontekstu* , w którym ta zmienna została zgłoszona.

## <a name="nullable-contexts"></a>Konteksty dopuszczającego wartość null

Konteksty dopuszczającego wartość null, Włącz szczegółową kontrolę dla jak kompilator interpretuje zmiennych typu odwołania. **Kontekstu annotation dopuszczający wartość null** z dowolnego źródła dany wiersz jest `enabled` lub `disabled`. Można potraktować przedC# 8 kompilatora jako kompilowania kodu w `disabled` nullable kontekstu: Dowolny typ odwołania może mieć wartości null. **Kontekstu nullable ostrzeżenia** może być ustawiona na `enabled`, `disabled`, lub `safeonly`. Kontekst ostrzeżenia dopuszczającego wartość null określa ostrzeżeń generowanych przez kompilator przy użyciu jego analizę przepływu.

Kontekst annotation dopuszczający wartość null i dopuszcza wartości null kontekstu Ostrzeżenie można ustawić dla projektu używającego `NullableContextOptions` elementu w Twojej `csproj` pliku. Ten element określa, jak kompilator interpretuje dopuszczania wartości null, typów i ostrzeżeń, które są generowane. Prawidłowe ustawienia to:

- `enable`: Kontekst annotation dopuszczający wartość null jest **włączone**. Kontekst ostrzeżenie dopuszczającego wartość null jest **włączone**.
  - Zmienne typu referencyjnego, `string` na przykład nie dopuszczają wartości.  Wszystkie ostrzeżenia dopuszczania wartości null są włączone.
- `disable`: Kontekst annotation dopuszczający wartość null jest **wyłączone**. Kontekst ostrzeżenie dopuszczającego wartość null jest **wyłączone**.
  - Zmienne typu referencyjnego są oblivious, podobnie jak wcześniejszych wersjach C#. Wszystkie ostrzeżenia dopuszczania wartości null są wyłączone.
- `safeonly`: Kontekst annotation dopuszczający wartość null jest **włączone**. Kontekst ostrzeżenie dopuszczającego wartość null jest **safeonly**.
  - Zmienne typu referencyjnego są kolumną. Wszystkie ostrzeżenia dopuszczania wartości null bezpieczeństwa są włączone.
- `warnings`: Kontekst annotation dopuszczający wartość null jest **wyłączone**. Kontekst ostrzeżenie dopuszczającego wartość null jest **włączone**.
  - Zmienne typu referencyjnego są oblivious. Wszystkie ostrzeżenia dopuszczania wartości null są włączone.
- `safeonlywarnings`: Kontekst annotation dopuszczający wartość null jest **wyłączone**. Kontekst ostrzeżenie dopuszczającego wartość null jest **safeonly**.
  - Zmienne typu referencyjnego są oblivious. Wszystkie ostrzeżenia dopuszczania wartości null bezpieczeństwa są włączone.

Dyrektywy umożliwia również ustawić te ten sam kontekst w dowolnym miejscu w projekcie:

- `#nullable enable`: Ustawia kontekst annotation dopuszczający wartość null i dopuszcza wartości null kontekst ostrzeżenie **włączone**.
- `#nullable disable`: Ustawia kontekst annotation dopuszczający wartość null i dopuszcza wartości null kontekst ostrzeżenie **wyłączone**.
- `#nullable safeonly`: Ustaw kontekst annotation dopuszczający wartość null **włączone**i kontekst ostrzeżenie do **safeonly**.
- `#nullable restore`: Przywraca ustawienia projektu kontekstu annotation dopuszczający wartość null i dopuszcza wartości null kontekstu ostrzeżenie.
- `#pragma warning disable nullable`: Ustaw kontekst ostrzeżenie dopuszczającego wartość null **wyłączone**.
- `#pragma warning enable nullable`: Ustaw kontekst ostrzeżenie dopuszczającego wartość null **włączone**.
- `#pragma warning restore nullable`: Przywraca ustawienia projektu kontekst ostrzeżenie dopuszczającego wartość null.
- `#pragma warning safeonly nullable`: Ustawia kontekst ostrzeżenie dopuszczającego wartość null **safeonly**.

Domyślne adnotacji dopuszcza wartości null i konteksty ostrzeżenia są `disabled`. Tej decyzji oznacza, że istniejący kod kompiluje bez zmian i wygenerowanie nowego ostrzeżenia.

Różnice między `enabled` i `safeonly` nullable kontekstów ostrzeżenia są ostrzeżenia dotyczące przypisywania dopuszczającego wartość null odwołanie do niedopuszczającej odwołania. Następujące przypisanie generuje ostrzeżenie w `enabled` ostrzeżenie kontekst, ale nie `safeonly` ostrzeżenie kontekstu. Jednak w drugim wierszu, gdzie `s` jest wyłuskiwany, generuje ostrzeżenie w `safeonly` kontekstu:

```csharp
string s = null; // warning when nullable warning context is enabled.
var txt = s.ToString(); // warning when nullable warnings context is safeonly, or enabled.
```

### <a name="nullable-annotation-context"></a>Kontekst annotation dopuszczający wartość null

Kompilator używa następujących reguł w kontekście wyłączone adnotacji dopuszczającego wartość null:

- Nie można zadeklarować odwołania dopuszczającego wartość null w kontekście wyłączone.
- Wszystkie zmienne odwołania można przypisać wartość null.
- Żadne ostrzeżenia nie są generowane, gdy zmienna typu odwołania jest wyłuskiwany.
- Operator forgiving o wartości null nie może służyć w kontekście wyłączone.

To zachowanie jest taka sama jak poprzednie wersje C#.

Kompilator używa następujących reguł w kontekście włączone adnotacji dopuszczającego wartość null:

- Jakakolwiek zmienna typu odwołania jest **dopuszcza odwołanie**.
- Bezpiecznie może zostać wyłuskany dowolnego odwołania do wartości null.
- Dowolny typ dopuszczający wartość null odwołanie (oznaczone przez `?` po typie w deklaracji zmiennej) może mieć wartości null. Analiza statyczna decyduje o tym, jeśli wartość jest znane jako inna niż null, po wyłuskaniu. W przeciwnym razie kompilator wyświetla ostrzeżenie.
- Aby zadeklarować, że odwołaniem dopuszczającego wartość null nie jest null, można użyć operatora forgiving o wartości null.

W kontekście włączone adnotacji dopuszczającego wartość null `?` deklaruje znak dołączany do typu referencyjnego **typu dopuszczającego wartość null odwołania**. **Operatora wartości null umorzenie** (`!`) może zostać dołączone do wyrażenia, aby zadeklarować, że wyrażenie nie ma wartości null.

## <a name="nullable-warning-context"></a>Dopuszcza wartości null kontekstu ostrzeżenie

Dopuszcza wartości null kontekstu ostrzeżenie różni się od kontekstu annotation dopuszczający wartość null. Ostrzeżenia mogą być włączone, nawet wtedy, gdy nowych adnotacji są wyłączone. Kompilator używa analizy statycznej przepływu, aby określić **wartość null, stan** jakiegokolwiek odniesienia. Stanu wartości null jest **nie null** lub **może być null** podczas *nullable kontekstu ostrzeżenie* nie jest **wyłączone**. Jeśli użytkownik cofnie odwołanie odwołanie gdy kompilator stwierdził, ma ona **może być null**, kompilatora ostrzega przed. Stan odwołania jest **może być null** chyba, że kompilator może określić jeden z warunków:

1. Zmienna zdecydowanie przypisany do wartości innej niż null.
1. Zmiennej lub wyrażenia został sprawdzony null przed do odwoływania się do niego.

Kompilator generuje ostrzeżenia, gdy użytkownik cofnie odwołanie zmiennej lub wyrażenia w **może być null** stan, gdy kontekst ostrzeżenie dopuszczającego wartość null jest `enabled` lub `safeonly`. Ponadto ostrzeżenia są generowane, gdy **może być null** zmiennej lub wyrażenia jest przypisany do typu odwołania kolumną w kontekście annotation dopuszczający wartość null `enabled`.

## <a name="learn-more"></a>Dowiedz się więcej

- [Specyfikacja Nullable odwołania do projektu](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-8.0/nullable-reference-types-specification.md)
- [Wprowadzenie do samouczka odwołania dopuszczającego wartość null](tutorials/nullable-reference-types.md)
- [Migrowanie istniejącej bazy kodu w celu odwołania dopuszczającego wartość null](tutorials/upgrade-to-nullable-references.md)
