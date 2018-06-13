---
title: Punkt wejścia (F#)
description: 'Dowiedz się, jak ustawić punkt wejścia do programu F # jest skompilowany, ponieważ plik wykonywalny, gdzie wykonywanie formalnie uruchamiana.'
ms.date: 05/16/2016
ms.openlocfilehash: 3d6cab755dd89f2d3d669a8763aa08660432a0ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563623"
---
# <a name="entry-point"></a><span data-ttu-id="1ef72-103">Punkt wejścia</span><span class="sxs-lookup"><span data-stu-id="1ef72-103">Entry Point</span></span>

<span data-ttu-id="1ef72-104">W tym temacie opisano metody, która służy do ustawiania punktu wejścia do programu F #.</span><span class="sxs-lookup"><span data-stu-id="1ef72-104">This topic describes the method that you use to set the entry point to an F# program.</span></span>


## <a name="syntax"></a><span data-ttu-id="1ef72-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ef72-105">Syntax</span></span>

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a><span data-ttu-id="1ef72-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ef72-106">Remarks</span></span>
<span data-ttu-id="1ef72-107">W poprzednich składni *let funkcji wiązania* znajduje się definicja funkcji w `let` powiązania.</span><span class="sxs-lookup"><span data-stu-id="1ef72-107">In the previous syntax, *let-function-binding* is the definition of a function in a `let` binding.</span></span>

<span data-ttu-id="1ef72-108">Punkt wejścia do programu, który ma być kompilowana jako plik wykonywalny jest, gdzie formalnie rozpoczyna się wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="1ef72-108">The entry point to a program that is compiled as an executable file is where execution formally starts.</span></span> <span data-ttu-id="1ef72-109">Określ punkt wejścia do aplikacji F #, stosując `EntryPoint` atrybutu z programem `main` funkcji.</span><span class="sxs-lookup"><span data-stu-id="1ef72-109">You specify the entry point to an F# application by applying the `EntryPoint` attribute to the program's `main` function.</span></span> <span data-ttu-id="1ef72-110">Tej funkcji (utworzone za pomocą `let` powiązanie) musi być ostatnim funkcją ostatniego pliku skompilowany.</span><span class="sxs-lookup"><span data-stu-id="1ef72-110">This function (created by using a `let` binding) must be the last function in the last compiled file.</span></span> <span data-ttu-id="1ef72-111">Ostatni skompilowanego pliku jest ostatni plik projektu lub ostatni plik, który jest przekazywany do wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="1ef72-111">The last compiled file is the last file in the project or the last file that is passed to the command line.</span></span>

<span data-ttu-id="1ef72-112">Funkcja punktu wejścia ma typ `string array -> int`.</span><span class="sxs-lookup"><span data-stu-id="1ef72-112">The entry point function has type `string array -> int`.</span></span> <span data-ttu-id="1ef72-113">Podanych argumentów wiersza polecenia są przekazywane do `main` funkcji w tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="1ef72-113">The arguments provided on the command line are passed to the `main` function in the array of strings.</span></span> <span data-ttu-id="1ef72-114">Pierwszy element tablicy jest pierwszy argument; Nazwa pliku wykonywalnego nie jest uwzględniony w tablicy, jak w przypadku niektórych innych języków.</span><span class="sxs-lookup"><span data-stu-id="1ef72-114">The first element of the array is the first argument; the name of the executable file is not included in the array, as it is in some other languages.</span></span> <span data-ttu-id="1ef72-115">Wartość zwracana jest używany jako kod zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="1ef72-115">The return value is used as the exit code for the process.</span></span> <span data-ttu-id="1ef72-116">Zero zwykle wskazuje Powodzenie; podano niezerowe wartości oznaczać błąd.</span><span class="sxs-lookup"><span data-stu-id="1ef72-116">Zero usually indicates success; nonzero values indicate an error.</span></span> <span data-ttu-id="1ef72-117">Brak Brak Konwencji szczególne znaczenie niezerową kodów powrotnych; znaczenie kody powrotu są specyficzne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1ef72-117">There is no convention for the specific meaning of nonzero return codes; the meanings of the return codes are application-specific.</span></span>

<span data-ttu-id="1ef72-118">Poniższy przykład przedstawia prostą `main` funkcji.</span><span class="sxs-lookup"><span data-stu-id="1ef72-118">The following example illustrates a simple `main` function.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

<span data-ttu-id="1ef72-119">Gdy ten kod jest wykonywane przy użyciu wiersza polecenia `EntryPoint.exe 1 2 3`, dane wyjściowe ma następującą składnię.</span><span class="sxs-lookup"><span data-stu-id="1ef72-119">When this code is executed with the command line `EntryPoint.exe 1 2 3`, the output is as follows.</span></span>

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a><span data-ttu-id="1ef72-120">Niejawne punktu wejścia</span><span class="sxs-lookup"><span data-stu-id="1ef72-120">Implicit Entry Point</span></span>
<span data-ttu-id="1ef72-121">Jeśli program nie ma **punktu wejścia** atrybut określający, jawnie punktu wejścia, powiązania najwyższego poziomu w ostatnim pliku do kompilacji są używane jako punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="1ef72-121">When a program has no **EntryPoint** attribute that explicitly indicates the entry point, the top level bindings in the last file to be compiled are used as the entry point.</span></span>


## <a name="see-also"></a><span data-ttu-id="1ef72-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ef72-122">See Also</span></span>
[<span data-ttu-id="1ef72-123">Funkcje</span><span class="sxs-lookup"><span data-stu-id="1ef72-123">Functions</span></span>](index.md)

[<span data-ttu-id="1ef72-124">Powiązania „let”</span><span class="sxs-lookup"><span data-stu-id="1ef72-124">let Bindings</span></span>](let-bindings.md)
