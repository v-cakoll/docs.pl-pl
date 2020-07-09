---
title: loadFromContext MDA
description: Informacje o programie loadFromContext Managed Debug Assistant (MDA) w programie .NET, który jest uaktywniany w przypadku załadowania zestawu do kontekstu LoadFrom.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
ms.openlocfilehash: 8d55268f2b2106dde4e488a6f0271fd3b17349da
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051652"
---
# <a name="loadfromcontext-mda"></a><span data-ttu-id="fedcb-103">loadFromContext MDA</span><span class="sxs-lookup"><span data-stu-id="fedcb-103">loadFromContext MDA</span></span>
<span data-ttu-id="fedcb-104">`loadFromContext`Asystent debugowania zarządzanego (MDA) jest aktywowany, jeśli zestaw jest ładowany do `LoadFrom` kontekstu.</span><span class="sxs-lookup"><span data-stu-id="fedcb-104">The `loadFromContext` managed debugging assistant (MDA) is activated if an assembly is loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="fedcb-105">Taka sytuacja może wystąpić w wyniku wywołania <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> lub innych podobnych metod.</span><span class="sxs-lookup"><span data-stu-id="fedcb-105">This situation can occur as a result of calling <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or other similar methods.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="fedcb-106">Objawy</span><span class="sxs-lookup"><span data-stu-id="fedcb-106">Symptoms</span></span>  
 <span data-ttu-id="fedcb-107">Użycie niektórych metod ładujących może spowodować załadowanie zestawów w `LoadFrom` kontekście.</span><span class="sxs-lookup"><span data-stu-id="fedcb-107">The use of some loader methods can result in assemblies being loaded in the `LoadFrom` context.</span></span> <span data-ttu-id="fedcb-108">Użycie tego kontekstu może spowodować nieoczekiwane zachowanie serializacji, rzutowania i rozpoznawania zależności.</span><span class="sxs-lookup"><span data-stu-id="fedcb-108">The use of this context can result in unexpected behavior for serialization, casting, and dependency resolution.</span></span> <span data-ttu-id="fedcb-109">Ogólnie rzecz biorąc, zaleca się, aby zestawy zostały załadowane do `Load` kontekstu, aby uniknąć tych problemów.</span><span class="sxs-lookup"><span data-stu-id="fedcb-109">In general, it is recommended that assemblies be loaded into the `Load` context to avoid these problems.</span></span> <span data-ttu-id="fedcb-110">Trudno jest określić kontekst, do którego zestaw został załadowany, bez tego MDA.</span><span class="sxs-lookup"><span data-stu-id="fedcb-110">It is difficult to determine which context an assembly has been loaded into without this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="fedcb-111">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="fedcb-111">Cause</span></span>  
 <span data-ttu-id="fedcb-112">Ogólnie rzecz biorąc, zestaw został załadowany do `LoadFrom` kontekstu, jeśli został załadowany ze ścieżki poza `Load` kontekstem, takiej jak globalna pamięć podręczna zestawu lub <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="fedcb-112">Generally, an assembly was loaded into the `LoadFrom` context if it was loaded from a path outside the `Load` context, such as the global assembly cache or the <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="fedcb-113">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="fedcb-113">Resolution</span></span>  
 <span data-ttu-id="fedcb-114">Skonfiguruj aplikacje, takie jak wywołania, które <xref:System.Reflection.Assembly.LoadFrom%2A> nie są już potrzebne.</span><span class="sxs-lookup"><span data-stu-id="fedcb-114">Configure applications such that <xref:System.Reflection.Assembly.LoadFrom%2A> calls are no longer needed.</span></span> <span data-ttu-id="fedcb-115">W tym celu można użyć następujących technik:</span><span class="sxs-lookup"><span data-stu-id="fedcb-115">You can use the following techniques for doing so:</span></span>  
  
- <span data-ttu-id="fedcb-116">Zainstaluj zestawy w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="fedcb-116">Install assemblies in the global assembly cache.</span></span>  
  
- <span data-ttu-id="fedcb-117">Umieść zestawy w <xref:System.AppDomainSetup.ApplicationBase%2A> katalogu dla <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="fedcb-117">Place assemblies in the <xref:System.AppDomainSetup.ApplicationBase%2A> directory for the <xref:System.AppDomain>.</span></span> <span data-ttu-id="fedcb-118">W przypadku domeny domyślnej <xref:System.AppDomainSetup.ApplicationBase%2A> katalog jest tym, który zawiera plik wykonywalny, który uruchomił proces.</span><span class="sxs-lookup"><span data-stu-id="fedcb-118">In the case of the default domain, the <xref:System.AppDomainSetup.ApplicationBase%2A> directory is the one that contains the executable file that started the process.</span></span> <span data-ttu-id="fedcb-119">Może to również wymagać utworzenia nowego, <xref:System.AppDomain> Jeśli nie jest wygodne przenoszenie zestawu.</span><span class="sxs-lookup"><span data-stu-id="fedcb-119">This might also require creating a new <xref:System.AppDomain> if it is not convenient to move the assembly.</span></span>  
  
- <span data-ttu-id="fedcb-120">Dodaj ścieżkę do sondowania do pliku konfiguracji aplikacji (. config) lub do domen aplikacji pomocniczych, jeśli zależne zestawy znajdują się w katalogach podrzędnych względem pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="fedcb-120">Add a probing path to your application configuration (.config) file or to secondary  application domains if dependent assemblies are in child directories relative to the executable.</span></span>  
  
 <span data-ttu-id="fedcb-121">W każdym przypadku kod można zmienić, aby użyć <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="fedcb-121">In each case, the code can be changed to use the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="fedcb-122">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="fedcb-122">Effect on the Runtime</span></span>  
 <span data-ttu-id="fedcb-123">Zdarzenie MDA nie ma żadnego wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="fedcb-123">The MDA does not have any effect on the CLR.</span></span> <span data-ttu-id="fedcb-124">Raportuje kontekst, który został użyty w wyniku żądania załadowania.</span><span class="sxs-lookup"><span data-stu-id="fedcb-124">It reports the context that was used as a result of a load request.</span></span>  
  
## <a name="output"></a><span data-ttu-id="fedcb-125">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="fedcb-125">Output</span></span>  
 <span data-ttu-id="fedcb-126">Raport MDA, że zestaw został załadowany do `LoadFrom` kontekstu.</span><span class="sxs-lookup"><span data-stu-id="fedcb-126">The MDA reports that the assembly was loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="fedcb-127">Określa prostą nazwę zestawu i ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="fedcb-127">It specifies the simple name of the assembly and the path.</span></span> <span data-ttu-id="fedcb-128">Sugeruje również środki zaradcze, aby uniknąć korzystania z `LoadFrom` kontekstu.</span><span class="sxs-lookup"><span data-stu-id="fedcb-128">It also suggests mitigations to avoid using the `LoadFrom` context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="fedcb-129">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="fedcb-129">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="fedcb-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="fedcb-130">Example</span></span>  
 <span data-ttu-id="fedcb-131">Poniższy przykład kodu demonstruje sytuację, w której można aktywować to MDA:</span><span class="sxs-lookup"><span data-stu-id="fedcb-131">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fedcb-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fedcb-132">See also</span></span>

- [<span data-ttu-id="fedcb-133">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="fedcb-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
