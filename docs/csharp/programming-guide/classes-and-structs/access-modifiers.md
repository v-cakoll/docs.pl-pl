---
title: Modyfikatory dostępu — przewodnik programowania C#
ms.date: 03/08/2020
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: 749d53344a2518966cfa5d937069ba73dfd6be8f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628231"
---
# <a name="access-modifiers-c-programming-guide"></a>Modyfikatory dostępu (Przewodnik programowania w języku C#)

Wszystkie typy i elementy członkowskie typu mają poziom ułatwień dostępu. Poziom ułatwień dostępu określa, czy mogą być używane z innego kodu w zestawie lub innych zestawów. Użyj następujących modyfikatorów dostępu, aby określić dostępność typu lub elementu członkowskiego podczas deklarowania go:

- [public](../../language-reference/keywords/public.md): Typ lub element członkowski mogą być dostępne przez inny kod w tym samym zestawie lub innego zestawu, który odwołuje się do niego.
- [prywatny](../../language-reference/keywords/private.md): Typ lub element członkowski jest `class` dostępny `struct`tylko za pomocą kodu w tym samym lub .
- [protected](../../language-reference/keywords/protected.md): Typ lub element członkowski mogą `class`być dostępne `class` tylko przez kod `class`w tym samym lub w tym, który pochodzi z tego .
- [wewnętrzny](../../language-reference/keywords/internal.md): Typ lub element członkowski jest dostępny za pomocą dowolnego kodu w tym samym zestawie, ale nie z innego zestawu.
- [chronione wewnętrzne:](../../language-reference/keywords/protected-internal.md)Typ lub element członkowski mogą być dostępne przez dowolny kod w `class` zestawie, w którym jest zadeklarowany, lub z wewnątrz pochodną w innym zestawie.
- [chronione prywatne:](../../language-reference/keywords/private-protected.md)Typ lub element członkowski są dostępne tylko w `class` jego zestawu deklaratywnego, przez kod w tym samym lub w typie, który pochodzi od tego `class`.

W poniższych przykładach pokazano, jak określić modyfikatory dostępu dla typu i elementu członkowskiego:

[!code-csharp[PublicAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#PublicAccess)]

Nie wszystkie modyfikatory dostępu są prawidłowe dla wszystkich typów lub elementów członkowskich we wszystkich kontekstach. W niektórych przypadkach dostępność elementu członkowskiego typu jest ograniczona przez dostępność jego typu zawierającego.

## <a name="class-and-struct-accessibility"></a>Dostępność klasy i struktury  

Klasy i struktury zadeklarowane bezpośrednio w obszarze nazw (innymi słowy, które nie są zagnieżdżone w innych klasach lub strukturach) mogą być albo. `public` `internal` `Internal`jest ustawieniem domyślnym, jeśli nie określono modyfikatora dostępu.  

Elementy członkowskie struktury, w tym klasy zagnieżdżone i struktury, mogą być zadeklarowane `public`, `internal`lub `private`. Elementy członkowskie klasy, w tym klasy zagnieżdżone i struktury, mogą być `public`, `protected internal`, `protected`, `internal`, `private protected`lub `private`. Klasy i elementy członkowskie struktury, w tym klasy `private` zagnieżdżone i struktury, mają domyślnie dostęp. Prywatne typy zagnieżdżone nie są dostępne spoza typu zawierającego.

Klasy pochodne nie mogą mieć większej dostępności niż ich typy podstawowe. Nie można zadeklarować klasy `B` publicznej, która pochodzi `A`z klasy wewnętrznej . Jeśli jest to dozwolone, miałoby to wpływ `internal` na `A` upublicznienie, `A` ponieważ wszyscy `protected` lub członkowie są dostępni z klasy pochodnej.

Można włączyć określone inne zestawy, aby uzyskać `InternalsVisibleToAttribute`dostęp do typów wewnętrznych za pomocą pliku . Aby uzyskać więcej informacji, zobacz [Zestawy znajomych](../../../standard/assembly/friend.md).

## <a name="class-and-struct-member-accessibility"></a>Dostępność klasy i elementu członkowskiego struktury  

Elementy członkowskie klasy (w tym klasy zagnieżdżone i struktury) można zadeklarować za pomocą dowolnego z sześciu typów dostępu. Elementy członkowskie struktury nie mogą `protected` `protected internal`być `private protected` zadeklarowane jako , lub struktury nie obsługują dziedziczenia.

Zwykle dostępność elementu członkowskiego nie jest większa niż dostępność typu, który go zawiera. Jednak element `public` członkowski klasy wewnętrznej może być dostępny spoza zestawu, jeśli element członkowski implementuje metody interfejsu lub zastępuje metody wirtualne, które są zdefiniowane w publicznej klasie podstawowej.

Typ dowolnego pola członkowskiego, właściwości lub zdarzenia musi być co najmniej tak samo dostępny jak sam element członkowski. Podobnie typ zwracany i typy parametrów dowolnej metody, indeksatora lub delegata muszą być co najmniej tak samo dostępne jak sam element członkowski. Na przykład nie można mieć `public` `M` metody, która `C` zwraca `C` klasę, chyba że jest również `public`. Podobnie nie można mieć `protected` właściwości `A` typu, `A` jeśli `private`jest zadeklarowany jako .

Operatory zdefiniowane przez użytkownika muszą `public` `static`być zawsze deklarowane jako i . Aby uzyskać więcej informacji, zobacz [Przeciążenie operatora](../../language-reference/operators/operator-overloading.md).

Finalizatory nie mogą mieć modyfikatorów ułatwień dostępu.

Aby ustawić poziom dostępu `class` `struct` dla lub członka, dodaj odpowiednie słowo kluczowe do deklaracji elementu członkowskiego, jak pokazano w poniższym przykładzie.

[!code-csharp[MethodAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#MethodAccess)]

## <a name="other-types"></a>Inne typy

Interfejsy zadeklarowane bezpośrednio w `public` przestrzeni `internal` nazw może być lub, podobnie jak `internal` klasy i struktury, interfejsy domyślnie dostęp. Elementy członkowskie `public` interfejsu są domyślnie, ponieważ celem interfejsu jest umożliwienie innym typom dostępu do klasy lub struktury. Deklaracje elementów członkowskich interfejsu mogą zawierać wszelkie modyfikator dostępu. Jest to najbardziej przydatne w przypadku metod statycznych, aby zapewnić typowe implementacje potrzebne przez wszystkich implementatorów klasy.

Elementy członkowskie wyliczenia są zawsze `public`, i nie modyfikatory dostępu mogą być stosowane.

Delegaci zachowują się jak klasy i struktury. Domyślnie mają `internal` dostęp, gdy zadeklarowane bezpośrednio `private` w obszarze nazw i dostęp po zagnieżdżonych.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Klasy i struktury](./index.md)
- [Interfejsy](../interfaces/index.md)
- [Prywatny](../../language-reference/keywords/private.md)
- [Publicznego](../../language-reference/keywords/public.md)
- [Wewnętrznego](../../language-reference/keywords/internal.md)
- [protected](../../language-reference/keywords/protected.md)
- [protected internal](../../language-reference/keywords/protected-internal.md)
- [private protected](../../language-reference/keywords/private-protected.md)
- [Klasa](../../language-reference/keywords/class.md)
- [Struct](../../language-reference/builtin-types/struct.md)
- [Interfejs](../../language-reference/keywords/interface.md)
