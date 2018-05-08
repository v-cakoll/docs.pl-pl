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
ms.openlocfilehash: 07f04fb111863ca18d4966a7f0f967f11719aeec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="user-defined-data-type"></a>User-Defined Data Type
Przechowuje dane w formacie, który należy zdefiniować. `Structure` Instrukcji definiuje format.  
  
 Poprzednie wersje programu Visual Basic obsługuje typ zdefiniowany przez użytkownika (UDT). Bieżąca wersja rozszerza UDT do *struktury*. Struktura jest złączeniem co najmniej jeden *członków* różnych typów danych. Visual Basic traktuje jako pojedynczą jednostkę, struktury, chociaż można także przejść do jego elementów członkowskich indywidualnie.  
  
## <a name="remarks"></a>Uwagi  
 Definiowanie i używać typu danych struktury, gdy trzeba połączyć różnych typów danych w pojedynczą jednostkę, lub żaden z typów podstawowych danych z potrzebami.  
  
 Wartość domyślna typu danych struktury składa się z kombinacji wartości domyślne wszystkich jej członków.  
  
## <a name="declaration-format"></a>Format deklaracji  
 Rozpoczyna się od deklaracji struktury [Structure — instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md) i kończy `End``Structure` instrukcji. `Structure` Instrukcja zawiera nazwę struktury, która jest również identyfikator typu danych, jest zdefiniowanie struktury. Inne części kodu, można użyć tego identyfikatora do deklarowania zmiennych, parametry i funkcja zwracają wartości typu danych tej struktury.  
  
 Deklaracje między `Structure` i `End``Structure` instrukcje zdefiniować elementów członkowskich struktury.  
  
## <a name="member-access-levels"></a>Poziomy dostępu elementu członkowskiego  
 Musisz zadeklarować każdego elementu członkowskiego przy użyciu [instrukcji Dim](../../../visual-basic/language-reference/statements/dim-statement.md) lub instrukcję, która określa poziom dostępu, takich jak [publicznego](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), lub [prywatnego](../../../visual-basic/language-reference/modifiers/private.md). Jeśli używasz `Dim` instrukcji, wartości domyślnych poziomu dostępu do publicznej.  
  
## <a name="programming-tips"></a>Porady dla programistów  
  
-   **Zużycie pamięci.** Podobnie jak w przypadku wszystkich złożone typy danych, nie można bezpiecznie obliczania zużycia całkowitej ilości pamięci struktury przez dodanie alokacji magazynu nominalnego jego elementów członkowskich. Ponadto nie można bezpiecznie zakładać, że kolejność magazynu w pamięci jest taka sama jak zamówienia deklaracji. Jeśli potrzebujesz do sterowania układem magazynu struktury, możesz zastosować <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutu `Structure` instrukcji.  
  
-   **Zagadnienia dotyczące współdziałania.** Jeśli użytkownik są relacje ze składników, które nie są zapisywane dla programu .NET Framework, na przykład obiektów automatyzacji lub COM, należy pamiętać, że typy danych zdefiniowane przez użytkownika w innych środowiskach nie są zgodne z programem Visual Basic struktury typów.  
  
-   **Rozszerzanie.** Nie jest automatyczna konwersja do lub z dowolnego typu danych struktury. Operatory konwersji można zdefiniować na przy użyciu struktury [operator — instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md), a każdy operatora konwersji można zadeklarować `Widening` lub `Narrowing`.  
  
-   **Znaki typu.** Typy danych struktury mieć znak literalny typu lub znak typu identyfikator.  
  
-   **Typ struktury.** Nie ma odpowiedniego typu w programie .NET Framework. Wszystkie struktury dziedziczyć po klasie .NET Framework <xref:System.ValueType?displayProperty=nameWithType>, ale nie poszczególnych struktura odpowiada <xref:System.ValueType?displayProperty=nameWithType>.  
  
## <a name="example"></a>Przykład  
 Następujące modelu zawiera konturu deklaracji struktury.  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ValueType>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 [Typy danych](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)  
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
