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
ms.openlocfilehash: 2fc265e4a7ceec291d645346bb012e2ed4600d22
ms.sourcegitcommit: 5c2176883dc3107445702724a7caa7ac2f6cb0d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2019
ms.locfileid: "58890387"
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a>Marshaling delegata jako metoda wywołania zwrotnego
Niniejszy przykład pokazuje sposób przekazywania delegatów do niezarządzanej funkcji, oczekiwano wskaźników funkcji. Delegat to klasa, która może zawierać odwołanie do metody i jest równoważny wskaźnikowi funkcji bezpiecznego typu lub funkcji wywołania zwrotnego.

> [!NOTE]
>  Gdy używasz delegata w wywołaniu, środowisko uruchomieniowe języka wspólnego chroni delegata jako elementu bezużytecznego zebrane na czas trwania wywołania. Jednak jeśli delegata do użycia po ukończeniu wywołania są przechowywane w funkcji niezarządzanej, trzeba ręcznie chronić wyrzucania elementów bezużytecznych zakończenie niezarządzanej funkcji z obiektem delegowanym. Aby uzyskać więcej informacji, zobacz [HandleRef — przykład](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) i [GCHandle — przykład](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).

Przykład wywołania zwrotnego używa następujących funkcji niezarządzanych, wyświetlane wraz z ich oryginalną deklaracją funkcji:

-   `TestCallBack` exported from PinvokeLib.dll.

    ```cpp
    void TestCallBack(FPTR pf, int value);
    ```

-   `TestCallBack2` exported from PinvokeLib.dll.

    ```cpp
    void TestCallBack2(FPTR2 pf2, char* value);
    ```

[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) jest niestandardową biblioteką niezarządzaną, która zawiera implementację wyżej wymienionych funkcji.

W tym przykładzie `LibWrap` klasa zawiera zarządzane prototypy `TestCallBack` i `TestCallBack2` metody. Obie metody przekazać delegata do funkcji wywołania zwrotnego, jako parametr. Podpis delegata musi odpowiadać podpisowi metody, do którego się odwołuje. Na przykład `FPtr` i `FPtr2` delegatów opatrzone sygnaturami, które są takie same jak `DoSomething` i `DoSomething2` metody.

## <a name="declaring-prototypes"></a>Deklarowanie prototypów
[!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
[!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
[!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]

## <a name="calling-functions"></a>Wywoływanie funkcji
[!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
[!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
[!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]

## <a name="see-also"></a>Zobacz także
- [Różne przykłady organizowania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))
- [Typy danych w wywołaniu platformy](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [Tworzenie prototypów w kodzie zarządzanym](creating-prototypes-in-managed-code.md)
