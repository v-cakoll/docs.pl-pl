---
title: Potwierdzenia (F#)
description: 'Dowiedz się, jak używać wyrażeń "Potwierdź" jako funkcja debugowania do testowania wyrażenia w języku programowania F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 85b1e839bfd19bada48b7f1821d15ddd8fa77754
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48034313"
---
# <a name="assertions"></a><span data-ttu-id="dfbcb-103">Potwierdzenia</span><span class="sxs-lookup"><span data-stu-id="dfbcb-103">Assertions</span></span>

<span data-ttu-id="dfbcb-104">`assert` Wyrażenie jest funkcją debugowania, można użyć w celu przetestowania wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="dfbcb-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="dfbcb-105">W przypadku awarii w trybie debugowania potwierdzenie generuje okno dialogowe błędu systemu.</span><span class="sxs-lookup"><span data-stu-id="dfbcb-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="dfbcb-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="dfbcb-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="dfbcb-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dfbcb-107">Remarks</span></span>

<span data-ttu-id="dfbcb-108">`assert` Wyrażenie zawiera typ `bool -> unit`.</span><span class="sxs-lookup"><span data-stu-id="dfbcb-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="dfbcb-109">W poprzedniej składni *warunek* reprezentuje wyrażenie logiczne, które ma zostać przetestowana.</span><span class="sxs-lookup"><span data-stu-id="dfbcb-109">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="dfbcb-110">Jeśli wyrażenie ma `true`, wykonywanie jest kontynuowane bez zmian.</span><span class="sxs-lookup"><span data-stu-id="dfbcb-110">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="dfbcb-111">Jeśli daje w wyniku `false`, generowany jest okno dialogowe błędu systemu.</span><span class="sxs-lookup"><span data-stu-id="dfbcb-111">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="dfbcb-112">Okno dialogowe błędu ma podpis, który zawiera ciąg **potwierdzenie nie powiodło się**.</span><span class="sxs-lookup"><span data-stu-id="dfbcb-112">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="dfbcb-113">Okno dialogowe zawiera ślad stosu, która wskazuje, gdzie wystąpił błąd asercji.</span><span class="sxs-lookup"><span data-stu-id="dfbcb-113">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="dfbcb-114">Sprawdzanie potwierdzenia jest włączone, tylko wtedy, gdy kompilujesz w trybie debugowania; oznacza to jeśli stała `DEBUG` jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="dfbcb-114">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="dfbcb-115">W systemie projektu, domyślnie `DEBUG` stała jest zdefiniowany w konfiguracji debugowania, ale nie w konfiguracji wydania.</span><span class="sxs-lookup"><span data-stu-id="dfbcb-115">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="dfbcb-116">Błąd potwierdzenia nie można przechwycić za pomocą obsługi wyjątków w języku F #.</span><span class="sxs-lookup"><span data-stu-id="dfbcb-116">The assertion failure error cannot be caught by using F# exception handling.</span></span>

>[!NOTE]
<span data-ttu-id="dfbcb-117">`assert` Funkcji jest rozpoznawane jako <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dfbcb-117">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="dfbcb-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="dfbcb-118">Example</span></span>

<span data-ttu-id="dfbcb-119">Poniższy przykład kodu ilustruje użycie `assert` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="dfbcb-119">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a><span data-ttu-id="dfbcb-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dfbcb-120">See also</span></span>

- [<span data-ttu-id="dfbcb-121">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="dfbcb-121">F# Language Reference</span></span>](index.md)
