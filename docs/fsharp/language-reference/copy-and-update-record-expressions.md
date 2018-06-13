---
title: 'Kopiowanie i aktualizację wyrażenia rekordów (F #)'
description: Dowiedz się, jak napisać określone pola "Kopiuj i Aktualizuj rekordu wyrażenia" który kopiuje istniejących rekordów, aktualizacji i zwraca zaktualizowany rekord.
author: ChrSteinert
ms.date: 06/04/2016
ms.openlocfilehash: 000746b6e76349ae6d8f338519a58034f4e29020
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563062"
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="8b2ad-103">Kopiowanie i aktualizację wyrażenia rekordów</span><span class="sxs-lookup"><span data-stu-id="8b2ad-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="8b2ad-104">A *kopiowanie i aktualizację wyrażenia rekordu* jest wyrażenie, które kopiuje istniejącego rekordu, aktualizuje określone pola i zwraca zaktualizowany rekord.</span><span class="sxs-lookup"><span data-stu-id="8b2ad-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>


## <a name="syntax"></a><span data-ttu-id="8b2ad-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b2ad-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a><span data-ttu-id="8b2ad-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b2ad-106">Remarks</span></span>
<span data-ttu-id="8b2ad-107">Rekordy są niezmienne domyślnie, dzięki czemu możliwe jest Brak aktualizacji do istniejącego rekordu.</span><span class="sxs-lookup"><span data-stu-id="8b2ad-107">Records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="8b2ad-108">Aby utworzyć rekord zaktualizowane wszystkie pola rekordu musi mieścić się ponownie.</span><span class="sxs-lookup"><span data-stu-id="8b2ad-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="8b2ad-109">Aby uprościć zadanie *kopiowanie i aktualizację wyrażenia rekordu* mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="8b2ad-109">To simplify this task a *copy and update record expression* can be used.</span></span> <span data-ttu-id="8b2ad-110">To wyrażenie ma istniejącego rekordu, tworzy nową tego samego typu przy użyciu określonego pola z wyrażenia i brakujące pole określona przez wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="8b2ad-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>
<span data-ttu-id="8b2ad-111">Może to być przydatne, gdy trzeba skopiować istniejącego rekordu i prawdopodobnie zmieniają niektóre wartości pól.</span><span class="sxs-lookup"><span data-stu-id="8b2ad-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="8b2ad-112">Na przykład zająć nowo utworzony rekord.</span><span class="sxs-lookup"><span data-stu-id="8b2ad-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="8b2ad-113">Jeśli masz zamiar aktualizacji tylko na pola rekordu można użyć *kopiowanie i aktualizację wyrażenia rekordu* podobnie do następującego:</span><span class="sxs-lookup"><span data-stu-id="8b2ad-113">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="8b2ad-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b2ad-114">See Also</span></span>
[<span data-ttu-id="8b2ad-115">Rekordy</span><span class="sxs-lookup"><span data-stu-id="8b2ad-115">Records</span></span>](records.md)

[<span data-ttu-id="8b2ad-116">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="8b2ad-116">F# Language Reference</span></span>](index.md)
