---
title: Zabezpieczenia i sytuacja wyścigu
'description:': Describes pitfalls to avoid around security holes exploited by race conditions, including dispose methods, constructors, cached objects, and finalizers.
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
ms.openlocfilehash: 09d8d0d6e85af04fe0fb00f53df408126012081e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186777"
---
# <a name="security-and-race-conditions"></a>Zabezpieczenia i sytuacja wyścigu
Innym obszarem zainteresowania jest możliwość luk w zabezpieczeniach wykorzystywanych przez warunki rasowe. Istnieje kilka sposobów, w których może się to zdarzyć. Podtematy, które następują zarys niektórych głównych pułapek, które deweloper musi unikać.  
  
## <a name="race-conditions-in-the-dispose-method"></a>Warunki wyścigu w metodzie utylizacji  
 Jeśli klasy **Dispose** metody (aby uzyskać więcej informacji, zobacz [Wyrzucanie elementów bezużytecznych)](../../../docs/standard/garbage-collection/index.md)nie jest zsynchronizowany, jest możliwe, że kod oczyszczania wewnątrz **Dispose** można uruchomić więcej niż jeden raz, jak pokazano w poniższym przykładzie.  
  
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
  
 Ponieważ ta **implementacja Dispose** nie jest `Cleanup` zsynchronizowana, możliwe jest wywołanie przez `_myObj` pierwszy jeden wątek, a następnie drugi wątek, zanim **ustawiono wartość null**. Czy jest to problem zabezpieczeń zależy `Cleanup` od tego, co się dzieje po uruchomieniu kodu. Głównym problemem z niezsynchronizowane **Implementacje dispose** polega na użyciu dojścia zasobów, takich jak pliki. Niewłaściwa utylizacja może spowodować niewłaściwe uchylnie, co często prowadzi do luk w zabezpieczeniach.  
  
## <a name="race-conditions-in-constructors"></a>Warunki wyścigu w konstruktorów  
 W niektórych aplikacjach może być możliwe dla innych wątków, aby uzyskać dostęp do elementów członkowskich klasy, zanim ich konstruktory klasy zostały całkowicie uruchomione. Należy przejrzeć wszystkie konstruktory klasy, aby upewnić się, że nie ma żadnych problemów z zabezpieczeniami, jeśli tak się stanie, lub w razie potrzeby zsynchronizować wątki.  
  
## <a name="race-conditions-with-cached-objects"></a>Warunki wyścigu z obiektami buforowanymi  
 Kod, który buforuje informacje o zabezpieczeniach lub używa zabezpieczeń dostępu do kodu [Assert](../../../docs/framework/misc/using-the-assert-method.md) operacji może być również narażony na warunki wyścigu, jeśli inne części klasy nie są odpowiednio zsynchronizowane, jak pokazano w poniższym przykładzie.  
  
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
  
 Jeśli istnieją inne `DoOtherWork` ścieżki do tego można wywołać z innego wątku z tego samego obiektu, niezaufany obiekt wywołujący może poślizgu przeszłości popytu.  
  
 Jeśli kod buforuje informacje zabezpieczające, upewnij się, że sprawdzasz je pod kątem tej luki.  
  
## <a name="race-conditions-in-finalizers"></a>Warunki wyścigu w finalizatorów  
 Warunki wyścigu mogą również wystąpić w obiekcie, który odwołuje się do zasobu statycznego lub niezarządzanego, który następnie zwalnia w finalizatora. Jeśli wiele obiektów współużytkuje zasób, który jest manipulowany w finalizatora klasy, obiekty muszą synchronizować cały dostęp do tego zasobu.  
  
## <a name="see-also"></a>Zobacz też

- [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
