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
# <a name="external-functions"></a><span data-ttu-id="3ffc2-103">Funkcje zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="3ffc2-103">External Functions</span></span>

<span data-ttu-id="3ffc2-104">W tym temacie F# opisano obsługę języka na potrzeby wywoływania funkcji w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="3ffc2-104">This topic describes F# language support for calling functions in native code.</span></span>

## <a name="syntax"></a><span data-ttu-id="3ffc2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ffc2-105">Syntax</span></span>

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a><span data-ttu-id="3ffc2-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3ffc2-106">Remarks</span></span>

<span data-ttu-id="3ffc2-107">W poprzedniej składni *argumenty* reprezentują argumenty, które są dostarczone do `System.Runtime.InteropServices.DllImportAttribute` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="3ffc2-107">In the previous syntax, *arguments* represents arguments that are supplied to the `System.Runtime.InteropServices.DllImportAttribute` attribute.</span></span> <span data-ttu-id="3ffc2-108">Pierwszy argument jest ciągiem, który reprezentuje nazwę biblioteki DLL, która zawiera tę funkcję, bez rozszerzenia dll.</span><span class="sxs-lookup"><span data-stu-id="3ffc2-108">The first argument is a string that represents the name of the DLL that contains this function, without the .dll extension.</span></span> <span data-ttu-id="3ffc2-109">Dodatkowe argumenty można dostarczyć dla którejkolwiek z właściwości `System.Runtime.InteropServices.DllImportAttribute` publicznych klasy, takich jak Konwencja wywoływania.</span><span class="sxs-lookup"><span data-stu-id="3ffc2-109">Additional arguments can be supplied for any of the public properties of the `System.Runtime.InteropServices.DllImportAttribute` class, such as the calling convention.</span></span>

<span data-ttu-id="3ffc2-110">Załóżmy, że masz natywną C++ bibliotekę DLL, która zawiera następującą wyeksportowaną funkcję.</span><span class="sxs-lookup"><span data-stu-id="3ffc2-110">Assume you have a native C++ DLL that contains the following exported function.</span></span>

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

<span data-ttu-id="3ffc2-111">Można wywołać tę funkcję z F# programu przy użyciu następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="3ffc2-111">You can call this function from F# by using the following code.</span></span>

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

<span data-ttu-id="3ffc2-112">Współdziałanie z kodem natywnym jest określane jako *wywołanie platformy* i jest funkcją środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="3ffc2-112">Interoperability with native code is referred to as *platform invoke* and is a feature of the CLR.</span></span> <span data-ttu-id="3ffc2-113">Aby uzyskać więcej informacji, zobacz Współdziałanie [z kodem](../../../framework/interop/index.md)niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="3ffc2-113">For more information, see [Interoperating with Unmanaged Code](../../../framework/interop/index.md).</span></span> <span data-ttu-id="3ffc2-114">Informacje zawarte w tej sekcji dotyczą programu F#.</span><span class="sxs-lookup"><span data-stu-id="3ffc2-114">The information in that section is applicable to F#.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ffc2-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ffc2-115">See also</span></span>

- [<span data-ttu-id="3ffc2-116">Funkcje</span><span class="sxs-lookup"><span data-stu-id="3ffc2-116">Functions</span></span>](index.md)
