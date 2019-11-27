---
title: Udostępniona
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
ms.openlocfilehash: 98fa25d2283408dfb80e82fbc620a1b284e5c530
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349118"
---
# <a name="shared-visual-basic"></a>Shared (Visual Basic)
Określa, że co najmniej jeden zadeklarowany element programistyczny jest skojarzony z klasą lub strukturą w dużej, a nie z określonym wystąpieniem klasy lub struktury.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="when-to-use-shared"></a>Kiedy używać udostępnionego  
 Udostępnienie składowej klasy lub struktury sprawia, że jest ona dostępna dla każdego wystąpienia, a nie bez *udziału*, gdzie każde wystąpienie zachowuje własną kopię. Jest to przydatne, na przykład jeśli wartość zmiennej dotyczy całej aplikacji. Jeśli zadeklarujesz tę zmienną do `Shared`, wszystkie wystąpienia uzyskują dostęp do tej samej lokalizacji magazynu, a jeśli jedno wystąpienie zmieni wartość zmiennej, wszystkie wystąpienia uzyskują dostęp do zaktualizowanej wartości.  
  
 Udostępnianie nie zmienia poziomu dostępu elementu członkowskiego. Na przykład element członkowski klasy może być współużytkowany i prywatny (dostępny tylko w ramach klasy) lub nieudostępniony i publiczny. Aby uzyskać więcej informacji, zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Reguły  
  
- **Kontekst deklaracji.** `Shared` można używać tylko na poziomie modułu. Oznacza to, że kontekst deklaracji dla elementu `Shared` musi być klasą lub strukturą i nie może być plikiem źródłowym, przestrzenią nazw ani procedurą.  
  
- **Połączone modyfikatory.** Nie można określić `Shared` razem z [zastąpień](../../../visual-basic/language-reference/modifiers/overrides.md), [zastąpienia](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)lub [static](../../../visual-basic/language-reference/modifiers/static.md) w tej samej deklaracji.  
  
- **Korzystając.** Dostęp do elementu udostępnionego można uzyskać, uprawniając do jego nazwy klasy lub struktury, a nie nazwy zmiennej określonego wystąpienia jego klasy lub struktury. Nie trzeba nawet utworzyć wystąpienia klasy lub struktury, aby uzyskać dostęp do jego udostępnionych elementów członkowskich.  
  
     Poniższy przykład wywołuje procedurę udostępnioną <xref:System.Double.IsNaN%2A> uwidocznioną przez strukturę <xref:System.Double>.  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
- **Niejawne udostępnianie.** Nie można użyć modyfikatora `Shared` w [instrukcji const](../../../visual-basic/language-reference/statements/const-statement.md), ale stałe są niejawnie udostępnione. Podobnie nie można zadeklarować elementu członkowskiego modułu lub interfejsu do `Shared`, ale są one niejawnie udostępnione.  
  
## <a name="behavior"></a>Zachowanie  
  
- **Chowan.** Współdzielona zmienna lub zdarzenie jest przechowywane w pamięci tylko raz, niezależnie od tego, jak wiele lub kilka wystąpień utworzonych przez siebie klasy lub struktury. Podobnie wspólna procedura lub właściwość zawiera tylko jeden zestaw zmiennych lokalnych.  
  
- **Uzyskiwanie dostępu za za poorednictwem zmiennej wystąpienia.** Istnieje możliwość uzyskania dostępu do elementu udostępnionego przez zakwalifikowanie go o nazwę zmiennej, która zawiera określone wystąpienie jego klasy lub struktury. Chociaż zwykle działa to w oczekiwany sposób, kompilator generuje komunikat ostrzegawczy i zapewnia dostęp za pomocą nazwy klasy lub struktury zamiast zmiennej.  
  
- **Uzyskiwanie dostępu za poorednictwem wyrażenia wystąpienia.** Jeśli uzyskujesz dostęp do udostępnionego elementu za pomocą wyrażenia, które zwraca wystąpienie jego klasy lub struktury, kompilator uzyskuje dostęp poprzez nazwę klasy lub struktury zamiast oceniania wyrażenia. Daje to nieoczekiwane wyniki, jeśli zamierzasz wykonać wyrażenie do wykonania innych czynności, a także zwracające wystąpienie. Ilustruje to poniższy przykład.  
  
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
  
     W poprzednim przykładzie kompilator generuje komunikat ostrzegawczy, gdy kod uzyskuje dostęp do zmiennej udostępnionej `total` za pomocą wystąpienia. W każdym przypadku uzyskuje dostęp bezpośrednio za pomocą klasy `shareTotal` i nie korzysta z żadnego wystąpienia. W przypadku zamierzonego wywołania procedury `returnClass`oznacza to, że nie generuje nawet wywołania do `returnClass`, więc dodatkowa akcja przedstawiająca "Function returnClass () wywołana" nie jest wykonywana.  
  
 Modyfikator `Shared` może być używany w tych kontekstach:  
  
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Static](../../../visual-basic/language-reference/modifiers/static.md)
- [Okres istnienia w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
