---
title: Funkcje zewnętrzne
description: Dowiedz się F# więcej o obsłudze języka dla wywoływania funkcji w kodzie natywnym.
ms.date: 05/16/2016
ms.openlocfilehash: 3c8edaba25e07b6ca2c44a58c4b55dc98a13b4fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968730"
---
# <a name="external-functions"></a>Funkcje zewnętrzne

W tym temacie F# opisano obsługę języka na potrzeby wywoływania funkcji w kodzie natywnym.

## <a name="syntax"></a>Składnia

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a>Uwagi

W poprzedniej składni *argumenty* reprezentują argumenty, które są dostarczone do `System.Runtime.InteropServices.DllImportAttribute` atrybutu. Pierwszy argument jest ciągiem, który reprezentuje nazwę biblioteki DLL, która zawiera tę funkcję, bez rozszerzenia dll. Dodatkowe argumenty można dostarczyć dla którejkolwiek z właściwości `System.Runtime.InteropServices.DllImportAttribute` publicznych klasy, takich jak Konwencja wywoływania.

Załóżmy, że masz natywną C++ bibliotekę DLL, która zawiera następującą wyeksportowaną funkcję.

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

Można wywołać tę funkcję z F# programu przy użyciu następującego kodu.

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

Współdziałanie z kodem natywnym jest określane jako *wywołanie platformy* i jest funkcją środowiska CLR. Aby uzyskać więcej informacji, zobacz Współdziałanie [z kodem](../../../framework/interop/index.md)niezarządzanym. Informacje zawarte w tej sekcji dotyczą programu F#.

## <a name="see-also"></a>Zobacz także

- [Funkcje](index.md)
