---
title: 'Kopiowanie i aktualizację wyrażenia rekordów (F #)'
description: Dowiedz się, jak napisać określone pola "Kopiuj i Aktualizuj rekordu wyrażenia" który kopiuje istniejących rekordów, aktualizacji i zwraca zaktualizowany rekord.
author: ChrSteinert
ms.author: phcart
ms.date: 06/04/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 98a515b5f053e9339588157185848e8315a580f4
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="a26dd-103">Kopiowanie i aktualizację wyrażenia rekordów</span><span class="sxs-lookup"><span data-stu-id="a26dd-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="a26dd-104">A *kopiowanie i aktualizację wyrażenia rekordu* jest wyrażenie, które kopiuje istniejącego rekordu, aktualizuje określone pola i zwraca zaktualizowany rekord.</span><span class="sxs-lookup"><span data-stu-id="a26dd-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>


## <a name="syntax"></a><span data-ttu-id="a26dd-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a26dd-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a><span data-ttu-id="a26dd-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a26dd-106">Remarks</span></span>
<span data-ttu-id="a26dd-107">Rekordy są niezmienne domyślnie, dzięki czemu możliwe jest Brak aktualizacji do istniejącego rekordu.</span><span class="sxs-lookup"><span data-stu-id="a26dd-107">Records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="a26dd-108">Aby utworzyć rekord zaktualizowane wszystkie pola rekordu musi mieścić się ponownie.</span><span class="sxs-lookup"><span data-stu-id="a26dd-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="a26dd-109">Aby uprościć zadanie *kopiowanie i aktualizację wyrażenia rekordu* mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="a26dd-109">To simplify this task a *copy and update record expression* can be used.</span></span> <span data-ttu-id="a26dd-110">To wyrażenie ma istniejącego rekordu, tworzy nową tego samego typu przy użyciu określonego pola z wyrażenia i brakujące pole określona przez wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="a26dd-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>
<span data-ttu-id="a26dd-111">Może to być przydatne, gdy trzeba skopiować istniejącego rekordu i prawdopodobnie zmieniają niektóre wartości pól.</span><span class="sxs-lookup"><span data-stu-id="a26dd-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="a26dd-112">Na przykład zająć nowo utworzony rekord.</span><span class="sxs-lookup"><span data-stu-id="a26dd-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="a26dd-113">Jeśli masz zamiar aktualizacji tylko na pola rekordu można użyć *kopiowanie i aktualizację wyrażenia rekordu* podobnie do następującego:</span><span class="sxs-lookup"><span data-stu-id="a26dd-113">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="a26dd-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a26dd-114">See Also</span></span>
[<span data-ttu-id="a26dd-115">Rekordy</span><span class="sxs-lookup"><span data-stu-id="a26dd-115">Records</span></span>](records.md)

[<span data-ttu-id="a26dd-116">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="a26dd-116">F# Language Reference</span></span>](index.md)
