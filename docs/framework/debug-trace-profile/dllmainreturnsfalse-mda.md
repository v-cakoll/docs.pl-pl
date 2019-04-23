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
ms.openlocfilehash: fd987cea78d082eee26032d5f98a54dc0cd3e1d5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072626"
---
# <a name="dllmainreturnsfalse-mda"></a><span data-ttu-id="bcafd-102">dllMainReturnsFalse MDA</span><span class="sxs-lookup"><span data-stu-id="bcafd-102">dllMainReturnsFalse MDA</span></span>
<span data-ttu-id="bcafd-103">`dllMainReturnsFalse` Zarządzanego Asystenta debugowania (MDA) jest włączone, jeśli zarządzanej `DllMain` funkcja zestawu użytkownika o nazwie z powodu DLL_PROCESS_ATTACH, zwraca wartość FALSE.</span><span class="sxs-lookup"><span data-stu-id="bcafd-103">The `dllMainReturnsFalse` managed debugging assistant (MDA) is activated if the managed `DllMain` function of a user assembly, called with reason DLL_PROCESS_ATTACH, returns FALSE.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="bcafd-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="bcafd-104">Symptoms</span></span>  
 <span data-ttu-id="bcafd-105">`DllMain` Funkcja zwróciła wartość FALSE, wskazujący, że jej nie zostało wykonane prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="bcafd-105">The `DllMain` function returned FALSE, indicating that it did not execute properly.</span></span> <span data-ttu-id="bcafd-106">Może to spowodować problemy z nieokreślonej, ponieważ `DllMain` funkcje zwykle zawierają kod inicjujący ważne.</span><span class="sxs-lookup"><span data-stu-id="bcafd-106">This can cause undetermined issues because `DllMain` functions typically contain important initialization code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="bcafd-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="bcafd-107">Cause</span></span>  
 <span data-ttu-id="bcafd-108">`DllMain` Funkcja jest wywoływana z przyczyną DLL_PROCESS_ATTACH Inicjowanie biblioteki DLL, podczas ładowania.</span><span class="sxs-lookup"><span data-stu-id="bcafd-108">The `DllMain` function is called with reason DLL_PROCESS_ATTACH for DLL initialization upon load.</span></span> <span data-ttu-id="bcafd-109">Jeśli zostanie zwrócona wartość FALSE, oznacza to, że inicjowanie biblioteki DLL nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="bcafd-109">If it returns FALSE, it means that DLL initialization failed.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="bcafd-110">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="bcafd-110">Resolution</span></span>  
 <span data-ttu-id="bcafd-111">Analizowanie kodu `DllMain` funkcji DLL nie powiodło się i zidentyfikować przyczynę niepowodzenia inicjowania.</span><span class="sxs-lookup"><span data-stu-id="bcafd-111">Analyze the code of the `DllMain` function of the failed DLL and identify the cause of the initialization failure.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="bcafd-112">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="bcafd-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="bcafd-113">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="bcafd-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="bcafd-114">Informuje jedynie dane o wartości zwracanej przez `DllMain`.</span><span class="sxs-lookup"><span data-stu-id="bcafd-114">It only reports data about the return value for `DllMain`.</span></span>  
  
## <a name="output"></a><span data-ttu-id="bcafd-115">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="bcafd-115">Output</span></span>  
 <span data-ttu-id="bcafd-116">Komunikat wskazujący, że `DllMain` funkcja, o nazwie powodu DLL_PROCESS_ATTACH, zwróciła wartość FALSE.</span><span class="sxs-lookup"><span data-stu-id="bcafd-116">A message indicating that a `DllMain` function, called for reason DLL_PROCESS_ATTACH, returned FALSE.</span></span> <span data-ttu-id="bcafd-117">Należy pamiętać, że to zdarzenie MDA jest aktywowane tylko wtedy, gdy `DllMain` zaimplementowano w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="bcafd-117">Note that this MDA is activated only if `DllMain` is implemented in managed code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="bcafd-118">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="bcafd-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bcafd-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bcafd-119">See also</span></span>

- [<span data-ttu-id="bcafd-120">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="bcafd-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
