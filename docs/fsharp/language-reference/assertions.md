---
title: Potwierdzenia (F#)
description: "Dowiedz się, jak użyć wyrażenia \"assert\" jako funkcja debugowania do testowania wyrażenia w języku programowania w języku F #."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2badaad7-f086-47e7-99c1-91f35117da83
ms.openlocfilehash: 56891769602afaa765ebfe7e7822a179c7a22968
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="assertions"></a><span data-ttu-id="78586-104">Potwierdzenia</span><span class="sxs-lookup"><span data-stu-id="78586-104">Assertions</span></span>

<span data-ttu-id="78586-105">`assert` Wyrażenie jest funkcja debugowania, którego można używać do testowania wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="78586-105">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="78586-106">W przypadku awarii w trybie debugowania potwierdzenia generuje okno dialogowe błędu systemu.</span><span class="sxs-lookup"><span data-stu-id="78586-106">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="78586-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="78586-107">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="78586-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="78586-108">Remarks</span></span>

<span data-ttu-id="78586-109">`assert` Wyrażenie zawiera typ `bool -> unit`.</span><span class="sxs-lookup"><span data-stu-id="78586-109">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="78586-110">W poprzednich składni *warunku* reprezentuje wyrażenie logiczne, która ma zostać przetestowana.</span><span class="sxs-lookup"><span data-stu-id="78586-110">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="78586-111">Jeśli wyrażenie ma `true`, wykonywanie będzie kontynuowane bez zmian.</span><span class="sxs-lookup"><span data-stu-id="78586-111">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="78586-112">Jeśli daje w wyniku `false`, generowany jest okno dialogowe błędu systemu.</span><span class="sxs-lookup"><span data-stu-id="78586-112">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="78586-113">Okno dialogowe błąd ma podpis zawierający ciąg **nie powiodła się Asercja**.</span><span class="sxs-lookup"><span data-stu-id="78586-113">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="78586-114">Okno dialogowe zawiera ślad stosu, który wskazuje, w którym wystąpił błąd potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="78586-114">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="78586-115">Sprawdzanie potwierdzenia jest włączone tylko wtedy, gdy kompilacja w trybie debugowania; oznacza to, że jeśli stała `DEBUG` jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="78586-115">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="78586-116">W systemie projektu, domyślnie `DEBUG` stała jest zdefiniowany w konfiguracji debugowania, ale nie w konfiguracji wydanie.</span><span class="sxs-lookup"><span data-stu-id="78586-116">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="78586-117">Błąd Błąd potwierdzenia nie można przechwycić przy użyciu obsługi wyjątków F #.</span><span class="sxs-lookup"><span data-stu-id="78586-117">The assertion failure error cannot be caught by using F# exception handling.</span></span>

>[!NOTE]
<span data-ttu-id="78586-118">`assert` Rozpoznawany jako funkcja <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="78586-118">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="78586-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="78586-119">Example</span></span>

<span data-ttu-id="78586-120">W poniższym przykładzie przedstawiono użycie `assert` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="78586-120">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]
    
## <a name="see-also"></a><span data-ttu-id="78586-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="78586-121">See Also</span></span>

[<span data-ttu-id="78586-122">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="78586-122">F# Language Reference</span></span>](index.md)
