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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90f59f4d593a8aa077a6710cc0f5c1747ac1a3ad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103769"
---
# <a name="memberinfocachecreation-mda"></a><span data-ttu-id="892e3-102">memberInfoCacheCreation MDA</span><span class="sxs-lookup"><span data-stu-id="892e3-102">memberInfoCacheCreation MDA</span></span>
<span data-ttu-id="892e3-103">`memberInfoCacheCreation` Zarządzanego Asystenta debugowania (MDA) jest aktywowany po <xref:System.Reflection.MemberInfo> utworzeniu pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="892e3-103">The `memberInfoCacheCreation` managed debugging assistant (MDA) is activated when a <xref:System.Reflection.MemberInfo> cache is created.</span></span> <span data-ttu-id="892e3-104">To silne wskazanie program, który wykonuje korzystania z funkcji odbicia drogich zasobów.</span><span class="sxs-lookup"><span data-stu-id="892e3-104">This is a strong indication of a program that is making use of resource-expensive reflection features.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="892e3-105">Symptomy</span><span class="sxs-lookup"><span data-stu-id="892e3-105">Symptoms</span></span>  
 <span data-ttu-id="892e3-106">Program użytkownika działa zestaw rośnie, ponieważ program używa odbicia drogich zasobów.</span><span class="sxs-lookup"><span data-stu-id="892e3-106">A program's working set increases because the program is using resource-expensive reflection.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="892e3-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="892e3-107">Cause</span></span>  
 <span data-ttu-id="892e3-108">Operacje odbicia, obejmujące <xref:System.Reflection.MemberInfo> obiekty są traktowane jako zasób kosztowne, ponieważ będzie musi odczytać metadane, które są przechowywane na stronach zimnych i ogólnie rzecz biorąc wskazują program używa jakiegoś rodzaju scenariusza z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="892e3-108">Reflection operations that involve <xref:System.Reflection.MemberInfo> objects are considered resource expensive because they must read metadata that is stored in cold pages and in general they indicate the program is using some type of late-bound scenario.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="892e3-109">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="892e3-109">Resolution</span></span>  
 <span data-ttu-id="892e3-110">Można określić, gdy odbicie jest używany w programie przez włączenie to zdarzenie MDA i ponownie uruchomić usługi kodu w debugerze lub dołączania za pomocą debugera, gdy zdarzenie MDA jest aktywowane.</span><span class="sxs-lookup"><span data-stu-id="892e3-110">You can determine where reflection is being used in your program by enabling this MDA and then running your code in a debugger or attaching with a debugger when the MDA is activated.</span></span> <span data-ttu-id="892e3-111">W debugerze, zostanie wyświetlony ślad stosu, przedstawiający miejsce <xref:System.Reflection.MemberInfo> pamięci podręcznej został utworzony, a w tym miejscu możesz określić, gdzie program używa odbicia.</span><span class="sxs-lookup"><span data-stu-id="892e3-111">Under a debugger you will get a stack trace showing where the <xref:System.Reflection.MemberInfo> cache was created and from there you can determine where your program is using reflection.</span></span>  
  
 <span data-ttu-id="892e3-112">Rozwiązanie jest zależna od celów kodu.</span><span class="sxs-lookup"><span data-stu-id="892e3-112">The resolution is dependent on the objectives of the code.</span></span> <span data-ttu-id="892e3-113">To zdarzenie MDA alertów, czy program ma scenariusza z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="892e3-113">This MDA alerts you that your program has a late-bound scenario.</span></span> <span data-ttu-id="892e3-114">Możesz chcieć ustalenia, czy należy zastąpić scenariusza z wczesnym wiązaniem lub należy wziąć pod uwagę wydajność pod koniec scenariusza związanego.</span><span class="sxs-lookup"><span data-stu-id="892e3-114">You might want to determine if you can substitute an early-bound scenario or consider the performance of the late bound scenario.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="892e3-115">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="892e3-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="892e3-116">To zdarzenie MDA jest aktywowane dla każdego <xref:System.Reflection.MemberInfo> pamięci podręcznej, który jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="892e3-116">This MDA is activated for every <xref:System.Reflection.MemberInfo> cache that is created.</span></span> <span data-ttu-id="892e3-117">Wpływ na wydajność jest niewielki.</span><span class="sxs-lookup"><span data-stu-id="892e3-117">The performance impact is negligible.</span></span>  
  
## <a name="output"></a><span data-ttu-id="892e3-118">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="892e3-118">Output</span></span>  
 <span data-ttu-id="892e3-119">MDA wyświetla komunikat informujący o <xref:System.Reflection.MemberInfo> pamięć podręczna została utworzona.</span><span class="sxs-lookup"><span data-stu-id="892e3-119">The MDA outputs a message indicating the <xref:System.Reflection.MemberInfo> cache was created.</span></span> <span data-ttu-id="892e3-120">Należy użyć debugera, aby uzyskać ślad stosu przedstawiający, gdzie program używa odbicia.</span><span class="sxs-lookup"><span data-stu-id="892e3-120">Use a debugger to get a stack trace showing where your program is using reflection.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="892e3-121">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="892e3-121">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="892e3-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="892e3-122">Example</span></span>  
 <span data-ttu-id="892e3-123">Ten przykładowy kod będą aktywowane `memberInfoCacheCreation` MDA.</span><span class="sxs-lookup"><span data-stu-id="892e3-123">This sample code will activate the `memberInfoCacheCreation` MDA.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="892e3-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="892e3-124">See also</span></span>

- <xref:System.Reflection.MemberInfo>
- [<span data-ttu-id="892e3-125">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="892e3-125">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
