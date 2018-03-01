---
title: Shared (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fce13c308a449e63eacc2bc4c94c274c7e25506a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="shared-visual-basic"></a>Shared (Visual Basic)
Określa, że co najmniej jeden zadeklarowany element programistyczny skojarzonych z klasy lub struktury w dużych, a nie z konkretnym wystąpieniem klasy lub struktury.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="when-to-use-shared"></a>Kiedy należy używać udostępnionych  
 Udostępnianie elementem członkowskim klasy lub struktury udostępnia go do każdego wystąpienia, a nie *udostępniana*, gdzie każde wystąpienie zachowuje własną kopię. Jest to przydatne, na przykład, jeśli wartość zmiennej, która ma zastosowanie do całej aplikacji. Deklarowanie zmiennej jako `Shared`, następnie wszystkie wystąpienia dostęp do tej samej lokalizacji magazynu, a jeśli jedno wystąpienie zmieni wartość zmiennej, wszystkich wystąpień dostęp zaktualizowanej wartości.  
  
 Udostępnianie nie zmienia poziom dostępu do elementu członkowskiego. Na przykład może być udostępniony element członkowski klasy i prywatny (dostępny tylko w obrębie klasy), lub udostępniana, jak i publicznych. Aby uzyskać więcej informacji, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Reguły  
  
-   **Kontekst deklaracji.** Można użyć `Shared` tylko na poziomie modułu. Oznacza to, że w kontekście deklaracji `Shared` elementu musi być klasy lub struktury i nie może być plik źródłowy, przestrzeni nazw lub procedury.  
  
-   **Łączna modyfikatorów.** Nie można określić `Shared` razem z [zastępuje](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), lub [ Statyczne](../../../visual-basic/language-reference/modifiers/static.md) w tej samej deklaracji.  
  
-   **Uzyskiwanie dostępu do.** Dostęp do udostępnionego elementu przy kwalifikujące go z nazwą klasy lub struktury, a nie z nazwę zmiennej określonego wystąpienia klasy lub struktury. Nawet nie trzeba tworzyć wystąpienia klasy lub struktury, dostęp do jego udostępniane elementy członkowskie.  
  
     Poniższy przykład wywołuje procedurę udostępnionego <xref:System.Double.IsNaN%2A> udostępnianych przez <xref:System.Double> struktury.  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
-   **Niejawne udostępniania.** Nie można użyć `Shared` modyfikator w [instrukcja Const](../../../visual-basic/language-reference/statements/const-statement.md), ale stałe niejawnie są udostępnione. Podobnie, nie można zadeklarować członka modułu lub interfejs `Shared`, ale niejawnie są one udostępniane.  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Magazyn.** Udostępniona zmienna lub zdarzenia jest przechowywany w pamięci tylko raz, niezależnie od tego, ile lub kilka wystąpień utworzyć jej klasy lub struktury. Podobnie współdzielonej procedury lub właściwości zawiera tylko jeden zestaw zmiennych lokalnych.  
  
-   **Uzyskiwanie dostępu za pośrednictwem zmiennej wystąpienia.** Istnieje możliwość uzyskania dostępu do udostępnionego elementu przy kwalifikujących się on na nazwę zmiennej, która zawiera określone wystąpienia klasy lub struktury. Chociaż to zwykle działa zgodnie z oczekiwaniami, kompilator generuje ostrzeżenie i umożliwia dostęp za pośrednictwem Nazwa klasy lub struktury, zamiast zmiennej.  
  
-   **Uzyskiwanie dostępu za pomocą wyrażenia wystąpienia.** Jeśli dostęp do udostępnionego elementu przez wyrażenie, które zwraca wystąpienie klasy lub struktury, kompilator sprawia, że dostęp za pośrednictwem Nazwa klasy lub struktury, zamiast obliczenie wyrażenia. Tworzy nieoczekiwane wyniki, jeśli przeznaczony wyrażenie, które ma wykonywać inne akcje, a także zwracanie wystąpienie. Ilustruje to poniższy przykład.  
  
    ```  
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
  
     W powyższym przykładzie kompilator generuje ostrzeżenie razem kod uzyskuje dostęp do współdzielonej zmiennej `total` za pomocą wystąpienia. W każdym przypadku ułatwia dostępu bezpośrednio za pomocą klasy `shareTotal` i nie należy używać wszystkie wystąpienia. W przypadku zamierzonej wywołanie procedury `returnClass`, oznacza to, że nie generuje nawet wywołanie `returnClass`, więc dodatkowych akcji wyświetlanie "returnClass() funkcji o nazwie" nie jest wykonywana.  
  
 `Shared` Modyfikatora można używać w tych sytuacjach:  
  
 [Dim — instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function — instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator — instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub — instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Statyczne](../../../visual-basic/language-reference/modifiers/static.md)  
 [Okres istnienia w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
