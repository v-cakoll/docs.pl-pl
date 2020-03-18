---
title: <returns> - Przewodnik programowania C#
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: 784d9effa589c962b8a2b982fd199f74309fb4dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789708"
---
# <a name="returns-c-programming-guide"></a><span data-ttu-id="3f053-102">\<zwraca> (przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="3f053-102">\<returns> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="3f053-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f053-103">Syntax</span></span>

```xml
<returns>description</returns>
```

## <a name="parameters"></a><span data-ttu-id="3f053-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="3f053-104">Parameters</span></span>

- `description`

  <span data-ttu-id="3f053-105">Opis wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="3f053-105">A description of the return value.</span></span>

## <a name="remarks"></a><span data-ttu-id="3f053-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3f053-106">Remarks</span></span>

<span data-ttu-id="3f053-107">Zwraca \<> tag powinien być używany w komentarzu dla deklaracji metody do opisania wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="3f053-107">The \<returns> tag should be used in the comment for a method declaration to describe the return value.</span></span>

<span data-ttu-id="3f053-108">Skompiluj za pomocą [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) aby przetworzyć komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="3f053-108">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="3f053-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="3f053-109">Example</span></span>

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a><span data-ttu-id="3f053-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3f053-110">See also</span></span>

- [<span data-ttu-id="3f053-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3f053-111">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="3f053-112">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="3f053-112">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
