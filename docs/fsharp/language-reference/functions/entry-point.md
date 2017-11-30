---
title: "Punkt wejścia (F#)"
description: "Dowiedz się, jak ustawić punkt wejścia do programu F # jest skompilowany, ponieważ plik wykonywalny, gdzie wykonywanie formalnie uruchamiana."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 91455443-ff9d-4510-a7e9-1560bdcd0bb0
ms.openlocfilehash: 685fd4da67119aa5fcaaffd142a0a17c8f5dc7f6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="entry-point"></a><span data-ttu-id="74248-104">Punkt wejścia</span><span class="sxs-lookup"><span data-stu-id="74248-104">Entry Point</span></span>

<span data-ttu-id="74248-105">W tym temacie opisano metody, która służy do ustawiania punktu wejścia do programu F #.</span><span class="sxs-lookup"><span data-stu-id="74248-105">This topic describes the method that you use to set the entry point to an F# program.</span></span>


## <a name="syntax"></a><span data-ttu-id="74248-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="74248-106">Syntax</span></span>

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a><span data-ttu-id="74248-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="74248-107">Remarks</span></span>
<span data-ttu-id="74248-108">W poprzednich składni *let funkcji wiązania* znajduje się definicja funkcji w `let` powiązania.</span><span class="sxs-lookup"><span data-stu-id="74248-108">In the previous syntax, *let-function-binding* is the definition of a function in a `let` binding.</span></span>

<span data-ttu-id="74248-109">Punkt wejścia do programu, który ma być kompilowana jako plik wykonywalny jest, gdzie formalnie rozpoczyna się wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="74248-109">The entry point to a program that is compiled as an executable file is where execution formally starts.</span></span> <span data-ttu-id="74248-110">Określ punkt wejścia do aplikacji F #, stosując `EntryPoint` atrybutu z programem `main` funkcji.</span><span class="sxs-lookup"><span data-stu-id="74248-110">You specify the entry point to an F# application by applying the `EntryPoint` attribute to the program's `main` function.</span></span> <span data-ttu-id="74248-111">Tej funkcji (utworzone za pomocą `let` powiązanie) musi być ostatnim funkcją ostatniego pliku skompilowany.</span><span class="sxs-lookup"><span data-stu-id="74248-111">This function (created by using a `let` binding) must be the last function in the last compiled file.</span></span> <span data-ttu-id="74248-112">Ostatni skompilowanego pliku jest ostatni plik projektu lub ostatni plik, który jest przekazywany do wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="74248-112">The last compiled file is the last file in the project or the last file that is passed to the command line.</span></span>

<span data-ttu-id="74248-113">Funkcja punktu wejścia ma typ `string array -> int`.</span><span class="sxs-lookup"><span data-stu-id="74248-113">The entry point function has type `string array -> int`.</span></span> <span data-ttu-id="74248-114">Podanych argumentów wiersza polecenia są przekazywane do `main` funkcji w tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="74248-114">The arguments provided on the command line are passed to the `main` function in the array of strings.</span></span> <span data-ttu-id="74248-115">Pierwszy element tablicy jest pierwszy argument; Nazwa pliku wykonywalnego nie jest uwzględniony w tablicy, jak w przypadku niektórych innych języków.</span><span class="sxs-lookup"><span data-stu-id="74248-115">The first element of the array is the first argument; the name of the executable file is not included in the array, as it is in some other languages.</span></span> <span data-ttu-id="74248-116">Wartość zwracana jest używany jako kod zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="74248-116">The return value is used as the exit code for the process.</span></span> <span data-ttu-id="74248-117">Zero zwykle wskazuje Powodzenie; podano niezerowe wartości oznaczać błąd.</span><span class="sxs-lookup"><span data-stu-id="74248-117">Zero usually indicates success; nonzero values indicate an error.</span></span> <span data-ttu-id="74248-118">Brak Brak Konwencji szczególne znaczenie niezerową kodów powrotnych; znaczenie kody powrotu są specyficzne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="74248-118">There is no convention for the specific meaning of nonzero return codes; the meanings of the return codes are application-specific.</span></span>

<span data-ttu-id="74248-119">Poniższy przykład przedstawia prostą `main` funkcji.</span><span class="sxs-lookup"><span data-stu-id="74248-119">The following example illustrates a simple `main` function.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

<span data-ttu-id="74248-120">Gdy ten kod jest wykonywane przy użyciu wiersza polecenia `EntryPoint.exe 1 2 3`, dane wyjściowe ma następującą składnię.</span><span class="sxs-lookup"><span data-stu-id="74248-120">When this code is executed with the command line `EntryPoint.exe 1 2 3`, the output is as follows.</span></span>

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a><span data-ttu-id="74248-121">Niejawne punktu wejścia</span><span class="sxs-lookup"><span data-stu-id="74248-121">Implicit Entry Point</span></span>
<span data-ttu-id="74248-122">Jeśli program nie ma **punktu wejścia** atrybut określający, jawnie punktu wejścia, powiązania najwyższego poziomu w ostatnim pliku do kompilacji są używane jako punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="74248-122">When a program has no **EntryPoint** attribute that explicitly indicates the entry point, the top level bindings in the last file to be compiled are used as the entry point.</span></span>


## <a name="see-also"></a><span data-ttu-id="74248-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="74248-123">See Also</span></span>
[<span data-ttu-id="74248-124">Funkcje</span><span class="sxs-lookup"><span data-stu-id="74248-124">Functions</span></span>](index.md)

[<span data-ttu-id="74248-125">Let — powiązania</span><span class="sxs-lookup"><span data-stu-id="74248-125">let Bindings</span></span>](let-bindings.md)
