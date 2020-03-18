---
title: void — odwołanie do języka C#
ms.date: 02/11/2020
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: c6c1c28e3d7a53a1dcadcf50d8d7f42c8c8aeee4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846214"
---
# <a name="void-c-reference"></a><span data-ttu-id="fd841-102">void (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="fd841-102">void (C# reference)</span></span>

<span data-ttu-id="fd841-103">Jako `void` typ zwracany [metody](../../programming-guide/classes-and-structs/methods.md) (lub [funkcji lokalnej)](../../programming-guide/classes-and-structs/local-functions.md)można określić, że metoda nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="fd841-103">You use `void` as the return type of a [method](../../programming-guide/classes-and-structs/methods.md) (or a [local function](../../programming-guide/classes-and-structs/local-functions.md)) to specify that the method doesn't return a value.</span></span>

[!code-csharp[void method](snippets/VoidType.cs#VoidExample)]

<span data-ttu-id="fd841-104">Można również `void` użyć jako typ referent do deklarowania wskaźnik a nieznany typ.</span><span class="sxs-lookup"><span data-stu-id="fd841-104">You can also use `void` as a referent type to declare a pointer to an unknown type.</span></span> <span data-ttu-id="fd841-105">Aby uzyskać więcej informacji, zobacz [Typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="fd841-105">For more information, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="fd841-106">Nie można `void` użyć jako typu zmiennej.</span><span class="sxs-lookup"><span data-stu-id="fd841-106">You cannot use `void` as the type of a variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd841-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd841-107">See also</span></span>

- [<span data-ttu-id="fd841-108">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="fd841-108">C# reference</span></span>](../index.md)
- <xref:System.Void?displayProperty=nameWithType>
