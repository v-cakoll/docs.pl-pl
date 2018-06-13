---
title: pInvokeStackImbalance MDA
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- stack depth
- platform invoke stack imbalance
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- PInvokeStackImbalance MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: 34ddc6bd-1675-4f35-86aa-de1645d5c631
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9938db3f4a3d054fde52139c166fb6a2e2a402df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388059"
---
# <a name="pinvokestackimbalance-mda"></a><span data-ttu-id="a9785-102">pInvokeStackImbalance MDA</span><span class="sxs-lookup"><span data-stu-id="a9785-102">pInvokeStackImbalance MDA</span></span>
<span data-ttu-id="a9785-103">`pInvokeStackImbalance` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy środowisko CLR wykryje, że głębokość stosu po wywołaniu wywołanie platformy nie odpowiada Głębokość stosu oczekiwanego, podane Konwencja wywoływania określona w <xref:System.Runtime.InteropServices.DllImportAttribute> atrybutu, jak również Deklaracja parametrów w zarządzanego podpisu.</span><span class="sxs-lookup"><span data-stu-id="a9785-103">The `pInvokeStackImbalance` managed debugging assistant (MDA) is activated when the CLR detects that the stack depth after a platform invoke call does not match the expected stack depth, given the calling convention specified in the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute as well as the declaration of the parameters in the managed signature.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9785-104">`pInvokeStackImbalance` MDA zaimplementowano tylko w przypadku x86 32-bitowych platform.</span><span class="sxs-lookup"><span data-stu-id="a9785-104">The `pInvokeStackImbalance` MDA is implemented only for 32-bit x86 platforms.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9785-105">W programie .NET Framework w wersji 3.5 `pInvokeStackImbalance` MDA jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="a9785-105">In the .NET Framework version 3.5, the `pInvokeStackImbalance` MDA is disabled by default.</span></span> <span data-ttu-id="a9785-106">Podczas korzystania z programu Visual Studio 2005, .NET Framework w wersji 3.5 `pInvokeStackImbalance` MDA pojawią się w **Asystenci zarządzanego debugowania** na liście **wyjątki** okno dialogowe (który jest wyświetlany, gdy Możesz kliknąć przycisk **wyjątki** na **debugowania** menu).</span><span class="sxs-lookup"><span data-stu-id="a9785-106">When you use the .NET Framework version 3.5 with Visual Studio 2005, the `pInvokeStackImbalance` MDA will appear in the **Managed Debugging Assistants** list in the **Exceptions** dialog box (which is displayed when you click **Exceptions** on the **Debug** menu).</span></span> <span data-ttu-id="a9785-107">Jednak zaznaczenie lub wyczyszczenie **wyrzuconych** pole wyboru dla `pInvokeStackImbalance` nie Włączanie lub wyłączanie MDA; tylko określa, czy program Visual Studio zgłasza wyjątek, po aktywowaniu MDA.</span><span class="sxs-lookup"><span data-stu-id="a9785-107">However, selecting or clearing the **Thrown** check box for `pInvokeStackImbalance` does not enable or disable the MDA; it only controls whether Visual Studio throws an exception when the MDA is activated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a9785-108">Symptomy</span><span class="sxs-lookup"><span data-stu-id="a9785-108">Symptoms</span></span>  
 <span data-ttu-id="a9785-109">Aplikacja napotka naruszenie zasad dostępu lub wywołania wywołania podczas wprowadzania lub po platformę uszkodzenie pamięci.</span><span class="sxs-lookup"><span data-stu-id="a9785-109">An application encounters an access violation or memory corruption when making or following a platform invoke call.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a9785-110">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="a9785-110">Cause</span></span>  
 <span data-ttu-id="a9785-111">Wywołanie invoke zarządzanego podpisu platformy może nie pasują do niezarządzanego podpisu metody wywoływane.</span><span class="sxs-lookup"><span data-stu-id="a9785-111">The managed signature of the platform invoke call might not match the unmanaged signature of the method being called.</span></span>  <span data-ttu-id="a9785-112">Ta niezgodność może być spowodowane zarządzanego podpisu nie deklarowanie poprawną liczbę parametrów lub nie określając odpowiedni rozmiar parametrów.</span><span class="sxs-lookup"><span data-stu-id="a9785-112">This mismatch can be caused by the managed signature not declaring the correct number of parameters or not specifying the appropriate size for the parameters.</span></span>  <span data-ttu-id="a9785-113">MDA mogą także aktywować, ponieważ Konwencja wywoływania prawdopodobnie określony przez <xref:System.Runtime.InteropServices.DllImportAttribute> atrybutu, jest niezgodny z niezarządzana konwencja wywołania.</span><span class="sxs-lookup"><span data-stu-id="a9785-113">The MDA can also activate because the calling convention, possibly specified by the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute, does not match the unmanaged calling convention.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a9785-114">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="a9785-114">Resolution</span></span>  
 <span data-ttu-id="a9785-115">Przejrzyj zarządzana platforma wywołania podpisu i Konwencja wywoływania potwierdzić, że jest on zgodny podpisu i Konwencja wywoływania natywnego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="a9785-115">Review the managed platform invoke signature and calling convention to confirm it matches the signature and calling convention of the native target.</span></span>  <span data-ttu-id="a9785-116">Spróbuj jawnie określić konwencję wywołania po obu stronach zarządzane i niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="a9785-116">Try explicitly specifying the calling convention on both the managed and unmanaged sides.</span></span> <span data-ttu-id="a9785-117">Istnieje również możliwość, mimo że nie jako prawdopodobne, że niezarządzanej funkcji równowagą stosu innego powodu, takich jak usterki w kompilatorze niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="a9785-117">It is also possible, although not as likely, that the unmanaged function unbalanced the stack for some other reason, such as a bug in the unmanaged compiler.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a9785-118">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="a9785-118">Effect on the Runtime</span></span>  
 <span data-ttu-id="a9785-119">Wymusza wywołanie platformy wszystkich wywołań korzysta ze ścieżki nonoptimized w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="a9785-119">Forces all platform invoke calls to take the nonoptimized path in the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a9785-120">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="a9785-120">Output</span></span>  
 <span data-ttu-id="a9785-121">Komunikat MDA nadaje nazwę platformy wywołania metody, która powoduje nierównowaga stosu wywołania.</span><span class="sxs-lookup"><span data-stu-id="a9785-121">The MDA message gives the name of the platform invoke method call that is causing the stack imbalance.</span></span>  <span data-ttu-id="a9785-122">Wywołanie metody invoke przykładowy komunikat platformy `SampleMethod` jest:</span><span class="sxs-lookup"><span data-stu-id="a9785-122">A sample message of a platform invoke call on method `SampleMethod` is:</span></span>  
  
```  
A call to PInvoke function 'SampleMethod' has unbalanced the stack.   
This is likely because the managed PInvoke signature does not match   
the unmanaged target signature. Check that the calling convention and   
parameters of the PInvoke signature match the target unmanaged signature.  
```  
  
## <a name="configuration"></a><span data-ttu-id="a9785-123">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="a9785-123">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeStackImbalance />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a9785-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9785-124">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="a9785-125">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="a9785-125">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="a9785-126">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="a9785-126">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
