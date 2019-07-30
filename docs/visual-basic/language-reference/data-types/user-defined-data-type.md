---
title: Typ danych zdefiniowany przez użytkownika (Visual Basic)
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
ms.openlocfilehash: 76073037dcaac0e87bc8a352f3b438332d11d881
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630133"
---
# <a name="user-defined-data-type"></a>User-Defined Data Type

Przechowuje dane w formacie zdefiniowanym przez użytkownika. `Structure` Instrukcja definiuje format.

Poprzednie wersje Visual Basic obsługują typ zdefiniowany przez użytkownika (UDT). Bieżąca wersja rozszerza UDT do *struktury*. Struktura jest połączeniem jednego lub większej liczby *elementów członkowskich* różnych typów danych. Visual Basic traktuje strukturę jako pojedynczą jednostkę, chociaż można także uzyskać dostęp do jej elementów członkowskich pojedynczo.

## <a name="remarks"></a>Uwagi

Zdefiniuj typ danych struktury i użyj go, jeśli chcesz połączyć różne typy danych w pojedynczą jednostkę lub gdy żaden z podstawowych typów danych nie odpowiada Twoim potrzebom.

Wartość domyślna struktury typu danych składa się z kombinacji wartości domyślnych każdego z jej elementów członkowskich.

## <a name="declaration-format"></a>Format deklaracji

Deklaracja struktury rozpoczyna się od [instrukcji Structure](../../../visual-basic/language-reference/statements/structure-statement.md) i kończyć się `End Structure` instrukcją. `Structure` Instrukcja dostarcza nazwę struktury, która jest również identyfikatorem typu danych, który definiuje struktura. Inne części kodu mogą używać tego identyfikatora do deklarowania zmiennych, parametrów i wartości zwracanych funkcji jako typu danych tej struktury.

Deklaracje między `Structure` instrukcjami i `End Structure` definiują elementy członkowskie struktury.

## <a name="member-access-levels"></a>Poziomy dostępu członków

Należy zadeklarować każdy element członkowski przy użyciu [instrukcji Dim](../../../visual-basic/language-reference/statements/dim-statement.md) lub instrukcji, która określa poziom dostępu, na przykład [Public](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md)lub [Private](../../../visual-basic/language-reference/modifiers/private.md). Jeśli używasz `Dim` instrukcji, poziom dostępu jest domyślnie publiczny.

## <a name="programming-tips"></a>Porady dla programistów

- **Użycie pamięci.** Podobnie jak w przypadku wszystkich złożonych typów danych, nie można bezpiecznie obliczyć łącznego zużycia pamięci przez strukturę, dodając do siebie nominalne alokacje magazynu jej składowych. Ponadto nie można bezpiecznie założyć, że kolejność magazynowania w pamięci jest taka sama jak kolejność deklaracji. Jeśli musisz kontrolować układ magazynu struktury, możesz zastosować atrybut <xref:System.Runtime.InteropServices.StructLayoutAttribute> w instrukcji `Structure`.

- **Zagadnienia dotyczące międzyoperacyjnych.** Jeśli masz połączenie ze składnikami niezapisanymi dla .NET Framework, na przykład obiekty automatyzacji lub COM, pamiętaj, że typy zdefiniowane przez użytkownika w innych środowiskach nie są zgodne z typami struktur Visual Basic.

- **Rozszerzającą.** Nie istnieje Automatyczna konwersja do lub z dowolnego typu danych struktury. Operatory konwersji można definiować w strukturze przy użyciu [instrukcji operatora](../../../visual-basic/language-reference/statements/operator-statement.md)i można zadeklarować każdy operator konwersji jako `Widening` lub. `Narrowing`

- **Znaki typu.** Typy danych struktury nie mają znaku typu literału lub znaku typu identyfikatora.

- **Typ struktury.** Brak odpowiedniego typu w .NET Framework. Wszystkie struktury dziedziczą z klasy <xref:System.ValueType?displayProperty=nameWithType>.NET Framework, ale żadna konkretna struktura nie odnosi się do. <xref:System.ValueType?displayProperty=nameWithType>

## <a name="example"></a>Przykład

Poniższy model przedstawia kontur deklaracji struktury.

```
[Public | Protected | Friend | Protected Friend | Private] Structure structname
    {Dim | Public | Friend | Private} member1 As datatype1
    ' ...
    {Dim | Public | Friend | Private} memberN As datatypeN
End Structure
```

## <a name="see-also"></a>Zobacz także

- <xref:System.ValueType>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Widening](../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
