---
title: loadFromContext MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
ms.openlocfilehash: d0090a0272d1c3b6175b351175689df1e1e4fdbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181808"
---
# <a name="loadfromcontext-mda"></a><span data-ttu-id="53944-102">loadFromContext MDA</span><span class="sxs-lookup"><span data-stu-id="53944-102">loadFromContext MDA</span></span>
<span data-ttu-id="53944-103">Asystent `loadFromContext` debugowania zarządzanego (MDA) jest aktywowany, `LoadFrom` jeśli zestaw jest ładowany do kontekstu.</span><span class="sxs-lookup"><span data-stu-id="53944-103">The `loadFromContext` managed debugging assistant (MDA) is activated if an assembly is loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="53944-104">Taka sytuacja może wystąpić w <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> wyniku wywołania lub innych podobnych metod.</span><span class="sxs-lookup"><span data-stu-id="53944-104">This situation can occur as a result of calling <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or other similar methods.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="53944-105">Objawy</span><span class="sxs-lookup"><span data-stu-id="53944-105">Symptoms</span></span>  
 <span data-ttu-id="53944-106">Użycie niektórych metod modułu ładującego może spowodować `LoadFrom` zestawy są ładowane w kontekście.</span><span class="sxs-lookup"><span data-stu-id="53944-106">The use of some loader methods can result in assemblies being loaded in the `LoadFrom` context.</span></span> <span data-ttu-id="53944-107">Użycie tego kontekstu może spowodować nieoczekiwane zachowanie serializacji, rzutowania i rozpoznawania zależności.</span><span class="sxs-lookup"><span data-stu-id="53944-107">The use of this context can result in unexpected behavior for serialization, casting, and dependency resolution.</span></span> <span data-ttu-id="53944-108">Ogólnie rzecz biorąc zaleca się, że `Load` zestawy mają być ładowane do kontekstu, aby uniknąć tych problemów.</span><span class="sxs-lookup"><span data-stu-id="53944-108">In general, it is recommended that assemblies be loaded into the `Load` context to avoid these problems.</span></span> <span data-ttu-id="53944-109">Trudno jest określić, który kontekst zestaw został załadowany do bez tego MDA.</span><span class="sxs-lookup"><span data-stu-id="53944-109">It is difficult to determine which context an assembly has been loaded into without this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="53944-110">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="53944-110">Cause</span></span>  
 <span data-ttu-id="53944-111">Ogólnie rzecz biorąc zestaw został `LoadFrom` załadowany do kontekstu, `Load` jeśli został załadowany ze ścieżki <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> poza kontekstem, takich jak globalnej pamięci podręcznej zestawu lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="53944-111">Generally, an assembly was loaded into the `LoadFrom` context if it was loaded from a path outside the `Load` context, such as the global assembly cache or the <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="53944-112">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="53944-112">Resolution</span></span>  
 <span data-ttu-id="53944-113">Skonfiguruj <xref:System.Reflection.Assembly.LoadFrom%2A> aplikacje w taki sposób, aby wywołania nie były już potrzebne.</span><span class="sxs-lookup"><span data-stu-id="53944-113">Configure applications such that <xref:System.Reflection.Assembly.LoadFrom%2A> calls are no longer needed.</span></span> <span data-ttu-id="53944-114">W tym celu można użyć następujących technik:</span><span class="sxs-lookup"><span data-stu-id="53944-114">You can use the following techniques for doing so:</span></span>  
  
- <span data-ttu-id="53944-115">Zainstaluj zestawy w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="53944-115">Install assemblies in the global assembly cache.</span></span>  
  
- <span data-ttu-id="53944-116">Umieść zestawy w <xref:System.AppDomainSetup.ApplicationBase%2A> katalogu dla <xref:System.AppDomain>pliku .</span><span class="sxs-lookup"><span data-stu-id="53944-116">Place assemblies in the <xref:System.AppDomainSetup.ApplicationBase%2A> directory for the <xref:System.AppDomain>.</span></span> <span data-ttu-id="53944-117">W przypadku domeny domyślnej <xref:System.AppDomainSetup.ApplicationBase%2A> katalog jest tym, który zawiera plik wykonywalny, który rozpoczął proces.</span><span class="sxs-lookup"><span data-stu-id="53944-117">In the case of the default domain, the <xref:System.AppDomainSetup.ApplicationBase%2A> directory is the one that contains the executable file that started the process.</span></span> <span data-ttu-id="53944-118">Może to również wymagać <xref:System.AppDomain> utworzenia nowego, jeśli nie jest wygodne, aby przenieść zestaw.</span><span class="sxs-lookup"><span data-stu-id="53944-118">This might also require creating a new <xref:System.AppDomain> if it is not convenient to move the assembly.</span></span>  
  
- <span data-ttu-id="53944-119">Dodaj ścieżkę sondowania do pliku konfiguracji aplikacji (.config) lub do domen aplikacji pomocniczych, jeśli zestawy zależne znajdują się w katalogach podrzędnych względem pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="53944-119">Add a probing path to your application configuration (.config) file or to secondary  application domains if dependent assemblies are in child directories relative to the executable.</span></span>  
  
 <span data-ttu-id="53944-120">W każdym przypadku kod można zmienić, aby użyć <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="53944-120">In each case, the code can be changed to use the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="53944-121">Wpływ na czas działania</span><span class="sxs-lookup"><span data-stu-id="53944-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="53944-122">MDA nie ma żadnego wpływu na CLR.</span><span class="sxs-lookup"><span data-stu-id="53944-122">The MDA does not have any effect on the CLR.</span></span> <span data-ttu-id="53944-123">Raportuje kontekst, który został użyty w wyniku żądania obciążenia.</span><span class="sxs-lookup"><span data-stu-id="53944-123">It reports the context that was used as a result of a load request.</span></span>  
  
## <a name="output"></a><span data-ttu-id="53944-124">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="53944-124">Output</span></span>  
 <span data-ttu-id="53944-125">MDA raporty, że zestaw został `LoadFrom` załadowany do kontekstu.</span><span class="sxs-lookup"><span data-stu-id="53944-125">The MDA reports that the assembly was loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="53944-126">Określa prostą nazwę zestawu i ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="53944-126">It specifies the simple name of the assembly and the path.</span></span> <span data-ttu-id="53944-127">Sugeruje również środki zaradcze, aby uniknąć korzystania z kontekstu. `LoadFrom`</span><span class="sxs-lookup"><span data-stu-id="53944-127">It also suggests mitigations to avoid using the `LoadFrom` context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="53944-128">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="53944-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="53944-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="53944-129">Example</span></span>  
 <span data-ttu-id="53944-130">Poniższy przykład kodu pokazuje sytuację, która może aktywować ten MDA:</span><span class="sxs-lookup"><span data-stu-id="53944-130">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="53944-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="53944-131">See also</span></span>

- [<span data-ttu-id="53944-132">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="53944-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
