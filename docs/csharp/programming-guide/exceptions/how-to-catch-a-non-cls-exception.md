---
title: Przechwytywanie wyjątku typu non-CLS
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: 635cf0a9142f56dea4b2722fbf3f3eda505d85ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75346279"
---
# <a name="how-to-catch-a-non-cls-exception"></a><span data-ttu-id="b7718-102">Przechwytywanie wyjątku typu non-CLS</span><span class="sxs-lookup"><span data-stu-id="b7718-102">How to catch a non-CLS exception</span></span>
<span data-ttu-id="b7718-103">Niektóre języki .NET, w tym C++/CLI, zezwalają obiektom <xref:System.Exception>na zgłaszanie wyjątków, które nie pochodzą z .</span><span class="sxs-lookup"><span data-stu-id="b7718-103">Some .NET languages, including C++/CLI, allow objects to throw exceptions that do not derive from <xref:System.Exception>.</span></span> <span data-ttu-id="b7718-104">Takie wyjątki są nazywane *wyjątkami innych* niż CLS lub *non-Exceptions*.</span><span class="sxs-lookup"><span data-stu-id="b7718-104">Such exceptions are called *non-CLS exceptions* or *non-Exceptions*.</span></span> <span data-ttu-id="b7718-105">W języku C# nie można zgłaszać wyjątków innych niż CLS, ale można je przechwycić na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="b7718-105">In C# you cannot throw non-CLS exceptions, but you can catch them in two ways:</span></span>  
  
- <span data-ttu-id="b7718-106">W `catch (RuntimeWrappedException e)` obrębie bloku.</span><span class="sxs-lookup"><span data-stu-id="b7718-106">Within a `catch (RuntimeWrappedException e)` block.</span></span>
  
     <span data-ttu-id="b7718-107">Domyślnie visual C# zestaw przechwytuje wyjątki innych niż CLS jako opakowane wyjątki.</span><span class="sxs-lookup"><span data-stu-id="b7718-107">By default, a Visual C# assembly catches non-CLS exceptions as wrapped exceptions.</span></span> <span data-ttu-id="b7718-108">Użyj tej metody, jeśli potrzebujesz dostępu do oryginalnego wyjątku, który jest dostępny za pośrednictwem <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b7718-108">Use this method if you need access to the original exception, which can be accessed through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="b7718-109">Procedura w dalszej części tego tematu wyjaśnia, jak w ten sposób wychwycić wyjątki.</span><span class="sxs-lookup"><span data-stu-id="b7718-109">The procedure later in this topic explains how to catch exceptions in this manner.</span></span>  
  
- <span data-ttu-id="b7718-110">W obrębie ogólnego bloku catch (catch bloku bez określonego typu `catch` wyjątku), który jest umieszczany po wszystkich innych bloków.</span><span class="sxs-lookup"><span data-stu-id="b7718-110">Within a general catch block (a catch block without an exception type specified) that is put after all other `catch` blocks.</span></span>
  
     <span data-ttu-id="b7718-111">Tej metody należy użyć, gdy chcesz wykonać niektóre działania (takie jak zapis do pliku dziennika) w odpowiedzi na wyjątki innych niż CLS i nie trzeba dostępu do informacji o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b7718-111">Use this method when you want to perform some action (such as writing to a log file) in response to non-CLS exceptions, and you do not need access to the exception information.</span></span> <span data-ttu-id="b7718-112">Domyślnie czas wykonywania języka wspólnego zawija wszystkie wyjątki.</span><span class="sxs-lookup"><span data-stu-id="b7718-112">By default the common language runtime wraps all exceptions.</span></span> <span data-ttu-id="b7718-113">Aby wyłączyć to zachowanie, dodaj ten atrybut na poziomie zestawu do `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`kodu, zazwyczaj w pliku AssemblyInfo.cs: .</span><span class="sxs-lookup"><span data-stu-id="b7718-113">To disable this behavior, add this assembly-level attribute to your code, typically in the AssemblyInfo.cs file: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span></span>  
  
### <a name="to-catch-a-non-cls-exception"></a><span data-ttu-id="b7718-114">Aby przechwycić wyjątek niebędący cls</span><span class="sxs-lookup"><span data-stu-id="b7718-114">To catch a non-CLS exception</span></span>  
  
<span data-ttu-id="b7718-115">W `catch(RuntimeWrappedException e)` bloku, dostęp do oryginalnego wyjątku <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> za pośrednictwem właściwości.</span><span class="sxs-lookup"><span data-stu-id="b7718-115">Within a `catch(RuntimeWrappedException e)` block, access the original exception through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7718-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="b7718-116">Example</span></span>  
 <span data-ttu-id="b7718-117">W poniższym przykładzie pokazano, jak przechwycić wyjątek niecls, który został wygenerowany z biblioteki klas napisanych w Języku C++/CLI.</span><span class="sxs-lookup"><span data-stu-id="b7718-117">The following example shows how to catch a non-CLS exception that was thrown from a class library written in C++/CLI.</span></span> <span data-ttu-id="b7718-118">Należy zauważyć, że w tym przykładzie kod klienta Języka C# <xref:System.String?displayProperty=nameWithType>wie z góry, że zgłaszany jest typ wyjątku .</span><span class="sxs-lookup"><span data-stu-id="b7718-118">Note that in this example, the C# client code knows in advance that the exception type being thrown is a <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b7718-119">Można rzutować <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> właściwość z powrotem jego oryginalny typ tak długo, jak ten typ jest dostępny z kodu.</span><span class="sxs-lookup"><span data-stu-id="b7718-119">You can cast the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property back its original type as long as that type is accessible from your code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b7718-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7718-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeWrappedException>
- [<span data-ttu-id="b7718-121">Wyjątki i obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="b7718-121">Exceptions and Exception Handling</span></span>](./index.md)
