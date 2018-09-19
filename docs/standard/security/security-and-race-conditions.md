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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57ceaedc7c38ae70a0db5a7fd584a765a7474aff
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "45991054"
---
# <a name="security-and-race-conditions"></a>Zabezpieczenia i sytuacja wyścigu
Kolejnym obszarem kwestią jest potencjalnych luk w zabezpieczeniach wykorzystana przez wyścigu. Istnieje kilka sposobów, w których może się to zdarzyć. Tematy podrzędne, które należy wykonać opisano niektóre z najważniejszych pułapek, których należy unikać dewelopera.  
  
## <a name="race-conditions-in-the-dispose-method"></a>Warunki wyścigu w metodzie Dispose  
 Jeśli klasa **Dispose** — metoda (Aby uzyskać więcej informacji, zobacz [wyrzucania elementów bezużytecznych](../../../docs/standard/garbage-collection/index.md)) jest nie jest zsynchronizowana, istnieje możliwość, ten kod porządkujący wewnątrz **Dispose** mogą być uruchamiane więcej niż jedno, jak pokazano w poniższym przykładzie.  
  
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
  
 Ponieważ to **Dispose** wdrożenia nie jest zsynchronizowana, możliwe jest `Cleanup` ma zostać wywołana przez najpierw jeden wątek, a następnie drugi wątek przed `_myObj` ustawiono **null**. Czy to jest kwestią zabezpieczeń zależy od tego, co się stanie, gdy `Cleanup` kod działa. Podstawowym problemem w niezsynchronizowane **Dispose** implementacje polega na użyciu tego dojścia zasobów, takich jak pliki. Niewłaściwy usuwania może spowodować nieprawidłowe dojście ma być używany, co często prowadzi do luk w zabezpieczeniach.  
  
## <a name="race-conditions-in-constructors"></a>Warunki wyścigu w konstruktorach  
 W niektórych aplikacji może być możliwe dla innych wątków do dostępu do składowych klasy, przed ich Konstruktory klasy całkowicie zostały uruchomione. Należy przejrzeć wszystkie Konstruktory klasy, aby upewnić się, że nie występują żadne problemy zabezpieczeń, jeśli to powinno to być spowodowane lub synchronizacji wątków, jeśli to konieczne.  
  
## <a name="race-conditions-with-cached-objects"></a>Warunki wyścigu przy użyciu buforowanych obiektów  
 Kod, który buforuje informacje o zabezpieczeniach lub wykorzystuje zabezpieczenia dostępu kodu [Asercja](../../../docs/framework/misc/using-the-assert-method.md) operacji może również występować sytuacje wyścigu w przypadku innych części klasy nie są odpowiednio zsynchronizowane, jak pokazano w poniższym przykładzie.  
  
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
  
 W przypadku innych ścieżek do `DoOtherWork` którą można wywołać z innego wątku za pomocą tego samego obiektu, niezaufanych obiekt wywołujący poślizg wcześniejsze żądanie.  
  
 Jeśli Twój kod buforuje informacje o zabezpieczeniach, upewnij się, przejrzyj luki w zabezpieczeniach.  
  
## <a name="race-conditions-in-finalizers"></a>Warunki wyścigu w finalizatory  
 Warunki wyścigu może również wystąpić w obiekcie, który odwołuje się do statycznego lub niezarządzany zasób, który następnie zwalnia jego finalizator. Jeśli wiele obiektów dzielą jakiś zasób, który jest przetwarzany w finalizatory klasy, obiekty należy zsynchronizować wszelki dostęp do tego zasobu.  
  
## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
