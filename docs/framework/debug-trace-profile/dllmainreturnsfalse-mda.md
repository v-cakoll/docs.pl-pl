---
title: dllMainReturnsFalse MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
ms.openlocfilehash: 0b413521e0a2dc06c2ff0be642f080eaf541202f
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216443"
---
# <a name="dllmainreturnsfalse-mda"></a><span data-ttu-id="a3932-102">dllMainReturnsFalse MDA</span><span class="sxs-lookup"><span data-stu-id="a3932-102">dllMainReturnsFalse MDA</span></span>
<span data-ttu-id="a3932-103">Asystent debugowania zarządzanego `dllMainReturnsFalse` (MDA) jest aktywowany, jeśli funkcja zarządzane `DllMain` zestawu użytkownika wywołana z przyczyną DLL_PROCESS_ATTACH zwraca wartość FALSE.</span><span class="sxs-lookup"><span data-stu-id="a3932-103">The `dllMainReturnsFalse` managed debugging assistant (MDA) is activated if the managed `DllMain` function of a user assembly, called with reason DLL_PROCESS_ATTACH, returns FALSE.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a3932-104">Objawy</span><span class="sxs-lookup"><span data-stu-id="a3932-104">Symptoms</span></span>  
 <span data-ttu-id="a3932-105">Funkcja `DllMain` zwróciła wartość FALSE, co oznacza, że nie została wykonana prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="a3932-105">The `DllMain` function returned FALSE, indicating that it did not execute properly.</span></span> <span data-ttu-id="a3932-106">Może to spowodować nieokreślone problemy, ponieważ funkcje `DllMain` zwykle zawierają ważny kod inicjujący.</span><span class="sxs-lookup"><span data-stu-id="a3932-106">This can cause undetermined issues because `DllMain` functions typically contain important initialization code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a3932-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="a3932-107">Cause</span></span>  
 <span data-ttu-id="a3932-108">Funkcja `DllMain` jest wywoływana z powodu DLL_PROCESS_ATTACH do inicjowania biblioteki DLL po załadowaniu.</span><span class="sxs-lookup"><span data-stu-id="a3932-108">The `DllMain` function is called with reason DLL_PROCESS_ATTACH for DLL initialization upon load.</span></span> <span data-ttu-id="a3932-109">Jeśli zwraca wartość FALSE, oznacza to, że inicjowanie biblioteki DLL nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="a3932-109">If it returns FALSE, it means that DLL initialization failed.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a3932-110">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="a3932-110">Resolution</span></span>  
 <span data-ttu-id="a3932-111">Analizuj kod funkcji `DllMain` nieudanej biblioteki DLL i zidentyfikuj przyczynę niepowodzenia inicjacji.</span><span class="sxs-lookup"><span data-stu-id="a3932-111">Analyze the code of the `DllMain` function of the failed DLL and identify the cause of the initialization failure.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a3932-112">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="a3932-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="a3932-113">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="a3932-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="a3932-114">Raportuje tylko dane dotyczące wartości zwracanej dla `DllMain`.</span><span class="sxs-lookup"><span data-stu-id="a3932-114">It only reports data about the return value for `DllMain`.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a3932-115">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="a3932-115">Output</span></span>  
 <span data-ttu-id="a3932-116">Komunikat wskazujący, że funkcja `DllMain` wywołana dla przyczyny DLL_PROCESS_ATTACH, zwróciła wartość FALSE.</span><span class="sxs-lookup"><span data-stu-id="a3932-116">A message indicating that a `DllMain` function, called for reason DLL_PROCESS_ATTACH, returned FALSE.</span></span> <span data-ttu-id="a3932-117">Należy pamiętać, że to MDA jest uaktywniane tylko wtedy, gdy `DllMain` jest zaimplementowana w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="a3932-117">Note that this MDA is activated only if `DllMain` is implemented in managed code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a3932-118">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="a3932-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3932-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3932-119">See also</span></span>

- [<span data-ttu-id="a3932-120">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="a3932-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
