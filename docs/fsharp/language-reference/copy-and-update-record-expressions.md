---
title: Kopiowanie i aktualizacja wyrażeń rekordów
description: Dowiedz się, jak napisać wyrażenie "kopiuj i aktualizuj" kopiuje istniejący rekord lub rekord anonimowy, aktualizuje określone pola i zwraca zaktualizowany rekord lub rekord anonimowy.
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: bec3e0ac2fb34e358b199c509c4599b55d7bf35e
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739286"
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="2fa6f-103">Kopiowanie i aktualizacja wyrażeń rekordów</span><span class="sxs-lookup"><span data-stu-id="2fa6f-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="2fa6f-104">*Wyrażenie kopiowania i aktualizowania rekordu* jest wyrażeniem, które kopiuje istniejący rekord, aktualizuje określone pola i zwraca zaktualizowany rekord.</span><span class="sxs-lookup"><span data-stu-id="2fa6f-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>

## <a name="syntax"></a><span data-ttu-id="2fa6f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2fa6f-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a><span data-ttu-id="2fa6f-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2fa6f-106">Remarks</span></span>

<span data-ttu-id="2fa6f-107">Rekordy i rekordy anonimowe są domyślnie niezmienne, więc nie można zaktualizować istniejącego rekordu.</span><span class="sxs-lookup"><span data-stu-id="2fa6f-107">Records and anonymous records are immutable by default, so it is not possible to update an existing record.</span></span> <span data-ttu-id="2fa6f-108">Aby utworzyć zaktualizowany rekord, wszystkie pola rekordu musiałyby zostać ponownie określone.</span><span class="sxs-lookup"><span data-stu-id="2fa6f-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="2fa6f-109">Aby uprościć to zadanie, można użyć *wyrażenia kopiowania i aktualizacji.*</span><span class="sxs-lookup"><span data-stu-id="2fa6f-109">To simplify this task a *copy and update expression* can be used.</span></span> <span data-ttu-id="2fa6f-110">To wyrażenie przyjmuje istniejący rekord, tworzy nowy tego samego typu przy użyciu określonych pól z wyrażenia i brakujące pole określone przez wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="2fa6f-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>

<span data-ttu-id="2fa6f-111">Może to być przydatne, gdy trzeba skopiować istniejący rekord i ewentualnie zmienić niektóre wartości pól.</span><span class="sxs-lookup"><span data-stu-id="2fa6f-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="2fa6f-112">Weźmy na przykład nowo utworzony rekord.</span><span class="sxs-lookup"><span data-stu-id="2fa6f-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="2fa6f-113">Aby zaktualizować tylko dwa pola w tym rekordzie, można użyć *wyrażenia rekordu kopiowania i aktualizowania:*</span><span class="sxs-lookup"><span data-stu-id="2fa6f-113">To update only two fields in that record you can use the *copy and update record expression*:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="2fa6f-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2fa6f-114">See also</span></span>

- [<span data-ttu-id="2fa6f-115">Rekordy</span><span class="sxs-lookup"><span data-stu-id="2fa6f-115">Records</span></span>](records.md)
- [<span data-ttu-id="2fa6f-116">Rekordy anonimowe</span><span class="sxs-lookup"><span data-stu-id="2fa6f-116">Anonymous Records</span></span>](anonymous-records.md)
- [<span data-ttu-id="2fa6f-117">Odwołanie do języka F#</span><span class="sxs-lookup"><span data-stu-id="2fa6f-117">F# Language Reference</span></span>](index.md)
