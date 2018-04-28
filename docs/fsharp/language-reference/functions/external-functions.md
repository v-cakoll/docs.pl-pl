---
title: Funkcje zewnętrzne (F#)
description: 'Dowiedz się więcej na temat obsługi języka F # na wywoływanie funkcji w kodzie natywnym.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 28e74258d91ff2d9742caa7a6c06f515cd987c0a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="external-functions"></a>Funkcje zewnętrzne

W tym temacie opisano obsługę języka F # dla wywoływanie funkcji w kodzie natywnym.

## <a name="syntax"></a>Składnia

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a>Uwagi

W poprzednich składni *argumenty* reprezentuje argumenty, które są dostarczane do `System.Runtime.InteropServices.DllImportAttribute` atrybutu. Pierwszy argument jest ciąg reprezentujący nazwę biblioteki DLL zawierającej tej funkcji bez rozszerzenia dll. Dodatkowe argumenty mogą być dostarczane w każdej publicznej właściwości `System.Runtime.InteropServices.DllImportAttribute` klasy, takie jak konwencję wywołania.

Załóżmy, że masz natywne biblioteki DLL języka C++, która zawiera następujące wyeksportowanej funkcji.

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

Tę funkcję można wywołać z F # przy użyciu następującego kodu.

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

Współdziałanie z kodem natywnym jest określany jako *wywołanie platformy* funkcja środowiska CLR. Aby uzyskać więcej informacji, zobacz [współdziałanie z kodem niezarządzanym](../../../../docs/framework/interop/index.md). Informacje przedstawione w tej sekcji ma zastosowanie do F #.


## <a name="see-also"></a>Zobacz też

[Funkcje](index.md)
