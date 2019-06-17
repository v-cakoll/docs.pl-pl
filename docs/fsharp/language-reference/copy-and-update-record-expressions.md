---
title: Kopiowanie i aktualizacja wyrażeń rekordów
description: Dowiedz się, jak pisać "Kopiuj i Aktualizuj wyrażenia" kopiuje istniejącego rekordu lub rekordów anonimowe, aktualizacje określone pola i zwraca zaktualizowanym rekordem lub anonimowe rekordu.
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: d16f5ca337047ab2eecc8828b21d8a423bf39a1f
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041730"
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="b5b8a-103">Kopiowanie i aktualizacja wyrażeń rekordów</span><span class="sxs-lookup"><span data-stu-id="b5b8a-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="b5b8a-104">A *kopiowanie i aktualizacja wyrażeń rekordów* jest wyrażeniem, które kopiuje istniejący rekord, aktualizuje określone pola i zwraca zaktualizowanym rekordem.</span><span class="sxs-lookup"><span data-stu-id="b5b8a-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>

## <a name="syntax"></a><span data-ttu-id="b5b8a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5b8a-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a><span data-ttu-id="b5b8a-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b5b8a-106">Remarks</span></span>

<span data-ttu-id="b5b8a-107">Rekordów i rekordów anonimowe są niezmienne domyślnie, dzięki czemu możliwe nie ma aktualizacji istniejącego rekordu.</span><span class="sxs-lookup"><span data-stu-id="b5b8a-107">Records and anonymous records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="b5b8a-108">Aby utworzyć rekord zaktualizowano wszystkie pola rekordu musi można określić ponownie.</span><span class="sxs-lookup"><span data-stu-id="b5b8a-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="b5b8a-109">Aby ułatwić to zadanie *Kopiuj i Aktualizuj wyrażenie* mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="b5b8a-109">To simplify this task a *copy and update expression* can be used.</span></span> <span data-ttu-id="b5b8a-110">To wyrażenie ma istniejącego rekordu, tworzy nową tego samego typu przy użyciu określone pola z wyrażenia i brakujące pole określona przez wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="b5b8a-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>

<span data-ttu-id="b5b8a-111">Może to być przydatne, gdy trzeba skopiować istniejący rekord, a być może zmienić niektóre wartości pól.</span><span class="sxs-lookup"><span data-stu-id="b5b8a-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="b5b8a-112">Na przykład potrwać nowo utworzony rekord.</span><span class="sxs-lookup"><span data-stu-id="b5b8a-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="b5b8a-113">Gdyby można zaktualizować tylko na pole tego rekordu można użyć *kopiowanie i aktualizacja wyrażeń rekordów* podobnie do następującego:</span><span class="sxs-lookup"><span data-stu-id="b5b8a-113">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="b5b8a-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5b8a-114">See also</span></span>

- [<span data-ttu-id="b5b8a-115">Rekordy</span><span class="sxs-lookup"><span data-stu-id="b5b8a-115">Records</span></span>](records.md)
- [<span data-ttu-id="b5b8a-116">Rekordy anonimowe</span><span class="sxs-lookup"><span data-stu-id="b5b8a-116">Anonymous Records</span></span>](anonymous-records.md)
- [<span data-ttu-id="b5b8a-117">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="b5b8a-117">F# Language Reference</span></span>](index.md)
