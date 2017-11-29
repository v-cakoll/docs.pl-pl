---
title: memberInfoCacheCreation MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member info cache creation
- MemberInfoCacheCreation MDA
- reflection, run-time errors
- MDAs (managed debugging assistants), cache
- cache [.NET Framework], reflection
- managed debugging assistants (MDAs), cache
- MemberInfo cache
ms.assetid: 5abdad23-1335-4744-8acb-934002c0b6fe
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1aeda59172e52c9880b39d6bf94ea9685a0203c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="memberinfocachecreation-mda"></a><span data-ttu-id="3f5b1-102">memberInfoCacheCreation MDA</span><span class="sxs-lookup"><span data-stu-id="3f5b1-102">memberInfoCacheCreation MDA</span></span>
<span data-ttu-id="3f5b1-103">`memberInfoCacheCreation` Zarządzany Asystent debugowania (MDA) została aktywowana po <xref:System.Reflection.MemberInfo> pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-103">The `memberInfoCacheCreation` managed debugging assistant (MDA) is activated when a <xref:System.Reflection.MemberInfo> cache is created.</span></span> <span data-ttu-id="3f5b1-104">To silne wskazanie program, który jest użycie funkcji odbicia zasobów.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-104">This is a strong indication of a program that is making use of resource-expensive reflection features.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="3f5b1-105">Symptomy</span><span class="sxs-lookup"><span data-stu-id="3f5b1-105">Symptoms</span></span>  
 <span data-ttu-id="3f5b1-106">Program roboczy zwiększa zestawu, ponieważ program jest za pomocą odbicia zasobów.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-106">A program's working set increases because the program is using resource-expensive reflection.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="3f5b1-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="3f5b1-107">Cause</span></span>  
 <span data-ttu-id="3f5b1-108">Operacje odbicia, które obejmują <xref:System.Reflection.MemberInfo> obiekty są traktowane jako zasób kosztowne, ponieważ muszą one odczytu metadanych, które są przechowywane na stronach zimnych i ogólnie wskazują one program używa pewien typ scenariusza z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-108">Reflection operations that involve <xref:System.Reflection.MemberInfo> objects are considered resource expensive because they must read metadata that is stored in cold pages and in general they indicate the program is using some type of late-bound scenario.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="3f5b1-109">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="3f5b1-109">Resolution</span></span>  
 <span data-ttu-id="3f5b1-110">Można określić, gdzie odbicia jest używane w programie przez włączenie to zdarzenie MDA i ponownie uruchomić kodu w debugerze lub związane z debugera, po aktywowaniu MDA.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-110">You can determine where reflection is being used in your program by enabling this MDA and then running your code in a debugger or attaching with a debugger when the MDA is activated.</span></span> <span data-ttu-id="3f5b1-111">W debugerze otrzymasz ślad stosu przedstawiający miejsce <xref:System.Reflection.MemberInfo> pamięci podręcznej został utworzony i z tego miejsca można określić, których program jest za pomocą odbicia.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-111">Under a debugger you will get a stack trace showing where the <xref:System.Reflection.MemberInfo> cache was created and from there you can determine where your program is using reflection.</span></span>  
  
 <span data-ttu-id="3f5b1-112">Rozdzielczość jest zależny od celów kodu.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-112">The resolution is dependent on the objectives of the code.</span></span> <span data-ttu-id="3f5b1-113">To zdarzenie MDA alertów, czy program ma scenariusza z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-113">This MDA alerts you that your program has a late-bound scenario.</span></span> <span data-ttu-id="3f5b1-114">Można określić, czy można podstawić scenariusza z wczesnym wiązaniem też należy wziąć pod uwagę wydajności późne powiązania scenariusza.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-114">You might want to determine if you can substitute an early-bound scenario or consider the performance of the late bound scenario.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="3f5b1-115">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="3f5b1-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="3f5b1-116">To zdarzenie MDA został aktywowany dla każdego <xref:System.Reflection.MemberInfo> pamięci podręcznej, która jest tworzona.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-116">This MDA is activated for every <xref:System.Reflection.MemberInfo> cache that is created.</span></span> <span data-ttu-id="3f5b1-117">Wpływ na wydajność jest niewielka.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-117">The performance impact is negligible.</span></span>  
  
## <a name="output"></a><span data-ttu-id="3f5b1-118">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="3f5b1-118">Output</span></span>  
 <span data-ttu-id="3f5b1-119">MDA wyświetla komunikat informujący <xref:System.Reflection.MemberInfo> pamięci podręcznej został utworzony.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-119">The MDA outputs a message indicating the <xref:System.Reflection.MemberInfo> cache was created.</span></span> <span data-ttu-id="3f5b1-120">Użyj debugera, aby uzyskać ślad stosu wyświetlane, gdy program jest za pomocą odbicia.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-120">Use a debugger to get a stack trace showing where your program is using reflection.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="3f5b1-121">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="3f5b1-121">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="3f5b1-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="3f5b1-122">Example</span></span>  
 <span data-ttu-id="3f5b1-123">Ten przykładowy kod uaktywni `memberInfoCacheCreation` MDA.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-123">This sample code will activate the `memberInfoCacheCreation` MDA.</span></span>  
  
```  
using System;  
  
public class Exe  
{  
    public static void Main()  
    {  
        typeof(object).GetMethods();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f5b1-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3f5b1-124">See Also</span></span>  
 <xref:System.Reflection.MemberInfo>  
 [<span data-ttu-id="3f5b1-125">Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="3f5b1-125">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
