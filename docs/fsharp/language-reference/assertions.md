---
title: Potwierdzenia
description: Dowiedz się, jak używać wyrażenia "Assert" jako funkcji debugowania do testowania wyrażeń w języku F# programowania.
ms.date: 10/22/2019
ms.openlocfilehash: 430db20e5ca307ba43a72e678a0424e03b0ac381
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799065"
---
# <a name="assertions"></a><span data-ttu-id="9a620-103">Potwierdzenia</span><span class="sxs-lookup"><span data-stu-id="9a620-103">Assertions</span></span>

<span data-ttu-id="9a620-104">Wyrażenie `assert` jest funkcją debugowania, której można użyć do przetestowania wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="9a620-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="9a620-105">W przypadku niepowodzenia w trybie debugowania potwierdzenie generuje okno dialogowe błędu systemu.</span><span class="sxs-lookup"><span data-stu-id="9a620-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="9a620-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a620-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="9a620-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a620-107">Remarks</span></span>

<span data-ttu-id="9a620-108">Wyrażenie `assert` ma `bool -> unit`typu.</span><span class="sxs-lookup"><span data-stu-id="9a620-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="9a620-109">Funkcja `assert` jest rozpoznawana jako <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9a620-109">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9a620-110">Oznacza to, że jego zachowanie jest takie samo jak wywołanie <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="9a620-110">This means its behavior is identical to having called <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> directly.</span></span>

<span data-ttu-id="9a620-111">Sprawdzanie potwierdzenia jest włączone tylko w przypadku kompilowania w trybie debugowania. oznacza to, że jeśli stała `DEBUG` jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="9a620-111">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="9a620-112">Domyślnie w systemie projektu stała `DEBUG` jest definiowana w konfiguracji debugowania, ale nie w konfiguracji wydania.</span><span class="sxs-lookup"><span data-stu-id="9a620-112">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="9a620-113">Błąd potwierdzenia nie może zostać przechwycony przy użyciu F# obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="9a620-113">The assertion failure error cannot be caught by using F# exception handling.</span></span>

## <a name="example"></a><span data-ttu-id="9a620-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a620-114">Example</span></span>

<span data-ttu-id="9a620-115">Poniższy przykład kodu ilustruje użycie wyrażenia `assert`.</span><span class="sxs-lookup"><span data-stu-id="9a620-115">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a><span data-ttu-id="9a620-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a620-116">See also</span></span>

- [<span data-ttu-id="9a620-117">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="9a620-117">F# Language Reference</span></span>](index.md)
