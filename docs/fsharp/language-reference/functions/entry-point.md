---
title: Punkt wejścia
description: Dowiedz się, jak ustawić punkt wejścia F# program, który jest kompilowany jako plik wykonywalny, gdzie formalnie się rozpoczyna wykonywanie.
ms.date: 05/16/2016
ms.openlocfilehash: c7aedda5834fb224507bfcecd4688978efa26547
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645453"
---
# <a name="entry-point"></a><span data-ttu-id="3c39c-103">Punkt wejścia</span><span class="sxs-lookup"><span data-stu-id="3c39c-103">Entry Point</span></span>

<span data-ttu-id="3c39c-104">W tym temacie opisano metody, która służy do ustawiania punkt wejścia F# program.</span><span class="sxs-lookup"><span data-stu-id="3c39c-104">This topic describes the method that you use to set the entry point to an F# program.</span></span>

## <a name="syntax"></a><span data-ttu-id="3c39c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c39c-105">Syntax</span></span>

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a><span data-ttu-id="3c39c-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3c39c-106">Remarks</span></span>

<span data-ttu-id="3c39c-107">W poprzedniej składni *umożliwiają funkcji wiązania* definicję funkcji w `let` powiązania.</span><span class="sxs-lookup"><span data-stu-id="3c39c-107">In the previous syntax, *let-function-binding* is the definition of a function in a `let` binding.</span></span>

<span data-ttu-id="3c39c-108">Punkt wejścia do programu, który jest kompilowany jako plik wykonywalny jest, gdzie formalnie się rozpoczyna wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="3c39c-108">The entry point to a program that is compiled as an executable file is where execution formally starts.</span></span> <span data-ttu-id="3c39c-109">Określ punkt wejścia do F# aplikacji, stosując `EntryPoint` atrybutu programu `main` funkcji.</span><span class="sxs-lookup"><span data-stu-id="3c39c-109">You specify the entry point to an F# application by applying the `EntryPoint` attribute to the program's `main` function.</span></span> <span data-ttu-id="3c39c-110">Tej funkcji (utworzone za pomocą `let` powiązania) musi być ostatniej funkcji ostatniego pliku skompilowany.</span><span class="sxs-lookup"><span data-stu-id="3c39c-110">This function (created by using a `let` binding) must be the last function in the last compiled file.</span></span> <span data-ttu-id="3c39c-111">Ostatnie skompilowanego pliku jest ostatni plik w projekcie lub ostatni plik, który jest przekazywany do wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="3c39c-111">The last compiled file is the last file in the project or the last file that is passed to the command line.</span></span>

<span data-ttu-id="3c39c-112">Funkcja punktu wejścia ma typ `string array -> int`.</span><span class="sxs-lookup"><span data-stu-id="3c39c-112">The entry point function has type `string array -> int`.</span></span> <span data-ttu-id="3c39c-113">Argumenty dostarczone w wierszu polecenia są przekazywane do `main` funkcji w tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="3c39c-113">The arguments provided on the command line are passed to the `main` function in the array of strings.</span></span> <span data-ttu-id="3c39c-114">Pierwszy element tablicy jest pierwszym argumentem; Nazwa pliku wykonywalnego nie znajduje się w tablicy, w przeciwieństwie do innych języków.</span><span class="sxs-lookup"><span data-stu-id="3c39c-114">The first element of the array is the first argument; the name of the executable file is not included in the array, as it is in some other languages.</span></span> <span data-ttu-id="3c39c-115">Wartość zwracana jest używany jako kod zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="3c39c-115">The return value is used as the exit code for the process.</span></span> <span data-ttu-id="3c39c-116">Wartość zero wskazuje zwykle sukcesu; niezerowe wartości wskazywać na błąd.</span><span class="sxs-lookup"><span data-stu-id="3c39c-116">Zero usually indicates success; nonzero values indicate an error.</span></span> <span data-ttu-id="3c39c-117">Istnieje nie Konwencji szczególne znaczenie wartość różną od zera kody powrotne; znaczenie kody powrotne są specyficzne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3c39c-117">There is no convention for the specific meaning of nonzero return codes; the meanings of the return codes are application-specific.</span></span>

<span data-ttu-id="3c39c-118">W poniższym przykładzie pokazano prosty `main` funkcji.</span><span class="sxs-lookup"><span data-stu-id="3c39c-118">The following example illustrates a simple `main` function.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

<span data-ttu-id="3c39c-119">Kiedy ten kod jest wykonywany przy użyciu wiersza polecenia `EntryPoint.exe 1 2 3`, dane wyjściowe wyglądają następująco.</span><span class="sxs-lookup"><span data-stu-id="3c39c-119">When this code is executed with the command line `EntryPoint.exe 1 2 3`, the output is as follows.</span></span>

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a><span data-ttu-id="3c39c-120">Niejawne punktu wejścia</span><span class="sxs-lookup"><span data-stu-id="3c39c-120">Implicit Entry Point</span></span>

<span data-ttu-id="3c39c-121">Jeśli nie ma programu **punktu wejścia** atrybutu, która wyraźnie wskazuje punkt wejścia, powiązania najwyższego poziomu ostatniego pliku do skompilowania służą jako punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="3c39c-121">When a program has no **EntryPoint** attribute that explicitly indicates the entry point, the top level bindings in the last file to be compiled are used as the entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c39c-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3c39c-122">See also</span></span>

- [<span data-ttu-id="3c39c-123">Funkcje</span><span class="sxs-lookup"><span data-stu-id="3c39c-123">Functions</span></span>](index.md)
- [<span data-ttu-id="3c39c-124">Powiązania „let”</span><span class="sxs-lookup"><span data-stu-id="3c39c-124">let Bindings</span></span>](let-bindings.md)
