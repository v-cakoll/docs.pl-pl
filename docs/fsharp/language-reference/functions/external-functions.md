---
title: Funkcje zewnętrzne (F#)
description: 'Dowiedz się więcej na temat obsługi języka F # na wywoływanie funkcji w kodzie natywnym.'
ms.date: 05/16/2016
ms.openlocfilehash: 398697c5e0deab7f8d81ec5198ab1918bd865e13
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564485"
---
# <a name="external-functions"></a><span data-ttu-id="b23a5-103">Funkcje zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="b23a5-103">External Functions</span></span>

<span data-ttu-id="b23a5-104">W tym temacie opisano obsługę języka F # dla wywoływanie funkcji w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="b23a5-104">This topic describes F# language support for calling functions in native code.</span></span>

## <a name="syntax"></a><span data-ttu-id="b23a5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b23a5-105">Syntax</span></span>

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a><span data-ttu-id="b23a5-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b23a5-106">Remarks</span></span>

<span data-ttu-id="b23a5-107">W poprzednich składni *argumenty* reprezentuje argumenty, które są dostarczane do `System.Runtime.InteropServices.DllImportAttribute` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b23a5-107">In the previous syntax, *arguments* represents arguments that are supplied to the `System.Runtime.InteropServices.DllImportAttribute` attribute.</span></span> <span data-ttu-id="b23a5-108">Pierwszy argument jest ciąg reprezentujący nazwę biblioteki DLL zawierającej tej funkcji bez rozszerzenia dll.</span><span class="sxs-lookup"><span data-stu-id="b23a5-108">The first argument is a string that represents the name of the DLL that contains this function, without the .dll extension.</span></span> <span data-ttu-id="b23a5-109">Dodatkowe argumenty mogą być dostarczane w każdej publicznej właściwości `System.Runtime.InteropServices.DllImportAttribute` klasy, takie jak konwencję wywołania.</span><span class="sxs-lookup"><span data-stu-id="b23a5-109">Additional arguments can be supplied for any of the public properties of the `System.Runtime.InteropServices.DllImportAttribute` class, such as the calling convention.</span></span>

<span data-ttu-id="b23a5-110">Załóżmy, że masz natywne biblioteki DLL języka C++, która zawiera następujące wyeksportowanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="b23a5-110">Assume you have a native C++ DLL that contains the following exported function.</span></span>

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

<span data-ttu-id="b23a5-111">Tę funkcję można wywołać z F # przy użyciu następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="b23a5-111">You can call this function from F# by using the following code.</span></span>

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

<span data-ttu-id="b23a5-112">Współdziałanie z kodem natywnym jest określany jako *wywołanie platformy* funkcja środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="b23a5-112">Interoperability with native code is referred to as *platform invoke* and is a feature of the CLR.</span></span> <span data-ttu-id="b23a5-113">Aby uzyskać więcej informacji, zobacz [współdziałanie z kodem niezarządzanym](../../../../docs/framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="b23a5-113">For more information, see [Interoperating with Unmanaged Code](../../../../docs/framework/interop/index.md).</span></span> <span data-ttu-id="b23a5-114">Informacje przedstawione w tej sekcji ma zastosowanie do F #.</span><span class="sxs-lookup"><span data-stu-id="b23a5-114">The information in that section is applicable to F#.</span></span>


## <a name="see-also"></a><span data-ttu-id="b23a5-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b23a5-115">See Also</span></span>

[<span data-ttu-id="b23a5-116">Funkcje</span><span class="sxs-lookup"><span data-stu-id="b23a5-116">Functions</span></span>](index.md)
