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
ms.openlocfilehash: 0caa3add1a35d460527ce665352e5861df7d5d7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="b7998-102">invalidMemberDeclaration MDA</span><span class="sxs-lookup"><span data-stu-id="b7998-102">invalidMemberDeclaration MDA</span></span>
<span data-ttu-id="b7998-103">`invalidMemberDeclaration` Zarządzany Asystent debugowania (MDA) jest aktywowana Aby zgłosić błąd występujący podczas ustalania sposobu zorganizowania parametrów członka do wywoływania z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="b7998-103">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="b7998-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="b7998-104">Symptoms</span></span>  
 <span data-ttu-id="b7998-105">Błąd HRESULT jest zwracana do modelu COM bez zarządzanego o została wywołana metoda.</span><span class="sxs-lookup"><span data-stu-id="b7998-105">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="b7998-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="b7998-106">Cause</span></span>  
 <span data-ttu-id="b7998-107">Jest to najprawdopodobniej spowodowane niezgodną <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu na jeden z parametrów.</span><span class="sxs-lookup"><span data-stu-id="b7998-107">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="b7998-108">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="b7998-108">Resolution</span></span>  
 <span data-ttu-id="b7998-109">Określ prawidłową <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutów dla parametrów.</span><span class="sxs-lookup"><span data-stu-id="b7998-109">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b7998-110">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="b7998-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="b7998-111">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="b7998-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b7998-112">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="b7998-112">Output</span></span>  
 <span data-ttu-id="b7998-113">Komunikat informacyjny zawierającego nazwę elementu członkowskiego, wpisz nazwę i komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="b7998-113">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b7998-114">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="b7998-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b7998-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7998-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="b7998-116">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="b7998-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="b7998-117">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="b7998-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
