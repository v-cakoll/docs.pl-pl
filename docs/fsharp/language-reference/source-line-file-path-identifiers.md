---
title: "Identyfikatory wiersza źródłowego, pliku i ścieżki (F#)"
description: "Dowiedz się, jak używać wbudowanych F # identyfikator wartości, które umożliwiają dostęp do numeru wiersza źródłowego, katalogu i nazwa pliku w kodzie."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4cfe7439-275c-4d08-980b-784e240bbf29
ms.openlocfilehash: 44cc0914226c120f2b877ce3decd25caa6817eec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="79df8-104">Identyfikatory wiersza źródłowego, pliku i ścieżki</span><span class="sxs-lookup"><span data-stu-id="79df8-104">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="79df8-105">Identyfikatory `__LINE__`, `__SOURCE_DIRECTORY__` i `__SOURCE_FILE__` są wbudowane wartości, które umożliwiają dostęp do źródła wiersza numer, katalogu i nazwa pliku w kodzie.</span><span class="sxs-lookup"><span data-stu-id="79df8-105">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>


## <a name="syntax"></a><span data-ttu-id="79df8-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="79df8-106">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="79df8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="79df8-107">Remarks</span></span>
<span data-ttu-id="79df8-108">Każda z tych wartości ma typ `string`.</span><span class="sxs-lookup"><span data-stu-id="79df8-108">Each of these values has type `string`.</span></span>

<span data-ttu-id="79df8-109">W poniższej tabeli przedstawiono wiersza źródłowego, pliku i ścieżki identyfikatorów, które są dostępne w języku F #.</span><span class="sxs-lookup"><span data-stu-id="79df8-109">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="79df8-110">Te identyfikatory nie są makra preprocesora; są one wbudowane wartości, które są rozpoznawane przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="79df8-110">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="79df8-111">Identyfikator wstępnie zdefiniowane</span><span class="sxs-lookup"><span data-stu-id="79df8-111">Predefined identifier</span></span>|<span data-ttu-id="79df8-112">Opis</span><span class="sxs-lookup"><span data-stu-id="79df8-112">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="79df8-113">Zwraca bieżący numer wiersza, biorąc pod uwagę `#line` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="79df8-113">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="79df8-114">Daje w wyniku bieżącej pełną ścieżkę katalogu źródłowego uwzględnieniu `#line` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="79df8-114">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="79df8-115">Daje w wyniku bieżącej nazwy pliku źródłowego i jego ścieżki, biorąc pod uwagę `#line` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="79df8-115">Evaluates to the current source file name and its path, considering `#line` directives.</span></span>|
<span data-ttu-id="79df8-116">Aby uzyskać więcej informacji na temat `#line` dyrektywy, zobacz [dyrektywy kompilatora](compiler-directives.md).</span><span class="sxs-lookup"><span data-stu-id="79df8-116">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="79df8-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="79df8-117">Example</span></span>

<span data-ttu-id="79df8-118">Poniższy przykład kodu pokazuje użycie tych wartości.</span><span class="sxs-lookup"><span data-stu-id="79df8-118">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="79df8-119">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="79df8-119">Output:</span></span>

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a><span data-ttu-id="79df8-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="79df8-120">See Also</span></span>
[<span data-ttu-id="79df8-121">Dyrektywy kompilatora</span><span class="sxs-lookup"><span data-stu-id="79df8-121">Compiler Directives</span></span>](compiler-directives.md)

[<span data-ttu-id="79df8-122">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="79df8-122">F# Language Reference</span></span>](index.md)
