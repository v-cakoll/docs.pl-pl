---
title: loadFromContext MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
ms.openlocfilehash: 28ef6e12c82cf5ca56962756b9ea964d0ae9baaa
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216169"
---
# <a name="loadfromcontext-mda"></a><span data-ttu-id="1c0ad-102">loadFromContext MDA</span><span class="sxs-lookup"><span data-stu-id="1c0ad-102">loadFromContext MDA</span></span>
<span data-ttu-id="1c0ad-103">Asystent debugowania zarządzanego `loadFromContext` (MDA) jest aktywowany, jeśli zestaw jest ładowany do kontekstu `LoadFrom`.</span><span class="sxs-lookup"><span data-stu-id="1c0ad-103">The `loadFromContext` managed debugging assistant (MDA) is activated if an assembly is loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="1c0ad-104">Taka sytuacja może wystąpić w wyniku wywołania <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> lub innych podobnych metod.</span><span class="sxs-lookup"><span data-stu-id="1c0ad-104">This situation can occur as a result of calling <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or other similar methods.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1c0ad-105">Objawy</span><span class="sxs-lookup"><span data-stu-id="1c0ad-105">Symptoms</span></span>  
 <span data-ttu-id="1c0ad-106">Użycie niektórych metod ładujących może spowodować załadowanie zestawów w kontekście `LoadFrom`.</span><span class="sxs-lookup"><span data-stu-id="1c0ad-106">The use of some loader methods can result in assemblies being loaded in the `LoadFrom` context.</span></span> <span data-ttu-id="1c0ad-107">Użycie tego kontekstu może spowodować nieoczekiwane zachowanie serializacji, rzutowania i rozpoznawania zależności.</span><span class="sxs-lookup"><span data-stu-id="1c0ad-107">The use of this context can result in unexpected behavior for serialization, casting, and dependency resolution.</span></span> <span data-ttu-id="1c0ad-108">Ogólnie rzecz biorąc, zaleca się, aby zestawy zostały załadowane do kontekstu `Load`, aby uniknąć tych problemów.</span><span class="sxs-lookup"><span data-stu-id="1c0ad-108">In general, it is recommended that assemblies be loaded into the `Load` context to avoid these problems.</span></span> <span data-ttu-id="1c0ad-109">Trudno jest określić kontekst, do którego zestaw został załadowany, bez tego MDA.</span><span class="sxs-lookup"><span data-stu-id="1c0ad-109">It is difficult to determine which context an assembly has been loaded into without this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1c0ad-110">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="1c0ad-110">Cause</span></span>  
 <span data-ttu-id="1c0ad-111">Ogólnie rzecz biorąc, zestaw został załadowany do kontekstu `LoadFrom`, jeśli został załadowany ze ścieżki poza kontekstem `Load`, takich jak globalna pamięć podręczna zestawów lub właściwość <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1c0ad-111">Generally, an assembly was loaded into the `LoadFrom` context if it was loaded from a path outside the `Load` context, such as the global assembly cache or the <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1c0ad-112">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="1c0ad-112">Resolution</span></span>  
 <span data-ttu-id="1c0ad-113">Skonfiguruj aplikacje, takie jak wywołania <xref:System.Reflection.Assembly.LoadFrom%2A> nie są już potrzebne.</span><span class="sxs-lookup"><span data-stu-id="1c0ad-113">Configure applications such that <xref:System.Reflection.Assembly.LoadFrom%2A> calls are no longer needed.</span></span> <span data-ttu-id="1c0ad-114">W tym celu można użyć następujących technik:</span><span class="sxs-lookup"><span data-stu-id="1c0ad-114">You can use the following techniques for doing so:</span></span>  
  
- <span data-ttu-id="1c0ad-115">Zainstaluj zestawy w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="1c0ad-115">Install assemblies in the global assembly cache.</span></span>  
  
- <span data-ttu-id="1c0ad-116">Umieść zestawy w <xref:System.AppDomainSetup.ApplicationBase%2A> katalogu dla <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="1c0ad-116">Place assemblies in the <xref:System.AppDomainSetup.ApplicationBase%2A> directory for the <xref:System.AppDomain>.</span></span> <span data-ttu-id="1c0ad-117">W przypadku domeny domyślnej katalog <xref:System.AppDomainSetup.ApplicationBase%2A> jest taki, który zawiera plik wykonywalny, który uruchomił proces.</span><span class="sxs-lookup"><span data-stu-id="1c0ad-117">In the case of the default domain, the <xref:System.AppDomainSetup.ApplicationBase%2A> directory is the one that contains the executable file that started the process.</span></span> <span data-ttu-id="1c0ad-118">Może to również wymagać utworzenia nowego <xref:System.AppDomain>, jeśli nie jest to wygodne do przenoszenia zestawu.</span><span class="sxs-lookup"><span data-stu-id="1c0ad-118">This might also require creating a new <xref:System.AppDomain> if it is not convenient to move the assembly.</span></span>  
  
- <span data-ttu-id="1c0ad-119">Dodaj ścieżkę do sondowania do pliku konfiguracji aplikacji (. config) lub do domen aplikacji pomocniczych, jeśli zależne zestawy znajdują się w katalogach podrzędnych względem pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="1c0ad-119">Add a probing path to your application configuration (.config) file or to secondary  application domains if dependent assemblies are in child directories relative to the executable.</span></span>  
  
 <span data-ttu-id="1c0ad-120">W każdym przypadku kod można zmienić, aby użyć metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1c0ad-120">In each case, the code can be changed to use the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1c0ad-121">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="1c0ad-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="1c0ad-122">Zdarzenie MDA nie ma żadnego wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="1c0ad-122">The MDA does not have any effect on the CLR.</span></span> <span data-ttu-id="1c0ad-123">Raportuje kontekst, który został użyty w wyniku żądania załadowania.</span><span class="sxs-lookup"><span data-stu-id="1c0ad-123">It reports the context that was used as a result of a load request.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1c0ad-124">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="1c0ad-124">Output</span></span>  
 <span data-ttu-id="1c0ad-125">Raport MDA, że zestaw został załadowany do kontekstu `LoadFrom`.</span><span class="sxs-lookup"><span data-stu-id="1c0ad-125">The MDA reports that the assembly was loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="1c0ad-126">Określa prostą nazwę zestawu i ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="1c0ad-126">It specifies the simple name of the assembly and the path.</span></span> <span data-ttu-id="1c0ad-127">Sugeruje również środki zaradcze, aby uniknąć używania kontekstu `LoadFrom`.</span><span class="sxs-lookup"><span data-stu-id="1c0ad-127">It also suggests mitigations to avoid using the `LoadFrom` context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="1c0ad-128">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="1c0ad-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="1c0ad-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c0ad-129">Example</span></span>  
 <span data-ttu-id="1c0ad-130">Poniższy przykład kodu demonstruje sytuację, w której można aktywować to MDA:</span><span class="sxs-lookup"><span data-stu-id="1c0ad-130">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1c0ad-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c0ad-131">See also</span></span>

- [<span data-ttu-id="1c0ad-132">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="1c0ad-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
