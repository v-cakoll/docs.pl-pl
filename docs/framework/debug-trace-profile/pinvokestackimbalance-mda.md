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
ms.openlocfilehash: 9ecdfd708217f260b0c02383159fab88948029c6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61874214"
---
# <a name="pinvokestackimbalance-mda"></a><span data-ttu-id="3bee8-102">PInvokeStackImbalance MDA</span><span class="sxs-lookup"><span data-stu-id="3bee8-102">PInvokeStackImbalance MDA</span></span>

<span data-ttu-id="3bee8-103">`PInvokeStackImbalance` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy CLR wykryje, że głębokość stosu po wywołaniu wywołania platformy jest niezgodna Głębokość stosu oczekiwanego, podane konwencja wywołania określona w <xref:System.Runtime.InteropServices.DllImportAttribute> atrybutu i Deklaracja parametrów w zarządzanego podpisu.</span><span class="sxs-lookup"><span data-stu-id="3bee8-103">The `PInvokeStackImbalance` managed debugging assistant (MDA) is activated when the CLR detects that the stack depth after a platform invoke call does not match the expected stack depth, given the calling convention specified in the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute and the declaration of the parameters in the managed signature.</span></span>

<span data-ttu-id="3bee8-104">`PInvokeStackImbalance` MDA jest zaimplementowanych tylko dla x86 32-bitowych platform.</span><span class="sxs-lookup"><span data-stu-id="3bee8-104">The `PInvokeStackImbalance` MDA is implemented only for 32-bit x86 platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="3bee8-105">`PInvokeStackImbalance` MDA jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="3bee8-105">The `PInvokeStackImbalance` MDA is disabled by default.</span></span> <span data-ttu-id="3bee8-106">W programie Visual Studio 2017 `PInvokeStackImbalance` MDA pojawia się w **asystentów zarządzanego debugowania** listy w **ustawienia wyjątków** okno dialogowe (który jest wyświetlany po wybraniu **debugowania**  >  **Windows** > **ustawienia wyjątków**).</span><span class="sxs-lookup"><span data-stu-id="3bee8-106">In Visual Studio 2017, The `PInvokeStackImbalance` MDA appears in the **Managed Debugging Assistants** list in the **Exception Settings** dialog box (which is displayed when you select **Debug** > **Windows** > **Exception Settings**).</span></span> <span data-ttu-id="3bee8-107">Jednakże, zaznaczając lub usuwając **Przerwij gdy zgłoszony** pole wyboru jest w stanie włączać lub wyłączać MDA; tylko kontroluje, czy program Visual Studio zgłasza wyjątek, gdy zdarzenie MDA jest aktywowane.</span><span class="sxs-lookup"><span data-stu-id="3bee8-107">However, selecting or clearing the **Break When Thrown** check box does not enable or disable the MDA; it only controls whether Visual Studio throws an exception when the MDA is activated.</span></span>

## <a name="symptoms"></a><span data-ttu-id="3bee8-108">Symptomy</span><span class="sxs-lookup"><span data-stu-id="3bee8-108">Symptoms</span></span>

<span data-ttu-id="3bee8-109">Aplikacja napotyka naruszenie zasad dostępu lub uszkodzenie podczas wprowadzania lub po platformie wywołania wywołania pamięci.</span><span class="sxs-lookup"><span data-stu-id="3bee8-109">An application encounters an access violation or memory corruption when making or following a platform invoke call.</span></span>

## <a name="cause"></a><span data-ttu-id="3bee8-110">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="3bee8-110">Cause</span></span>

<span data-ttu-id="3bee8-111">Zarządzanego podpisu platformy wywołania wywołania mogą być niezgodne z niezarządzanego podpisu metody wywoływane.</span><span class="sxs-lookup"><span data-stu-id="3bee8-111">The managed signature of the platform invoke call might not match the unmanaged signature of the method being called.</span></span>  <span data-ttu-id="3bee8-112">Taka niezgodność może być spowodowany zarządzanego podpisu nie deklarując poprawną liczbę parametrów lub brak określenia odpowiedniego rozmiaru dla parametrów.</span><span class="sxs-lookup"><span data-stu-id="3bee8-112">This mismatch can be caused by the managed signature not declaring the correct number of parameters or not specifying the appropriate size for the parameters.</span></span>  <span data-ttu-id="3bee8-113">MDA mogą także aktywować, ponieważ konwencji wywoływania, prawdopodobnie określony przez <xref:System.Runtime.InteropServices.DllImportAttribute> atrybutu, jest niezgodny z konwencji wywoływania niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="3bee8-113">The MDA can also activate because the calling convention, possibly specified by the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute, does not match the unmanaged calling convention.</span></span>

## <a name="resolution"></a><span data-ttu-id="3bee8-114">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="3bee8-114">Resolution</span></span>

<span data-ttu-id="3bee8-115">Przegląd zarządzanej platformie wywołać podpisu i konwencji wywoływania, aby upewnić się, że jest on zgodny podpis i konwencji wywoływania natywnego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="3bee8-115">Review the managed platform invoke signature and calling convention to confirm it matches the signature and calling convention of the native target.</span></span>  <span data-ttu-id="3bee8-116">Spróbuj jawnie określić konwencję wywołania po obu stronach zarządzanych i niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="3bee8-116">Try explicitly specifying the calling convention on both the managed and unmanaged sides.</span></span> <span data-ttu-id="3bee8-117">Jest również możliwe, ale nie jako prawdopodobne, że niezarządzanej funkcji niezrównoważone stosu innego powodu, takie jak usterki w kompilatorze niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="3bee8-117">It is also possible, although not as likely, that the unmanaged function unbalanced the stack for some other reason, such as a bug in the unmanaged compiler.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="3bee8-118">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="3bee8-118">Effect on the Runtime</span></span>

<span data-ttu-id="3bee8-119">Wymusza platformy wszystkie wywołania do podjęcia nonoptimized ścieżki w CLR.</span><span class="sxs-lookup"><span data-stu-id="3bee8-119">Forces all platform invoke calls to take the nonoptimized path in the CLR.</span></span>

## <a name="output"></a><span data-ttu-id="3bee8-120">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="3bee8-120">Output</span></span>

<span data-ttu-id="3bee8-121">Komunikat MDA zapewnia nazwę platformy wywołania metody, która powoduje nierównowaga stosu wywołania.</span><span class="sxs-lookup"><span data-stu-id="3bee8-121">The MDA message gives the name of the platform invoke method call that is causing the stack imbalance.</span></span> <span data-ttu-id="3bee8-122">Przykładowy komunikat platformy wywołania wywołanie metody `SampleMethod` jest:</span><span class="sxs-lookup"><span data-stu-id="3bee8-122">A sample message of a platform invoke call on method `SampleMethod` is:</span></span>

<span data-ttu-id="3bee8-123">**Wywołanie funkcji PInvoke "SampleMethod" ma niezrównoważone stosu. Jest to prawdopodobnie, ponieważ zarządzanego podpisu PInvoke jest niezgodna z niezarządzanego podpisu docelowego. Sprawdź, czy Konwencja wywoływania i parametry podpisu funkcji PInvoke odpowiadają niezarządzanego podpisu docelowego.**</span><span class="sxs-lookup"><span data-stu-id="3bee8-123">**A call to PInvoke function 'SampleMethod' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="configuration"></a><span data-ttu-id="3bee8-124">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="3bee8-124">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <pInvokeStackImbalance />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="3bee8-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3bee8-125">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="3bee8-126">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="3bee8-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="3bee8-127">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="3bee8-127">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
