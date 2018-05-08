---
title: Struktury (F#)
description: 'Dowiedz się więcej o F # struktury, typu obiektu compact często bardziej efektywne niż klasa dla typów z małej ilości danych i zachowania proste.'
ms.date: 05/16/2016
ms.openlocfilehash: 728533e24dcfae219ae5ab3d410389e95fcfaee1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="structures"></a>Struktury

A *struktury* jest typem obiektu compact, który może być skuteczniejsza niż klasa dla typów, które mają niewielką ilość danych i zachowania proste.

## <a name="syntax"></a>Składnia

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements
```

## <a name="remarks"></a>Uwagi
Struktury są *typów wartości*, co oznacza, że są przechowywane bezpośrednio na stosie, lub gdy są one używane jako pola lub typ elementów tablicy, wbudowanego w obiekcie nadrzędnym. W odróżnieniu od klasy i rejestruje struktury ma semantykę przebiegu przez wartość. Oznacza to, że są one przydatne głównie dla małych wartości zagregowanych danych, które są dostępne i często skopiowane.

W poprzednich składni są wyświetlane dwa formularze. Pierwszy nie jest lekkie składni, ale mimo to często jest używana, ponieważ, jeśli używasz `struct` i `end` słów kluczowych, można pominąć `StructAttribute` atrybut, który pojawi się w drugim formularzu. Można skrócić `StructAttribute` nieco `Struct`.

*Elementy definicji typu* w poprzednim składni reprezentuje element członkowski deklaracje i definicje. Struktury mogą mieć konstruktorów i modyfikowalne i modyfikować pola, a ich można zadeklarować elementów członkowskich i implementacje interfejsów. Aby uzyskać więcej informacji, zobacz [członków](members/index.md).

Struktury nie mogą uczestniczyć w dziedziczeniu, nie może zawierać `let` lub `do` powiązań, i nie można rekursywnie zawierać pola własne typu z (chociaż zawierają odwołanie do komórki, odwołujące się do ich własnych typu).

Ponieważ struktur nie zezwalaj na `let` powiązań, musisz zadeklarować pól struktur za pomocą `val` — słowo kluczowe. `val` — Słowo kluczowe definiuje pola i jego typ, ale nie zezwala na inicjowanie. Zamiast tego `val` deklaracje są zainicjowana na zero lub wartość null. Z tego powodu struktur, które mają niejawnego konstruktora (czyli parametry, które są podane natychmiast po nazwie struktury w deklaracji) wymaga, aby `val` deklaracje być adnotowany przy `DefaultValue` atrybutu. Struktury, które mają Konstruktor zdefiniowany nadal obsługuje inicjowania zero. W związku z tym `DefaultValue` atrybutu jest deklaracją nieprawidłowość nieprawidłowy dla pola takie wartość zero. Niejawne konstruktory struktury nie wykonuj żadnych akcji, ponieważ `let` i `do` powiązania nie są dozwolone w typie, ale przekazano wartości parametrów dorozumiany Konstruktor są dostępne jako pól prywatnych.

Jawne Konstruktory mogą dotyczyć inicjowania wartości pól. Jeśli masz struktury, która ma jawny Konstruktor nadal obsługuje inicjowania zero; jednak nie użyto `DefaultValue` atrybutu `val` deklaracje, ponieważ powoduje on konflikt z jawny Konstruktor. Aby uzyskać więcej informacji na temat `val` deklaracje, zobacz [pola jawne: `val` — słowo kluczowe](members/explicit-fields-the-val-keyword.md).

Atrybuty i modyfikatory dostępności są dozwolone w struktury i wykonaj te same zasady, jak w przypadku innych typów. Aby uzyskać więcej informacji, zobacz [atrybuty](attributes.md) i [kontroli dostępu](access-control.md).

Poniższe przykłady kodu przedstawiają definicji struktury.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="struct-records-and-discriminated-unions"></a>Struktura rekordów i sumy rozłączne

Począwszy od 4.1 F #, może reprezentować [rekordów](records.md) i [Suma rozłączna unie](discriminated-unions.md) jako struktury z `[<Struct>]` atrybutu.  Zobacz każdego artykułu, aby dowiedzieć się więcej.
    
## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)

[Klasy](classes.md)

[Rekordy](records.md)

[Elementy członkowskie](members/index.md)
