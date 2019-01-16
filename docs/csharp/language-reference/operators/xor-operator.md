---
title: ^ — operator - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
ms.openlocfilehash: 152be2d81d1bf340b839d74f169d63d7260f7ca5
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333710"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="79068-102">^ — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="79068-102">^ operator (C# Reference)</span></span>

<span data-ttu-id="79068-103">Operatory binarne `^` są wstępnie zdefiniowane dla typów całkowitych i `bool`.</span><span class="sxs-lookup"><span data-stu-id="79068-103">Binary `^` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="79068-104">W przypadku typów całkowitych `^` oblicza bitową alternatywę rozłączną dla operandu.</span><span class="sxs-lookup"><span data-stu-id="79068-104">For integral types, `^` computes the bitwise exclusive-OR of its operands.</span></span> <span data-ttu-id="79068-105">Dla operacji na zmiennych typu `bool` `^` oblicza alternatywę rozłączną dla jej argumentów. Wynik jest `true` tylko wtedy, gdy dokładnie jeden z argumentów to `true`.</span><span class="sxs-lookup"><span data-stu-id="79068-105">For `bool` operands, `^` computes the logical exclusive-or of its operands; that is, the result is `true` if and only if exactly one of its operands is `true`.</span></span>

## <a name="remarks"></a><span data-ttu-id="79068-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="79068-106">Remarks</span></span>

<span data-ttu-id="79068-107">Typy definiowane przez użytkownika mogą przeciążać operator `^` — (zobacz [operator](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="79068-107">User-defined types can overload the `^` operator (see [operator](../keywords/operator.md)).</span></span> <span data-ttu-id="79068-108">Operacje na typach całkowitych w wyliczeniach są zazwyczaj dozwolone.</span><span class="sxs-lookup"><span data-stu-id="79068-108">Operations on integral types are generally allowed on enumeration.</span></span>

## <a name="example"></a><span data-ttu-id="79068-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="79068-109">Example</span></span>

[!code-csharp[csRefOperators#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#30)]

<span data-ttu-id="79068-110">Obliczenie `0xf8 ^ 0x3f` w poprzednim przykładzie powoduje wykonanie bitowej operacji wyłącznej OR na następnych dwóch wartościach binarnych, które odpowiadają wartościom szesnastkowym F8 i 3F:</span><span class="sxs-lookup"><span data-stu-id="79068-110">The computation of `0xf8 ^ 0x3f` in the previous example performs a bitwise exclusive-OR of the following two binary values, which correspond to the hexadecimal values F8 and 3F:</span></span>

`1111 1000`

`0011 1111`

<span data-ttu-id="79068-111">Wynik alternatywy rozłącznej to `1100 0111`, czyli C7 w formacie szesnastkowym.</span><span class="sxs-lookup"><span data-stu-id="79068-111">The result of the exclusive-OR is `1100 0111`, which is C7 in hexadecimal.</span></span>

## <a name="see-also"></a><span data-ttu-id="79068-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="79068-112">See Also</span></span>

- [<span data-ttu-id="79068-113">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="79068-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="79068-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="79068-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="79068-115">C#Operatory</span><span class="sxs-lookup"><span data-stu-id="79068-115">C# operators</span></span>](index.md)
