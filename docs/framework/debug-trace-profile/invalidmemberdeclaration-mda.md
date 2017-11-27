---
title: invalidMemberDeclaration MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 71313a14ba1f9222e19dbf9f8180280d0e8c444d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="7f4e4-102">invalidMemberDeclaration MDA</span><span class="sxs-lookup"><span data-stu-id="7f4e4-102">invalidMemberDeclaration MDA</span></span>
<span data-ttu-id="7f4e4-103">`invalidMemberDeclaration` Zarządzany Asystent debugowania (MDA) jest aktywowana Aby zgłosić błąd występujący podczas ustalania sposobu zorganizowania parametrów członka do wywoływania z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="7f4e4-103">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7f4e4-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="7f4e4-104">Symptoms</span></span>  
 <span data-ttu-id="7f4e4-105">Błąd HRESULT jest zwracana do modelu COM bez zarządzanego o została wywołana metoda.</span><span class="sxs-lookup"><span data-stu-id="7f4e4-105">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7f4e4-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="7f4e4-106">Cause</span></span>  
 <span data-ttu-id="7f4e4-107">Jest to najprawdopodobniej spowodowane niezgodną <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu na jeden z parametrów.</span><span class="sxs-lookup"><span data-stu-id="7f4e4-107">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7f4e4-108">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="7f4e4-108">Resolution</span></span>  
 <span data-ttu-id="7f4e4-109">Określ prawidłową <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutów dla parametrów.</span><span class="sxs-lookup"><span data-stu-id="7f4e4-109">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7f4e4-110">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="7f4e4-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="7f4e4-111">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="7f4e4-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7f4e4-112">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="7f4e4-112">Output</span></span>  
 <span data-ttu-id="7f4e4-113">Komunikat informacyjny zawierającego nazwę elementu członkowskiego, wpisz nazwę i komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="7f4e4-113">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="7f4e4-114">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="7f4e4-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f4e4-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f4e4-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="7f4e4-116">Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="7f4e4-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="7f4e4-117">Przekazywanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="7f4e4-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
