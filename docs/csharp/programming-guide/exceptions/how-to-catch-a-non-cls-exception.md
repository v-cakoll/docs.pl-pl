---
title: 'Instrukcje: Przechwytywanie wyjątku typu non-CLS'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: d0ba212610372a89c2a3b4c6a249c6d8a02fa507
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590285"
---
# <a name="how-to-catch-a-non-cls-exception"></a><span data-ttu-id="f3d68-102">Instrukcje: Przechwytywanie wyjątku typu non-CLS</span><span class="sxs-lookup"><span data-stu-id="f3d68-102">How to: Catch a non-CLS Exception</span></span>
<span data-ttu-id="f3d68-103">Niektóre języki .NET, w C++tym/CLI, umożliwiają obiektom zgłaszanie wyjątków, które nie <xref:System.Exception>pochodzą od.</span><span class="sxs-lookup"><span data-stu-id="f3d68-103">Some .NET languages, including C++/CLI, allow objects to throw exceptions that do not derive from <xref:System.Exception>.</span></span> <span data-ttu-id="f3d68-104">Takie wyjątki są nazywane wyjątkami nienależącymi *do CLS* lub niewyjątkami.</span><span class="sxs-lookup"><span data-stu-id="f3d68-104">Such exceptions are called *non-CLS exceptions* or *non-Exceptions*.</span></span> <span data-ttu-id="f3d68-105">C# Nie można zgłosić wyjątków innych niż CLS, ale można je przechwycić na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="f3d68-105">In C# you cannot throw non-CLS exceptions, but you can catch them in two ways:</span></span>  
  
- <span data-ttu-id="f3d68-106">`catch (RuntimeWrappedException e)` Wewnątrz bloku.</span><span class="sxs-lookup"><span data-stu-id="f3d68-106">Within a `catch (RuntimeWrappedException e)` block.</span></span>
  
     <span data-ttu-id="f3d68-107">Domyślnie zestaw wizualizacji C# przechwytuje wyjątki niebędące CLS jako wyjątki opakowane.</span><span class="sxs-lookup"><span data-stu-id="f3d68-107">By default, a Visual C# assembly catches non-CLS exceptions as wrapped exceptions.</span></span> <span data-ttu-id="f3d68-108">Użyj tej metody, jeśli potrzebujesz dostępu do oryginalnego wyjątku, do którego można uzyskać dostęp za pomocą <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f3d68-108">Use this method if you need access to the original exception, which can be accessed through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="f3d68-109">Procedura w dalszej części tego tematu wyjaśnia, jak przechwytywać wyjątki w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="f3d68-109">The procedure later in this topic explains how to catch exceptions in this manner.</span></span>  
  
- <span data-ttu-id="f3d68-110">W obrębie ogólnego bloku catch (blok catch bez określonego typu wyjątku) jest umieszczany po wszystkich pozostałych `catch` blokach.</span><span class="sxs-lookup"><span data-stu-id="f3d68-110">Within a general catch block (a catch block without an exception type specified) that is put after all other `catch` blocks.</span></span>
  
     <span data-ttu-id="f3d68-111">Tej metody należy użyć, gdy chcesz wykonać pewne działania (takie jak zapis w pliku dziennika) w odpowiedzi na wyjątki nienależące do CLS i nie potrzebujesz dostępu do informacji o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="f3d68-111">Use this method when you want to perform some action (such as writing to a log file) in response to non-CLS exceptions, and you do not need access to the exception information.</span></span> <span data-ttu-id="f3d68-112">Domyślnie środowisko uruchomieniowe języka wspólnego otacza wszystkie wyjątki.</span><span class="sxs-lookup"><span data-stu-id="f3d68-112">By default the common language runtime wraps all exceptions.</span></span> <span data-ttu-id="f3d68-113">Aby wyłączyć to zachowanie, Dodaj ten atrybut poziomu zestawu do kodu, zazwyczaj w pliku AssemblyInfo.cs: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span><span class="sxs-lookup"><span data-stu-id="f3d68-113">To disable this behavior, add this assembly-level attribute to your code, typically in the AssemblyInfo.cs file: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span></span>  
  
### <a name="to-catch-a-non-cls-exception"></a><span data-ttu-id="f3d68-114">Aby przechwycić wyjątek niezgodny ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="f3d68-114">To catch a non-CLS exception</span></span>  
  
<span data-ttu-id="f3d68-115">W bloku Uzyskuj dostęp do oryginalnego wyjątku <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> przez właściwość. `catch(RuntimeWrappedException e)`</span><span class="sxs-lookup"><span data-stu-id="f3d68-115">Within a `catch(RuntimeWrappedException e)` block, access the original exception through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3d68-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="f3d68-116">Example</span></span>  
 <span data-ttu-id="f3d68-117">Poniższy przykład pokazuje, jak przechwytywać wyjątek niezgodny ze specyfikacją CLS zgłoszoną przez bibliotekę klas zapisaną C++w/CLI.</span><span class="sxs-lookup"><span data-stu-id="f3d68-117">The following example shows how to catch a non-CLS exception that was thrown from a class library written in C++/CLI.</span></span> <span data-ttu-id="f3d68-118">Należy zauważyć, że w tym przykładzie C# kod klienta wie z wyprzedzeniem, że zwracany typ wyjątku to <xref:System.String?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f3d68-118">Note that in this example, the C# client code knows in advance that the exception type being thrown is a <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f3d68-119">Można rzutować Właściwość <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> z powrotem na oryginalny typ, o ile ten typ jest dostępny z kodu.</span><span class="sxs-lookup"><span data-stu-id="f3d68-119">You can cast the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property back its original type as long as that type is accessible from your code.</span></span>  
  
```csharp
// Class library written in C++/CLI.
var myClass = new ThrowNonCLS.Class1();

try
{
    // throws gcnew System::String(  
    // "I do not derive from System.Exception!");  
    myClass.TestThrow();
}
catch (RuntimeWrappedException e)
{
    String s = e.WrappedException as String;
    if (s != null)
    {
        Console.WriteLine(s);
    }
}
```  
  
## <a name="see-also"></a><span data-ttu-id="f3d68-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3d68-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeWrappedException>
- [<span data-ttu-id="f3d68-121">Wyjątki i obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="f3d68-121">Exceptions and Exception Handling</span></span>](./index.md)
