---
title: "Funkcje zewnętrzne (F#)"
description: "Dowiedz się więcej na temat obsługi języka F # na wywoływanie funkcji w kodzie natywnym."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c26b6124-ceaa-471c-9dc9-861b4dfa332a
ms.openlocfilehash: 4f525b2b750c2ce42230c61aa0e72f957739b206
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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

Współdziałanie z kodem natywnym jest określany jako *wywołanie platformy* funkcja środowiska CLR. Aby uzyskać więcej informacji, zobacz [współdziałanie z kodem niezarządzanym](https://msdn.microsoft.com/library/sd10k43k.aspx). Informacje przedstawione w tej sekcji ma zastosowanie do F #.


## <a name="see-also"></a>Zobacz też

[Funkcje](index.md)
