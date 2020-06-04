---
title: User-Defined Data Type
ms.date: 07/20/2015
f1_keywords:
- UserDefined
- UDT
- vb.UDT
- User-Defined
- vb.UserDefined
- vb.User-Defined
helpviewer_keywords:
- user-defined data types [Visual Basic], Visual Basic
- user-defined types
- structures [Visual Basic], as user-defined data types
- user-defined types [Visual Basic], Visual Basic
- user-defined types [Visual Basic], structure declaration
- user-defined types [Visual Basic], structures in Visual Basic
- user-defined data types [Visual Basic], structure declaration
- data types [Visual Basic], assigning
- Structure statement [Visual Basic]
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], structures in Visual Basic
- user-defined data types
- types [Visual Basic], user-defined
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
ms.openlocfilehash: fbd9536a54d7fb471d6cb2e130b14a84e40a4940
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415495"
---
# <a name="user-defined-data-type"></a>User-Defined Data Type

Przechowuje dane w formacie zdefiniowanym przez użytkownika. `Structure`Instrukcja definiuje format.

Poprzednie wersje Visual Basic obsługują typ zdefiniowany przez użytkownika (UDT). Bieżąca wersja rozszerza UDT do *struktury*. Struktura jest połączeniem jednego lub większej liczby *elementów członkowskich* różnych typów danych. Visual Basic traktuje strukturę jako pojedynczą jednostkę, chociaż można także uzyskać dostęp do jej elementów członkowskich pojedynczo.

## <a name="remarks"></a>Uwagi

Zdefiniuj typ danych struktury i użyj go, jeśli chcesz połączyć różne typy danych w pojedynczą jednostkę lub gdy żaden z podstawowych typów danych nie odpowiada Twoim potrzebom.

Wartość domyślna struktury typu danych składa się z kombinacji wartości domyślnych każdego z jej elementów członkowskich.

## <a name="declaration-format"></a>Format deklaracji

Deklaracja struktury rozpoczyna się od [instrukcji Structure](../statements/structure-statement.md) i kończyć się `End Structure` instrukcją. `Structure`Instrukcja dostarcza nazwę struktury, która jest również identyfikatorem typu danych, który definiuje struktura. Inne części kodu mogą używać tego identyfikatora do deklarowania zmiennych, parametrów i wartości zwracanych funkcji jako typu danych tej struktury.

Deklaracje między `Structure` instrukcjami i `End Structure` definiują elementy członkowskie struktury.

## <a name="member-access-levels"></a>Poziomy dostępu członków

Należy zadeklarować każdy element członkowski przy użyciu [instrukcji Dim](../statements/dim-statement.md) lub instrukcji, która określa poziom dostępu, na przykład [Public](../modifiers/public.md), [Friend](../modifiers/friend.md)lub [Private](../modifiers/private.md). Jeśli używasz `Dim` instrukcji, poziom dostępu jest domyślnie publiczny.

## <a name="programming-tips"></a>Porady dla programistów

- **Użycie pamięci.** Podobnie jak w przypadku wszystkich złożonych typów danych, nie można bezpiecznie obliczyć całkowitego zużycia pamięci przez dodanie do nich nominalnych przydziałów pamięci masowej. Ponadto nie można bezpiecznie założyć, że kolejność przechowywania w pamięci jest taka sama jak w przypadku kolejności deklaracji. Jeśli konieczne jest kontrolowanie układu pamięci masowej struktury, można zastosować <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybut do `Structure` instrukcji.

- **Zagadnienia dotyczące międzyoperacyjnych.** Jeśli masz połączenie ze składnikami niezapisanymi dla .NET Framework, na przykład obiekty automatyzacji lub COM, pamiętaj, że typy zdefiniowane przez użytkownika w innych środowiskach nie są zgodne z typami struktur Visual Basic.

- **Rozszerzającą.** Nie istnieje Automatyczna konwersja do lub z dowolnego typu danych struktury. Operatory konwersji można definiować w strukturze przy użyciu [instrukcji operatora](../statements/operator-statement.md)i można zadeklarować każdy operator konwersji jako `Widening` lub `Narrowing` .

- **Znaki typu.** Typy danych struktury nie mają znaku typu literału lub znaku typu identyfikatora.

- **Typ struktury.** Brak odpowiedniego typu w .NET Framework. Wszystkie struktury dziedziczą z klasy .NET Framework <xref:System.ValueType?displayProperty=nameWithType> , ale żadna konkretna struktura nie odnosi się do <xref:System.ValueType?displayProperty=nameWithType> .

## <a name="example"></a>Przykład

Poniższy model przedstawia kontur deklaracji struktury.

```vb
[Public | Protected | Friend | Protected Friend | Private] Structure structname
    {Dim | Public | Friend | Private} member1 As datatype1
    ' ...
    {Dim | Public | Friend | Private} memberN As datatypeN
End Structure
```

## <a name="see-also"></a>Zobacz też

- <xref:System.ValueType>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [Typy danych](index.md)
- [Funkcje konwersji typu](../functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../keywords/conversion-summary.md)
- [Structure — Instrukcja](../statements/structure-statement.md)
- [Widening](../modifiers/widening.md)
- [Narrowing](../modifiers/narrowing.md)
- [Struktury](../../programming-guide/language-features/data-types/structures.md)
- [Skuteczne stosowanie typów danych](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
