---
title: Identyfikatory wiersza źródłowego, pliku i ścieżki (F#)
description: 'Dowiedz się, jak używać wbudowanych F # identyfikator wartości, które umożliwiają dostęp do numeru wiersza źródłowego, katalogu i nazwa pliku w kodzie.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 18a26f0aa0a0c1f9c0b448ec46eaebd540391324
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="def1d-103">Identyfikatory wiersza źródłowego, pliku i ścieżki</span><span class="sxs-lookup"><span data-stu-id="def1d-103">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="def1d-104">Identyfikatory `__LINE__`, `__SOURCE_DIRECTORY__` i `__SOURCE_FILE__` są wbudowane wartości, które umożliwiają dostęp do źródła wiersza numer, katalogu i nazwa pliku w kodzie.</span><span class="sxs-lookup"><span data-stu-id="def1d-104">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>


## <a name="syntax"></a><span data-ttu-id="def1d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="def1d-105">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="def1d-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="def1d-106">Remarks</span></span>
<span data-ttu-id="def1d-107">Każda z tych wartości ma typ `string`.</span><span class="sxs-lookup"><span data-stu-id="def1d-107">Each of these values has type `string`.</span></span>

<span data-ttu-id="def1d-108">W poniższej tabeli przedstawiono wiersza źródłowego, pliku i ścieżki identyfikatorów, które są dostępne w języku F #.</span><span class="sxs-lookup"><span data-stu-id="def1d-108">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="def1d-109">Te identyfikatory nie są makra preprocesora; są one wbudowane wartości, które są rozpoznawane przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="def1d-109">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="def1d-110">Identyfikator wstępnie zdefiniowane</span><span class="sxs-lookup"><span data-stu-id="def1d-110">Predefined identifier</span></span>|<span data-ttu-id="def1d-111">Opis</span><span class="sxs-lookup"><span data-stu-id="def1d-111">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="def1d-112">Zwraca bieżący numer wiersza, biorąc pod uwagę `#line` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="def1d-112">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="def1d-113">Daje w wyniku bieżącej pełną ścieżkę katalogu źródłowego uwzględnieniu `#line` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="def1d-113">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="def1d-114">Daje w wyniku bieżącej nazwy pliku źródłowego i jego ścieżki, biorąc pod uwagę `#line` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="def1d-114">Evaluates to the current source file name and its path, considering `#line` directives.</span></span>|
<span data-ttu-id="def1d-115">Aby uzyskać więcej informacji na temat `#line` dyrektywy, zobacz [dyrektywy kompilatora](compiler-directives.md).</span><span class="sxs-lookup"><span data-stu-id="def1d-115">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="def1d-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="def1d-116">Example</span></span>

<span data-ttu-id="def1d-117">Poniższy przykład kodu pokazuje użycie tych wartości.</span><span class="sxs-lookup"><span data-stu-id="def1d-117">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="def1d-118">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="def1d-118">Output:</span></span>

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a><span data-ttu-id="def1d-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="def1d-119">See Also</span></span>
[<span data-ttu-id="def1d-120">Dyrektywy kompilatora</span><span class="sxs-lookup"><span data-stu-id="def1d-120">Compiler Directives</span></span>](compiler-directives.md)

[<span data-ttu-id="def1d-121">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="def1d-121">F# Language Reference</span></span>](index.md)
