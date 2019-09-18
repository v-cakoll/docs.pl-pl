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
ms.openlocfilehash: 3a49bdce78c1445cd25de8755ded0f27a4902937
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052817"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="1c3f2-102">exceptionSwallowedOnCallFromCom MDA</span><span class="sxs-lookup"><span data-stu-id="1c3f2-102">exceptionSwallowedOnCallFromCom MDA</span></span>
<span data-ttu-id="1c3f2-103">Asystent `exceptionSwallowedOnCallFromCOM` debugowania zarządzanego (MDA) jest uaktywniany, gdy wyjątek jest zgłaszany z kodu środowiska uruchomieniowego języka wspólnego (CLR) wywoływanego z modelu COM za pomocą metody, która nie ma niezarządzanego zwracanego typu HRESULT.</span><span class="sxs-lookup"><span data-stu-id="1c3f2-103">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1c3f2-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="1c3f2-104">Symptoms</span></span>  
 <span data-ttu-id="1c3f2-105">Wywołanie zarządzanego składnika z modelu COM zwraca wartość FALSE lub 0.</span><span class="sxs-lookup"><span data-stu-id="1c3f2-105">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="1c3f2-106">Alternatywnie, jeśli metoda ma typ zwracany void, może nie być wskazywać, że wyjątek został zgłoszony podczas wykonywania metody.</span><span class="sxs-lookup"><span data-stu-id="1c3f2-106">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="1c3f2-107">W takim przypadku wyjątek zostanie przechwycony w trybie dyskretnym, a wykonywanie zwróci do obiektu wywołującego COM.</span><span class="sxs-lookup"><span data-stu-id="1c3f2-107">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1c3f2-108">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="1c3f2-108">Cause</span></span>  
 <span data-ttu-id="1c3f2-109">Zgłoszono wyjątek, ale nie ma prawidłowego sposobu na jego raportowanie.</span><span class="sxs-lookup"><span data-stu-id="1c3f2-109">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1c3f2-110">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="1c3f2-110">Resolution</span></span>  
 <span data-ttu-id="1c3f2-111">Tylko informacyjne, niekoniecznie wskazujące usterkę.</span><span class="sxs-lookup"><span data-stu-id="1c3f2-111">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1c3f2-112">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="1c3f2-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="1c3f2-113">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="1c3f2-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="1c3f2-114">Raport dotyczy tylko danych o przechwyconych dyskretnie wyjątkach.</span><span class="sxs-lookup"><span data-stu-id="1c3f2-114">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1c3f2-115">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="1c3f2-115">Output</span></span>  
 <span data-ttu-id="1c3f2-116">Komunikat informacyjny zawierający nazwę metody, nazwę typu i komunikat o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="1c3f2-116">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="1c3f2-117">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="1c3f2-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1c3f2-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c3f2-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="1c3f2-119">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="1c3f2-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="1c3f2-120">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="1c3f2-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
