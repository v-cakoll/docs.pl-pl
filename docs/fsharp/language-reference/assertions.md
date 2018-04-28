---
title: Potwierdzenia (F#)
description: 'Dowiedz się, jak użyć wyrażenia "assert" jako funkcja debugowania do testowania wyrażenia w języku programowania w języku F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 195b4a34977a63d92559003b5cd0bb89490a1e7a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="assertions"></a><span data-ttu-id="54790-103">Potwierdzenia</span><span class="sxs-lookup"><span data-stu-id="54790-103">Assertions</span></span>

<span data-ttu-id="54790-104">`assert` Wyrażenie jest funkcja debugowania, którego można używać do testowania wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="54790-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="54790-105">W przypadku awarii w trybie debugowania potwierdzenia generuje okno dialogowe błędu systemu.</span><span class="sxs-lookup"><span data-stu-id="54790-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="54790-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="54790-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="54790-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54790-107">Remarks</span></span>

<span data-ttu-id="54790-108">`assert` Wyrażenie zawiera typ `bool -> unit`.</span><span class="sxs-lookup"><span data-stu-id="54790-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="54790-109">W poprzednich składni *warunku* reprezentuje wyrażenie logiczne, która ma zostać przetestowana.</span><span class="sxs-lookup"><span data-stu-id="54790-109">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="54790-110">Jeśli wyrażenie ma `true`, wykonywanie będzie kontynuowane bez zmian.</span><span class="sxs-lookup"><span data-stu-id="54790-110">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="54790-111">Jeśli daje w wyniku `false`, generowany jest okno dialogowe błędu systemu.</span><span class="sxs-lookup"><span data-stu-id="54790-111">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="54790-112">Okno dialogowe błąd ma podpis zawierający ciąg **nie powiodła się Asercja**.</span><span class="sxs-lookup"><span data-stu-id="54790-112">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="54790-113">Okno dialogowe zawiera ślad stosu, który wskazuje, w którym wystąpił błąd potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="54790-113">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="54790-114">Sprawdzanie potwierdzenia jest włączone tylko wtedy, gdy kompilacja w trybie debugowania; oznacza to, że jeśli stała `DEBUG` jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="54790-114">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="54790-115">W systemie projektu, domyślnie `DEBUG` stała jest zdefiniowany w konfiguracji debugowania, ale nie w konfiguracji wydanie.</span><span class="sxs-lookup"><span data-stu-id="54790-115">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="54790-116">Błąd Błąd potwierdzenia nie można przechwycić przy użyciu obsługi wyjątków F #.</span><span class="sxs-lookup"><span data-stu-id="54790-116">The assertion failure error cannot be caught by using F# exception handling.</span></span>

>[!NOTE]
<span data-ttu-id="54790-117">`assert` Rozpoznawany jako funkcja <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="54790-117">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="54790-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="54790-118">Example</span></span>

<span data-ttu-id="54790-119">W poniższym przykładzie przedstawiono użycie `assert` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="54790-119">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]
    
## <a name="see-also"></a><span data-ttu-id="54790-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54790-120">See Also</span></span>

[<span data-ttu-id="54790-121">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="54790-121">F# Language Reference</span></span>](index.md)
