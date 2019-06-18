---
title: Identyfikatory wiersza źródłowego, pliku i ścieżki
description: Dowiedz się, jak używać wbudowanych F# wartości identyfikatorów, które umożliwiają uzyskiwanie dostępu do źródła wierszy numer, katalogu i nazwa pliku w kodzie.
ms.date: 05/16/2016
ms.openlocfilehash: 3f2048aed9ef75037b43cd091a749e3d6bbaf9a3
ms.sourcegitcommit: 5e05f983e63d5bbd8c0b246d02c6e4f23d2fc1db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2019
ms.locfileid: "67152051"
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="a5cbd-103">Identyfikatory wiersza źródłowego, pliku i ścieżki</span><span class="sxs-lookup"><span data-stu-id="a5cbd-103">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="a5cbd-104">Identyfikatory `__LINE__`, `__SOURCE_DIRECTORY__` i `__SOURCE_FILE__` są wbudowane wartości, które umożliwiają dostęp do źródła wiersza numer, katalogów i plików nazwy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a5cbd-104">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="a5cbd-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5cbd-105">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="a5cbd-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5cbd-106">Remarks</span></span>

<span data-ttu-id="a5cbd-107">Każda z tych wartości ma typ `string`.</span><span class="sxs-lookup"><span data-stu-id="a5cbd-107">Each of these values has type `string`.</span></span>

<span data-ttu-id="a5cbd-108">W poniższej tabeli przedstawiono źródła wiersza, pliku i ścieżkę identyfikatorów, które są dostępne w F#.</span><span class="sxs-lookup"><span data-stu-id="a5cbd-108">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="a5cbd-109">Te identyfikatory nie są makra preprocesora; są one wbudowane wartości, które są rozpoznawane przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="a5cbd-109">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="a5cbd-110">Predefiniowany identyfikator</span><span class="sxs-lookup"><span data-stu-id="a5cbd-110">Predefined identifier</span></span>|<span data-ttu-id="a5cbd-111">Opis</span><span class="sxs-lookup"><span data-stu-id="a5cbd-111">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="a5cbd-112">Daje w wyniku bieżący numer wiersza, biorąc pod uwagę `#line` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="a5cbd-112">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="a5cbd-113">Daje w wyniku pełną ścieżkę bieżącego katalogu źródłowym, biorąc pod uwagę `#line` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="a5cbd-113">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="a5cbd-114">Daje w wyniku nazwę bieżącego pliku źródłowego, bez ścieżki, biorąc pod uwagę `#line` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="a5cbd-114">Evaluates to the current source file name, without its path, considering `#line` directives.</span></span>|

<span data-ttu-id="a5cbd-115">Aby uzyskać więcej informacji na temat `#line` dyrektywy, zobacz [dyrektywy kompilatora](compiler-directives.md).</span><span class="sxs-lookup"><span data-stu-id="a5cbd-115">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="a5cbd-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5cbd-116">Example</span></span>

<span data-ttu-id="a5cbd-117">Poniższy przykład kodu demonstruje użycie tych wartości.</span><span class="sxs-lookup"><span data-stu-id="a5cbd-117">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="a5cbd-118">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="a5cbd-118">Output:</span></span>

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: Program.fs
```

## <a name="see-also"></a><span data-ttu-id="a5cbd-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5cbd-119">See also</span></span>

- [<span data-ttu-id="a5cbd-120">Dyrektywy kompilatora</span><span class="sxs-lookup"><span data-stu-id="a5cbd-120">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="a5cbd-121">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="a5cbd-121">F# Language Reference</span></span>](index.md)
