---
title: marshalCleanupError MDA
ms.date: 03/30/2017
helpviewer_keywords:
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
ms.openlocfilehash: 1a14c548ce960d53f47934595171189db28edfbb
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216153"
---
# <a name="marshalcleanuperror-mda"></a><span data-ttu-id="c7490-102">marshalCleanupError MDA</span><span class="sxs-lookup"><span data-stu-id="c7490-102">marshalCleanupError MDA</span></span>
<span data-ttu-id="c7490-103">Asystent debugowania zarządzanego `marshalCleanupError` (MDA) jest uaktywniany, gdy środowisko uruchomieniowe języka wspólnego (CLR) napotka błąd podczas próby oczyszczenia tymczasowych struktur i pamięci używanej do organizowania typów danych między natywną i zarządzaną granicami kodu.</span><span class="sxs-lookup"><span data-stu-id="c7490-103">The `marshalCleanupError` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters an error while attempting to clean up temporary structures and memory used for marshaling data types between native and managed code boundaries.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c7490-104">Objawy</span><span class="sxs-lookup"><span data-stu-id="c7490-104">Symptoms</span></span>  
 <span data-ttu-id="c7490-105">Przeciek pamięci występuje podczas wykonywania natywnych i zarządzanych przejść do kodu, stan środowiska uruchomieniowego, taki jak kultura wątku nie jest przywracany lub błędy występujące w <xref:System.Runtime.InteropServices.SafeHandle> oczyszczanie.</span><span class="sxs-lookup"><span data-stu-id="c7490-105">A memory leak occurs when making native and managed code transitions, runtime state such as thread culture is not restored, or errors occur in <xref:System.Runtime.InteropServices.SafeHandle> cleanup.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c7490-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="c7490-106">Cause</span></span>  
 <span data-ttu-id="c7490-107">Wystąpił nieoczekiwany błąd podczas czyszczenia struktur tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="c7490-107">An unexpected error occurred while cleaning up temporary structures.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c7490-108">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="c7490-108">Resolution</span></span>  
 <span data-ttu-id="c7490-109">Przejrzyj wszystkie za<xref:System.Runtime.InteropServices.SafeHandle> destruktory, finalizatory i niestandardowe implementacje organizatora pod kątem błędów.</span><span class="sxs-lookup"><span data-stu-id="c7490-109">Review all <xref:System.Runtime.InteropServices.SafeHandle> destructor, finalizer, and custom marshaler implementations for errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c7490-110">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="c7490-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="c7490-111">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="c7490-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c7490-112">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="c7490-112">Output</span></span>  
 <span data-ttu-id="c7490-113">Komunikat zgłaszający operację, która nie powiodła się podczas czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="c7490-113">A message reporting the operation that failed during cleanup.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c7490-114">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="c7490-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7490-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7490-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="c7490-116">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="c7490-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c7490-117">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="c7490-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
