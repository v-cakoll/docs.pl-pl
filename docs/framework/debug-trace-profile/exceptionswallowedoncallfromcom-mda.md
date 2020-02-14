---
title: exceptionSwallowedOnCallFromCom MDA
ms.date: 03/30/2017
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
ms.openlocfilehash: 4ccb03c9a8a473c10f15b00e64810b04f21504c9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217525"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="76c93-102">exceptionSwallowedOnCallFromCom MDA</span><span class="sxs-lookup"><span data-stu-id="76c93-102">exceptionSwallowedOnCallFromCom MDA</span></span>
<span data-ttu-id="76c93-103">Asystent debugowania zarządzanego `exceptionSwallowedOnCallFromCOM` (MDA) jest uaktywniany, gdy wyjątek jest zgłaszany z kodu środowiska uruchomieniowego języka wspólnego (CLR) wywoływanego z modelu COM za pomocą metody, która nie ma niezarządzanego typu zwracanego HRESULT.</span><span class="sxs-lookup"><span data-stu-id="76c93-103">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="76c93-104">Objawy</span><span class="sxs-lookup"><span data-stu-id="76c93-104">Symptoms</span></span>  
 <span data-ttu-id="76c93-105">Wywołanie zarządzanego składnika z modelu COM zwraca wartość FALSE lub 0.</span><span class="sxs-lookup"><span data-stu-id="76c93-105">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="76c93-106">Alternatywnie, jeśli metoda ma typ zwracany void, może nie być wskazywać, że wyjątek został zgłoszony podczas wykonywania metody.</span><span class="sxs-lookup"><span data-stu-id="76c93-106">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="76c93-107">W takim przypadku wyjątek zostanie przechwycony w trybie dyskretnym, a wykonywanie zwróci do obiektu wywołującego COM.</span><span class="sxs-lookup"><span data-stu-id="76c93-107">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="76c93-108">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="76c93-108">Cause</span></span>  
 <span data-ttu-id="76c93-109">Zgłoszono wyjątek, ale nie ma prawidłowego sposobu na jego raportowanie.</span><span class="sxs-lookup"><span data-stu-id="76c93-109">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="76c93-110">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="76c93-110">Resolution</span></span>  
 <span data-ttu-id="76c93-111">Tylko informacyjne, niekoniecznie wskazujące usterkę.</span><span class="sxs-lookup"><span data-stu-id="76c93-111">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="76c93-112">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="76c93-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="76c93-113">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="76c93-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="76c93-114">Raport dotyczy tylko danych o przechwyconych dyskretnie wyjątkach.</span><span class="sxs-lookup"><span data-stu-id="76c93-114">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="76c93-115">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="76c93-115">Output</span></span>  
 <span data-ttu-id="76c93-116">Komunikat informacyjny zawierający nazwę metody, nazwę typu i komunikat o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="76c93-116">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="76c93-117">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="76c93-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="76c93-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76c93-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="76c93-119">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="76c93-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="76c93-120">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="76c93-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
