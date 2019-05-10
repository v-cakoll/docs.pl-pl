---
title: Marshaling delegata jako metoda wywołania zwrotnego
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, Callback sample
- marshaling, Callback sample
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 145e6b8891735c904aa98a36ccfd27958bdf788d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648615"
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a><span data-ttu-id="70cfa-102">Marshaling delegata jako metoda wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="70cfa-102">Marshaling a Delegate as a Callback Method</span></span>
<span data-ttu-id="70cfa-103">Niniejszy przykład pokazuje sposób przekazywania delegatów do niezarządzanej funkcji, oczekiwano wskaźników funkcji.</span><span class="sxs-lookup"><span data-stu-id="70cfa-103">This sample demonstrates how to pass delegates to an unmanaged function expecting function pointers.</span></span> <span data-ttu-id="70cfa-104">Delegat to klasa, która może zawierać odwołanie do metody i jest równoważny wskaźnikowi funkcji bezpiecznego typu lub funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="70cfa-104">A delegate is a class that can hold a reference to a method and is equivalent to a type-safe function pointer or a callback function.</span></span>

> [!NOTE]
>  <span data-ttu-id="70cfa-105">Gdy używasz delegata w wywołaniu, środowisko uruchomieniowe języka wspólnego chroni delegata jako elementu bezużytecznego zebrane na czas trwania wywołania.</span><span class="sxs-lookup"><span data-stu-id="70cfa-105">When you use a delegate inside a call, the common language runtime protects the delegate from being garbage collected for the duration of that call.</span></span> <span data-ttu-id="70cfa-106">Jednak jeśli delegata do użycia po ukończeniu wywołania są przechowywane w funkcji niezarządzanej, trzeba ręcznie chronić wyrzucania elementów bezużytecznych zakończenie niezarządzanej funkcji z obiektem delegowanym.</span><span class="sxs-lookup"><span data-stu-id="70cfa-106">However, if the unmanaged function stores the delegate to use after the call completes, you must manually prevent garbage collection until the unmanaged function finishes with the delegate.</span></span> <span data-ttu-id="70cfa-107">Aby uzyskać więcej informacji, zobacz [HandleRef — przykład](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) i [GCHandle — przykład](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="70cfa-107">For more information, see the [HandleRef Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) and [GCHandle Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).</span></span>

<span data-ttu-id="70cfa-108">Przykład wywołania zwrotnego używa następujących funkcji niezarządzanych, wyświetlane wraz z ich oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="70cfa-108">The Callback sample uses the following unmanaged functions, shown with their original function declaration:</span></span>

- <span data-ttu-id="70cfa-109">`TestCallBack` eksportowany z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="70cfa-109">`TestCallBack` exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestCallBack(FPTR pf, int value);
    ```

- <span data-ttu-id="70cfa-110">`TestCallBack2` eksportowany z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="70cfa-110">`TestCallBack2` exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestCallBack2(FPTR2 pf2, char* value);
    ```

<span data-ttu-id="70cfa-111">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) jest niestandardową biblioteką niezarządzaną, która zawiera implementację wyżej wymienionych funkcji.</span><span class="sxs-lookup"><span data-stu-id="70cfa-111">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed functions.</span></span>

<span data-ttu-id="70cfa-112">W tym przykładzie `LibWrap` klasa zawiera zarządzane prototypy `TestCallBack` i `TestCallBack2` metody.</span><span class="sxs-lookup"><span data-stu-id="70cfa-112">In this sample, the `LibWrap` class contains managed prototypes for the `TestCallBack` and `TestCallBack2` methods.</span></span> <span data-ttu-id="70cfa-113">Obie metody przekazać delegata do funkcji wywołania zwrotnego, jako parametr.</span><span class="sxs-lookup"><span data-stu-id="70cfa-113">Both methods pass a delegate to a callback function as a parameter.</span></span> <span data-ttu-id="70cfa-114">Podpis delegata musi odpowiadać podpisowi metody, do którego się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="70cfa-114">The signature of the delegate must match the signature of the method it references.</span></span> <span data-ttu-id="70cfa-115">Na przykład `FPtr` i `FPtr2` delegatów opatrzone sygnaturami, które są takie same jak `DoSomething` i `DoSomething2` metody.</span><span class="sxs-lookup"><span data-stu-id="70cfa-115">For example, the `FPtr` and `FPtr2` delegates have signatures that are identical to the `DoSomething` and `DoSomething2` methods.</span></span>

## <a name="declaring-prototypes"></a><span data-ttu-id="70cfa-116">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="70cfa-116">Declaring Prototypes</span></span>
[!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
[!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
[!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]

## <a name="calling-functions"></a><span data-ttu-id="70cfa-117">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="70cfa-117">Calling Functions</span></span>
[!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
[!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
[!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]

## <a name="see-also"></a><span data-ttu-id="70cfa-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70cfa-118">See also</span></span>

- <span data-ttu-id="70cfa-119">[Różne przykłady organizowania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="70cfa-119">[Miscellaneous Marshaling Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span></span>
- [<span data-ttu-id="70cfa-120">Typy danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="70cfa-120">Platform Invoke Data Types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="70cfa-121">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="70cfa-121">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
