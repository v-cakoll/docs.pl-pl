---
title: Funkcje zewnętrzne
description: Dowiedz się więcej o F# Obsługa języków w programie wywoływanie funkcji w kodzie natywnym.
ms.date: 05/16/2016
ms.openlocfilehash: 86ea78844fb812361233f8360c377465d83be203
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934631"
---
# <a name="external-functions"></a><span data-ttu-id="c2f33-103">Funkcje zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="c2f33-103">External Functions</span></span>

<span data-ttu-id="c2f33-104">W tym temacie opisano F# Obsługa języków w programie wywoływanie funkcji w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="c2f33-104">This topic describes F# language support for calling functions in native code.</span></span>

## <a name="syntax"></a><span data-ttu-id="c2f33-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2f33-105">Syntax</span></span>

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a><span data-ttu-id="c2f33-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c2f33-106">Remarks</span></span>

<span data-ttu-id="c2f33-107">W poprzedniej składni *argumenty* reprezentuje argumenty, które są dostarczane do `System.Runtime.InteropServices.DllImportAttribute` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c2f33-107">In the previous syntax, *arguments* represents arguments that are supplied to the `System.Runtime.InteropServices.DllImportAttribute` attribute.</span></span> <span data-ttu-id="c2f33-108">Pierwszy argument jest ciąg reprezentujący nazwę pliku dll, który zawiera tej funkcji bez rozszerzenie dll.</span><span class="sxs-lookup"><span data-stu-id="c2f33-108">The first argument is a string that represents the name of the DLL that contains this function, without the .dll extension.</span></span> <span data-ttu-id="c2f33-109">Dodatkowe argumenty mogą być podawane dla każdej właściwości publicznej `System.Runtime.InteropServices.DllImportAttribute` klasę, takie jak konwencji wywoływania.</span><span class="sxs-lookup"><span data-stu-id="c2f33-109">Additional arguments can be supplied for any of the public properties of the `System.Runtime.InteropServices.DllImportAttribute` class, such as the calling convention.</span></span>

<span data-ttu-id="c2f33-110">Załóżmy, że masz natywne biblioteki DLL C++, który zawiera następujące wyeksportowanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="c2f33-110">Assume you have a native C++ DLL that contains the following exported function.</span></span>

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

<span data-ttu-id="c2f33-111">Możesz wywołać tę funkcję z F# przy użyciu następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="c2f33-111">You can call this function from F# by using the following code.</span></span>

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

<span data-ttu-id="c2f33-112">Współdziałanie z kodem natywnym nazywa się *wywołania platformy* funkcja środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="c2f33-112">Interoperability with native code is referred to as *platform invoke* and is a feature of the CLR.</span></span> <span data-ttu-id="c2f33-113">Aby uzyskać więcej informacji, zobacz [współdziałanie z kodem niezarządzanym](../../../../docs/framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="c2f33-113">For more information, see [Interoperating with Unmanaged Code](../../../../docs/framework/interop/index.md).</span></span> <span data-ttu-id="c2f33-114">Informacje przedstawione w tej sekcji ma zastosowanie do F#.</span><span class="sxs-lookup"><span data-stu-id="c2f33-114">The information in that section is applicable to F#.</span></span>

## <a name="see-also"></a><span data-ttu-id="c2f33-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2f33-115">See also</span></span>

- [<span data-ttu-id="c2f33-116">Funkcje</span><span class="sxs-lookup"><span data-stu-id="c2f33-116">Functions</span></span>](index.md)