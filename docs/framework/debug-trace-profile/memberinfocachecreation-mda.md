---
title: memberInfoCacheCreation MDA
description: Informacje o programie memberInfoCacheCreation Managed Debug Assistant (MDA) w programie .NET, który jest uaktywniany podczas tworzenia pamięci podręcznej MemberInfo.
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
ms.openlocfilehash: c48be7ac8632b8072981be01e01997ee8c34b6b3
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051145"
---
# <a name="memberinfocachecreation-mda"></a><span data-ttu-id="4ec32-103">memberInfoCacheCreation MDA</span><span class="sxs-lookup"><span data-stu-id="4ec32-103">memberInfoCacheCreation MDA</span></span>
<span data-ttu-id="4ec32-104">`memberInfoCacheCreation`Asystent debugowania zarządzanego (MDA) jest uaktywniany po <xref:System.Reflection.MemberInfo> utworzeniu pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="4ec32-104">The `memberInfoCacheCreation` managed debugging assistant (MDA) is activated when a <xref:System.Reflection.MemberInfo> cache is created.</span></span> <span data-ttu-id="4ec32-105">Jest to mocne wskazanie programu, który korzysta z funkcji odbicia kosztownych zasobów.</span><span class="sxs-lookup"><span data-stu-id="4ec32-105">This is a strong indication of a program that is making use of resource-expensive reflection features.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="4ec32-106">Objawy</span><span class="sxs-lookup"><span data-stu-id="4ec32-106">Symptoms</span></span>  
 <span data-ttu-id="4ec32-107">Zestaw roboczy programu zostaje zwiększony, ponieważ program korzysta z bardziej kosztownego odbicia zasobów.</span><span class="sxs-lookup"><span data-stu-id="4ec32-107">A program's working set increases because the program is using resource-expensive reflection.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="4ec32-108">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="4ec32-108">Cause</span></span>  
 <span data-ttu-id="4ec32-109">Operacje odbicia obejmujące <xref:System.Reflection.MemberInfo> obiekty są uznawane za kosztowne, ponieważ muszą odczytywać metadane przechowywane na zimnych stronach i ogólnie wskazują, że program używa pewnego typu scenariusza z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="4ec32-109">Reflection operations that involve <xref:System.Reflection.MemberInfo> objects are considered resource expensive because they must read metadata that is stored in cold pages and in general they indicate the program is using some type of late-bound scenario.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="4ec32-110">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="4ec32-110">Resolution</span></span>  
 <span data-ttu-id="4ec32-111">Możesz określić, gdzie odbicie jest używane w programie, włączając ten MDA, a następnie uruchamiając kod w debugerze lub dołączając debuger, gdy zostanie uaktywnione zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="4ec32-111">You can determine where reflection is being used in your program by enabling this MDA and then running your code in a debugger or attaching with a debugger when the MDA is activated.</span></span> <span data-ttu-id="4ec32-112">W ramach debugera uzyskasz śledzenie stosu pokazujące miejsce <xref:System.Reflection.MemberInfo> utworzenia pamięci podręcznej, a następnie można określić, gdzie program używa odbicia.</span><span class="sxs-lookup"><span data-stu-id="4ec32-112">Under a debugger you will get a stack trace showing where the <xref:System.Reflection.MemberInfo> cache was created and from there you can determine where your program is using reflection.</span></span>  
  
 <span data-ttu-id="4ec32-113">Rozwiązanie zależy od celów kodu.</span><span class="sxs-lookup"><span data-stu-id="4ec32-113">The resolution is dependent on the objectives of the code.</span></span> <span data-ttu-id="4ec32-114">To zdarzenie MDA ostrzega o tym, że program ma scenariusz z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="4ec32-114">This MDA alerts you that your program has a late-bound scenario.</span></span> <span data-ttu-id="4ec32-115">Warto określić, czy można zastąpić scenariusz wczesny, czy też wziąć pod uwagę wydajność scenariusza z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="4ec32-115">You might want to determine if you can substitute an early-bound scenario or consider the performance of the late bound scenario.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="4ec32-116">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="4ec32-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="4ec32-117">To zdarzenie MDA jest aktywowane dla każdej <xref:System.Reflection.MemberInfo> tworzonej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="4ec32-117">This MDA is activated for every <xref:System.Reflection.MemberInfo> cache that is created.</span></span> <span data-ttu-id="4ec32-118">Wpływ na wydajność jest nieznaczny.</span><span class="sxs-lookup"><span data-stu-id="4ec32-118">The performance impact is negligible.</span></span>  
  
## <a name="output"></a><span data-ttu-id="4ec32-119">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="4ec32-119">Output</span></span>  
 <span data-ttu-id="4ec32-120">Po utworzeniu pamięci podręcznej MDA zostanie wyświetlony komunikat wskazujący, że <xref:System.Reflection.MemberInfo> została utworzona.</span><span class="sxs-lookup"><span data-stu-id="4ec32-120">The MDA outputs a message indicating the <xref:System.Reflection.MemberInfo> cache was created.</span></span> <span data-ttu-id="4ec32-121">Użyj debugera, aby uzyskać ślad stosu pokazujący, gdzie program używa odbicia.</span><span class="sxs-lookup"><span data-stu-id="4ec32-121">Use a debugger to get a stack trace showing where your program is using reflection.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="4ec32-122">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="4ec32-122">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="4ec32-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ec32-123">Example</span></span>  
 <span data-ttu-id="4ec32-124">Ten przykładowy kod spowoduje aktywowanie `memberInfoCacheCreation` MDA.</span><span class="sxs-lookup"><span data-stu-id="4ec32-124">This sample code will activate the `memberInfoCacheCreation` MDA.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4ec32-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ec32-125">See also</span></span>

- <xref:System.Reflection.MemberInfo>
- [<span data-ttu-id="4ec32-126">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="4ec32-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
