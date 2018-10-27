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
ms.openlocfilehash: 579bc56a538707fd19d6d089c7f3c0c0561ea9eb
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49454424"
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a>Marshaling delegata jako metoda wywołania zwrotnego
Niniejszy przykład pokazuje sposób przekazywania delegatów do niezarządzanej funkcji, oczekiwano wskaźników funkcji. Delegat to klasa, która może zawierać odwołanie do metody i jest równoważny wskaźnikowi funkcji bezpiecznego typu lub funkcji wywołania zwrotnego.  
  
> [!NOTE]
>  Gdy używasz delegata w wywołaniu, środowisko uruchomieniowe języka wspólnego chroni delegata jako elementu bezużytecznego zebrane na czas trwania wywołania. Jednak jeśli delegata do użycia po ukończeniu wywołania są przechowywane w funkcji niezarządzanej, trzeba ręcznie chronić wyrzucania elementów bezużytecznych zakończenie niezarządzanej funkcji z obiektem delegowanym. Aby uzyskać więcej informacji, zobacz [HandleRef — przykład](https://msdn.microsoft.com/library/ab23b04e-1d53-4ec7-b27a-e892d9298959(v=vs.100)) i [GCHandle — przykład](https://msdn.microsoft.com/library/6acce798-0385-4ded-a790-77da842c113f(v=vs.100)).  
  
 Przykład wywołania zwrotnego używa następujących funkcji niezarządzanych, wyświetlane wraz z ich oryginalną deklaracją funkcji:  
  
-   **TestCallBack** eksportowany z PinvokeLib.dll.  
  
    ```  
    void TestCallBack(FPTR pf, int value);  
    ```  
  
-   **TestCallBack2** eksportowany z PinvokeLib.dll.  
  
    ```  
    void TestCallBack2(FPTR2 pf2, char* value);  
    ```  
  
 [PinvokeLib.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as6wyhwt(v=vs.100)) jest niestandardową biblioteką niezarządzaną, która zawiera implementację wyżej wymienionych funkcji.  
  
 W tym przykładzie `LibWrap` klasa zawiera zarządzane prototypy `TestCallBack` i `TestCallBack2` metody. Obie metody przekazać delegata do funkcji wywołania zwrotnego, jako parametr. Podpis delegata musi odpowiadać podpisowi metody, do którego się odwołuje. Na przykład `FPtr` i `FPtr2` delegatów opatrzone sygnaturami, które są takie same jak `DoSomething` i `DoSomething2` metody.  
  
## <a name="declaring-prototypes"></a>Deklarowanie prototypów  
 [!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
 [!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
 [!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]  
  
## <a name="calling-functions"></a>Wywoływanie funkcji  
 [!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
 [!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
 [!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]  
  
## <a name="see-also"></a>Zobacz też  
 [Różne przykłady organizowania](https://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70(v=vs.100))  
 [Typy danych w wywołaniu platformy](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))  
 [Tworzenie prototypów w kodzie zarządzanym](creating-prototypes-in-managed-code.md)
