---
title: Współdziałanie wyjątków
ms.date: 01/16/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- interop, exceptions
- exceptions, interop
ms.openlocfilehash: 2aff71e97e1be0dbb584f4fe43c322cea86d2480
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76795176"
---
# <a name="working-with-interop-exceptions-in-unmanaged-code"></a><span data-ttu-id="cb1a2-102">Praca z wyjątkami międzyoperacyjnymi w kodzie niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="cb1a2-102">Working with Interop Exceptions in Unmanaged Code</span></span>

<span data-ttu-id="cb1a2-103">Międzyoperacyjność wyjątku kodu niezarządzanego jest obsługiwana tylko na platformach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="cb1a2-103">Unmanaged code exception interop is supported on Windows platforms only.</span></span> <span data-ttu-id="cb1a2-104">Problemy z przenośnością powstają na platformach innych niż Windows.</span><span class="sxs-lookup"><span data-stu-id="cb1a2-104">Portability issues arise on non-Windows platforms.</span></span> <span data-ttu-id="cb1a2-105">Ponieważ ABI systemu UNIX nie ma definicji obsługi wyjątków, kod zarządzany nie może wiedzieć, jak mechanizmy wyjątków działają w ramach okładek.</span><span class="sxs-lookup"><span data-stu-id="cb1a2-105">Since the Unix ABI has no definition for exception handling, managed code can't know how exception mechanisms work under the covers.</span></span> <span data-ttu-id="cb1a2-106">W związku z tym wyjątki mogą kończyć się wynikiem nieprzewidywalnych zachowań i awarii.</span><span class="sxs-lookup"><span data-stu-id="cb1a2-106">Therefore, exceptions can end up resulting in unpredictable behaviors and crashes.</span></span>

## <a name="setjmplongjmp-behaviors"></a><span data-ttu-id="cb1a2-107">Zachowania setjmp/longjmp</span><span class="sxs-lookup"><span data-stu-id="cb1a2-107">Setjmp/Longjmp Behaviors</span></span>

<span data-ttu-id="cb1a2-108">Współdziałanie z funkcjami `setjmp` i `longjmp` języka C nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="cb1a2-108">Interop with `setjmp` and `longjmp` C functions is not supported.</span></span> <span data-ttu-id="cb1a2-109">Nie można użyć `longjmp`, aby pominąć ramki zarządzane.</span><span class="sxs-lookup"><span data-stu-id="cb1a2-109">You can't use `longjmp` to skip over managed frames.</span></span>

<span data-ttu-id="cb1a2-110">Aby uzyskać więcej informacji, zobacz [dokumentację longjmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/longjmp).</span><span class="sxs-lookup"><span data-stu-id="cb1a2-110">For more information, see [longjmp documentation](https://docs.microsoft.com/cpp/c-runtime-library/reference/longjmp).</span></span>

## <a name="see-also"></a><span data-ttu-id="cb1a2-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb1a2-111">See also</span></span>

- [<span data-ttu-id="cb1a2-112">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="cb1a2-112">Exceptions</span></span>](index.md)
- [<span data-ttu-id="cb1a2-113">Współdziałanie z natywnymi bibliotekami</span><span class="sxs-lookup"><span data-stu-id="cb1a2-113">Interop with Native Libraries</span></span>](https://www.mono-project.com/docs/advanced/pinvoke/#runtime-exception-propagation)
