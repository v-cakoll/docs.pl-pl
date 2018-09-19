---
title: 'Kopiowanie i aktualizacja wyrażeń rekordów (F #)'
description: Dowiedz się, jak napisać "Kopiuj i Aktualizuj rekordu wyrażenia" istniejących aktualizacji rekordu, kopiuje określone pola i zwraca zaktualizowanym rekordem.
author: ChrSteinert
ms.date: 06/04/2016
ms.openlocfilehash: d2b089e8a7fc5c7ee26139003e23d2eaa8a3174e
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "45990846"
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="323fd-103">Kopiowanie i aktualizacja wyrażeń rekordów</span><span class="sxs-lookup"><span data-stu-id="323fd-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="323fd-104">A *kopiowanie i aktualizacja wyrażeń rekordów* jest wyrażeniem, które kopiuje istniejący rekord, aktualizuje określone pola i zwraca zaktualizowanym rekordem.</span><span class="sxs-lookup"><span data-stu-id="323fd-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>

## <a name="syntax"></a><span data-ttu-id="323fd-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="323fd-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a><span data-ttu-id="323fd-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="323fd-106">Remarks</span></span>

<span data-ttu-id="323fd-107">Rekordy są niezmienne domyślnie, tak aby była możliwa ma aktualizacji istniejącego rekordu.</span><span class="sxs-lookup"><span data-stu-id="323fd-107">Records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="323fd-108">Aby utworzyć rekord zaktualizowano wszystkie pola rekordu musi można określić ponownie.</span><span class="sxs-lookup"><span data-stu-id="323fd-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="323fd-109">Aby ułatwić to zadanie *kopiowanie i aktualizacja wyrażeń rekordów* mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="323fd-109">To simplify this task a *copy and update record expression* can be used.</span></span> <span data-ttu-id="323fd-110">To wyrażenie ma istniejącego rekordu, tworzy nową tego samego typu przy użyciu określone pola z wyrażenia i brakujące pole określona przez wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="323fd-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>
<span data-ttu-id="323fd-111">Może to być przydatne, gdy trzeba skopiować istniejący rekord, a być może zmienić niektóre wartości pól.</span><span class="sxs-lookup"><span data-stu-id="323fd-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="323fd-112">Na przykład potrwać nowo utworzony rekord.</span><span class="sxs-lookup"><span data-stu-id="323fd-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="323fd-113">Gdyby można zaktualizować tylko na pole tego rekordu można użyć *kopiowanie i aktualizacja wyrażeń rekordów* podobnie do następującego:</span><span class="sxs-lookup"><span data-stu-id="323fd-113">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="323fd-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="323fd-114">See also</span></span>

- [<span data-ttu-id="323fd-115">Rekordy</span><span class="sxs-lookup"><span data-stu-id="323fd-115">Records</span></span>](records.md)
- [<span data-ttu-id="323fd-116">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="323fd-116">F# Language Reference</span></span>](index.md)
