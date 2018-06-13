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
ms.openlocfilehash: 4987b025450f2207a01a472a0c39fc6da2de0782
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386496"
---
# <a name="dllmainreturnsfalse-mda"></a><span data-ttu-id="51c3a-102">dllMainReturnsFalse MDA</span><span class="sxs-lookup"><span data-stu-id="51c3a-102">dllMainReturnsFalse MDA</span></span>
<span data-ttu-id="51c3a-103">`dllMainReturnsFalse` Zarządzany Asystent debugowania (MDA) jest włączone, jeśli zarządzanej `DllMain` funkcja zestawu użytkownika, wywołana z przyczyny DLL_PROCESS_ATTACH, zwraca wartość FALSE.</span><span class="sxs-lookup"><span data-stu-id="51c3a-103">The `dllMainReturnsFalse` managed debugging assistant (MDA) is activated if the managed `DllMain` function of a user assembly, called with reason DLL_PROCESS_ATTACH, returns FALSE.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="51c3a-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="51c3a-104">Symptoms</span></span>  
 <span data-ttu-id="51c3a-105">`DllMain` Funkcja zwróciła wartość FALSE, wskazujący, że jej nie zostało wykonane prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="51c3a-105">The `DllMain` function returned FALSE, indicating that it did not execute properly.</span></span> <span data-ttu-id="51c3a-106">Ponieważ mogą powodować problemy nieokreślonej `DllMain` funkcje zwykle zawierają kod inicjujący ważne.</span><span class="sxs-lookup"><span data-stu-id="51c3a-106">This can cause undetermined issues because `DllMain` functions typically contain important initialization code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="51c3a-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="51c3a-107">Cause</span></span>  
 <span data-ttu-id="51c3a-108">`DllMain` Eval jest wywołana z przyczyny DLL_PROCESS_ATTACH inicjowania biblioteki DLL od obciążenia.</span><span class="sxs-lookup"><span data-stu-id="51c3a-108">The `DllMain` function is called with reason DLL_PROCESS_ATTACH for DLL initialization upon load.</span></span> <span data-ttu-id="51c3a-109">Jeśli zwraca wartość FALSE, oznacza to, że nie można zainicjować biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="51c3a-109">If it returns FALSE, it means that DLL initialization failed.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="51c3a-110">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="51c3a-110">Resolution</span></span>  
 <span data-ttu-id="51c3a-111">Analizowanie kodu `DllMain` funkcji DLL nie powiodło się i zidentyfikować przyczynę niepowodzenia inicjowania.</span><span class="sxs-lookup"><span data-stu-id="51c3a-111">Analyze the code of the `DllMain` function of the failed DLL and identify the cause of the initialization failure.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="51c3a-112">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="51c3a-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="51c3a-113">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="51c3a-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="51c3a-114">Tylko raporty danych o wartości zwracanej przez `DllMain`.</span><span class="sxs-lookup"><span data-stu-id="51c3a-114">It only reports data about the return value for `DllMain`.</span></span>  
  
## <a name="output"></a><span data-ttu-id="51c3a-115">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="51c3a-115">Output</span></span>  
 <span data-ttu-id="51c3a-116">Komunikat wskazujący, że `DllMain` funkcji o nazwie przyczyny DLL_PROCESS_ATTACH, zwróciła wartość FALSE.</span><span class="sxs-lookup"><span data-stu-id="51c3a-116">A message indicating that a `DllMain` function, called for reason DLL_PROCESS_ATTACH, returned FALSE.</span></span> <span data-ttu-id="51c3a-117">Należy pamiętać, że to zdarzenie MDA jest włączona tylko wtedy, gdy `DllMain` zaimplementowano w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="51c3a-117">Note that this MDA is activated only if `DllMain` is implemented in managed code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="51c3a-118">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="51c3a-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="51c3a-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51c3a-119">See Also</span></span>  
 [<span data-ttu-id="51c3a-120">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="51c3a-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
