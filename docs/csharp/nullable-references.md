---
title: Typy referencyjne dopuszczające wartość null
description: Ten artykuł zawiera omówienie typów odwołań nullable, dodane w języku C# 8.0. Dowiesz się, jak funkcja zapewnia bezpieczeństwo przed wyjątkami odwołania zerowego dla nowych i istniejących projektów.
ms.technology: csharp-null-safety
ms.date: 02/19/2019
ms.openlocfilehash: bb4c2b6951a38eeb705c7de50ef5d9645350e336
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399428"
---
# <a name="nullable-reference-types"></a>Typy referencyjne dopuszczające wartość null

C# 8.0 wprowadza **typy odwołań nullable** i **typy odwołań niedopuszczające wartości null,** które umożliwiają tworzenie ważnych instrukcji dotyczących właściwości zmiennych typu odwołania:

- **Odwołanie nie ma być null**. Gdy zmienne nie powinny mieć wartości null, kompilator wymusza reguły, które zapewniają, że można bezpiecznie wyłuskować te zmienne bez uprzedniego sprawdzenia, czy nie jest null:
  - Zmienna musi zostać zainicjowana do wartości niezerowej.
  - Zmiennej nigdy nie można `null`przypisać wartości .
- **Odwołanie może mieć wartość null**. Gdy zmienne mogą mieć wartość null, kompilator wymusza różne reguły, aby upewnić się, że poprawnie zaznaczono odwołanie null:
  - Zmienna może być wyłuskana tylko wtedy, gdy kompilator może zagwarantować, że wartość nie jest null.
  - Zmienne te mogą być inicjowane `null` z wartością domyślną `null` i mogą być przypisane wartość w innym kodzie.

Ta nowa funkcja zapewnia znaczne korzyści w zakresie obsługi zmiennych referencyjnych we wcześniejszych wersjach języka C#, gdzie nie można określić intencji projektu na podstawie deklaracji zmiennej. Kompilator nie zapewnia bezpieczeństwa przed wyjątkami odwołania null dla typów odwołań:

- **Odwołanie może mieć wartość null**. Nie jest wydawane żadne ostrzeżenie, gdy typ odwołania jest inicjowany do wartości null lub null jest później przypisany do niego.
- **Przyjmuje się, że odwołanie nie jest null**. Kompilator nie wydaje żadnych ostrzeżeń, gdy typy odwołań są wyłuskowane. (Z odwołaniami nullable kompilator generuje ostrzeżenia za każdym razem, gdy wyłudzanie zmiennej, która może być null).

Z dodatkiem typów odwołań nullable można zadeklarować zamiar jaśniej. Wartość `null` jest prawidłowym sposobem reprezentowania, że zmienna nie odwołuje się do wartości. Nie używaj tej funkcji, `null` aby usunąć wszystkie wartości z kodu. Zamiast tego należy zadeklarować zamiar do kompilatora i innych deweloperów, które czytają kod. Deklarując zamiar, kompilator informuje o zapisaniu kodu, który jest niezgodny z tym zamiarem.

**Typ odwołania z wartością null** jest odnotowany przy użyciu tej samej składni co typy wartości [null:](language-reference/builtin-types/nullable-value-types.md)a `?` jest dołączany do typu zmiennej. Na przykład następująca deklaracja zmiennej reprezentuje `name`zmienną ciągu z wartością null, :

```csharp
string? name;
```

Każda zmienna, w której `?` nie jest dołączona do nazwy typu, jest **typem odwołania niepodlegającym wartości null.** Obejmuje to wszystkie zmienne typu odwołania w istniejącym kodzie po włączeniu tej funkcji.

Kompilator używa analizy statycznej, aby ustalić, czy odwołanie nullable jest znany jako non-null. Kompilator ostrzega, jeśli odniesiesz odwołanie unieważnione, gdy może być null. To zachowanie można zastąpić za pomocą `!` [operatora wyrozumiałego dla wartości null](language-reference/operators/null-forgiving.md) po nazwie zmiennej. Na przykład jeśli wiesz, że `name` zmienna nie jest null, ale kompilator generuje ostrzeżenie, można napisać następujący kod, aby zastąpić analizę kompilatora:

