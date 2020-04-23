---
title: Typy referencyjne dopuszczające wartość null
description: Ten artykuł zawiera omówienie typów odwołań nullable, dodane w języku C# 8.0. Dowiesz się, jak funkcja zapewnia bezpieczeństwo przed wyjątkami odwołania null dla nowych i istniejących projektów.
ms.technology: csharp-null-safety
ms.date: 04/21/2020
ms.openlocfilehash: 589118ffaa9ad39f000e3e5adf2896d114f68dd3
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82101982"
---
# <a name="nullable-reference-types"></a>Typy referencyjne dopuszczające wartość null

C# 8.0 wprowadza **typy odwołań nullable** i **typy odwołań niepodjętych do null,** które umożliwiają dokonywanie ważnych instrukcji dotyczących właściwości dla zmiennych typu odwołania:

- **Odwołanie nie ma być null**. Gdy zmienne nie powinny być null, kompilator wymusza reguły, które zapewniają, że można bezpiecznie wyłuskać te zmienne bez uprzedniego sprawdzenia, czy nie jest null:
  - Zmienna musi zostać zainicjowana do wartości innej niż null.
  - Zmiennej nigdy nie można `null`przypisać wartości .
- **Odwołanie może mieć wartość null**. Gdy zmienne mogą mieć wartość null, kompilator wymusza różne reguły, aby upewnić się, że poprawnie zaznaczono odwołanie null:
  - Zmienna może być wyłuskiwane tylko wtedy, gdy kompilator może zagwarantować, że wartość nie jest null.
  - Zmienne te mogą być inicjowane z wartością domyślną `null` i mogą być przypisane do wartości `null` w innym kodzie.

Ta nowa funkcja zapewnia znaczne korzyści w zakresie obsługi zmiennych referencyjnych we wcześniejszych wersjach języka C#, gdzie intencji projektu nie można określić na podstawie deklaracji zmiennej. Kompilator nie zapewnia bezpieczeństwa przed wyjątkami odwołania null dla typów odwołań:

- **Odwołanie może mieć wartość null**. Kompilator nie wydaje ostrzeżeń, gdy typ odwołania jest inicjowany do wartości null lub później przypisany do wartości null. Kompilator wydaje ostrzeżenia, gdy te zmienne są wyłuskiwane bez sprawdzania wartości null.
- **Przyjmuje się, że odwołanie nie jest zerowe.** Kompilator nie wydaje żadnych ostrzeżeń, gdy typy odwołań są wyłuskiwane. Kompilator wydaje ostrzeżenia, jeśli zmienna jest ustawiona na wyrażenie, które może mieć wartość null.

Te ostrzeżenia są emitowane w czasie kompilacji. Kompilator nie dodaje żadnych kontroli null lub innych konstrukcji środowiska uruchomieniowego w kontekście nullable. W czasie wykonywania odwołanie do nullable i odwołanie niepodjednalne są równoważne.

Z dodatkiem nullable typów odwołań, można zadeklarować swój zamiar jaśniej. Wartość `null` jest prawidłowy sposób do reprezentowania, że zmienna nie odwołuje się do wartości. Nie używaj tej funkcji, `null` aby usunąć wszystkie wartości z kodu. Zamiast tego należy zadeklarować zamiar do kompilatora i innych deweloperów, którzy czytają kod. Deklarując intencji, kompilator informuje podczas pisania kodu, który jest niezgodny z tym zamiarem.

**Typ odwołania z wartością null jest** odnotowywany przy użyciu tej samej składni co [typy wartości nullowalnych:](language-reference/builtin-types/nullable-value-types.md)a `?` jest dołączany do typu zmiennej. Na przykład następująca deklaracja zmiennej reprezentuje `name`zmienną ciągów dopuszczania do wartości null, :

```csharp
string? name;
```

Każda zmienna, w której `?` nie jest dołączana do nazwy typu, jest **typem odwołania niepodważalnym.** Obejmuje to wszystkie zmienne typu odwołania w istniejącym kodzie po włączeniu tej funkcji.

Kompilator używa analizy statycznej, aby ustalić, czy nullable odwołania jest znany jako null. Kompilator ostrzega, jeśli wyłuskanie odwołania nullable, gdy może być null. To zachowanie można zastąpić przy użyciu `!` [operatora wyrozumiałości zerowej](language-reference/operators/null-forgiving.md) o nazwie zmiennej. Na przykład jeśli wiesz, że `name` zmienna nie ma wartości null, ale kompilator generuje ostrzeżenie, możesz napisać następujący kod, aby zastąpić analizę kompilatora:

