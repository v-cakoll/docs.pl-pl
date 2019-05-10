---
title: loadFromContext MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 632d9119cf32aab66c87e345ec98c6867ed51592
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614371"
---
# <a name="loadfromcontext-mda"></a><span data-ttu-id="0d633-102">loadFromContext MDA</span><span class="sxs-lookup"><span data-stu-id="0d633-102">loadFromContext MDA</span></span>
<span data-ttu-id="0d633-103">`loadFromContext` Zarządzanego Asystenta debugowania (MDA) jest włączone, jeśli zestaw jest ładowany do `LoadFrom` kontekstu.</span><span class="sxs-lookup"><span data-stu-id="0d633-103">The `loadFromContext` managed debugging assistant (MDA) is activated if an assembly is loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="0d633-104">Taka sytuacja może wystąpić w wyniku wywołania <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> lub inne podobne metody.</span><span class="sxs-lookup"><span data-stu-id="0d633-104">This situation can occur as a result of calling <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or other similar methods.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="0d633-105">Symptomy</span><span class="sxs-lookup"><span data-stu-id="0d633-105">Symptoms</span></span>  
 <span data-ttu-id="0d633-106">Korzystanie z niektórych metod modułu ładującego może doprowadzić do zestawów, które są ładowane `LoadFrom` kontekstu.</span><span class="sxs-lookup"><span data-stu-id="0d633-106">The use of some loader methods can result in assemblies being loaded in the `LoadFrom` context.</span></span> <span data-ttu-id="0d633-107">Użycie tego kontekstu może spowodować nieoczekiwane zachowanie serializacji, rzutowania i rozpoznawania zależności.</span><span class="sxs-lookup"><span data-stu-id="0d633-107">The use of this context can result in unexpected behavior for serialization, casting, and dependency resolution.</span></span> <span data-ttu-id="0d633-108">Ogólnie rzecz biorąc, zalecane jest, że zestawy wczytanie `Load` kontekstu, aby uniknąć tych problemów.</span><span class="sxs-lookup"><span data-stu-id="0d633-108">In general, it is recommended that assemblies be loaded into the `Load` context to avoid these problems.</span></span> <span data-ttu-id="0d633-109">Trudno określić, w którym kontekście zestaw został załadowany do bez to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="0d633-109">It is difficult to determine which context an assembly has been loaded into without this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="0d633-110">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="0d633-110">Cause</span></span>  
 <span data-ttu-id="0d633-111">Ogólnie rzecz biorąc, zestaw został załadowany do `LoadFrom` kontekstu, jeśli został załadowany ze ścieżki poza `Load` kontekstu, takich jak pamięci podręcznej zestawów globalnych lub <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d633-111">Generally, an assembly was loaded into the `LoadFrom` context if it was loaded from a path outside the `Load` context, such as the global assembly cache or the <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="0d633-112">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="0d633-112">Resolution</span></span>  
 <span data-ttu-id="0d633-113">Skonfigurowanie aplikacji tak, aby <xref:System.Reflection.Assembly.LoadFrom%2A> wywołania nie są już potrzebne.</span><span class="sxs-lookup"><span data-stu-id="0d633-113">Configure applications such that <xref:System.Reflection.Assembly.LoadFrom%2A> calls are no longer needed.</span></span> <span data-ttu-id="0d633-114">Aby to zrobić, można użyć następujących technik:</span><span class="sxs-lookup"><span data-stu-id="0d633-114">You can use the following techniques for doing so:</span></span>  
  
- <span data-ttu-id="0d633-115">Instalowanie zestawów w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="0d633-115">Install assemblies in the global assembly cache.</span></span>  
  
- <span data-ttu-id="0d633-116">Umieść zestawów w <xref:System.AppDomainSetup.ApplicationBase%2A> katalog dla <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="0d633-116">Place assemblies in the <xref:System.AppDomainSetup.ApplicationBase%2A> directory for the <xref:System.AppDomain>.</span></span> <span data-ttu-id="0d633-117">W przypadku domyślnej domeny <xref:System.AppDomainSetup.ApplicationBase%2A> katalog jest ten, który zawiera plik wykonywalny, który uruchomił proces.</span><span class="sxs-lookup"><span data-stu-id="0d633-117">In the case of the default domain, the <xref:System.AppDomainSetup.ApplicationBase%2A> directory is the one that contains the executable file that started the process.</span></span> <span data-ttu-id="0d633-118">Może to również wymagać utworzenie nowego <xref:System.AppDomain> Jeśli nie jest wygodne przenieść zestawu.</span><span class="sxs-lookup"><span data-stu-id="0d633-118">This might also require creating a new <xref:System.AppDomain> if it is not convenient to move the assembly.</span></span>  
  
- <span data-ttu-id="0d633-119">Dodaj badania ścieżki do pliku konfiguracji (.config) aplikacji lub do domen aplikacji dodatkowych zestawów zależnych znajdują się w katalogach podrzędnych względem pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="0d633-119">Add a probing path to your application configuration (.config) file or to secondary  application domains if dependent assemblies are in child directories relative to the executable.</span></span>  
  
 <span data-ttu-id="0d633-120">W każdym przypadku można zmienić kod do użycia <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="0d633-120">In each case, the code can be changed to use the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="0d633-121">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="0d633-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="0d633-122">MDA nie ma żadnego wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="0d633-122">The MDA does not have any effect on the CLR.</span></span> <span data-ttu-id="0d633-123">Zgłasza kontekstu, który został użyty w wyniku żądania obciążenia.</span><span class="sxs-lookup"><span data-stu-id="0d633-123">It reports the context that was used as a result of a load request.</span></span>  
  
## <a name="output"></a><span data-ttu-id="0d633-124">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="0d633-124">Output</span></span>  
 <span data-ttu-id="0d633-125">MDA zgłasza, że zestaw został załadowany do `LoadFrom` kontekstu.</span><span class="sxs-lookup"><span data-stu-id="0d633-125">The MDA reports that the assembly was loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="0d633-126">Określa prostą nazwę zestawu oraz ścieżki.</span><span class="sxs-lookup"><span data-stu-id="0d633-126">It specifies the simple name of the assembly and the path.</span></span> <span data-ttu-id="0d633-127">Podano tu także środków zaradczych, które należy unikać `LoadFrom` kontekstu.</span><span class="sxs-lookup"><span data-stu-id="0d633-127">It also suggests mitigations to avoid using the `LoadFrom` context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="0d633-128">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="0d633-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="0d633-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="0d633-129">Example</span></span>  
 <span data-ttu-id="0d633-130">W poniższym przykładzie kodu pokazano sytuację, która może aktywować to zdarzenie MDA:</span><span class="sxs-lookup"><span data-stu-id="0d633-130">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
```csharp
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // The following call caused the LoadFrom context to be used  
            // because the assembly is loaded using LoadFrom and the path is   
            // located outside of the Load context probing path.   
            Assembly.LoadFrom(@"C:\Text\Test.dll");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d633-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d633-131">See also</span></span>

- [<span data-ttu-id="0d633-132">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="0d633-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
