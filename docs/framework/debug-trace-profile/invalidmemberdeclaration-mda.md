---
title: invalidMemberDeclaration MDA
ms.date: 03/30/2017
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fe15d718a9c5f91bfae4f37c04e726990e2fbd45
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052585"
---
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="37370-102">invalidMemberDeclaration MDA</span><span class="sxs-lookup"><span data-stu-id="37370-102">invalidMemberDeclaration MDA</span></span>
<span data-ttu-id="37370-103">Asystent `invalidMemberDeclaration` debugowania zarządzanego (MDA) został aktywowany, aby zgłosić błąd, który występuje podczas określania sposobu organizowania parametrów elementu członkowskiego, który ma być wywoływany z modelu com.</span><span class="sxs-lookup"><span data-stu-id="37370-103">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="37370-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="37370-104">Symptoms</span></span>  
 <span data-ttu-id="37370-105">Błąd HRESULT jest zwracany do modelu COM bez wywołania metody zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="37370-105">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="37370-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="37370-106">Cause</span></span>  
 <span data-ttu-id="37370-107">Najprawdopodobniej ze względu na niezgodny <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybut na jednym z parametrów.</span><span class="sxs-lookup"><span data-stu-id="37370-107">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="37370-108">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="37370-108">Resolution</span></span>  
 <span data-ttu-id="37370-109">Określ prawidłowe <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybuty dla parametrów.</span><span class="sxs-lookup"><span data-stu-id="37370-109">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="37370-110">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="37370-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="37370-111">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="37370-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="37370-112">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="37370-112">Output</span></span>  
 <span data-ttu-id="37370-113">Komunikat informacyjny zawierający nazwę elementu członkowskiego, nazwę typu i komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="37370-113">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="37370-114">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="37370-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="37370-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37370-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="37370-116">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="37370-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="37370-117">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="37370-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
