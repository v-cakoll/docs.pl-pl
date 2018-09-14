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
ms.openlocfilehash: 1dac93145b6e11a0d149f03b43e1e0b28b770925
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45509847"
---
# <a name="user-defined-data-type"></a>User-Defined Data Type
Przechowuje dane w postaci, jaką zdefiniujesz. `Structure` Instrukcja definiuje format.  
  
 Poprzednie wersje języka Visual Basic obsługuje typ zdefiniowany przez użytkownika (UDT). Bieżąca wersja rozwija UDT do *struktury*. Struktura jest łączenia jednej lub więcej *członków* różnych typów danych. Visual Basic traktuje struktury jako pojedynczą jednostkę, chociaż można także przejść do jego członków indywidualnie.  
  
## <a name="remarks"></a>Uwagi  
 Definiowanie i korzystanie z typem struktury danych, gdy trzeba połączyć różne typy danych w pojedynczą jednostkę, lub gdy żaden z typów podstawowych danych spełniały Twoje potrzeby.  
  
 Wartość domyślna typu danych struktury składa się z kombinacji wartości domyślne wszystkich członków.  
  
## <a name="declaration-format"></a>Format deklaracji  
 Deklaracji struktury zaczyna się od [Structure — instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md) i kończy `End Structure` instrukcji. `Structure` Instrukcji dostarcza nazwę struktury, która jest również identyfikator typu danych jest zdefiniowanie struktury. Inne części kodu można użyć tego identyfikatora do deklarowania zmiennych, parametrów i funkcja zwraca wartości o typie danych tej struktury.  
  
 Deklaracje między `Structure` i `End Structure` instrukcji Definiowanie elementów członkowskich struktury.  
  
## <a name="member-access-levels"></a>Poziomy dostępu elementu członkowskiego  
 Należy zadeklarować każdego członka za pomocą [instrukcji Dim](../../../visual-basic/language-reference/statements/dim-statement.md) lub instrukcję, która określa poziom dostępu, takich jak [publicznych](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), lub [prywatne](../../../visual-basic/language-reference/modifiers/private.md). Jeśli używasz `Dim` instrukcja, wartości domyślnych poziomu dostępu na wartość publiczne.  
  
## <a name="programming-tips"></a>Porady dla programistów  
  
-   **Zużycie pamięci.** Podobnie jak w przypadku wszystkich złożonych typów danych, nie można bezpiecznie obliczyć łącznego zużycia pamięci przez strukturę, dodając do siebie nominalne alokacje magazynu jej składowych. Ponadto nie można bezpiecznie założyć, że kolejność magazynowania w pamięci jest taka sama jak kolejność deklaracji. Jeśli musisz kontrolować układ magazynu struktury, możesz zastosować atrybut <xref:System.Runtime.InteropServices.StructLayoutAttribute> w instrukcji `Structure`.  
  
-   **Uwagi dotyczące współdziałania.** Jeśli są komunikowanie się ze składnikami programu .NET Framework, na przykład obiektami automatyzacji lub COM, należy pamiętać, że typy danych zdefiniowane przez użytkownika w innych środowiskach nie są zgodne z języka Visual Basic strukturę typów.  
  
-   **Rozszerzanie.** Nie jest automatyczna konwersja do / z dowolnego typu danych struktury. Operatory konwersji można zdefiniować w sieci za pomocą struktury [operator — instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md), i można zadeklarować każdego operatora konwersji `Widening` lub `Narrowing`.  
  
-   **Znaki typu.** Typy danych struktury mieć znak literalny typu lub znak typu identyfikator.  
  
-   **Typ Framework.** W .NET Framework, nie ma żadnego odpowiedniego typu. Wszystkie struktury dziedziczą z klasy .NET Framework <xref:System.ValueType?displayProperty=nameWithType>, ale nie struktury poszczególnych odnosi się do <xref:System.ValueType?displayProperty=nameWithType>.  
  
## <a name="example"></a>Przykład  
 Następujące paradygmat przedstawia zarys deklaracji struktury.  
  
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
 [Typy danych](../../../visual-basic/language-reference/data-types/index.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)  
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
