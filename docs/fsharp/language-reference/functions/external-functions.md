---
title: Funkcje zewnętrzne
description: Dowiedz się więcej o F# Obsługa języków w programie wywoływanie funkcji w kodzie natywnym.
ms.date: 05/16/2016
ms.openlocfilehash: 86ea78844fb812361233f8360c377465d83be203
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611734"
---
# <a name="external-functions"></a>Funkcje zewnętrzne

W tym temacie opisano F# Obsługa języków w programie wywoływanie funkcji w kodzie natywnym.

## <a name="syntax"></a>Składnia

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a>Uwagi

W poprzedniej składni *argumenty* reprezentuje argumenty, które są dostarczane do `System.Runtime.InteropServices.DllImportAttribute` atrybutu. Pierwszy argument jest ciąg reprezentujący nazwę pliku dll, który zawiera tej funkcji bez rozszerzenie dll. Dodatkowe argumenty mogą być podawane dla każdej właściwości publicznej `System.Runtime.InteropServices.DllImportAttribute` klasę, takie jak konwencji wywoływania.

Załóżmy, że masz natywne biblioteki DLL C++, który zawiera następujące wyeksportowanej funkcji.

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

Możesz wywołać tę funkcję z F# przy użyciu następującego kodu.

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

Współdziałanie z kodem natywnym nazywa się *wywołania platformy* funkcja środowiska CLR. Aby uzyskać więcej informacji, zobacz [współdziałanie z kodem niezarządzanym](../../../../docs/framework/interop/index.md). Informacje przedstawione w tej sekcji ma zastosowanie do F#.

## <a name="see-also"></a>Zobacz także

- [Funkcje](index.md)