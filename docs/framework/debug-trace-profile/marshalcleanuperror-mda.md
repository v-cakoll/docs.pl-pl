---
title: marshalCleanupError MDA
description: Przejrzyj marshalCleanupError Managed Debug Assistant (MDA), który jest wywoływany ze względu na to, że wystąpił nieoczekiwany błąd podczas czyszczenia struktur tymczasowych.
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
ms.openlocfilehash: 3c7498d6f51484de3a2e84d611a2634f53724ab6
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051614"
---
# <a name="marshalcleanuperror-mda"></a><span data-ttu-id="7a77b-103">marshalCleanupError MDA</span><span class="sxs-lookup"><span data-stu-id="7a77b-103">marshalCleanupError MDA</span></span>
<span data-ttu-id="7a77b-104">`marshalCleanupError`Asystent debugowania zarządzanego (MDA) jest uaktywniany, gdy środowisko uruchomieniowe języka wspólnego (CLR) napotka błąd podczas próby oczyszczenia tymczasowych struktur i pamięci używanej do organizowania typów danych między natywnymi i zarządzanymi granicami kodu.</span><span class="sxs-lookup"><span data-stu-id="7a77b-104">The `marshalCleanupError` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters an error while attempting to clean up temporary structures and memory used for marshaling data types between native and managed code boundaries.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7a77b-105">Objawy</span><span class="sxs-lookup"><span data-stu-id="7a77b-105">Symptoms</span></span>  
 <span data-ttu-id="7a77b-106">Przeciek pamięci występuje podczas wykonywania natywnych i zarządzanych przejść do kodu, stan środowiska uruchomieniowego, taki jak kultura wątku nie jest przywracany lub błędy pojawiają się w wyniku <xref:System.Runtime.InteropServices.SafeHandle> czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="7a77b-106">A memory leak occurs when making native and managed code transitions, runtime state such as thread culture is not restored, or errors occur in <xref:System.Runtime.InteropServices.SafeHandle> cleanup.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7a77b-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="7a77b-107">Cause</span></span>  
 <span data-ttu-id="7a77b-108">Wystąpił nieoczekiwany błąd podczas czyszczenia struktur tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="7a77b-108">An unexpected error occurred while cleaning up temporary structures.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7a77b-109">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="7a77b-109">Resolution</span></span>  
 <span data-ttu-id="7a77b-110">Przejrzyj wszystkie <xref:System.Runtime.InteropServices.SafeHandle> implementacje destruktora, finalizatora i niestandardowego organizatora pod kątem błędów.</span><span class="sxs-lookup"><span data-stu-id="7a77b-110">Review all <xref:System.Runtime.InteropServices.SafeHandle> destructor, finalizer, and custom marshaler implementations for errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7a77b-111">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="7a77b-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="7a77b-112">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="7a77b-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7a77b-113">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="7a77b-113">Output</span></span>  
 <span data-ttu-id="7a77b-114">Komunikat zgłaszający operację, która nie powiodła się podczas czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="7a77b-114">A message reporting the operation that failed during cleanup.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="7a77b-115">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="7a77b-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a77b-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a77b-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="7a77b-117">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="7a77b-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="7a77b-118">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="7a77b-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
