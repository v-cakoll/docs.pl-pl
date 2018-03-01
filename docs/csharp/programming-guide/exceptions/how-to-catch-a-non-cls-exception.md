---
title: "Porady: przechwytywanie wyjątku typu non-CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 473cace033983915c66647d14cae16dc7f5d5b9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-catch-a-non-cls-exception"></a>Porady: przechwytywanie wyjątku typu non-CLS
Niektóre języków .NET, w tym C + +/ CLI, pozwalają na zgłaszają wyjątki, które nie pochodzą z obiektów <xref:System.Exception>. Takie wyjątki są nazywane *wyjątki niezgodny ze specyfikacją CLS* lub *niebędące wyjątkami*. W [!INCLUDE[csprcs](~/includes/csprcs-md.md)] nie zgłaszają wyjątki niezgodny ze specyfikacją CLS, ale można je catch na dwa sposoby:  
  
-   W ramach `catch (Exception e)` zablokować jako <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.  
  
     Domyślnie [!INCLUDE[csprcs](~/includes/csprcs-md.md)] zestawu przechwytuje wyjątków niezgodny ze specyfikacją CLS, ponieważ wyjątki opakowana. Użyj tej metody, aby uzyskać dostęp do oryginalnego wyjątków, które mogą być udostępniane za pośrednictwem <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> właściwości. Procedury później w tym temacie wyjaśniono, jak przechwytywanie wyjątków w ten sposób.  
  
-   W bloku catch ogólne (blok catch bez określony typ wyjątku), który jest umieszczany po `catch (Exception)` lub `catch (Exception e)` bloku.  
  
     Użyj tej metody, gdy ma być wykonanie akcji (na przykład zapisywania do pliku dziennika) w odpowiedzi na wyjątki niezgodny ze specyfikacją CLS, oraz czy nie potrzebują dostępu do informacji o wyjątkach. Domyślnie środowisko uruchomieniowe języka wspólnego opakowuje wszystkie wyjątki. Aby wyłączyć to zachowanie, należy dodać ten atrybut poziomu zestawu do kodu, zwykle w pliku AssemblyInfo.cs: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.  
  
### <a name="to-catch-a-non-cls-exception"></a>Aby przechwytywać elementu exception niezgodny ze specyfikacją CLS  
  
1.  W ramach `catch(Exception e) block`, użyj `as` — słowo kluczowe, aby sprawdzić czy `e` mogą być rzutowane na <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.  
  
2.  Dostęp do oryginalnego wyjątku za pomocą <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> właściwości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób catch wyjątek niezgodny ze specyfikacją CLS, który został zgłoszony z biblioteki klas napisany w języku C + +/ CLR. Należy pamiętać, że w tym przykładzie [!INCLUDE[csprcs](~/includes/csprcs-md.md)] kodu klienta z wyprzedzeniem wie, czy ten typ wyjątek został zgłoszony jest <xref:System.String?displayProperty=nameWithType>. Można rzutować <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> właściwości kopii jej oryginalnej typu pod warunkiem, że typ jest dostępny w kodzie.  
  
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
