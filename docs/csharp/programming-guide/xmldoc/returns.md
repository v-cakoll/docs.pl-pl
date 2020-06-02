---
title: <returns> — Przewodnik programowania w języku C#
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: 7bc950a8d89a3ac2b5c3b7a68e05c7778e97f85c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287236"
---
# <a name="returns-c-programming-guide"></a><span data-ttu-id="86482-102">\<returns>(Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="86482-102">\<returns> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="86482-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="86482-103">Syntax</span></span>

```xml
<returns>description</returns>
```

## <a name="parameters"></a><span data-ttu-id="86482-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="86482-104">Parameters</span></span>

- `description`

  <span data-ttu-id="86482-105">Opis wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="86482-105">A description of the return value.</span></span>

## <a name="remarks"></a><span data-ttu-id="86482-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86482-106">Remarks</span></span>

<span data-ttu-id="86482-107">`<returns>`Tag powinien być używany w komentarzu dla deklaracji metody, aby opisać wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="86482-107">The `<returns>` tag should be used in the comment for a method declaration to describe the return value.</span></span>

<span data-ttu-id="86482-108">Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="86482-108">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="86482-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="86482-109">Example</span></span>

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a><span data-ttu-id="86482-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86482-110">See also</span></span>

- [<span data-ttu-id="86482-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="86482-111">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="86482-112">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="86482-112">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
