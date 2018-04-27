---
title: 'Porady: przechwytywanie wyjątku typu non-CLS'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
caps.latest.revision: 8
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5647fc8501afe2a4bf74739fd8efd4e6b74559a2
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-catch-a-non-cls-exception"></a>Porady: przechwytywanie wyjątku typu non-CLS
Niektóre języków .NET, w tym C + +/ CLI, pozwalają na zgłaszają wyjątki, które nie pochodzą z obiektów <xref:System.Exception>. Takie wyjątki są nazywane *wyjątki niezgodny ze specyfikacją CLS* lub *niebędące wyjątkami*. W środowisku Visual C# możesz nie można zgłosić wyjątki niezgodny ze specyfikacją CLS, ale można je catch na dwa sposoby:  
  
-   W ramach `catch (Exception e)` zablokować jako <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.  
  
     Domyślnie zestawu Visual C# przechwytuje wyjątki niezgodny ze specyfikacją CLS jako wyjątki opakowana. Użyj tej metody, aby uzyskać dostęp do oryginalnego wyjątków, które mogą być udostępniane za pośrednictwem <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> właściwości. Procedury później w tym temacie wyjaśniono, jak przechwytywanie wyjątków w ten sposób.  
  
-   W bloku catch ogólne (blok catch bez określony typ wyjątku), który jest umieszczany po `catch (Exception)` lub `catch (Exception e)` bloku.  
  
     Użyj tej metody, gdy ma być wykonanie akcji (na przykład zapisywania do pliku dziennika) w odpowiedzi na wyjątki niezgodny ze specyfikacją CLS, oraz czy nie potrzebują dostępu do informacji o wyjątkach. Domyślnie środowisko uruchomieniowe języka wspólnego opakowuje wszystkie wyjątki. Aby wyłączyć to zachowanie, należy dodać ten atrybut poziomu zestawu do kodu, zwykle w pliku AssemblyInfo.cs: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.  
  
### <a name="to-catch-a-non-cls-exception"></a>Aby przechwytywać elementu exception niezgodny ze specyfikacją CLS  
  
1.  W ramach `catch(Exception e) block`, użyj `as` — słowo kluczowe, aby sprawdzić czy `e` mogą być rzutowane na <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.  
  
2.  Dostęp do oryginalnego wyjątku za pomocą <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> właściwości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób catch wyjątek niezgodny ze specyfikacją CLS, który został zgłoszony z biblioteki klas napisany w języku C + +/ CLR. Należy pamiętać, że w tym przykładzie kodu klienta Visual C# zna wcześniej się typ wyjątek został zgłoszony <xref:System.String?displayProperty=nameWithType>. Można rzutować <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> właściwości kopii jej oryginalnej typu pod warunkiem, że typ jest dostępny w kodzie.  
  
```  
// Class library written in C++/CLR.  
   ThrowNonCLS.Class1 myClass = new ThrowNonCLS.Class1();  
  
   try  
   {  
    // throws gcnew System::String(  
    // "I do not derive from System.Exception!");  
    myClass.TestThrow();   
   }  
  
   catch (Exception e)  
   {  
    RuntimeWrappedException rwe = e as RuntimeWrappedException;  
    if (rwe != null)      
    {  
      String s = rwe.WrappedException as String;  
      if (s != null)  
      {  
        Console.WriteLine(s);  
      }  
    }  
    else  
    {  
       // Handle other System.Exception types.  
    }  
   }             
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.CompilerServices.RuntimeWrappedException>  
 [Wyjątki i obsługa wyjątków](../../../csharp/programming-guide/exceptions/index.md)