```csharp
name!.Length;
```

## <a name="nullability-of-types"></a>Niemożliwość nieważność typów

Każdy typ odwołania może mieć jedną z czterech *nullabilities*, która opisuje, kiedy są generowane ostrzeżenia:

- *Nonnullable:* Null nie można przypisać do zmiennych tego typu. Zmienne tego typu nie muszą być sprawdzane z wartością null przed dereferencing.
- *Nullable*: Null można przypisać do zmiennych tego typu. Dereferencing zmienne tego typu bez `null` uprzedniego sprawdzania przyczyn ostrzeżenie.
- *Oblivious*: Oblivious jest stanem pre-C# 8.0. Zmienne tego typu mogą być wyłuskiwane lub przypisywane bez ostrzeżeń.
- *Nieznany:* Nieznany jest zazwyczaj dla parametrów typu, gdzie ograniczenia nie informują kompilatora, że typ musi być *nullable* lub *nonnullable*.

Nullability typu w deklaracji zmiennej jest kontrolowana przez *kontekst nullable,* w którym zmienna jest zadeklarowana.

## <a name="nullable-contexts"></a>Konteksty możliwe do unieważnienia

Konteksty nullable włączyć precyzyjne sterowanie jak kompilator interpretuje zmienne typu odwołania. Kontekst **adnotacji z możliwością nullowania** danego wiersza źródłowego jest włączony lub wyłączony. Kompilator pre-C# 8.0 można myśleć jako kompilowanie całego kodu w kontekście wyłączonej wartości null: dowolny typ odwołania może mieć wartość null. **Kontekst ostrzeżenia nullable** może być również włączone lub wyłączone. Kontekst ostrzeżenia nullable określa ostrzeżenia generowane przez kompilator przy użyciu analizy przepływu.

Kontekst adnotacji z wartością null i kontekst ostrzeżenia o `Nullable` wartości null można ustawić dla projektu przy użyciu elementu w pliku *csproj.* Ten element konfiguruje sposób, w jaki kompilator interpretuje nullability typów i jakie ostrzeżenia są generowane. Prawidłowe ustawienia to:

- `enable`: Włączony **jest**kontekst adnotacji z możliwością null . Włączony jest kontekst ostrzeżenia o możliwości **anulowania**.
  - Zmienne typu odwołania, `string` na przykład, są nie można nullable.  Wszystkie ostrzeżenia o niemożności unieważnienia są włączone.
- `warnings`: Kontekst adnotacji z dopuszczalną wartością null jest **wyłączony**. Włączony jest kontekst ostrzeżenia o możliwości **anulowania**.
  - Zmienne typu odwołania są zapomniane. Wszystkie ostrzeżenia o niemożności unieważnienia są włączone.
- `annotations`: Włączony **jest**kontekst adnotacji z możliwością null . Kontekst ostrzeżenia o wartości nullable jest **wyłączony**.
  - Zmienne typu odwołania, ciąg na przykład, są nie można null. Wszystkie ostrzeżenia o niemożności unieważnienia są wyłączone.
- `disable`: Kontekst adnotacji z dopuszczalną wartością null jest **wyłączony**. Kontekst ostrzeżenia o wartości nullable jest **wyłączony**.
  - Zmienne typu odwołania są zapomniane, podobnie jak wcześniejsze wersje języka C#. Wszystkie ostrzeżenia o niemożności unieważnienia są wyłączone.

**Przykład:**

```xml
<Nullable>enable</Nullable>
```

Można również użyć dyrektyw, aby ustawić te same konteksty w dowolnym miejscu w projekcie:

- `#nullable enable`: Ustawia włączona kontekst adnotacji z możliwością nullowania i kontekst ostrzeżenia o wartości **null.**
- `#nullable disable`: Ustawia kontekst adnotacji z dopuszczalną **disabled**do wartości null i kontekst ostrzeżenia o wartości null.
- `#nullable restore`: Przywraca kontekst adnotacji z dopuszczalną do wartości null i kontekst ostrzeżenia o wartości null do ustawień projektu.
- `#nullable disable warnings`: Ustaw wyłączony kontekst ostrzeżenia o wartości nullable **.**
- `#nullable enable warnings`: Ustaw włączony kontekst ostrzeżenia o możliwości **null.**
- `#nullable restore warnings`: Przywraca kontekst ostrzeżenia o wartości nullable do ustawień projektu.
- `#nullable disable annotations`: Ustaw wyłączony kontekst adnotacji z dopuszczaniem do wartości **null.**
- `#nullable enable annotations`: Ustaw włączony kontekst adnotacji z możliwością wartości **null.**
- `#nullable restore annotations`: Przywraca kontekst ostrzeżenia adnotacji do ustawień projektu.

