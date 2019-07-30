---
title: Kopiowanie i aktualizacja wyrażeń rekordów
description: Dowiedz się, jak napisać "Copy and Update Expression", który kopiuje istniejący rekord lub rekord anonimowy, aktualizuje określone pola i zwraca zaktualizowany rekord lub rekord anonimowy.
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: dfb20a6ff8282ae5988772cc0f0841db23aad942
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630380"
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="3d594-103">Kopiowanie i aktualizacja wyrażeń rekordów</span><span class="sxs-lookup"><span data-stu-id="3d594-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="3d594-104">*Wyrażenie Copy and Update Record* jest wyrażeniem, które kopiuje istniejący rekord, aktualizuje określone pola i zwraca zaktualizowany rekord.</span><span class="sxs-lookup"><span data-stu-id="3d594-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>

## <a name="syntax"></a><span data-ttu-id="3d594-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3d594-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a><span data-ttu-id="3d594-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3d594-106">Remarks</span></span>

<span data-ttu-id="3d594-107">Rekordy i rekordy anonimowe są domyślnie niezmienne, dlatego nie ma możliwości aktualizacji istniejącego rekordu.</span><span class="sxs-lookup"><span data-stu-id="3d594-107">Records and anonymous records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="3d594-108">Aby utworzyć zaktualizowany rekord, należy ponownie określić wszystkie pola rekordu.</span><span class="sxs-lookup"><span data-stu-id="3d594-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="3d594-109">Aby uprościć to zadanie, można użyć *wyrażenia kopiowania i aktualizowania* .</span><span class="sxs-lookup"><span data-stu-id="3d594-109">To simplify this task a *copy and update expression* can be used.</span></span> <span data-ttu-id="3d594-110">To wyrażenie przyjmuje istniejący rekord, tworzy nowy jeden z tego samego typu przy użyciu określonych pól z wyrażenia i brakującego pola określonego przez wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="3d594-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>

<span data-ttu-id="3d594-111">Może to być przydatne, gdy konieczne jest skopiowanie istniejącego rekordu i prawdopodobnie zmiana niektórych wartości pól.</span><span class="sxs-lookup"><span data-stu-id="3d594-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="3d594-112">Zrób wystąpienie nowo utworzonego rekordu.</span><span class="sxs-lookup"><span data-stu-id="3d594-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="3d594-113">Jeśli aktualizacja dotyczy tylko pola tego rekordu, można użyć *wyrażenia Kopiuj i Aktualizuj rekord* w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3d594-113">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="3d594-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d594-114">See also</span></span>

- [<span data-ttu-id="3d594-115">Rekordy</span><span class="sxs-lookup"><span data-stu-id="3d594-115">Records</span></span>](records.md)
- [<span data-ttu-id="3d594-116">Rekordy anonimowe</span><span class="sxs-lookup"><span data-stu-id="3d594-116">Anonymous Records</span></span>](anonymous-records.md)
- [<span data-ttu-id="3d594-117">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="3d594-117">F# Language Reference</span></span>](index.md)
