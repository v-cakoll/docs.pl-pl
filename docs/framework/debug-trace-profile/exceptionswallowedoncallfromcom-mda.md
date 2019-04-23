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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4f076cbc556c7d9feff8a226f050743cd7728622
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148151"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="a9533-102">exceptionSwallowedOnCallFromCom MDA</span><span class="sxs-lookup"><span data-stu-id="a9533-102">exceptionSwallowedOnCallFromCom MDA</span></span>
<span data-ttu-id="a9533-103">`exceptionSwallowedOnCallFromCOM` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy wyjątek jest generowany z wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) kodu wywoływane z modelu COM za pomocą metody, która nie ma wartość HRESULT niezarządzany typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="a9533-103">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a9533-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="a9533-104">Symptoms</span></span>  
 <span data-ttu-id="a9533-105">Wywołanie zarządzanego składnika z modelu COM zwraca wartość FALSE lub 0.</span><span class="sxs-lookup"><span data-stu-id="a9533-105">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="a9533-106">Alternatywnie Jeśli metoda ma zwracać typ void, może istnieć żadnego wskazania, że wystąpił wyjątek podczas wykonywania metody.</span><span class="sxs-lookup"><span data-stu-id="a9533-106">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="a9533-107">W tym przypadku wyjątek zostanie zgłoszony dyskretnie i wykonanie nastąpi powrót do obiektu wywołującego COM.</span><span class="sxs-lookup"><span data-stu-id="a9533-107">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a9533-108">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="a9533-108">Cause</span></span>  
 <span data-ttu-id="a9533-109">Wystąpił wyjątek, ale nie istnieje prawidłowy sposób Zgłoś ją.</span><span class="sxs-lookup"><span data-stu-id="a9533-109">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a9533-110">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="a9533-110">Resolution</span></span>  
 <span data-ttu-id="a9533-111">Komunikat o charakterze informacyjnym tylko, nie zawsze wskazuje usterkę.</span><span class="sxs-lookup"><span data-stu-id="a9533-111">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a9533-112">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="a9533-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="a9533-113">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="a9533-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="a9533-114">Informuje jedynie dane o dyskretnie przechwycone wyjątki.</span><span class="sxs-lookup"><span data-stu-id="a9533-114">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a9533-115">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="a9533-115">Output</span></span>  
 <span data-ttu-id="a9533-116">Komunikat informacyjny, zawierające nazwę metody, wpisz nazwę i komunikat o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a9533-116">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a9533-117">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="a9533-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a9533-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9533-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="a9533-119">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="a9533-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="a9533-120">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="a9533-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
