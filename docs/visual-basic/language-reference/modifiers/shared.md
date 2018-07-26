---
title: Shared (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
ms.openlocfilehash: b76d999bfe3f7ae5205cb9486e040c1d6191b78c
ms.sourcegitcommit: dc02d7d95f1e3efcc7166eaf431b0ec0dc9d8dca
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37143534"
---
# <a name="shared-visual-basic"></a>Shared (Visual Basic)
Określa, że co najmniej jeden zadeklarowany element programistyczny skojarzonych z klasy lub struktury w dużych, a nie przy użyciu określonego wystąpienia klasy lub struktury.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="when-to-use-shared"></a>Kiedy należy używać udostępnionych  
 Udostępnianie składowej klasy lub struktury sprawia, że dostępne dla każdego wystąpienia zamiast *nieudostępnionych*, gdzie każde wystąpienie zachowuje własną kopię. Jest to przydatne, na przykład, jeśli wartość zmiennej ma zastosowanie do całej aplikacji. Przy deklarowaniu zmiennej jako `Shared`, następnie wszystkie wystąpienia dostęp do tej samej lokalizacji magazynu, a jeśli jedno wystąpienie zmienia wartość zmiennej, wszystkie wystąpienia dostęp zaktualizowane wartości.  
  
 Udostępnianie nie zmienia poziom dostępu do elementu członkowskiego. Na przykład, członek klasy mogą być udostępniane i prywatne (dostępny tylko w obrębie klasy), lub nieudostępnionych, jak i publicznych. Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>reguły  
  
-   **Kontekst deklaracji.** Możesz użyć `Shared` tylko na poziomie modułu. Oznacza to, że kontekst deklaracji `Shared` element musi być klasą lub strukturą i nie może być plikiem źródłowym, przestrzeń nazw lub procedury.  
  
-   **Modyfikatory połączone.** Nie można określić `Shared` wraz z [zastępuje](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), lub [ Statyczne](../../../visual-basic/language-reference/modifiers/static.md) w tej samej deklaracji.  
  
-   **Uzyskiwanie dostępu do.** Możesz uzyskać dostęp udostępnionego elementu kwalifikując jego nazwą klasy lub struktury, a nie nazwę zmiennej konkretnego wystąpienia swojej klasy lub struktury. Nawet nie trzeba utworzyć wystąpienia klasy lub struktury dostęp do jego udostępnionych elementów członkowskich.  
  
     Poniższy przykład wywołuje procedury udostępnianej <xref:System.Double.IsNaN%2A> udostępnianych przez <xref:System.Double> struktury.  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
-   **Niejawne udostępniania.** Nie można użyć `Shared` modyfikator w [instrukcja Const](../../../visual-basic/language-reference/statements/const-statement.md), ale stałe są niejawnie. Podobnie nie można zadeklarować członek modułem lub interfejsem `Shared`, ale niejawnie są one udostępniane.  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Magazyn.** Udostępniona zmienna lub zdarzenia są przechowywane w pamięci tylko raz, niezależnie od tego, ile lub kilka wystąpień tworzenia swojej klasy lub struktury. Podobnie procedury udostępnianej lub właściwość zawiera tylko jeden zestaw zmiennych lokalnych.  
  
-   **Dostęp za pośrednictwem zmiennej wystąpienia.** Użytkownik może uzyskać dostęp do udostępnionego elementu kwalifikując nazwę zmiennej, która zawiera określone wystąpienie jego klasy lub struktury. Mimo że to zazwyczaj działa zgodnie z oczekiwaniami, kompilator generuje komunikat ostrzegawczy i sprawia, że dostęp za pośrednictwem nazwy klasy lub struktury, zamiast zmiennej.  
  
-   **Uzyskiwanie dostępu do przy użyciu wyrażenia wystąpienia.** Jeśli uzyskujesz dostęp do udostępnionego elementu za pomocą wyrażenia, która zwraca wystąpienie jego klasy lub struktury, kompilator sprawia, że dostęp za pośrednictwem nazwy klasy lub struktury, zamiast obliczając wartość wyrażenia. Daje nieoczekiwane wyniki, jeśli Twoim zamiarem wyrażenie które ma wykonywać inne czynności, a także zwracanie wystąpienia. Ilustruje to poniższy przykład.  
  
    ```vb
    Sub main()  
        shareTotal.total = 10  
        ' The preceding line is the preferred way to access total.  
        Dim instanceVar As New shareTotal  
        instanceVar.total += 100  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of through  
        ' the variable instanceVar. This works as expected and adds  
        ' 100 to total.  
        returnClass().total += 1000  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of calling  
        ' returnClass(). This adds 1000 to total but does not work as  
        ' expected, because the MsgBox in returnClass() does not run.  
        MsgBox("Value of total is " & CStr(shareTotal.total))  
    End Sub  
    Public Function returnClass() As shareTotal  
        MsgBox("Function returnClass() called")  
        Return New shareTotal  
    End Function  
    Public Class shareTotal  
        Public Shared total As Integer  
    End Class  
    ```  
  
     W poprzednim przykładzie, kompilator generuje ostrzeżenie razem kod uzyskuje dostęp do współdzielonej zmiennej `total` za pośrednictwem wystąpienia. W każdym przypadku to sprawia, że dostęp bezpośrednio za pomocą klasy `shareTotal` i nie powoduje użycie dowolnego wystąpienia. W przypadku zamierzonej wywołaniu do procedury `returnClass`, oznacza to, że nie generuje nawet po wywołaniu `returnClass`, więc dodatkowe działania wyświetlania "returnClass() funkcji o nazwie" nie jest wykonywane.  
  
 `Shared` Modyfikator mogą być używane w tych kontekstach:  
  
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Static](../../../visual-basic/language-reference/modifiers/static.md)  
 [Okres istnienia w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
