---
title: Zabezpieczanie obsługi wyjątków
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- code security, exception handling
- security [.NET Framework], exception handling
- secure coding, exception handling
- exception handling, security
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc8cd20a4183ffd002f1399b6b50c8956208a21b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61868808"
---
# <a name="securing-exception-handling"></a>Zabezpieczanie obsługi wyjątków
W programie Visual C++ i Visual Basic, wyrażenie filtru do dalszego w górę stosu jest uruchamiany przed każdą **na koniec** instrukcji. **Catch** bloku skojarzony z filtrem, który jest uruchamiany po **na koniec** instrukcji. Aby uzyskać więcej informacji, zobacz [wyjątki Using User-Filtered](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md). Tej części są rozpatrywane ryzyko związane z tej kolejności. Rozważmy następujący przykład pseudokodzie, który ilustruje kolejność, w której instrukcji filtrów i **na koniec** instrukcje uruchamiania.  
  
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
  
 Filtr, który jest uruchamiany przed **na koniec** instrukcji, dzięki czemu problemy z zabezpieczeniami mogą zostać wprowadzone przez wszystko, co sprawia, że stan zmiany, których wykonanie innego kodu, możesz wykorzystać. Na przykład:  
  
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
  
 Ta pseudokodzie umożliwia filtr wyższego rzędu stosu do uruchamiania dowolnego kodu. Inne przykłady działań, które będą miały ten sam efekt są tymczasowe personifikacja innego tożsamości, ustawienie flagi wewnętrznej omija niektóre sprawdzanie zabezpieczeń lub zmiana kulturę skojarzonych z wątkiem. Zalecanym rozwiązaniem jest wprowadzenie obsługi wyjątków do izolowania zmian w kodzie na stan wątku z bloków filtru obiekty wywołujące. Jednak należy prawidłowo wprowadzane obsługi wyjątków lub ten problem nie zostanie rozwiązany. Poniższy przykład zmienia kultura interfejsu użytkownika, ale podobnie narażeni każdego rodzaju zmiany stanu wątku.  
  
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
  
 Słuszność poprawki w tym przypadku jest opakowanie, istniejące **spróbuj**/**na koniec** bloku **spróbuj**/**catch** blok. Po prostu Przedstawiamy **catch throw** klauzuli się z istniejącymi **spróbuj**/**na koniec** bloku nie rozwiąże problemu, jak pokazano w poniższym przykładzie.  
  
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
  
 To nie rozwiąże problemu, ponieważ **na koniec** instrukcji nie został wcześniej uruchomiony `FilterFunc` przejmie kontrolę.  
  
 Poniższy przykład naprawia problem przez zapewnienie, że **na koniec** klauzuli zostało wykonane przed oferty wyjątek bloki filtru wyjątków obiekty wywołujące.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
