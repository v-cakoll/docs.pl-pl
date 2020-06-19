---
title: Shared
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
ms.openlocfilehash: b51c88e1af3a720912af8ba6aaf8ae4016af9cfa
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990191"
---
# <a name="shared-visual-basic"></a>Shared (Visual Basic)

Określa, że co najmniej jeden zadeklarowany element programistyczny jest skojarzony z klasą lub strukturą w dużej, a nie z określonym wystąpieniem klasy lub struktury.

## <a name="when-to-use-shared"></a>Kiedy używać udostępnionego

Udostępnienie składowej klasy lub struktury sprawia, że jest ona dostępna dla każdego wystąpienia, a nie jako *nieudostępnione*, gdzie każde wystąpienie zachowuje własną kopię. Udostępnianie jest przydatne, na przykład jeśli wartość zmiennej dotyczy całej aplikacji. Jeśli ta zmienna jest zadeklarowana `Shared` , wszystkie wystąpienia uzyskują dostęp do tej samej lokalizacji magazynu, a jeśli jedno wystąpienie zmieni wartość zmiennej, wszystkie wystąpienia uzyskują dostęp do zaktualizowanej wartości.

Udostępnianie nie zmienia poziomu dostępu elementu członkowskiego. Na przykład element członkowski klasy może być współużytkowany i prywatny (dostępny tylko w ramach klasy) lub nieudostępniony i publiczny. Aby uzyskać więcej informacji, zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

## <a name="rules"></a>Reguły

- **Kontekst deklaracji.** Można używać `Shared` tylko na poziomie modułu. Oznacza to, że kontekst deklaracji dla `Shared` elementu musi być klasą lub strukturą i nie może być plikiem źródłowym, przestrzenią nazw ani procedurą.

- **Połączone modyfikatory.** Nie można określić `Shared` razem z [zastąpień](overrides.md), [zastąpienia](overridable.md), [NotOverridable](notoverridable.md), [MustOverride](mustoverride.md)lub [static](static.md) w tej samej deklaracji.

- **Korzystając.** Dostęp do elementu udostępnionego można uzyskać, uprawniając do jego nazwy klasy lub struktury, a nie nazwy zmiennej określonego wystąpienia jego klasy lub struktury. Nie trzeba nawet utworzyć wystąpienia klasy lub struktury, aby uzyskać dostęp do jego udostępnionych elementów członkowskich.

     Poniższy przykład wywołuje procedurę udostępnioną <xref:System.Double.IsNaN%2A> uwidocznioną przez <xref:System.Double> strukturę.

     ```vb
     If Double.IsNaN(result) Then Console.WriteLine("Result is mathematically undefined.")
     ```

- **Niejawne udostępnianie.** Nie można użyć `Shared` modyfikatora w [instrukcji const](../statements/const-statement.md), ale stałe są niejawnie udostępnione. Podobnie nie można zadeklarować elementu członkowskiego modułu lub interfejsu jako `Shared` , ale są one niejawnie udostępnione.

## <a name="behavior"></a>Zachowanie

- **Chowan.** Współdzielona zmienna lub zdarzenie jest przechowywane w pamięci tylko raz, niezależnie od tego, jak wiele lub kilka wystąpień utworzonych przez siebie klasy lub struktury. Podobnie wspólna procedura lub właściwość zawiera tylko jeden zestaw zmiennych lokalnych.

- **Uzyskiwanie dostępu za za poorednictwem zmiennej wystąpienia.** Istnieje możliwość uzyskania dostępu do elementu udostępnionego przez zakwalifikowanie go o nazwę zmiennej, która zawiera określone wystąpienie jego klasy lub struktury. Chociaż zwykle działa to w oczekiwany sposób, kompilator generuje komunikat ostrzegawczy i zapewnia dostęp za pomocą nazwy klasy lub struktury zamiast zmiennej.

- **Uzyskiwanie dostępu za poorednictwem wyrażenia wystąpienia.** Jeśli uzyskujesz dostęp do udostępnionego elementu za pomocą wyrażenia, które zwraca wystąpienie jego klasy lub struktury, kompilator uzyskuje dostęp poprzez nazwę klasy lub struktury zamiast oceniania wyrażenia. Ten dostęp daje nieoczekiwane wyniki, jeśli zamierzasz wykonać wyrażenie do wykonania innych czynności, a także zwracające wystąpienie. Poniższy przykład ilustruje tę sytuację.
  
    ```vb
    Sub Main()
        ' The following line is the preferred way to access Total.
        ShareTotal.Total = 10

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of through
        ' the variable instanceVar. This works as expected and adds
        ' 100 to Total.
        Dim instanceVar As New ShareTotal
        instanceVar.Total += 100

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of calling
        ' ReturnClass(). This adds 1000 to total but does not work as
        ' expected, because the WriteLine in ReturnClass() does not run.
        Console.WriteLine("Value of total is " & CStr(ShareTotal.Total))
        ReturnClass().Total += 1000
    End Sub

    Public Function ReturnClass() As ShareTotal
        Console.WriteLine("Function ReturnClass() called")
        Return New ShareTotal
    End Function

    Public Class ShareTotal
        Public Shared Property Total As Integer
    End Class
    ```

     W poprzednim przykładzie kompilator generuje komunikat ostrzegawczy, gdy kod uzyskuje dostęp do właściwości udostępnionej `Total` za pomocą wystąpienia. W każdym przypadku uzyskuje dostęp bezpośrednio za pomocą klasy i nie `ShareTotal` korzysta z żadnego wystąpienia. W przypadku zamierzonego wywołania procedury `ReturnClass` oznacza to, że nie generuje nawet wywołania do `ReturnClass` , więc dodatkowa akcja wyświetlania "Function ReturnClass () wywołana" nie jest wykonywana.

`Shared`Modyfikator może być używany w tych kontekstach:

- [Dim, instrukcja](../statements/dim-statement.md)
- [Event — Instrukcja](../statements/event-statement.md)
- [Function, instrukcja](../statements/function-statement.md)
- [Operator — Instrukcja](../statements/operator-statement.md)
- [Property — Instrukcja](../statements/property-statement.md)
- [Sub, instrukcja](../statements/sub-statement.md)
  
## <a name="see-also"></a>Zobacz też

- [Shadows](shadows.md)
- [Ruchom](static.md)
- [Okres istnienia w Visual Basic](../../programming-guide/language-features/declared-elements/lifetime.md)
- [Procedury](../../programming-guide/language-features/procedures/index.md)
- [Struktury](../../programming-guide/language-features/data-types/structures.md)
- [Obiekty i klasy](../../programming-guide/language-features/objects-and-classes/index.md)
