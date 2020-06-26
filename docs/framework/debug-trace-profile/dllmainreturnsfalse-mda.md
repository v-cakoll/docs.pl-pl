---
title: dllMainReturnsFalse MDA
description: Przeczytaj o Asystencie debugowania zarządzanego przez program dllMainReturnsFalse w programie .NET. To zdarzenie MDA zostanie aktywowane w przypadku niepowodzenia inicjacji biblioteki DLL.
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
ms.openlocfilehash: 21d5e37d6823876e07cf5b2cbb881c1cf8b47b11
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416060"
---
# <a name="dllmainreturnsfalse-mda"></a><span data-ttu-id="ef642-104">dllMainReturnsFalse MDA</span><span class="sxs-lookup"><span data-stu-id="ef642-104">dllMainReturnsFalse MDA</span></span>
<span data-ttu-id="ef642-105">`dllMainReturnsFalse`Asystent debugowania zarządzanego (MDA) jest aktywowany, jeśli zarządzana `DllMain` Funkcja zestawu użytkownika wywołana z powodu DLL_PROCESS_ATTACH, zwraca wartość false.</span><span class="sxs-lookup"><span data-stu-id="ef642-105">The `dllMainReturnsFalse` managed debugging assistant (MDA) is activated if the managed `DllMain` function of a user assembly, called with reason DLL_PROCESS_ATTACH, returns FALSE.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ef642-106">Objawy</span><span class="sxs-lookup"><span data-stu-id="ef642-106">Symptoms</span></span>  
 <span data-ttu-id="ef642-107">`DllMain`Funkcja zwróciła wartość false, co oznacza, że nie została wykonana prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="ef642-107">The `DllMain` function returned FALSE, indicating that it did not execute properly.</span></span> <span data-ttu-id="ef642-108">Może to spowodować nieokreślone problemy, ponieważ `DllMain` funkcje zwykle zawierają ważny kod inicjujący.</span><span class="sxs-lookup"><span data-stu-id="ef642-108">This can cause undetermined issues because `DllMain` functions typically contain important initialization code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ef642-109">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="ef642-109">Cause</span></span>  
 <span data-ttu-id="ef642-110">`DllMain`Funkcja jest wywoływana z powodu DLL_PROCESS_ATTACH dla inicjalizacji biblioteki DLL po załadowaniu.</span><span class="sxs-lookup"><span data-stu-id="ef642-110">The `DllMain` function is called with reason DLL_PROCESS_ATTACH for DLL initialization upon load.</span></span> <span data-ttu-id="ef642-111">Jeśli zwraca wartość FALSE, oznacza to, że inicjowanie biblioteki DLL nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="ef642-111">If it returns FALSE, it means that DLL initialization failed.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="ef642-112">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="ef642-112">Resolution</span></span>  
 <span data-ttu-id="ef642-113">Analizuj kod `DllMain` funkcji nieudanej biblioteki DLL i zidentyfikuj przyczynę niepowodzenia inicjacji.</span><span class="sxs-lookup"><span data-stu-id="ef642-113">Analyze the code of the `DllMain` function of the failed DLL and identify the cause of the initialization failure.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ef642-114">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="ef642-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="ef642-115">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="ef642-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="ef642-116">Raportuje tylko dane dotyczące wartości zwracanej dla `DllMain` .</span><span class="sxs-lookup"><span data-stu-id="ef642-116">It only reports data about the return value for `DllMain`.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ef642-117">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="ef642-117">Output</span></span>  
 <span data-ttu-id="ef642-118">Komunikat informujący o tym `DllMain` , że funkcja wywołana dla przyczyny DLL_PROCESS_ATTACH zwraca wartość false.</span><span class="sxs-lookup"><span data-stu-id="ef642-118">A message indicating that a `DllMain` function, called for reason DLL_PROCESS_ATTACH, returned FALSE.</span></span> <span data-ttu-id="ef642-119">Należy zauważyć, że to MDA jest uaktywniane tylko wtedy, gdy `DllMain` jest zaimplementowany w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="ef642-119">Note that this MDA is activated only if `DllMain` is implemented in managed code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="ef642-120">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ef642-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef642-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef642-121">See also</span></span>

- [<span data-ttu-id="ef642-122">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="ef642-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