```csharp
name!.Length;
```

## <a name="nullability-of-types"></a>Nieważność typów

Każdy typ odwołania może mieć jeden z czterech *nullabilities*, który opisuje, kiedy generowane są ostrzeżenia:

- *Nieunieważnialne:* Null nie można przypisać do zmiennych tego typu. Zmienne tego typu nie muszą być sprawdzane wartości null przed dereferencing.
- *Null:* Null można przypisać do zmiennych tego typu. Dereferencing zmiennych tego typu bez `null` uprzedniego sprawdzania przyczyn ostrzeżenie.
- *Oblivious*: Jest to stan pre-C# 8.0. Zmienne tego typu mogą być wyłuskowane lub przypisane bez ostrzeżeń.
- *Nieznany:* Jest to zazwyczaj dla parametrów typu, gdzie ograniczenia nie informują kompilatora, że typ musi być *unieważnialny* lub *nieunieważnialny*.

Nullability typu w deklaracji zmiennej jest kontrolowana przez *kontekst nullable,* w którym zmienna jest zadeklarowana.

## <a name="nullable-contexts"></a>Konteksty podlegające wartości null

Konteksty null umożliwiają precyzyjną kontrolę, jak kompilator interpretuje zmienne typu odwołania. **Kontekst adnotacji null** dowolnego danego wiersza źródłowego jest włączony lub wyłączony. Kompilator pre-C# 8.0 można myśleć jako kompilacji całego kodu w kontekście wyłączone nullable: każdy typ odwołania może być null. **Kontekst ostrzeżeń unieważnianych** może być również włączony lub wyłączony. Kontekst ostrzeżeń nullable określa ostrzeżenia generowane przez kompilator przy użyciu jego analizy przepływu.

Kontekst adnotacji nullable i nullable kontekście ostrzeżenia `Nullable` można ustawić dla projektu przy użyciu elementu w pliku *csproj.* Ten element konfiguruje sposób, w jaki kompilator interpretuje nullability typów i jakie ostrzeżenia są generowane. Prawidłowe ustawienia to:

- `enable`: **Włączony**jest kontekst adnotacji nullable . Kontekst ostrzeżenia nullable jest **włączona**.
  - Zmienne typu odwołania, `string` na przykład, nie są nullable.  Wszystkie ostrzeżenia o nullability są włączone.
- `warnings`: Kontekst adnotacji nullable jest **wyłączony**. Kontekst ostrzeżenia nullable jest **włączona**.
  - Zmienne typu odwołania są nieświadome. Wszystkie ostrzeżenia o nullability są włączone.
- `annotations`: **Włączony**jest kontekst adnotacji nullable . Kontekst ostrzeżenia nullable jest **wyłączony**.
  - Zmienne typu odwołania, ciąg na przykład, są niedopuszczające wartości null. Wszystkie ostrzeżenia o nullability są wyłączone.
- `disable`: Kontekst adnotacji nullable jest **wyłączony**. Kontekst ostrzeżenia nullable jest **wyłączony**.
  - Zmienne typu odwołania są nieświadome, podobnie jak wcześniejsze wersje języka C#. Wszystkie ostrzeżenia o nullability są wyłączone.

**Przykład:**

```xml
<Nullable>enable</Nullable>
```

Można również użyć dyrektyw, aby ustawić te same konteksty w dowolnym miejscu w projekcie:

