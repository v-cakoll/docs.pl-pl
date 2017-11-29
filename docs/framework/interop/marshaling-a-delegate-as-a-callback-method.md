---
title: "Marshaling delegata jako metoda wywołania zwrotnego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, Callback sample
- marshaling, Callback sample
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c8c4eca35c406b38da603dc10358920ee887b137
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a><span data-ttu-id="85df8-102">Marshaling delegata jako metoda wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="85df8-102">Marshaling a Delegate as a Callback Method</span></span>
<span data-ttu-id="85df8-103">W tym przykładzie pokazano, jak przekazać delegatów niezarządzanych funkcji, oczekiwano wskaźników funkcji.</span><span class="sxs-lookup"><span data-stu-id="85df8-103">This sample demonstrates how to pass delegates to an unmanaged function expecting function pointers.</span></span> <span data-ttu-id="85df8-104">Delegat jest klasa, która może zawierać odwołań do metody i stanowi odpowiednik wskaźnika funkcji bezpieczny lub funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="85df8-104">A delegate is a class that can hold a reference to a method and is equivalent to a type-safe function pointer or a callback function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85df8-105">Gdy używasz delegata w wywołaniu środowisko uruchomieniowe języka wspólnego uniemożliwia jako elementu bezużytecznego zebrane na czas trwania tego wywołania delegata.</span><span class="sxs-lookup"><span data-stu-id="85df8-105">When you use a delegate inside a call, the common language runtime protects the delegate from being garbage collected for the duration of that call.</span></span> <span data-ttu-id="85df8-106">Jednak jeśli niezarządzanej funkcji przechowuje delegata po zakończeniu wywołania, należy ręcznie uniemożliwienie wyrzucanie elementów bezużytecznych zakończenie niezarządzanej funkcji z obiektem delegowanym.</span><span class="sxs-lookup"><span data-stu-id="85df8-106">However, if the unmanaged function stores the delegate to use after the call completes, you must manually prevent garbage collection until the unmanaged function finishes with the delegate.</span></span> <span data-ttu-id="85df8-107">Aby uzyskać więcej informacji, zobacz [Przykładowy element HandleRef](http://msdn.microsoft.com/en-us/ab23b04e-1d53-4ec7-b27a-e892d9298959) i [próbki dojścia GCHandle](http://msdn.microsoft.com/en-us/6acce798-0385-4ded-a790-77da842c113f).</span><span class="sxs-lookup"><span data-stu-id="85df8-107">For more information, see the [HandleRef Sample](http://msdn.microsoft.com/en-us/ab23b04e-1d53-4ec7-b27a-e892d9298959) and [GCHandle Sample](http://msdn.microsoft.com/en-us/6acce798-0385-4ded-a790-77da842c113f).</span></span>  
  
 <span data-ttu-id="85df8-108">Przykład wywołania zwrotnego używa następujących funkcji niezarządzane, przedstawiono ich oryginalnej deklaracji funkcji:</span><span class="sxs-lookup"><span data-stu-id="85df8-108">The Callback sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="85df8-109">**TestCallBack** wyeksportowane z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="85df8-109">**TestCallBack** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestCallBack(FPTR pf, int value);  
    ```  
  
-   <span data-ttu-id="85df8-110">**TestCallBack2** wyeksportowane z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="85df8-110">**TestCallBack2** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestCallBack2(FPTR2 pf2, char* value);  
    ```  
  
 <span data-ttu-id="85df8-111">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) jest niestandardowa biblioteka niezarządzane zawierającego implementację funkcji wymienione wcześniej.</span><span class="sxs-lookup"><span data-stu-id="85df8-111">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) is a custom unmanaged library that contains an implementation for the previously listed functions.</span></span>  
  
 <span data-ttu-id="85df8-112">W tym przykładzie `LibWrap` klasa zawiera zarządzanych prototypy dla `TestCallBack` i `TestCallBack2` metody.</span><span class="sxs-lookup"><span data-stu-id="85df8-112">In this sample, the `LibWrap` class contains managed prototypes for the `TestCallBack` and `TestCallBack2` methods.</span></span> <span data-ttu-id="85df8-113">Obie metody przekazywanie obiektu delegate funkcji wywołania zwrotnego jako parametr.</span><span class="sxs-lookup"><span data-stu-id="85df8-113">Both methods pass a delegate to a callback function as a parameter.</span></span> <span data-ttu-id="85df8-114">Podpis delegata musi być zgodna podpis metody, których się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="85df8-114">The signature of the delegate must match the signature of the method it references.</span></span> <span data-ttu-id="85df8-115">Na przykład `FPtr` i `FPtr2` delegatów mają podpisy, które są takie same jak `DoSomething` i `DoSomething2` metody.</span><span class="sxs-lookup"><span data-stu-id="85df8-115">For example, the `FPtr` and `FPtr2` delegates have signatures that are identical to the `DoSomething` and `DoSomething2` methods.</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="85df8-116">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="85df8-116">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
 [!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
 [!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]  
  
## <a name="calling-functions"></a><span data-ttu-id="85df8-117">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="85df8-117">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
 [!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
 [!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="85df8-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85df8-118">See Also</span></span>  
 [<span data-ttu-id="85df8-119">Dodatkowe przykłady Marshalingu</span><span class="sxs-lookup"><span data-stu-id="85df8-119">Miscellaneous Marshaling Samples</span></span>](http://msdn.microsoft.com/en-us/a915c948-54e9-4d0f-a525-95a77fd8ed70)  
 [<span data-ttu-id="85df8-120">Typy danych wywołanie platformy</span><span class="sxs-lookup"><span data-stu-id="85df8-120">Platform Invoke Data Types</span></span>](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [<span data-ttu-id="85df8-121">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="85df8-121">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
