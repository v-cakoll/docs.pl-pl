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
ms.openlocfilehash: 256d9c9b825081e3bcfafd6e0e09de825d046d20
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894542"
---
# <a name="securing-exception-handling"></a>Zabezpieczanie obsługi wyjątków
W wizualizacjach C++ i Visual Basic, wyrażenie filtru uzupełnia stos działa przed jakąkolwiek instrukcją **finally** . Blok **catch** skojarzony z tym filtrem jest uruchamiany po instrukcji **finally** . Aby uzyskać więcej informacji, zobacz [Używanie wyjątków filtrowanych przez użytkownika](../../standard/exceptions/using-user-filtered-exception-handlers.md). Ta sekcja analizuje implikacje związane z bezpieczeństwem tej kolejności. Rozważmy następujący przykład pseudokodzie, który ilustruje kolejność, w której są uruchamiane instrukcje filtru i **finally** .  
  
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
  
 Ten kod drukuje następujące elementy:  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 Filtr jest uruchamiany przed instrukcją **finally** , więc problemy z zabezpieczeniami mogą być wprowadzane przez wszystkie elementy, które wprowadzają zmianę stanu, w którym może zostać wykorzystana funkcja innego kodu. Na przykład:  
  
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
  
 Ta pseudokodzie umożliwia filtrowi zwiększenie poziomu stosu do uruchamiania dowolnego kodu. Inne przykłady operacji, które byłyby podobne, są tymczasowym personifikacją innej tożsamości, ustawiając wewnętrzną flagę, która pomija pewne sprawdzanie zabezpieczeń lub zmieniając kulturę skojarzoną z wątkiem. Zalecanym rozwiązaniem jest wprowadzenie procedury obsługi wyjątków w celu odizolowania zmian kodu stanu wątku z bloków filtrów wywołujących. Należy jednak pamiętać, że program obsługi wyjątków został poprawnie wprowadzony lub ten problem nie zostanie rozwiązany. Poniższy przykład przełącza kulturę interfejsu użytkownika, ale każdy rodzaj zmiany stanu wątku może być podobnie narażony.  
  
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
  
 Poprawna poprawka w tym przypadku polega na zawijaniu istniejącego bloku **try**/**finally** w bloku **try**/**catch** . Po prostu wprowadzenie klauzuli **catch-throw** do istniejącego bloku **try**/**finally** nie rozwiąże problemu, jak pokazano w poniższym przykładzie.  
  
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
  
 Nie rozwiąże to problemu, ponieważ instrukcja **finally** nie została uruchomiona przed `FilterFunc` formantem get.  
  
 Poniższy przykład rozwiązuje problem, upewniając się, że klauzula **finally** została wykonana przed wystąpieniem wyjątku filtru wyjątków wywołań.  
  
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

- [Wytyczne dotyczące bezpiecznego programowania](../../standard/security/secure-coding-guidelines.md)
