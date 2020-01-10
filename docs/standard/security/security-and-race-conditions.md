---
title: Zabezpieczenia i sytuacja wyścigu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
ms.openlocfilehash: 8980122acdd069bc840aa09129483a1cb9a379fd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705876"
---
# <a name="security-and-race-conditions"></a>Zabezpieczenia i sytuacja wyścigu
Innym obszarem zainteresowania jest potencjalna liczba luk w zabezpieczeniach wykorzystywanych przez sytuacje wyścigu. Może się to zdarzyć na kilka sposobów. Tematy podrzędne, które przestrzegają konspektu, niektórych głównych pułapek, które muszą być unikane przez dewelopera.  
  
## <a name="race-conditions-in-the-dispose-method"></a>Warunki wyścigu w metodzie Dispose  
 Jeśli metoda **Dispose** klasy (Aby uzyskać więcej informacji, zobacz [zbieranie elementów bezużytecznych](../../../docs/standard/garbage-collection/index.md)) nie jest zsynchronizowana, istnieje możliwość, że kod czyszczący wewnątrz elementu **Dispose** można uruchomić więcej niż jeden raz, jak pokazano w poniższym przykładzie.  
  
```vb  
Sub Dispose()  
    If Not (myObj Is Nothing) Then  
       Cleanup(myObj)  
       myObj = Nothing  
    End If  
End Sub  
```  
  
```csharp  
void Dispose()   
{  
    if (myObj != null)   
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 Ponieważ ta implementacja **usuwania** nie jest zsynchronizowana, możliwe jest `Cleanup` wywoływany przez pierwszy wątek, a następnie drugi wątek przed ustawieniem `_myObj` na **wartość null**. To, czy jest to problem dotyczący zabezpieczeń, zależy od tego, co się dzieje w przypadku uruchamiania kodu `Cleanup`. Istotny problem z niezsynchronizowanymi implementacjami **Dispose** obejmuje użycie dojścia do zasobów, takich jak pliki. Niewłaściwe usunięcie może spowodować niewłaściwe użycie, które często prowadzi do luk w zabezpieczeniach.  
  
## <a name="race-conditions-in-constructors"></a>Warunki wyścigu w konstruktorach  
 W niektórych aplikacjach może być możliwe, aby inne wątki miały dostęp do elementów członkowskich klasy, zanim ich konstruktory klas zostały całkowicie uruchomione. Należy przejrzeć wszystkie konstruktory klas, aby upewnić się, że nie występują problemy z zabezpieczeniami, jeśli taka sytuacja powinna mieć miejsce lub zsynchronizować wątki w razie potrzeby.  
  
## <a name="race-conditions-with-cached-objects"></a>Warunki wyścigu z buforowanymi obiektami  
 Kod, który buforuje informacje o zabezpieczeniach lub używa operacji [potwierdzenia](../../../docs/framework/misc/using-the-assert-method.md) zabezpieczeń dostępu kodu może być również narażony na sytuacje wyścigu, jeśli inne części klasy nie są odpowiednio zsynchronizowane, jak pokazano w poniższym przykładzie.  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False  
    End If  
End Sub  
  
Sub DoOtherWork()  
    If fCallersOK Then  
        DoSomethingTrusted()  
    Else  
        DemandSomething()  
        DoSomethingTrusted()  
    End If  
End Sub  
```  
  
```csharp  
void SomeSecureFunction()   
{  
    if (SomeDemandPasses())   
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false;  
    }  
}  
void DoOtherWork()   
{  
    if (fCallersOK)   
    {  
        DoSomethingTrusted();  
    }  
    else   
    {  
        DemandSomething();  
        DoSomethingTrusted();  
    }  
}  
```  
  
 Jeśli istnieją inne ścieżki do `DoOtherWork`, które mogą być wywoływane z innego wątku z tym samym obiektem, niezaufany obiekt wywołujący może wykasować poza zapotrzebowaniem.  
  
 Jeśli kod buforuje informacje o zabezpieczeniach, należy zapoznać się z informacjami dotyczącymi tej luki w zabezpieczeniach.  
  
## <a name="race-conditions-in-finalizers"></a>Sytuacje wyścigu w finalizatorach  
 Sytuacje wyścigu mogą również wystąpić w obiekcie, który odwołuje się do zasobu statycznego lub niezarządzanego, który następnie zwolni w jego finalizatorie. Jeśli wiele obiektów współużytkuje zasób, który jest manipulowany przez finalizator klasy, obiekty muszą zsynchronizować wszystkie dostęp do tego zasobu.  
  
## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
