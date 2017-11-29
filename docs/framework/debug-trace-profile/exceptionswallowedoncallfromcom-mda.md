---
title: exceptionSwallowedOnCallFromCom MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d68e3f8659b0d5fe212c58443fe9a8b42f9cef89
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="be84c-102">exceptionSwallowedOnCallFromCom MDA</span><span class="sxs-lookup"><span data-stu-id="be84c-102">exceptionSwallowedOnCallFromCom MDA</span></span>
<span data-ttu-id="be84c-103">`exceptionSwallowedOnCallFromCOM` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy wyjątek z wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) kodu wywoływana z modelu COM za pomocą metody, która nie ma typu zwracanego HRESULT niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="be84c-103">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="be84c-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="be84c-104">Symptoms</span></span>  
 <span data-ttu-id="be84c-105">Zwraca wywołania do zarządzanego składnika modelu COM o wartości FALSE lub 0.</span><span class="sxs-lookup"><span data-stu-id="be84c-105">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="be84c-106">Alternatywnie Jeśli metoda ma zwrócony typ void, może istnieć żadnego wskazania, że wystąpił wyjątek podczas wykonywania metody.</span><span class="sxs-lookup"><span data-stu-id="be84c-106">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="be84c-107">W takim przypadku wyjątek zostanie przechwycony dyskretnej i wykonywania nastąpi powrót do metody wywołującej COM.</span><span class="sxs-lookup"><span data-stu-id="be84c-107">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="be84c-108">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="be84c-108">Cause</span></span>  
 <span data-ttu-id="be84c-109">Wystąpił wyjątek, ale nie istnieje prawidłowy sposób do raportu.</span><span class="sxs-lookup"><span data-stu-id="be84c-109">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="be84c-110">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="be84c-110">Resolution</span></span>  
 <span data-ttu-id="be84c-111">Komunikat informacyjny tylko, nie zawsze świadczy o usterki.</span><span class="sxs-lookup"><span data-stu-id="be84c-111">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="be84c-112">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="be84c-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="be84c-113">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="be84c-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="be84c-114">Zwraca tylko dane dotyczące wyjątków w trybie dyskretnym zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="be84c-114">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="be84c-115">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="be84c-115">Output</span></span>  
 <span data-ttu-id="be84c-116">Komunikat informacyjny zawierający nazwę metody, wpisz nazwę i komunikat o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="be84c-116">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="be84c-117">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="be84c-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="be84c-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be84c-118">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="be84c-119">Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="be84c-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="be84c-120">Przekazywanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="be84c-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
