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
ms.openlocfilehash: 2697950a371d66f2e57731e0ff01ed531a07955e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946399"
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a><span data-ttu-id="550fe-102">Marshaling delegata jako metoda wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="550fe-102">Marshaling a Delegate as a Callback Method</span></span>
<span data-ttu-id="550fe-103">Ten przykład ilustruje sposób przekazywania delegatów do funkcji niezarządzanej, oczekiwanie wskaźników funkcji.</span><span class="sxs-lookup"><span data-stu-id="550fe-103">This sample demonstrates how to pass delegates to an unmanaged function expecting function pointers.</span></span> <span data-ttu-id="550fe-104">Delegat jest klasą, która może przechowywać odwołanie do metody i jest równoznaczna z bezpiecznym dla typu wskaźnikiem funkcji lub funkcją wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="550fe-104">A delegate is a class that can hold a reference to a method and is equivalent to a type-safe function pointer or a callback function.</span></span>

> [!NOTE]
> <span data-ttu-id="550fe-105">W przypadku korzystania z delegata wewnątrz wywołania środowisko uruchomieniowe języka wspólnego chroni delegata przed wyrzucaniem elementów bezużytecznych na czas trwania tego wywołania.</span><span class="sxs-lookup"><span data-stu-id="550fe-105">When you use a delegate inside a call, the common language runtime protects the delegate from being garbage collected for the duration of that call.</span></span> <span data-ttu-id="550fe-106">Jeśli jednak funkcja niezarządzana przechowuje delegata, który ma być używany po zakończeniu wywołania, należy ręcznie zablokować odzyskiwanie pamięci do momentu zakończenia niezarządzanej funkcji z delegatem.</span><span class="sxs-lookup"><span data-stu-id="550fe-106">However, if the unmanaged function stores the delegate to use after the call completes, you must manually prevent garbage collection until the unmanaged function finishes with the delegate.</span></span> <span data-ttu-id="550fe-107">Aby uzyskać więcej informacji, zobacz przykład [HandleRef —](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) i [GCHandle](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="550fe-107">For more information, see the [HandleRef Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) and [GCHandle Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).</span></span>

<span data-ttu-id="550fe-108">Przykład wywołania zwrotnego używa następujących funkcji niezarządzanych, które są wyświetlane wraz z ich oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="550fe-108">The Callback sample uses the following unmanaged functions, shown with their original function declaration:</span></span>

- <span data-ttu-id="550fe-109">`TestCallBack`wyeksportowane z PinvokeLib. dll.</span><span class="sxs-lookup"><span data-stu-id="550fe-109">`TestCallBack` exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestCallBack(FPTR pf, int value);
    ```

- <span data-ttu-id="550fe-110">`TestCallBack2`wyeksportowane z PinvokeLib. dll.</span><span class="sxs-lookup"><span data-stu-id="550fe-110">`TestCallBack2` exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestCallBack2(FPTR2 pf2, char* value);
    ```

<span data-ttu-id="550fe-111">[PinvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) to niestandardowa Biblioteka niezarządzana, która zawiera implementację wcześniej wymienionych funkcji.</span><span class="sxs-lookup"><span data-stu-id="550fe-111">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed functions.</span></span>

<span data-ttu-id="550fe-112">W tym przykładzie `LibWrap` Klasa zawiera zarządzane prototypy `TestCallBack` dla metod i `TestCallBack2` .</span><span class="sxs-lookup"><span data-stu-id="550fe-112">In this sample, the `LibWrap` class contains managed prototypes for the `TestCallBack` and `TestCallBack2` methods.</span></span> <span data-ttu-id="550fe-113">Obie metody przekażą delegata do funkcji wywołania zwrotnego jako parametr.</span><span class="sxs-lookup"><span data-stu-id="550fe-113">Both methods pass a delegate to a callback function as a parameter.</span></span> <span data-ttu-id="550fe-114">Podpis delegata musi być zgodny z podpisem metody, do której się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="550fe-114">The signature of the delegate must match the signature of the method it references.</span></span> <span data-ttu-id="550fe-115">Na przykład `FPtr` Delegaty i `FPtr2` mają podpisy identyczne `DoSomething` z metodami i `DoSomething2` .</span><span class="sxs-lookup"><span data-stu-id="550fe-115">For example, the `FPtr` and `FPtr2` delegates have signatures that are identical to the `DoSomething` and `DoSomething2` methods.</span></span>

## <a name="declaring-prototypes"></a><span data-ttu-id="550fe-116">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="550fe-116">Declaring Prototypes</span></span>
[!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
[!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
[!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]

## <a name="calling-functions"></a><span data-ttu-id="550fe-117">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="550fe-117">Calling Functions</span></span>
[!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
[!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
[!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]

## <a name="see-also"></a><span data-ttu-id="550fe-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="550fe-118">See also</span></span>

- <span data-ttu-id="550fe-119">[Różne przykłady organizowania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="550fe-119">[Miscellaneous Marshaling Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span></span>
- [<span data-ttu-id="550fe-120">Typy danych wywołania platformy</span><span class="sxs-lookup"><span data-stu-id="550fe-120">Platform Invoke Data Types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="550fe-121">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="550fe-121">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
