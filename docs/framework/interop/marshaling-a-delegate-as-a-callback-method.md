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
ms.openlocfilehash: c71c89e5797745144a2baed2d4846e3d9f9f26be
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114020"
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a>Marshaling delegata jako metoda wywołania zwrotnego
Ten przykład ilustruje sposób przekazywania delegatów do funkcji niezarządzanej, oczekiwanie wskaźników funkcji. Delegat jest klasą, która może przechowywać odwołanie do metody i jest równoznaczna z bezpiecznym dla typu wskaźnikiem funkcji lub funkcją wywołania zwrotnego.

> [!NOTE]
> W przypadku korzystania z delegata wewnątrz wywołania środowisko uruchomieniowe języka wspólnego chroni delegata przed wyrzucaniem elementów bezużytecznych na czas trwania tego wywołania. Jeśli jednak funkcja niezarządzana przechowuje delegata, który ma być używany po zakończeniu wywołania, należy ręcznie zablokować odzyskiwanie pamięci do momentu zakończenia niezarządzanej funkcji z delegatem. Aby uzyskać więcej informacji, zobacz przykład [HandleRef —](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) i [GCHandle](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).

Przykład wywołania zwrotnego używa następujących funkcji niezarządzanych, które są wyświetlane wraz z ich oryginalną deklaracją funkcji:

- `TestCallBack`wyeksportowane z PinvokeLib. dll.

    ```cpp
    void TestCallBack(FPTR pf, int value);
    ```

- `TestCallBack2`wyeksportowane z PinvokeLib. dll.

    ```cpp
    void TestCallBack2(FPTR2 pf2, char* value);
    ```

[PinvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) to niestandardowa Biblioteka niezarządzana, która zawiera implementację wcześniej wymienionych funkcji.

W tym przykładzie `NativeMethods` Klasa zawiera zarządzane prototypy dla metod `TestCallBack` i. `TestCallBack2` Obie metody przekażą delegata do funkcji wywołania zwrotnego jako parametr. Podpis delegata musi być zgodny z podpisem metody, do której się odwołuje. Na przykład Delegaty `FPtr` i `FPtr2` mają podpisy identyczne z metodami `DoSomething` i. `DoSomething2`

## <a name="declaring-prototypes"></a>Deklarowanie prototypów
[!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
[!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
[!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]

## <a name="calling-functions"></a>Wywoływanie funkcji
[!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
[!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
[!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]

## <a name="see-also"></a>Zobacz też

- [Różne przykłady organizowania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))
- [Typy danych wywołania platformy](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [Tworzenie prototypów w kodzie zarządzanym](creating-prototypes-in-managed-code.md)
