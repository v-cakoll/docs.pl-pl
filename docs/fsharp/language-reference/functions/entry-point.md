---
title: Punkt wejścia
description: Dowiedz się, jak ustawić punkt wejścia do F# programu, który jest kompilowany jako plik wykonywalny, gdzie wykonywanie zostanie rozpoczęte.
ms.date: 05/16/2016
ms.openlocfilehash: 5e13416131d4dfd22583439fedf51f18f7a461da
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630522"
---
# <a name="entry-point"></a><span data-ttu-id="c6f51-103">Punkt wejścia</span><span class="sxs-lookup"><span data-stu-id="c6f51-103">Entry Point</span></span>

<span data-ttu-id="c6f51-104">W tym temacie opisano metodę, która służy do ustawiania punktu wejścia do F# programu.</span><span class="sxs-lookup"><span data-stu-id="c6f51-104">This topic describes the method that you use to set the entry point to an F# program.</span></span>

## <a name="syntax"></a><span data-ttu-id="c6f51-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c6f51-105">Syntax</span></span>

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a><span data-ttu-id="c6f51-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c6f51-106">Remarks</span></span>

<span data-ttu-id="c6f51-107">W poprzedniej składni, *Let-Function-Binding* jest definicją funkcji w `let` powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="c6f51-107">In the previous syntax, *let-function-binding* is the definition of a function in a `let` binding.</span></span>

<span data-ttu-id="c6f51-108">Punkt wejścia do programu, który jest kompilowany jako plik wykonywalny, to miejsce, w którym wykonywanie jest uruchamiane od początku.</span><span class="sxs-lookup"><span data-stu-id="c6f51-108">The entry point to a program that is compiled as an executable file is where execution formally starts.</span></span> <span data-ttu-id="c6f51-109">Należy określić punkt wejścia do F# aplikacji przez zastosowanie `EntryPoint` atrybutu `main` do funkcji programu.</span><span class="sxs-lookup"><span data-stu-id="c6f51-109">You specify the entry point to an F# application by applying the `EntryPoint` attribute to the program's `main` function.</span></span> <span data-ttu-id="c6f51-110">Ta funkcja (utworzona przy użyciu `let` powiązania) musi być ostatnią funkcją w ostatnim skompilowanym pliku.</span><span class="sxs-lookup"><span data-stu-id="c6f51-110">This function (created by using a `let` binding) must be the last function in the last compiled file.</span></span> <span data-ttu-id="c6f51-111">Ostatni skompilowany plik to ostatni plik w projekcie lub ostatni plik, który jest przesyłany do wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="c6f51-111">The last compiled file is the last file in the project or the last file that is passed to the command line.</span></span>

<span data-ttu-id="c6f51-112">Funkcja punktu wejścia ma typ `string array -> int`.</span><span class="sxs-lookup"><span data-stu-id="c6f51-112">The entry point function has type `string array -> int`.</span></span> <span data-ttu-id="c6f51-113">Argumenty podane w wierszu polecenia są przekazywane do `main` funkcji w tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="c6f51-113">The arguments provided on the command line are passed to the `main` function in the array of strings.</span></span> <span data-ttu-id="c6f51-114">Pierwszy element tablicy jest pierwszym argumentem; Nazwa pliku wykonywalnego nie jest uwzględniona w tablicy, ponieważ znajduje się w innych językach.</span><span class="sxs-lookup"><span data-stu-id="c6f51-114">The first element of the array is the first argument; the name of the executable file is not included in the array, as it is in some other languages.</span></span> <span data-ttu-id="c6f51-115">Wartość zwracana jest używana jako kod zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="c6f51-115">The return value is used as the exit code for the process.</span></span> <span data-ttu-id="c6f51-116">Wartość zerowa zazwyczaj oznacza sukces; wartości niezerowe wskazują na błąd.</span><span class="sxs-lookup"><span data-stu-id="c6f51-116">Zero usually indicates success; nonzero values indicate an error.</span></span> <span data-ttu-id="c6f51-117">Nie ma Konwencji dla określonego znaczenia niezerowych kodów powrotu; znaczenie kodów powrotu jest specyficzne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c6f51-117">There is no convention for the specific meaning of nonzero return codes; the meanings of the return codes are application-specific.</span></span>

<span data-ttu-id="c6f51-118">Poniższy przykład ilustruje prostą `main` funkcję.</span><span class="sxs-lookup"><span data-stu-id="c6f51-118">The following example illustrates a simple `main` function.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/entry-point/snippet501.fs)]

<span data-ttu-id="c6f51-119">Gdy ten kod jest wykonywany z wierszem `EntryPoint.exe 1 2 3`polecenia, dane wyjściowe są następujące.</span><span class="sxs-lookup"><span data-stu-id="c6f51-119">When this code is executed with the command line `EntryPoint.exe 1 2 3`, the output is as follows.</span></span>

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a><span data-ttu-id="c6f51-120">Niejawny punkt wejścia</span><span class="sxs-lookup"><span data-stu-id="c6f51-120">Implicit Entry Point</span></span>

<span data-ttu-id="c6f51-121">Gdy program nie ma atrybutu **EntryPoint** , który jawnie wskazuje punkt wejścia, powiązania najwyższego poziomu w ostatnim pliku do skompilowania są używane jako punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="c6f51-121">When a program has no **EntryPoint** attribute that explicitly indicates the entry point, the top level bindings in the last file to be compiled are used as the entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6f51-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c6f51-122">See also</span></span>

- [<span data-ttu-id="c6f51-123">Funkcje</span><span class="sxs-lookup"><span data-stu-id="c6f51-123">Functions</span></span>](index.md)
- [<span data-ttu-id="c6f51-124">Powiązania „let”</span><span class="sxs-lookup"><span data-stu-id="c6f51-124">let Bindings</span></span>](let-bindings.md)
