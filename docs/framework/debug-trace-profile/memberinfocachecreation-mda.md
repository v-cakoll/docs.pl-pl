---
title: memberInfoCacheCreation MDA
ms.date: 03/30/2017
helpviewer_keywords:
- member info cache creation
- MemberInfoCacheCreation MDA
- reflection, run-time errors
- MDAs (managed debugging assistants), cache
- cache [.NET Framework], reflection
- managed debugging assistants (MDAs), cache
- MemberInfo cache
ms.assetid: 5abdad23-1335-4744-8acb-934002c0b6fe
ms.openlocfilehash: e5dbc769bd634afae06582ee614addafd611fad9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217313"
---
# <a name="memberinfocachecreation-mda"></a><span data-ttu-id="7c049-102">memberInfoCacheCreation MDA</span><span class="sxs-lookup"><span data-stu-id="7c049-102">memberInfoCacheCreation MDA</span></span>
<span data-ttu-id="7c049-103">`memberInfoCacheCreation` Asystent debugowania zarządzanego (MDA) jest uaktywniany podczas tworzenia <xref:System.Reflection.MemberInfo> pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="7c049-103">The `memberInfoCacheCreation` managed debugging assistant (MDA) is activated when a <xref:System.Reflection.MemberInfo> cache is created.</span></span> <span data-ttu-id="7c049-104">Jest to mocne wskazanie programu, który korzysta z funkcji odbicia kosztownych zasobów.</span><span class="sxs-lookup"><span data-stu-id="7c049-104">This is a strong indication of a program that is making use of resource-expensive reflection features.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7c049-105">Objawy</span><span class="sxs-lookup"><span data-stu-id="7c049-105">Symptoms</span></span>  
 <span data-ttu-id="7c049-106">Zestaw roboczy programu zostaje zwiększony, ponieważ program korzysta z bardziej kosztownego odbicia zasobów.</span><span class="sxs-lookup"><span data-stu-id="7c049-106">A program's working set increases because the program is using resource-expensive reflection.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7c049-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="7c049-107">Cause</span></span>  
 <span data-ttu-id="7c049-108">Operacje odbicia, które obejmują <xref:System.Reflection.MemberInfo> obiektów, są uznawane za zasoby kosztowne, ponieważ muszą odczytywać metadane przechowywane na zimnych stronach i ogólnie wskazują, że program używa pewnego typu scenariusza z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="7c049-108">Reflection operations that involve <xref:System.Reflection.MemberInfo> objects are considered resource expensive because they must read metadata that is stored in cold pages and in general they indicate the program is using some type of late-bound scenario.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7c049-109">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="7c049-109">Resolution</span></span>  
 <span data-ttu-id="7c049-110">Możesz określić, gdzie odbicie jest używane w programie, włączając ten MDA, a następnie uruchamiając kod w debugerze lub dołączając debuger, gdy zostanie uaktywnione zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="7c049-110">You can determine where reflection is being used in your program by enabling this MDA and then running your code in a debugger or attaching with a debugger when the MDA is activated.</span></span> <span data-ttu-id="7c049-111">W ramach debugera zostanie wyświetlony ślad stosu przedstawiający miejsce utworzenia pamięci podręcznej <xref:System.Reflection.MemberInfo>, a w tym miejscu można określić, gdzie program używa odbicia.</span><span class="sxs-lookup"><span data-stu-id="7c049-111">Under a debugger you will get a stack trace showing where the <xref:System.Reflection.MemberInfo> cache was created and from there you can determine where your program is using reflection.</span></span>  
  
 <span data-ttu-id="7c049-112">Rozwiązanie zależy od celów kodu.</span><span class="sxs-lookup"><span data-stu-id="7c049-112">The resolution is dependent on the objectives of the code.</span></span> <span data-ttu-id="7c049-113">To zdarzenie MDA ostrzega o tym, że program ma scenariusz z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="7c049-113">This MDA alerts you that your program has a late-bound scenario.</span></span> <span data-ttu-id="7c049-114">Warto określić, czy można zastąpić scenariusz wczesny, czy też wziąć pod uwagę wydajność scenariusza z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="7c049-114">You might want to determine if you can substitute an early-bound scenario or consider the performance of the late bound scenario.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7c049-115">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="7c049-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="7c049-116">To zdarzenie MDA jest aktywowane dla każdej tworzonej pamięci podręcznej <xref:System.Reflection.MemberInfo>.</span><span class="sxs-lookup"><span data-stu-id="7c049-116">This MDA is activated for every <xref:System.Reflection.MemberInfo> cache that is created.</span></span> <span data-ttu-id="7c049-117">Wpływ na wydajność jest nieznaczny.</span><span class="sxs-lookup"><span data-stu-id="7c049-117">The performance impact is negligible.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7c049-118">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="7c049-118">Output</span></span>  
 <span data-ttu-id="7c049-119">W wyniku tego zostanie wyświetlony komunikat z informacją o utworzeniu pamięci podręcznej <xref:System.Reflection.MemberInfo>.</span><span class="sxs-lookup"><span data-stu-id="7c049-119">The MDA outputs a message indicating the <xref:System.Reflection.MemberInfo> cache was created.</span></span> <span data-ttu-id="7c049-120">Użyj debugera, aby uzyskać ślad stosu pokazujący, gdzie program używa odbicia.</span><span class="sxs-lookup"><span data-stu-id="7c049-120">Use a debugger to get a stack trace showing where your program is using reflection.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="7c049-121">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="7c049-121">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="7c049-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c049-122">Example</span></span>  
 <span data-ttu-id="7c049-123">Ten przykładowy kod aktywuje `memberInfoCacheCreation` MDA.</span><span class="sxs-lookup"><span data-stu-id="7c049-123">This sample code will activate the `memberInfoCacheCreation` MDA.</span></span>  
  
```csharp
using System;  
  
public class Exe  
{  
    public static void Main()  
    {  
        typeof(object).GetMethods();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c049-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c049-124">See also</span></span>

- <xref:System.Reflection.MemberInfo>
- [<span data-ttu-id="7c049-125">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="7c049-125">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
