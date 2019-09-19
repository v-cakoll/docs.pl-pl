---
title: dllMainReturnsFalse MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
author: mairaw
ms.author: mairaw
ms.openlocfilehash: adc05ae9bd357c142ff09de069aff446b5ea60e8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052855"
---
# <a name="dllmainreturnsfalse-mda"></a><span data-ttu-id="08d5c-102">dllMainReturnsFalse MDA</span><span class="sxs-lookup"><span data-stu-id="08d5c-102">dllMainReturnsFalse MDA</span></span>
<span data-ttu-id="08d5c-103">Asystent debugowania `DllMain` zarządzanego (MDA) jest aktywowany, jeśli zarządzana funkcja zestawu użytkownika wywołana z przyczyną DLL_PROCESS_ATTACH zwraca wartość false. `dllMainReturnsFalse`</span><span class="sxs-lookup"><span data-stu-id="08d5c-103">The `dllMainReturnsFalse` managed debugging assistant (MDA) is activated if the managed `DllMain` function of a user assembly, called with reason DLL_PROCESS_ATTACH, returns FALSE.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="08d5c-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="08d5c-104">Symptoms</span></span>  
 <span data-ttu-id="08d5c-105">`DllMain` Funkcja zwróciła wartość false, co oznacza, że nie została wykonana prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="08d5c-105">The `DllMain` function returned FALSE, indicating that it did not execute properly.</span></span> <span data-ttu-id="08d5c-106">Może to spowodować nieokreślone problemy, ponieważ `DllMain` funkcje zwykle zawierają ważny kod inicjujący.</span><span class="sxs-lookup"><span data-stu-id="08d5c-106">This can cause undetermined issues because `DllMain` functions typically contain important initialization code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="08d5c-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="08d5c-107">Cause</span></span>  
 <span data-ttu-id="08d5c-108">`DllMain` Funkcja jest wywoływana z przyczyną DLL_PROCESS_ATTACH dla inicjalizacji biblioteki DLL po załadowaniu.</span><span class="sxs-lookup"><span data-stu-id="08d5c-108">The `DllMain` function is called with reason DLL_PROCESS_ATTACH for DLL initialization upon load.</span></span> <span data-ttu-id="08d5c-109">Jeśli zwraca wartość FALSE, oznacza to, że inicjowanie biblioteki DLL nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="08d5c-109">If it returns FALSE, it means that DLL initialization failed.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="08d5c-110">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="08d5c-110">Resolution</span></span>  
 <span data-ttu-id="08d5c-111">Analizuj kod `DllMain` funkcji nieudanej biblioteki DLL i zidentyfikuj przyczynę niepowodzenia inicjacji.</span><span class="sxs-lookup"><span data-stu-id="08d5c-111">Analyze the code of the `DllMain` function of the failed DLL and identify the cause of the initialization failure.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="08d5c-112">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="08d5c-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="08d5c-113">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="08d5c-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="08d5c-114">Raportuje tylko dane dotyczące wartości zwracanej dla `DllMain`.</span><span class="sxs-lookup"><span data-stu-id="08d5c-114">It only reports data about the return value for `DllMain`.</span></span>  
  
## <a name="output"></a><span data-ttu-id="08d5c-115">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="08d5c-115">Output</span></span>  
 <span data-ttu-id="08d5c-116">Komunikat informujący o tym `DllMain` , że funkcja wywołana dla przyczyny DLL_PROCESS_ATTACH zwraca wartość false.</span><span class="sxs-lookup"><span data-stu-id="08d5c-116">A message indicating that a `DllMain` function, called for reason DLL_PROCESS_ATTACH, returned FALSE.</span></span> <span data-ttu-id="08d5c-117">Należy zauważyć, że to MDA jest uaktywniane tylko wtedy, gdy `DllMain` jest zaimplementowany w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="08d5c-117">Note that this MDA is activated only if `DllMain` is implemented in managed code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="08d5c-118">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="08d5c-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="08d5c-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="08d5c-119">See also</span></span>

- [<span data-ttu-id="08d5c-120">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="08d5c-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
