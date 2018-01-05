---
title: "Zabezpieczanie obsługi wyjątków"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- code security, exception handling
- security [.NET Framework], exception handling
- secure coding, exception handling
- exception handling, security
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 548606a0196012fdd21bf5512e8ea7b089c723ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="securing-exception-handling"></a>Zabezpieczanie obsługi wyjątków
W programie Visual C++ i Visual Basic, wyrażenie filtru dalsze górę stosu jest uruchamiany przed każdą **koniec** instrukcji. **Catch** blok skojarzonych z tym filtru jest uruchamiany po **finally** instrukcji. Aby uzyskać więcej informacji, zobacz [wyjątki Using User-Filtered](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md). W tej sekcji sprawdza, czy zabezpieczenia tego zamówienia. Należy wziąć pod uwagę w poniższym przykładzie pseudocode, która ilustruje kolejności, w których instrukcji filtrów i **koniec** instrukcje uruchamiania.  
  
```cpp  
void Main()   
{  
    try   
    {  
        Sub();  
    }   
    except (Filter())   
    {  
        Console.WriteLine("catch");  
    }  
}  
bool Filter () {  
    Console.WriteLine("filter");  
    return true;  
}  
void Sub()   
{  
    try   
    {  
        Console.WriteLine("throw");  
        throw new Exception();  
    }   
    finally   
    {  
        Console.WriteLine("finally");  
    }  
}                        
```  
  
 Ten kod wyświetla następujące czynności.  
  
```  
Throw  
Filter  
Finally  
Catch  
```  
  
 Filtr jest uruchamiany przed **koniec** instrukcji, więc problemy dotyczące zabezpieczeń mogą zostać wprowadzone przez wszystko, co sprawia, że stan zmienianie, gdzie wykonywanie innych kodu można wykorzystać. Na przykład:  
  
```cpp  
try   
{  
    Alter_Security_State();  
    // This means changing anything (state variables,  
    // switching unmanaged context, impersonation, and   
    // so on) that could be exploited if malicious   
    // code ran before state is restored.  
    Do_some_work();  
}   
finally   
{  
    Restore_Security_State();  
    // This simply restores the state change above.  
}  
```  
  
 Ta pseudocode umożliwia filtr górę stosu do uruchomienia dowolnego kodu. Inne przykłady działań, które będą miały ten sam efekt są tymczasowe podszywania się pod innego tożsamości, ustawienie flaga wewnętrzna omija niektóre sprawdzania zabezpieczeń lub zmiana kultura skojarzonym z wątkiem. Zalecanym rozwiązaniem jest wprowadzenie obsługi wyjątków do izolowania zmiany kodu do stanu wątku z bloków filtr wywołań. Jest ważne, czy program obsługi wyjątku prawidłowo wprowadzić lub, ten problem nie zostanie rozwiązany. Poniższy przykład zmienia kultury interfejsu użytkownika, ale podobnie narażeni każdego rodzaju zmiany stanu wątku.  
  
```cpp  
YourObject.YourMethod()  
{  
   CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
   try {  
      Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
      // Do something that throws an exception.  
}  
   finally {  
      Thread.CurrentThread.CurrentUICulture = saveCulture;  
   }  
}  
```  
  
```vb  
Public Class UserCode  
   Public Shared Sub Main()  
      Try  
         Dim obj As YourObject = new YourObject  
         obj.YourMethod()  
      Catch e As Exception When FilterFunc  
         Console.WriteLine("An error occurred: '{0}'", e)  
         Console.WriteLine("Current Culture: {0}",   
Thread.CurrentThread.CurrentUICulture)  
      End Try  
   End Sub  
  
   Public Function FilterFunc As Boolean  
      Console.WriteLine("Current Culture: {0}", Thread.CurrentThread.CurrentUICulture)  
      Return True  
   End Sub  
  
End Class  
```  
  
 Poprawne w tym przypadku będzie opakowywać istniejące **spróbuj**/**koniec** blok w **spróbuj**/**catch** blok. Po prostu wprowadzenie **catch throw** klauzuli do istniejącego **spróbuj**/**koniec** bloku nie rozwiąże to problemu, jak pokazano w poniższym przykładzie.  
  
```cpp  
YourObject.YourMethod()  
{  
    CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
  
    try   
    {  
        Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
        // Do something that throws an exception.  
    }  
    catch { throw; }  
    finally   
    {  
        Thread.CurrentThread.CurrentUICulture = saveCulture;  
    }  
}  
```  
  
 To nie rozwiąże problemu, ponieważ **koniec** instrukcji nie został wcześniej uruchomiony `FilterFunc` pobiera formant.  
  
 Poniższy przykład problem został rozwiązany przez zapewnienie, że **koniec** klauzuli zostało wykonane przed oferty wyjątek się bloki filtru wyjątków wywołań.  
  
```cpp  
YourObject.YourMethod()  
{  
    CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
    try    
    {  
        try   
        {  
            Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
            // Do something that throws an exception.  
        }  
        finally   
        {  
            Thread.CurrentThread.CurrentUICulture = saveCulture;  
        }  
    }  
    catch { throw; }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
