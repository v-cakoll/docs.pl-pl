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
# <a name="how-to-catch-a-non-cls-exception"></a><span data-ttu-id="44ae5-102">Porady: przechwytywanie wyjątku typu non-CLS</span><span class="sxs-lookup"><span data-stu-id="44ae5-102">How to: Catch a non-CLS Exception</span></span>
<span data-ttu-id="44ae5-103">Niektóre języków .NET, w tym C + +/ CLI, pozwalają na zgłaszają wyjątki, które nie pochodzą z obiektów <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="44ae5-103">Some .NET languages, including C++/CLI, allow objects to throw exceptions that do not derive from <xref:System.Exception>.</span></span> <span data-ttu-id="44ae5-104">Takie wyjątki są nazywane *wyjątki niezgodny ze specyfikacją CLS* lub *niebędące wyjątkami*.</span><span class="sxs-lookup"><span data-stu-id="44ae5-104">Such exceptions are called *non-CLS exceptions* or *non-Exceptions*.</span></span> <span data-ttu-id="44ae5-105">W środowisku Visual C# możesz nie można zgłosić wyjątki niezgodny ze specyfikacją CLS, ale można je catch na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="44ae5-105">In Visual C# you cannot throw non-CLS exceptions, but you can catch them in two ways:</span></span>  
  
-   <span data-ttu-id="44ae5-106">W ramach `catch (Exception e)` zablokować jako <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span><span class="sxs-lookup"><span data-stu-id="44ae5-106">Within a `catch (Exception e)` block as a <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span></span>  
  
     <span data-ttu-id="44ae5-107">Domyślnie zestawu Visual C# przechwytuje wyjątki niezgodny ze specyfikacją CLS jako wyjątki opakowana.</span><span class="sxs-lookup"><span data-stu-id="44ae5-107">By default, a Visual C# assembly catches non-CLS exceptions as wrapped exceptions.</span></span> <span data-ttu-id="44ae5-108">Użyj tej metody, aby uzyskać dostęp do oryginalnego wyjątków, które mogą być udostępniane za pośrednictwem <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="44ae5-108">Use this method if you need access to the original exception, which can be accessed through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> property.</span></span> <span data-ttu-id="44ae5-109">Procedury później w tym temacie wyjaśniono, jak przechwytywanie wyjątków w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="44ae5-109">The procedure later in this topic explains how to catch exceptions in this manner.</span></span>  
  
-   <span data-ttu-id="44ae5-110">W bloku catch ogólne (blok catch bez określony typ wyjątku), który jest umieszczany po `catch (Exception)` lub `catch (Exception e)` bloku.</span><span class="sxs-lookup"><span data-stu-id="44ae5-110">Within a general catch block (a catch block without an exception type specified) that is put after a `catch (Exception)` or `catch (Exception e)` block.</span></span>  
  
     <span data-ttu-id="44ae5-111">Użyj tej metody, gdy ma być wykonanie akcji (na przykład zapisywania do pliku dziennika) w odpowiedzi na wyjątki niezgodny ze specyfikacją CLS, oraz czy nie potrzebują dostępu do informacji o wyjątkach.</span><span class="sxs-lookup"><span data-stu-id="44ae5-111">Use this method when you want to perform some action (such as writing to a log file) in response to non-CLS exceptions, and you do not need access to the exception information.</span></span> <span data-ttu-id="44ae5-112">Domyślnie środowisko uruchomieniowe języka wspólnego opakowuje wszystkie wyjątki.</span><span class="sxs-lookup"><span data-stu-id="44ae5-112">By default the common language runtime wraps all exceptions.</span></span> <span data-ttu-id="44ae5-113">Aby wyłączyć to zachowanie, należy dodać ten atrybut poziomu zestawu do kodu, zwykle w pliku AssemblyInfo.cs: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span><span class="sxs-lookup"><span data-stu-id="44ae5-113">To disable this behavior, add this assembly-level attribute to your code, typically in the AssemblyInfo.cs file: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span></span>  
  
### <a name="to-catch-a-non-cls-exception"></a><span data-ttu-id="44ae5-114">Aby przechwytywać elementu exception niezgodny ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="44ae5-114">To catch a non-CLS exception</span></span>  
  
1.  <span data-ttu-id="44ae5-115">W ramach `catch(Exception e) block`, użyj `as` — słowo kluczowe, aby sprawdzić czy `e` mogą być rzutowane na <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span><span class="sxs-lookup"><span data-stu-id="44ae5-115">Within a `catch(Exception e) block`, use the `as` keyword to test whether `e` can be cast to a <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span></span>  
  
2.  <span data-ttu-id="44ae5-116">Dostęp do oryginalnego wyjątku za pomocą <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="44ae5-116">Access the original exception through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44ae5-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="44ae5-117">Example</span></span>  
 <span data-ttu-id="44ae5-118">Poniższy przykład przedstawia sposób catch wyjątek niezgodny ze specyfikacją CLS, który został zgłoszony z biblioteki klas napisany w języku C + +/ CLR.</span><span class="sxs-lookup"><span data-stu-id="44ae5-118">The following example shows how to catch a non-CLS exception that was thrown from a class library written in C++/CLR.</span></span> <span data-ttu-id="44ae5-119">Należy pamiętać, że w tym przykładzie kodu klienta Visual C# zna wcześniej się typ wyjątek został zgłoszony <xref:System.String?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="44ae5-119">Note that in this example, the Visual C# client code knows in advance that the exception type being thrown is a <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="44ae5-120">Można rzutować <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> właściwości kopii jej oryginalnej typu pod warunkiem, że typ jest dostępny w kodzie.</span><span class="sxs-lookup"><span data-stu-id="44ae5-120">You can cast the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> property back its original type as long as that type is accessible from your code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="44ae5-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="44ae5-121">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.RuntimeWrappedException>  
 [<span data-ttu-id="44ae5-122">Wyjątki i obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="44ae5-122">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)