- `#nullable enable`: Ustawia kontekst adnotacji null able i nullable warning context to **enabled**.
- `#nullable disable`: Ustawia kontekst adnotacji null able i nullable warning context to **disabled**.
- `#nullable restore`: Przywraca kontekst adnotacji nullable i nullable kontekście ostrzeżenia do ustawień projektu.
- `#nullable disable warnings`: Ustaw kontekst ostrzeżenia nullable na **wyłączone**.
- `#nullable enable warnings`: Ustaw kontekst ostrzeżenia nullable **włączone**.
- `#nullable restore warnings`: Przywraca kontekst ostrzeżenia nullable do ustawień projektu.
- `#nullable disable annotations`: Ustaw kontekst adnotacji nullable na **wyłączone**.
- `#nullable enable annotations`: Ustaw kontekst adnotacji null able **włączona**.
- `#nullable restore annotations`: Przywraca kontekst ostrzeżenia adnotacji do ustawień projektu.

Domyślnie konteksty adnotacji i ostrzeżeń null są **wyłączone**. Oznacza to, że istniejący kod kompiluje się bez zmian i bez generowania żadnych nowych ostrzeżeń.

## <a name="nullable-annotation-context"></a>Kontekst adnotacji z możliwością null

Kompilator używa następujących reguł w kontekście adnotacji z możliwością null:

- Nie można zadeklarować odwołania nullable w kontekście wyłączony.
- Wszystkim zmiennym referencyjnym można przypisać wartość null.
- Nie są generowane żadne ostrzeżenia, gdy zmienna typu odwołania jest wywaodowane.
- Operator wyrozumiały nie może być używany w kontekście wyłączonym.

Zachowanie jest takie samo jak poprzednie wersje języka C#.

Kompilator używa następujących reguł w włączonym kontekście adnotacji nullable:

- Każda zmienna typu odwołania jest **odwołaniem niepodlegającym wartości null.**
- Wszelkie odwołania niepodlegające unieważnieniu mogą być bezpiecznie wyłuskowane.
- Każdy typ odwołania z wartością null (odnotowany po `?` typie w deklaracji zmiennej) może mieć wartość null. Analiza statyczna określa, czy wartość jest znana jako niezerowa, gdy jest wyłuskwana. Jeśli nie, kompilator ostrzega.
- Operator jest wyrozumiały, aby zadeklarować, że odwołanie unieważnione nie jest null.

W włączonym kontekście adnotacji `?` nullable znak dołączony do typu odwołania deklaruje **typ odwołania możliwy do przeliczenia wartości null**. `!` **Operator wyrozumiały null** mogą być dołączone do wyrażenia, aby zadeklarować, że wyrażenie nie jest null.

## <a name="nullable-warning-context"></a>Kontekst ostrzeżenia unieważnianego

Kontekst ostrzeżenia nulljest inny od kontekstu adnotacji nullable. Ostrzeżenia można włączyć nawet wtedy, gdy nowe adnotacje są wyłączone. Kompilator używa analizy przepływu statycznego do określenia **stanu zerowego** dowolnego odwołania. Stan null nie jest **null** lub **może null,** gdy kontekst ostrzeżenia *nullable* nie jest **wyłączona**. Jeśli wyłusk odwołania, gdy kompilator ustalił, że może to **null**, kompilator ostrzega. Stan odwołania jest **może null,** chyba że kompilator można określić jeden z dwóch warunków:

1. Zmienna została zdecydowanie przypisana do wartości niezerowej.
1. Zmienna lub wyrażenie zostało sprawdzone względem wartości null przed odwiązaniem się od niej.

Kompilator generuje ostrzeżenia za każdym razem, gdy wyłudzisz zmienną lub wyrażenie **m.in.** Ponadto ostrzeżenia są generowane, gdy **może** null zmiennej lub wyrażenia jest przypisany do typu odwołania niemożliwy chyliń w włączonym kontekście adnotacji nullable.

## <a name="see-also"></a>Zobacz też

- [Projekt specyfikacji typów odwołań nullable](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)
- [Intro do nullable odwołania samouczek](tutorials/nullable-reference-types.md)
- [Migracja istniejącej bazy kodu do odwołań podlegających wartości null](tutorials/upgrade-to-nullable-references.md)
