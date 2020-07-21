---
title: Modyfikatory dostępu — Przewodnik programowania w języku C#
description: Wszystkie typy i elementy członkowskie typu w języku C# mają poziom dostępności, który kontroluje, czy mogą być używane z innego kodu. Przejrzyj tę listę modyfikatorów dostępu.
ms.date: 03/08/2020
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: 557f5d9f302b08d32896b462e86ce1d96710ff36
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474530"
---
# <a name="access-modifiers-c-programming-guide"></a>Modyfikatory dostępu (Przewodnik programowania w języku C#)

Wszystkie typy i elementy członkowskie typu mają poziom dostępności. Poziom dostępności kontroluje, czy mogą być używane z innego kodu w zestawie lub w innych zestawach. Użyj następujących modyfikatorów dostępu, aby określić dostępność typu lub elementu członkowskiego podczas deklarowania:

- [Public](../../language-reference/keywords/public.md): dostęp do typu lub elementu członkowskiego można uzyskać za pomocą dowolnego innego kodu w tym samym zestawie lub w innym zestawie, który odwołuje się do niego.
- [prywatne](../../language-reference/keywords/private.md): dostęp do typu lub elementu członkowskiego można uzyskać tylko za pomocą kodu w tym samym `class` lub `struct` .
- [chronione](../../language-reference/keywords/protected.md): typ lub element członkowski można uzyskać dostęp tylko do kodu w tym samym `class` lub w `class` odróżnieniu od tego, który jest pochodny `class` .
- [wewnętrzny](../../language-reference/keywords/internal.md): dostęp do typu lub elementu członkowskiego można uzyskać za pomocą dowolnego kodu w tym samym zestawie, ale nie z innego zestawu.
- [chroniona wewnętrznie](../../language-reference/keywords/protected-internal.md): typ lub element członkowski może być dostępny przez dowolny kod w zestawie, w którym jest zadeklarowany, lub z elementu pochodnego `class` w innym zestawie.
- [chroniona prywatnie](../../language-reference/keywords/private-protected.md): typ lub członek jest dostępny tylko w obrębie swojego zestawu deklarującego, przez kod w tym samym `class` lub w typie, który pochodzi od tego `class` .

W poniższych przykładach pokazano, jak określić Modyfikatory dostępu dla typu i składowej:

[!code-csharp[PublicAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#PublicAccess)]

Nie wszystkie Modyfikatory dostępu są prawidłowe dla wszystkich typów lub elementów członkowskich we wszystkich kontekstach. W niektórych przypadkach dostępność elementu członkowskiego typu jest ograniczona przez dostępność typu zawierającego.

## <a name="class-and-struct-accessibility"></a>Ułatwienia dostępu klasy i struktury  

Klasy i struktury zadeklarowane bezpośrednio w przestrzeni nazw (innymi słowy, które nie są zagnieżdżone w innych klasach lub strukturach) mogą być `public` albo `internal` . `Internal`jest wartością domyślną, jeśli nie określono modyfikatora dostępu.  

Elementy członkowskie struktury, w tym zagnieżdżone klasy i struktury, można zadeklarować `public` , `internal` lub `private` . Elementy członkowskie klasy, w tym zagnieżdżone klasy i struktury, mogą mieć `public` , `protected internal` ,,,, `protected` `internal` `private protected` lub `private` . Elementy członkowskie klasy i struktury, w tym zagnieżdżone klasy i struktury, mają `private` Domyślnie dostęp. Prywatne typy zagnieżdżone nie są dostępne spoza typu zawierającego.

Klasy pochodne nie mogą mieć większej dostępności niż ich typy podstawowe. Nie można zadeklarować klasy publicznej `B` , która pochodzi od klasy wewnętrznej `A` . Jeśli jest to dozwolone, miałoby to wpływ na `A` publiczną, ponieważ wszyscy `protected` lub `internal` członkowie `A` są dostępni z klasy pochodnej.

Można włączyć określone inne zestawy, aby uzyskać dostęp do typów wewnętrznych przy użyciu `InternalsVisibleToAttribute` . Aby uzyskać więcej informacji, zobacz [zaprzyjaźnione zestawy](../../../standard/assembly/friend.md).

## <a name="class-and-struct-member-accessibility"></a>Ułatwienia dostępu do elementów członkowskich klasy i struktury  

Elementy członkowskie klasy (w tym zagnieżdżone klasy i struktury) mogą być deklarowane przy użyciu dowolnego z sześciu typów dostępu. Elementy członkowskie struktury nie mogą być deklarowane jako `protected` , `protected internal` lub, `private protected` ponieważ struktury nie obsługują dziedziczenia.

Zwykle dostępność elementu członkowskiego nie jest większa niż dostępność typu, który go zawiera. Jednak `public` element członkowski klasy wewnętrznej może być dostępny spoza zestawu, jeśli element członkowski implementuje metody interfejsu lub zastępuje metody wirtualne, które są zdefiniowane w publicznej klasie bazowej.

Typ dowolnego pola elementu członkowskiego, właściwości lub zdarzenia musi być co najmniej tak samo samo jak element członkowski. Analogicznie, typ zwracany i typy parametrów dowolnej metody, indeksatora lub delegata muszą być co najmniej tak samo samo jak element członkowski. Na przykład nie można mieć `public` metody `M` , która zwraca klasę, `C` chyba że `C` jest również `public` . Podobnie nie można mieć `protected` właściwości typu, `A` Jeśli `A` jest zadeklarowana jako `private` .

Operatory zdefiniowane przez użytkownika muszą być zawsze deklarowane jako `public` i `static` . Aby uzyskać więcej informacji, zobacz [przeciążanie operatora](../../language-reference/operators/operator-overloading.md).

Finalizatory nie mogą mieć modyfikatorów dostępności.

Aby ustawić poziom dostępu dla `class` `struct` elementu członkowskiego lub, Dodaj odpowiednie słowo kluczowe do deklaracji elementu członkowskiego, jak pokazano w poniższym przykładzie.

[!code-csharp[MethodAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#MethodAccess)]

## <a name="other-types"></a>Inne typy

Interfejsy zadeklarowane bezpośrednio w przestrzeni nazw mogą być `public` lub `internal` i, podobnie jak klasy i struktury, są domyślnie dostępne dla interfejsów `internal` . Elementy członkowskie interfejsu są `public` Domyślnie, ponieważ celem interfejsu jest umożliwienie innym typom dostępu do klasy lub struktury. Deklaracje elementu członkowskiego interfejsu mogą zawierać dowolny modyfikator dostępu. Jest to najbardziej przydatne w przypadku metod statycznych w celu zapewnienia wspólnych implementacji wymaganych przez wszystkie implementujące klasy.

Elementy członkowskie wyliczenia są zawsze `public` i nie można zastosować modyfikatorów dostępu.

Delegaty zachowują się jak klasy i struktury. Domyślnie mają `internal` dostęp, gdy jest zadeklarowany bezpośrednio w przestrzeni nazw, i `private` uzyskuje dostęp, gdy jest zagnieżdżony.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](./index.md)
- [Interfejsy](../interfaces/index.md)
- [private](../../language-reference/keywords/private.md)
- [public](../../language-reference/keywords/public.md)
- [internal](../../language-reference/keywords/internal.md)
- [protected](../../language-reference/keywords/protected.md)
- [protected internal](../../language-reference/keywords/protected-internal.md)
- [private protected](../../language-reference/keywords/private-protected.md)
- [określonej](../../language-reference/keywords/class.md)
- [konstrukcja](../../language-reference/builtin-types/struct.md)
- [interfejsu](../../language-reference/keywords/interface.md)
