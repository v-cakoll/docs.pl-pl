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
ms.openlocfilehash: fdfc4d9e9ba3653bd1a762767e3c39a4f62e587a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="security-and-race-conditions"></a>Zabezpieczenia i sytuacja wyścigu
Inny obszar dotyczą jest potencjalnych luk w zabezpieczeniach wykorzystana przez wyścigu. Istnieje kilka sposobów, w których taka sytuacja może wystąpić. Tematy podrzędne, które należy wykonać opisano niektóre z najważniejszych problemów, które należy unikać dewelopera.  
  
## <a name="race-conditions-in-the-dispose-method"></a>Warunki wyścigu w metodzie Dispose  
 Jeśli klasa **Dispose** — metoda (Aby uzyskać więcej informacji, zobacz [wyrzucanie elementów bezużytecznych](../../../docs/standard/garbage-collection/index.md)) jest nie są zsynchronizowane, możliwe jest oczyszczanie kodu wewnątrz **Dispose** może działać więcej niż jedno, jak pokazano w poniższym przykładzie.  
  
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
    if( myObj != null )   
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 Ponieważ to **Dispose** implementacja nie są zsynchronizowane, istnieje możliwość `Cleanup` ma zostać wywołana przez wątek pierwszy z nich, a następnie drugi wątek przed `_myObj` ustawiono **null**. Czy jest to problem dotyczący zabezpieczeń zależy od tego, co się stanie, gdy `Cleanup` kod działa. Główne problem z niezsynchronizowane **Dispose** implementacje polega na użyciu dojść zasobów, takich jak pliki. Niewłaściwy usuwania może spowodować nieprawidłowe dojście mają być używane, która często prowadzi do luk w zabezpieczeniach.  
  
## <a name="race-conditions-in-constructors"></a>Warunki wyścigu w konstruktorach  
 W niektórych aplikacjach może być możliwe na inne wątki na dostęp do elementów członkowskich klasy, przed ich konstruktorów klas całkowicie zostało uruchomione. Należy przejrzeć wszystkie konstruktorów klas, aby upewnić się, że nie ma żadnych zabezpieczeń problemów, jeśli to powinien być lub synchronizowanie wątków w razie potrzeby.  
  
## <a name="race-conditions-with-cached-objects"></a>Warunki wyścigu buforowanych obiektów  
 Kod, który przechowuje informacje o zabezpieczeniach lub używa zabezpieczenia dostępu kodu [Assert](../../../docs/framework/misc/using-the-assert-method.md) operacji może również być narażony na ataki wyścigu Jeśli inne części klasy nie są odpowiednio zsynchronizowane, jak pokazano w poniższym przykładzie.  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False()  
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
    if(SomeDemandPasses())   
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false();  
    }  
}  
void DoOtherWork()   
{  
    if( fCallersOK )   
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
  
 Jeśli istnieją inne ścieżki do `DoOtherWork` który można wywołać z wątku innego za pomocą tego samego obiektu, niezaufanej wywołujący może dostawy popyt w przeszłości.  
  
 Jeśli kod buforuje informacje o zabezpieczeniach, upewnij się, przejrzyj luki w zabezpieczeniach.  
  
## <a name="race-conditions-in-finalizers"></a>Warunki wyścigu w finalizatory  
 Warunki wyścigu może również wystąpić w obiekt, który odwołuje się do zasobu statyczne lub niezarządzane, który następnie powoduje zwolnienie w jego finalizator. Jeśli wiele obiektów korzystają z zasobem, który jest przetwarzane w finalizator klasy, obiekty musi zsynchronizować dostęp do tego zasobu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
