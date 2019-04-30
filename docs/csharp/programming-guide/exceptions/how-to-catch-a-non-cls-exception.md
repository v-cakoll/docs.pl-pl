---
title: 'Instrukcje: Przechwytywanie wyjątku typu non-CLS'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: f64a5de3c09b2f270d49a46ed4170c27483e17d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710865"
---
# <a name="how-to-catch-a-non-cls-exception"></a><span data-ttu-id="490aa-102">Instrukcje: Przechwytywanie wyjątku typu non-CLS</span><span class="sxs-lookup"><span data-stu-id="490aa-102">How to: Catch a non-CLS Exception</span></span>
<span data-ttu-id="490aa-103">Niektórych języków .NET, w tym C++sposób niezamierzony, dopuszcza się użycia obiektów zgłaszają wyjątki, które nie pochodzą z <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="490aa-103">Some .NET languages, including C++/CLI, allow objects to throw exceptions that do not derive from <xref:System.Exception>.</span></span> <span data-ttu-id="490aa-104">Takie wyjątki są nazywane *wyjątki niezgodnych ze specyfikacją CLS* lub *niebędące wyjątkami*.</span><span class="sxs-lookup"><span data-stu-id="490aa-104">Such exceptions are called *non-CLS exceptions* or *non-Exceptions*.</span></span> <span data-ttu-id="490aa-105">W języku C# nie generują wyjątki niezgodnych ze specyfikacją CLS, ale można przechwytywać na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="490aa-105">In C# you cannot throw non-CLS exceptions, but you can catch them in two ways:</span></span>  
  
- <span data-ttu-id="490aa-106">W ramach `catch (RuntimeWrappedException e)` bloku.</span><span class="sxs-lookup"><span data-stu-id="490aa-106">Within a `catch (RuntimeWrappedException e)` block.</span></span>
  
     <span data-ttu-id="490aa-107">Domyślnie zestaw Visual C# przechwytuje wyjątki niezgodnych ze specyfikacją CLS, jako wyjątki opakowana.</span><span class="sxs-lookup"><span data-stu-id="490aa-107">By default, a Visual C# assembly catches non-CLS exceptions as wrapped exceptions.</span></span> <span data-ttu-id="490aa-108">Użyj tej metody, jeśli potrzebny jest dostęp do oryginalnego wyjątku, który jest możliwy za pośrednictwem <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="490aa-108">Use this method if you need access to the original exception, which can be accessed through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="490aa-109">Procedury w dalszej części tego tematu opisano sposób przechwytywanie wyjątków w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="490aa-109">The procedure later in this topic explains how to catch exceptions in this manner.</span></span>  
  
- <span data-ttu-id="490aa-110">W ramach ogólnego bloku catch (catch blok bez określony typ wyjątku), który jest umieszczany po wszystkich innych `catch` bloków.</span><span class="sxs-lookup"><span data-stu-id="490aa-110">Within a general catch block (a catch block without an exception type specified) that is put after all other `catch` blocks.</span></span>
  
     <span data-ttu-id="490aa-111">Metoda ta jest używana, gdy chcesz wykonać pewne działania (na przykład zapis do pliku dziennika) w odpowiedzi na wyjątki niezgodnych ze specyfikacją CLS i nie potrzebujesz dostępu do informacji o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="490aa-111">Use this method when you want to perform some action (such as writing to a log file) in response to non-CLS exceptions, and you do not need access to the exception information.</span></span> <span data-ttu-id="490aa-112">Domyślnie środowisko uruchomieniowe języka wspólnego opakowuje wszystkie wyjątki.</span><span class="sxs-lookup"><span data-stu-id="490aa-112">By default the common language runtime wraps all exceptions.</span></span> <span data-ttu-id="490aa-113">Aby wyłączyć to zachowanie, należy dodać ten atrybut na poziomie zestawu w kodzie, zwykle w pliku AssemblyInfo.cs: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span><span class="sxs-lookup"><span data-stu-id="490aa-113">To disable this behavior, add this assembly-level attribute to your code, typically in the AssemblyInfo.cs file: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span></span>  
  
### <a name="to-catch-a-non-cls-exception"></a><span data-ttu-id="490aa-114">Aby przechwycić wyjątek niezgodny ze specyfikacją</span><span class="sxs-lookup"><span data-stu-id="490aa-114">To catch a non-CLS exception</span></span>  
  
<span data-ttu-id="490aa-115">W ramach `catch(RuntimeWrappedException e)` blokowania, dostęp do oryginalnego wyjątku za pośrednictwem <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="490aa-115">Within a `catch(RuntimeWrappedException e)` block, access the original exception through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="490aa-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="490aa-116">Example</span></span>  
 <span data-ttu-id="490aa-117">Poniższy przykład pokazuje, jak przechwycić wyjątek niezgodny ze specyfikacją, który został zgłoszony z biblioteki klas, napisany w C++sposób niezamierzony.</span><span class="sxs-lookup"><span data-stu-id="490aa-117">The following example shows how to catch a non-CLS exception that was thrown from a class library written in C++/CLI.</span></span> <span data-ttu-id="490aa-118">Należy pamiętać, że w tym przykładzie kodu klienta języka C# wie, z wyprzedzeniem to typ wyjątku jest zgłaszana <xref:System.String?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="490aa-118">Note that in this example, the C# client code knows in advance that the exception type being thrown is a <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="490aa-119">Można rzutować <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> właściwości kopii jego typ oryginalny, tak długo, jak ten typ jest dostępny z poziomu kodu.</span><span class="sxs-lookup"><span data-stu-id="490aa-119">You can cast the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property back its original type as long as that type is accessible from your code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="490aa-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="490aa-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeWrappedException>
- [<span data-ttu-id="490aa-121">Wyjątki i obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="490aa-121">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)
