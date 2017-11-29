---
title: "Kopiowanie i aktualizację wyrażenia rekordów (F #)"
description: "Dowiedz się, jak napisać określone pola \"Kopiuj i Aktualizuj rekordu wyrażenia\" który kopiuje istniejących rekordów, aktualizacji i zwraca zaktualizowany rekord."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: ChrSteinert
ms.author: phcart
ms.date: 06/04/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b5fc4ef0-64eb-4272-96a7-bb4dffbb634a
ms.openlocfilehash: 2eb51842b678780a1d6da96e237ebb92d1ea5cec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="f24c0-104">Kopiowanie i aktualizację wyrażenia rekordów</span><span class="sxs-lookup"><span data-stu-id="f24c0-104">Copy and Update Record Expressions</span></span>

<span data-ttu-id="f24c0-105">A *kopiowanie i aktualizację wyrażenia rekordu* jest wyrażenie, które kopiuje istniejącego rekordu, aktualizuje określone pola i zwraca zaktualizowany rekord.</span><span class="sxs-lookup"><span data-stu-id="f24c0-105">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>


## <a name="syntax"></a><span data-ttu-id="f24c0-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f24c0-106">Syntax</span></span>

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a><span data-ttu-id="f24c0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f24c0-107">Remarks</span></span>
<span data-ttu-id="f24c0-108">Rekordy są niezmienne domyślnie, dzięki czemu możliwe jest Brak aktualizacji do istniejącego rekordu.</span><span class="sxs-lookup"><span data-stu-id="f24c0-108">Records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="f24c0-109">Aby utworzyć rekord zaktualizowane wszystkie pola rekordu musi mieścić się ponownie.</span><span class="sxs-lookup"><span data-stu-id="f24c0-109">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="f24c0-110">Aby uprościć zadanie *kopiowanie i aktualizację wyrażenia rekordu* mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="f24c0-110">To simplify this task a *copy and update record expression* can be used.</span></span> <span data-ttu-id="f24c0-111">To wyrażenie ma istniejącego rekordu, tworzy nową tego samego typu przy użyciu określonego pola z wyrażenia i brakujące pole określona przez wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="f24c0-111">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>
<span data-ttu-id="f24c0-112">Może to być przydatne, gdy trzeba skopiować istniejącego rekordu i prawdopodobnie zmieniają niektóre wartości pól.</span><span class="sxs-lookup"><span data-stu-id="f24c0-112">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="f24c0-113">Na przykład zająć nowo utworzony rekord.</span><span class="sxs-lookup"><span data-stu-id="f24c0-113">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="f24c0-114">Jeśli masz zamiar aktualizacji tylko na pola rekordu można użyć *kopiowanie i aktualizację wyrażenia rekordu* podobnie do następującego:</span><span class="sxs-lookup"><span data-stu-id="f24c0-114">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="f24c0-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f24c0-115">See Also</span></span>
[<span data-ttu-id="f24c0-116">Rekordy</span><span class="sxs-lookup"><span data-stu-id="f24c0-116">Records</span></span>](records.md)

[<span data-ttu-id="f24c0-117">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="f24c0-117">F# Language Reference</span></span>](index.md)