Domyślnie można anulować adnotacji i konteksty ostrzeżenia są **wyłączone,** w tym nowych projektów. Oznacza to, że istniejący kod kompiluje się bez zmian i bez generowania nowych ostrzeżeń.

Te opcje zapewniają dwie różne strategie, aby [zaktualizować istniejącą bazę kodu,](nullable-migration-strategies.md) aby użyć typów odwołań z możliwością null.

## <a name="nullable-annotation-context"></a>Kontekst adnotacji z dopuszczalną wartością null

Kompilator używa następujących reguł w kontekście adnotacji wyłączonej z wartością null:

- Nie można zadeklarować odwołań nullable w kontekście wyłączone.
- Wszystkie zmienne referencyjne mogą być przypisane wartość null.
- Żadne ostrzeżenia nie są generowane, gdy zmienna typu odwołania jest wyłuskiwane.
- Operator wyrozumiały null nie może być używany w kontekście wyłączone.

Zachowanie jest taka sama jak poprzednie wersje języka C#.

Kompilator używa następujących reguł w włączonym kontekście adnotacji z możliwością null:

- Każda zmienna typu odwołania jest **odwołaniem niepodjętym do wartości null.**
- Wszelkie odwołania niepodjednania nienastępujne mogą być wyłuskiwane bezpiecznie.
- Każdy typ odwołania nullable `?` (zauważyć po typ w deklaracji zmiennej) może mieć wartość null. Analiza statyczna określa, czy wartość jest znana jako null, gdy jest wyłuskiwana. Jeśli nie, kompilator ostrzega.
- Operatoru wyrozumiałości zerowej można użyć, aby zadeklarować, że odwołanie do null nie jest null.

W włączonym kontekście adnotacji `?` z możliwością nullowania znak dołączony do typu odwołania deklaruje **typ odwołania z możliwością null.** `!` **Operator odpuszczający wartość null** może zostać dołączona do wyrażenia, aby zadeklarować, że wyrażenie nie jest null.

## <a name="nullable-warning-context"></a>Kontekst ostrzeżenia, który można unieważnić

Kontekst ostrzeżenia o wartości nullable różni się od kontekstu adnotacji możliwej do unieważnienia. Ostrzeżenia można włączyć nawet wtedy, gdy nowe adnotacje są wyłączone. Kompilator używa analizy przepływu statycznego, aby określić **stan null** dowolnego odwołania. Stan null nie jest **null** lub **może null,** gdy kontekst ostrzeżenia *nullable* nie jest **wyłączona.** Jeśli odwołanie odwołuje się, gdy kompilator ustalił, że może być **null,** kompilator ostrzega. Stan odwołania jest **może null,** chyba że kompilator może określić jeden z dwóch warunków:

1. Zmienna została zdecydowanie przypisana do wartości innej niż null.
1. Zmienna lub wyrażenie zostało sprawdzone względem null przed odsyłaniem do niej.

Kompilator generuje ostrzeżenia podczas wyłuskiwki zmiennej lub wyrażenia, które **może być null** w kontekście ostrzeżenia nullable. Ponadto kompilator generuje ostrzeżenia, gdy niesyklny typ odwołania jest przypisany do **zmiennej lub** wyrażenia może null w włączonym kontekście adnotacji można anulować.

## <a name="attributes-describe-apis"></a>Atrybuty opisują interfejsy API

Dodaj atrybuty do interfejsów API, które zapewniają kompilatorowi więcej informacji o tym, kiedy argumenty lub zwracane wartości mogą lub nie mogą mieć wartości null. Więcej informacji na temat tych atrybutów można dowiedzieć się w naszym artykule w odniesieniu do języka obejmującego [atrybuty nullable](language-reference/attributes/nullable-analysis.md). Te atrybuty są dodawane do bibliotek platformy .NET w bieżących i nadchodzących wersjach. Najczęściej używane interfejsy API są aktualizowane jako pierwsze.

## <a name="see-also"></a>Zobacz też

- [Specyfikacja typów odwołań z nieważność](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)
- [Samouczek wprowadzający do nullable references](tutorials/nullable-reference-types.md)
- [Migrowanie istniejącej bazy kodu do odwołań z nullable](tutorials/upgrade-to-nullable-references.md)
