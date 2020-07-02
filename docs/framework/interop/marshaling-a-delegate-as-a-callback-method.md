---
title: Marshaling delegata jako metoda wywołania zwrotnego
description: Dowiedz się, jak zorganizować delegata jako metodę wywołania zwrotnego. Zobacz przykład sposobu przekazywania delegatów do niezarządzanej funkcji, która oczekuje wskaźników funkcji.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, Callback sample
- marshaling, Callback sample
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
ms.openlocfilehash: bf9ef3b9d48c0869dcc96820c3a2fb6fb608479e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618951"
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a><span data-ttu-id="cff5e-104">Marshaling delegata jako metoda wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="cff5e-104">Marshaling a Delegate as a Callback Method</span></span>
<span data-ttu-id="cff5e-105">Ten przykład ilustruje sposób przekazywania delegatów do funkcji niezarządzanej, oczekiwanie wskaźników funkcji.</span><span class="sxs-lookup"><span data-stu-id="cff5e-105">This sample demonstrates how to pass delegates to an unmanaged function expecting function pointers.</span></span> <span data-ttu-id="cff5e-106">Delegat jest klasą, która może przechowywać odwołanie do metody i jest równoznaczna z bezpiecznym dla typu wskaźnikiem funkcji lub funkcją wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="cff5e-106">A delegate is a class that can hold a reference to a method and is equivalent to a type-safe function pointer or a callback function.</span></span>

> [!NOTE]
> <span data-ttu-id="cff5e-107">W przypadku korzystania z delegata wewnątrz wywołania środowisko uruchomieniowe języka wspólnego chroni delegata przed wyrzucaniem elementów bezużytecznych na czas trwania tego wywołania.</span><span class="sxs-lookup"><span data-stu-id="cff5e-107">When you use a delegate inside a call, the common language runtime protects the delegate from being garbage collected for the duration of that call.</span></span> <span data-ttu-id="cff5e-108">Jeśli jednak funkcja niezarządzana przechowuje delegata, który ma być używany po zakończeniu wywołania, należy ręcznie zablokować odzyskiwanie pamięci do momentu zakończenia niezarządzanej funkcji z delegatem.</span><span class="sxs-lookup"><span data-stu-id="cff5e-108">However, if the unmanaged function stores the delegate to use after the call completes, you must manually prevent garbage collection until the unmanaged function finishes with the delegate.</span></span> <span data-ttu-id="cff5e-109">Aby uzyskać więcej informacji, zobacz przykład [HandleRef —](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) i [GCHandle](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="cff5e-109">For more information, see the [HandleRef Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) and [GCHandle Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).</span></span>

<span data-ttu-id="cff5e-110">Przykład wywołania zwrotnego używa następujących funkcji niezarządzanych, które są wyświetlane wraz z ich oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="cff5e-110">The Callback sample uses the following unmanaged functions, shown with their original function declaration:</span></span>

- <span data-ttu-id="cff5e-111">`TestCallBack`wyeksportowane z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="cff5e-111">`TestCallBack` exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestCallBack(FPTR pf, int value);
    ```

- <span data-ttu-id="cff5e-112">`TestCallBack2`wyeksportowane z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="cff5e-112">`TestCallBack2` exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestCallBack2(FPTR2 pf2, char* value);
    ```

<span data-ttu-id="cff5e-113">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) to niestandardowa Biblioteka niezarządzana, która zawiera implementację wcześniej wymienionych funkcji.</span><span class="sxs-lookup"><span data-stu-id="cff5e-113">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed functions.</span></span>

<span data-ttu-id="cff5e-114">W tym przykładzie `NativeMethods` Klasa zawiera zarządzane prototypy dla `TestCallBack` `TestCallBack2` metod i.</span><span class="sxs-lookup"><span data-stu-id="cff5e-114">In this sample, the `NativeMethods` class contains managed prototypes for the `TestCallBack` and `TestCallBack2` methods.</span></span> <span data-ttu-id="cff5e-115">Obie metody przekażą delegata do funkcji wywołania zwrotnego jako parametr.</span><span class="sxs-lookup"><span data-stu-id="cff5e-115">Both methods pass a delegate to a callback function as a parameter.</span></span> <span data-ttu-id="cff5e-116">Podpis delegata musi być zgodny z podpisem metody, do której się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="cff5e-116">The signature of the delegate must match the signature of the method it references.</span></span> <span data-ttu-id="cff5e-117">Na przykład `FPtr` `FPtr2` Delegaty i mają podpisy identyczne z `DoSomething` `DoSomething2` metodami i.</span><span class="sxs-lookup"><span data-stu-id="cff5e-117">For example, the `FPtr` and `FPtr2` delegates have signatures that are identical to the `DoSomething` and `DoSomething2` methods.</span></span>

## <a name="declaring-prototypes"></a><span data-ttu-id="cff5e-118">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="cff5e-118">Declaring Prototypes</span></span>
[!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
[!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
[!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]

## <a name="calling-functions"></a><span data-ttu-id="cff5e-119">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="cff5e-119">Calling Functions</span></span>
[!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
[!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
[!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]

## <a name="see-also"></a><span data-ttu-id="cff5e-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cff5e-120">See also</span></span>

- <span data-ttu-id="cff5e-121">[Różne przykłady organizowania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="cff5e-121">[Miscellaneous Marshaling Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span></span>
- [<span data-ttu-id="cff5e-122">Typy danych wywołania platformy</span><span class="sxs-lookup"><span data-stu-id="cff5e-122">Platform Invoke Data Types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="cff5e-123">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="cff5e-123">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
