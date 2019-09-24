---
title: Identyfikatory wiersza źródłowego, pliku i ścieżki
description: Dowiedz się, jak używać wbudowanych F# wartości identyfikatorów, które umożliwiają uzyskiwanie dostępu do numeru wiersza źródłowego, katalogu i nazwy pliku w kodzie.
ms.date: 05/16/2016
ms.openlocfilehash: f22c3dfb3cb106fbe45883ffd7de01feac30db00
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216747"
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="0f7eb-103">Identyfikatory wiersza źródłowego, pliku i ścieżki</span><span class="sxs-lookup"><span data-stu-id="0f7eb-103">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="0f7eb-104">Identyfikatory `__LINE__` `__SOURCE_DIRECTORY__` i sąwbudowanymiwartościami,któreumożliwiajądostępdonumeruwierszaźródłowego,kataloguinazwyplikuwkodzie.`__SOURCE_FILE__`</span><span class="sxs-lookup"><span data-stu-id="0f7eb-104">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="0f7eb-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0f7eb-105">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="0f7eb-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0f7eb-106">Remarks</span></span>

<span data-ttu-id="0f7eb-107">Każda z tych wartości ma typ `string`.</span><span class="sxs-lookup"><span data-stu-id="0f7eb-107">Each of these values has type `string`.</span></span>

<span data-ttu-id="0f7eb-108">Poniższa tabela zawiera podsumowanie identyfikatorów wiersza źródłowego, pliku i ścieżki, które są dostępne w programie F#.</span><span class="sxs-lookup"><span data-stu-id="0f7eb-108">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="0f7eb-109">Te identyfikatory nie są makrami preprocesora; są to wbudowane wartości, które są rozpoznawane przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="0f7eb-109">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="0f7eb-110">Wstępnie zdefiniowany identyfikator</span><span class="sxs-lookup"><span data-stu-id="0f7eb-110">Predefined identifier</span></span>|<span data-ttu-id="0f7eb-111">Opis</span><span class="sxs-lookup"><span data-stu-id="0f7eb-111">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="0f7eb-112">Oblicza bieżący numer wiersza, rozważając `#line` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="0f7eb-112">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="0f7eb-113">Oblicza bieżącą pełną ścieżkę katalogu źródłowego, rozważając `#line` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="0f7eb-113">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="0f7eb-114">Oblicza bieżącą nazwę pliku źródłowego bez jego ścieżki, rozważając `#line` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="0f7eb-114">Evaluates to the current source file name, without its path, considering `#line` directives.</span></span>|

<span data-ttu-id="0f7eb-115">Aby uzyskać więcej informacji na `#line` temat dyrektywy, zobacz [dyrektywy kompilatora](compiler-directives.md).</span><span class="sxs-lookup"><span data-stu-id="0f7eb-115">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="0f7eb-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="0f7eb-116">Example</span></span>

<span data-ttu-id="0f7eb-117">Poniższy przykład kodu demonstruje użycie tych wartości.</span><span class="sxs-lookup"><span data-stu-id="0f7eb-117">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="0f7eb-118">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="0f7eb-118">Output:</span></span>

```console
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: Program.fs
```

## <a name="see-also"></a><span data-ttu-id="0f7eb-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f7eb-119">See also</span></span>

- [<span data-ttu-id="0f7eb-120">Dyrektywy kompilatora</span><span class="sxs-lookup"><span data-stu-id="0f7eb-120">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="0f7eb-121">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="0f7eb-121">F# Language Reference</span></span>](index.md)
