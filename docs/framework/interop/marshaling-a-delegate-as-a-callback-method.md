---
title: Marshaling delegata jako metoda wywołania zwrotnego
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
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
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0f51c3b4e948abd23c1c2de443c80248011a28bd
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a>Marshaling delegata jako metoda wywołania zwrotnego
W tym przykładzie pokazano, jak przekazać delegatów niezarządzanych funkcji, oczekiwano wskaźników funkcji. Delegat jest klasa, która może zawierać odwołań do metody i stanowi odpowiednik wskaźnika funkcji bezpieczny lub funkcji wywołania zwrotnego.  
  
> [!NOTE]
>  Gdy używasz delegata w wywołaniu środowisko uruchomieniowe języka wspólnego uniemożliwia jako elementu bezużytecznego zebrane na czas trwania tego wywołania delegata. Jednak jeśli niezarządzanej funkcji przechowuje delegata po zakończeniu wywołania, należy ręcznie uniemożliwienie wyrzucanie elementów bezużytecznych zakończenie niezarządzanej funkcji z obiektem delegowanym. Aby uzyskać więcej informacji, zobacz [Przykładowy element HandleRef](https://msdn.microsoft.com/library/ab23b04e-1d53-4ec7-b27a-e892d9298959(v=vs.100)) i [próbki dojścia GCHandle](https://msdn.microsoft.com/library/6acce798-0385-4ded-a790-77da842c113f(v=vs.100)).  
  
 Przykład wywołania zwrotnego używa następujących funkcji niezarządzane, przedstawiono ich oryginalnej deklaracji funkcji:  
  
-   **TestCallBack** wyeksportowane z PinvokeLib.dll.  
  
    ```  
    void TestCallBack(FPTR pf, int value);  
    ```  
  
-   **TestCallBack2** wyeksportowane z PinvokeLib.dll.  
  
    ```  
    void TestCallBack2(FPTR2 pf2, char* value);  
    ```  
  
 [PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) jest niestandardowa biblioteka niezarządzane zawierającego implementację funkcji wymienione wcześniej.  
  
 W tym przykładzie `LibWrap` klasa zawiera zarządzanych prototypy dla `TestCallBack` i `TestCallBack2` metody. Obie metody przekazywanie obiektu delegate funkcji wywołania zwrotnego jako parametr. Podpis delegata musi być zgodna podpis metody, których się odwołuje. Na przykład `FPtr` i `FPtr2` delegatów mają podpisy, które są takie same jak `DoSomething` i `DoSomething2` metody.  
  
## <a name="declaring-prototypes"></a>Deklarowanie prototypów  
 [!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
 [!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
 [!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]  
  
## <a name="calling-functions"></a>Wywoływanie funkcji  
 [!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
 [!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
 [!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]  
  
## <a name="see-also"></a>Zobacz też  
 [Dodatkowe przykłady Marshalingu](https://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70(v=vs.100))  
 [Typy danych wywołanie platformy](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))  
 [Tworzenie prototypów w kodzie zarządzanym](creating-prototypes-in-managed-code.md)
