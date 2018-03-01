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
# <a name="how-to-catch-a-non-cls-exception"></a><span data-ttu-id="8357e-102">Porady: przechwytywanie wyjątku typu non-CLS</span><span class="sxs-lookup"><span data-stu-id="8357e-102">How to: Catch a non-CLS Exception</span></span>
<span data-ttu-id="8357e-103">Niektóre języków .NET, w tym C + +/ CLI, pozwalają na zgłaszają wyjątki, które nie pochodzą z obiektów <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="8357e-103">Some .NET languages, including C++/CLI, allow objects to throw exceptions that do not derive from <xref:System.Exception>.</span></span> <span data-ttu-id="8357e-104">Takie wyjątki są nazywane *wyjątki niezgodny ze specyfikacją CLS* lub *niebędące wyjątkami*.</span><span class="sxs-lookup"><span data-stu-id="8357e-104">Such exceptions are called *non-CLS exceptions* or *non-Exceptions*.</span></span> <span data-ttu-id="8357e-105">W [!INCLUDE[csprcs](~/includes/csprcs-md.md)] nie zgłaszają wyjątki niezgodny ze specyfikacją CLS, ale można je catch na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="8357e-105">In [!INCLUDE[csprcs](~/includes/csprcs-md.md)] you cannot throw non-CLS exceptions, but you can catch them in two ways:</span></span>  
  
-   <span data-ttu-id="8357e-106">W ramach `catch (Exception e)` zablokować jako <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span><span class="sxs-lookup"><span data-stu-id="8357e-106">Within a `catch (Exception e)` block as a <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span></span>  
  
     <span data-ttu-id="8357e-107">Domyślnie [!INCLUDE[csprcs](~/includes/csprcs-md.md)] zestawu przechwytuje wyjątków niezgodny ze specyfikacją CLS, ponieważ wyjątki opakowana.</span><span class="sxs-lookup"><span data-stu-id="8357e-107">By default, a [!INCLUDE[csprcs](~/includes/csprcs-md.md)] assembly catches non-CLS exceptions as wrapped exceptions.</span></span> <span data-ttu-id="8357e-108">Użyj tej metody, aby uzyskać dostęp do oryginalnego wyjątków, które mogą być udostępniane za pośrednictwem <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8357e-108">Use this method if you need access to the original exception, which can be accessed through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> property.</span></span> <span data-ttu-id="8357e-109">Procedury później w tym temacie wyjaśniono, jak przechwytywanie wyjątków w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="8357e-109">The procedure later in this topic explains how to catch exceptions in this manner.</span></span>  
  
-   <span data-ttu-id="8357e-110">W bloku catch ogólne (blok catch bez określony typ wyjątku), który jest umieszczany po `catch (Exception)` lub `catch (Exception e)` bloku.</span><span class="sxs-lookup"><span data-stu-id="8357e-110">Within a general catch block (a catch block without an exception type specified) that is put after a `catch (Exception)` or `catch (Exception e)` block.</span></span>  
  
     <span data-ttu-id="8357e-111">Użyj tej metody, gdy ma być wykonanie akcji (na przykład zapisywania do pliku dziennika) w odpowiedzi na wyjątki niezgodny ze specyfikacją CLS, oraz czy nie potrzebują dostępu do informacji o wyjątkach.</span><span class="sxs-lookup"><span data-stu-id="8357e-111">Use this method when you want to perform some action (such as writing to a log file) in response to non-CLS exceptions, and you do not need access to the exception information.</span></span> <span data-ttu-id="8357e-112">Domyślnie środowisko uruchomieniowe języka wspólnego opakowuje wszystkie wyjątki.</span><span class="sxs-lookup"><span data-stu-id="8357e-112">By default the common language runtime wraps all exceptions.</span></span> <span data-ttu-id="8357e-113">Aby wyłączyć to zachowanie, należy dodać ten atrybut poziomu zestawu do kodu, zwykle w pliku AssemblyInfo.cs: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span><span class="sxs-lookup"><span data-stu-id="8357e-113">To disable this behavior, add this assembly-level attribute to your code, typically in the AssemblyInfo.cs file: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span></span>  
  
### <a name="to-catch-a-non-cls-exception"></a><span data-ttu-id="8357e-114">Aby przechwytywać elementu exception niezgodny ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="8357e-114">To catch a non-CLS exception</span></span>  
  
1.  <span data-ttu-id="8357e-115">W ramach `catch(Exception e) block`, użyj `as` — słowo kluczowe, aby sprawdzić czy `e` mogą być rzutowane na <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span><span class="sxs-lookup"><span data-stu-id="8357e-115">Within a `catch(Exception e) block`, use the `as` keyword to test whether `e` can be cast to a <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span></span>  
  
2.  <span data-ttu-id="8357e-116">Dostęp do oryginalnego wyjątku za pomocą <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8357e-116">Access the original exception through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8357e-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="8357e-117">Example</span></span>  
 <span data-ttu-id="8357e-118">Poniższy przykład przedstawia sposób catch wyjątek niezgodny ze specyfikacją CLS, który został zgłoszony z biblioteki klas napisany w języku C + +/ CLR.</span><span class="sxs-lookup"><span data-stu-id="8357e-118">The following example shows how to catch a non-CLS exception that was thrown from a class library written in C++/CLR.</span></span> <span data-ttu-id="8357e-119">Należy pamiętać, że w tym przykładzie [!INCLUDE[csprcs](~/includes/csprcs-md.md)] kodu klienta z wyprzedzeniem wie, czy ten typ wyjątek został zgłoszony jest <xref:System.String?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8357e-119">Note that in this example, the [!INCLUDE[csprcs](~/includes/csprcs-md.md)] client code knows in advance that the exception type being thrown is a <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8357e-120">Można rzutować <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> właściwości kopii jej oryginalnej typu pod warunkiem, że typ jest dostępny w kodzie.</span><span class="sxs-lookup"><span data-stu-id="8357e-120">You can cast the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> property back its original type as long as that type is accessible from your code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8357e-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8357e-121">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.RuntimeWrappedException>  
 [<span data-ttu-id="8357e-122">Wyjątki i obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="8357e-122">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)
