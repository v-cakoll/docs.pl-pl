---
title: Potwierdzenia
description: Dowiedz się, jak użyć wyrażenia "Potwierdź" jako funkcja debugowania do testowania wyrażeń w F# języka programowania.
ms.date: 05/16/2016
ms.openlocfilehash: c2d97386e87e9b915da490a78fff9aedb9def616
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703221"
---
# <a name="assertions"></a><span data-ttu-id="ffd59-103">Potwierdzenia</span><span class="sxs-lookup"><span data-stu-id="ffd59-103">Assertions</span></span>

<span data-ttu-id="ffd59-104">`assert` Wyrażenie jest funkcją debugowania, można użyć w celu przetestowania wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="ffd59-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="ffd59-105">W przypadku awarii w trybie debugowania potwierdzenie generuje okno dialogowe błędu systemu.</span><span class="sxs-lookup"><span data-stu-id="ffd59-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="ffd59-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ffd59-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="ffd59-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ffd59-107">Remarks</span></span>

<span data-ttu-id="ffd59-108">`assert` Wyrażenie zawiera typ `bool -> unit`.</span><span class="sxs-lookup"><span data-stu-id="ffd59-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="ffd59-109">W poprzedniej składni *warunek* reprezentuje wyrażenie logiczne, które ma zostać przetestowana.</span><span class="sxs-lookup"><span data-stu-id="ffd59-109">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="ffd59-110">Jeśli wyrażenie ma `true`, wykonywanie jest kontynuowane bez zmian.</span><span class="sxs-lookup"><span data-stu-id="ffd59-110">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="ffd59-111">Jeśli daje w wyniku `false`, generowany jest okno dialogowe błędu systemu.</span><span class="sxs-lookup"><span data-stu-id="ffd59-111">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="ffd59-112">Okno dialogowe błędu ma podpis, który zawiera ciąg **potwierdzenie nie powiodło się**.</span><span class="sxs-lookup"><span data-stu-id="ffd59-112">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="ffd59-113">Okno dialogowe zawiera ślad stosu, która wskazuje, gdzie wystąpił błąd asercji.</span><span class="sxs-lookup"><span data-stu-id="ffd59-113">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="ffd59-114">Sprawdzanie potwierdzenia jest włączone, tylko wtedy, gdy kompilujesz w trybie debugowania; oznacza to jeśli stała `DEBUG` jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="ffd59-114">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="ffd59-115">W systemie projektu, domyślnie `DEBUG` stała jest zdefiniowany w konfiguracji debugowania, ale nie w konfiguracji wydania.</span><span class="sxs-lookup"><span data-stu-id="ffd59-115">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="ffd59-116">Błąd potwierdzenia nie można przechwycić za pomocą F# obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="ffd59-116">The assertion failure error cannot be caught by using F# exception handling.</span></span>

> [!NOTE]
> <span data-ttu-id="ffd59-117">`assert` Funkcji jest rozpoznawane jako <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ffd59-117">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="ffd59-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="ffd59-118">Example</span></span>

<span data-ttu-id="ffd59-119">Poniższy przykład kodu ilustruje użycie `assert` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="ffd59-119">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a><span data-ttu-id="ffd59-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ffd59-120">See also</span></span>

- [<span data-ttu-id="ffd59-121">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="ffd59-121">F# Language Reference</span></span>](index.md)