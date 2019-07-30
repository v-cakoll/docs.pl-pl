---
title: Potwierdzenia
description: Dowiedz się, jak używać wyrażenia "Assert" jako funkcji debugowania do testowania wyrażeń w języku F# programowania.
ms.date: 05/16/2016
ms.openlocfilehash: b8b7e9662143b432d650f87515d4af31cced4149
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630025"
---
# <a name="assertions"></a><span data-ttu-id="7d1ee-103">Potwierdzenia</span><span class="sxs-lookup"><span data-stu-id="7d1ee-103">Assertions</span></span>

<span data-ttu-id="7d1ee-104">`assert` Wyrażenie jest funkcją debugowania, której można użyć do przetestowania wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="7d1ee-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="7d1ee-105">W przypadku niepowodzenia w trybie debugowania potwierdzenie generuje okno dialogowe błędu systemu.</span><span class="sxs-lookup"><span data-stu-id="7d1ee-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="7d1ee-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d1ee-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="7d1ee-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d1ee-107">Remarks</span></span>

<span data-ttu-id="7d1ee-108">Wyrażenie ma typ `bool -> unit`. `assert`</span><span class="sxs-lookup"><span data-stu-id="7d1ee-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="7d1ee-109">W poprzedniej składni *warunek* reprezentuje wyrażenie logiczne, które ma zostać przetestowane.</span><span class="sxs-lookup"><span data-stu-id="7d1ee-109">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="7d1ee-110">Jeśli wyrażenie zwróci wartość `true`, wykonanie nie będzie miało żadnych zmian.</span><span class="sxs-lookup"><span data-stu-id="7d1ee-110">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="7d1ee-111">Jeśli zostanie obliczona `false`wartość, zostanie wygenerowane okno dialogowe błędu systemu.</span><span class="sxs-lookup"><span data-stu-id="7d1ee-111">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="7d1ee-112">Okno dialogowe błędu zawiera podpis zawierający **potwierdzenie ciągu nie powiodło się**.</span><span class="sxs-lookup"><span data-stu-id="7d1ee-112">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="7d1ee-113">Okno dialogowe zawiera ślad stosu, który wskazuje, gdzie wystąpił błąd potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="7d1ee-113">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="7d1ee-114">Sprawdzanie potwierdzenia jest włączone tylko w przypadku kompilowania w trybie debugowania. oznacza to, że jeśli stała `DEBUG` jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="7d1ee-114">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="7d1ee-115">Domyślnie w systemie projektu `DEBUG` stała jest definiowana w konfiguracji debugowania, ale nie w konfiguracji wydania.</span><span class="sxs-lookup"><span data-stu-id="7d1ee-115">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="7d1ee-116">Błąd potwierdzenia nie może zostać przechwycony przy użyciu F# obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="7d1ee-116">The assertion failure error cannot be caught by using F# exception handling.</span></span>

> [!NOTE]
> <span data-ttu-id="7d1ee-117">Funkcja `assert` jest<xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>rozpoznawana jako.</span><span class="sxs-lookup"><span data-stu-id="7d1ee-117">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="7d1ee-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d1ee-118">Example</span></span>

<span data-ttu-id="7d1ee-119">Poniższy przykład kodu ilustruje użycie `assert` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="7d1ee-119">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a><span data-ttu-id="7d1ee-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d1ee-120">See also</span></span>

- [<span data-ttu-id="7d1ee-121">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="7d1ee-121">F# Language Reference</span></span>](index.md)
