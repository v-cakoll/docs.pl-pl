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
ms.openlocfilehash: ad27e62197f6fdaa6b5e706f4ae02c03fecae9f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181139"
---
# <a name="securing-exception-handling"></a>Zabezpieczanie obsługi wyjątków
W językach Visual C++ i Visual Basic wyrażenie filtru dalej w górę stosu jest uruchamiane przed dowolną **instrukcją finally.** Blok **catch** skojarzony z tym filtrem jest uruchamiany po instrukcji **finally.** Aby uzyskać więcej informacji, zobacz [Korzystanie z wyjątków filtrowanych przez użytkownika](../../standard/exceptions/using-user-filtered-exception-handlers.md). W tej sekcji przeanalizowano implikacje dla bezpieczeństwa tej kolejności. Należy wziąć pod uwagę następujący przykład pseudokodu, który ilustruje kolejność uruchamiania instrukcji filtrowania i instrukcji **finally.**  
  
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
  
 Ten kod drukuje następujące.  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 Filtr jest uruchamiany przed **instrukcją finally,** więc problemy z zabezpieczeniami mogą być wprowadzane przez wszystko, co powoduje zmianę stanu, w którym wykonanie innego kodu może skorzystać. Przykład:  
  
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
  
 Ten pseudokod umożliwia filtr wyżej stosu, aby uruchomić dowolny kod. Inne przykłady operacji, które mogłyby mieć podobny efekt, to tymczasowe personifikacja innej tożsamości, ustawienie flagi wewnętrznej, która omija niektóre sprawdzanie zabezpieczeń lub zmiana kultury skojarzonej z wątkiem. Zalecane rozwiązanie jest wprowadzenie obsługi wyjątków do izolowania zmian kodu do stanu wątku z bloków filtrów wywołujących. Jednak ważne jest, aby program obsługi wyjątków został prawidłowo wprowadzony lub ten problem nie zostanie rozwiązany. W poniższym przykładzie przełącza kultury interfejsu użytkownika, ale wszelkiego rodzaju zmiany stanu wątku może być podobnie widoczne.  
  
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
  
 Poprawną poprawką w tym przypadku jest zawijanie istniejącej **próby**/**ostatecznie** bloku w bloku catch **try.**/**catch** Po prostu wprowadzenie **catch-throw** klauzuli do istniejącej **try**/**finally** bloku nie rozwiązuje problemu, jak pokazano w poniższym przykładzie.  
  
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
  
 To nie rozwiązuje problemu, ponieważ **instrukcja finally** nie została uruchomiony przed `FilterFunc` pobiera kontroli.  
  
 Poniższy przykład rozwiązuje problem, upewniając się, że **finally** klauzula została wykonana przed oferowaniem wyjątku się bloków filtru wyjątków wywołujących.  
  
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

- [Wytyczne dotyczące bezpiecznego programowania](../../standard/security/secure-coding-guidelines.md)
