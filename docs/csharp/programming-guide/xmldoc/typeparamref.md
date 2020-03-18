---
title: <typeparamref>- Przewodnik programowania C#
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 266eadad322fd3c4167c7a911cb57ef1e1333012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789659"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="117bc-102">\<typeparamref> (przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="117bc-102">\<typeparamref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="117bc-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="117bc-103">Syntax</span></span>

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="117bc-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="117bc-104">Parameters</span></span>

- `name`

  <span data-ttu-id="117bc-105">Nazwa parametru typu.</span><span class="sxs-lookup"><span data-stu-id="117bc-105">The name of the type parameter.</span></span> <span data-ttu-id="117bc-106">Nazwę ująć w podwójne cudzysłowy (" ").</span><span class="sxs-lookup"><span data-stu-id="117bc-106">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="117bc-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="117bc-107">Remarks</span></span>

<span data-ttu-id="117bc-108">Aby uzyskać więcej informacji na temat parametrów typu w typach ogólnych i metodach, zobacz [Generyk.](../generics/index.md)</span><span class="sxs-lookup"><span data-stu-id="117bc-108">For more information on type parameters in generic types and methods, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="117bc-109">Użyj tego tagu, aby umożliwić konsumentom pliku dokumentacji formatowanie wyrazu w różny sposób, na przykład kursywą.</span><span class="sxs-lookup"><span data-stu-id="117bc-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>

<span data-ttu-id="117bc-110">Skompiluj za pomocą [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) aby przetworzyć komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="117bc-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="117bc-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="117bc-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="117bc-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="117bc-112">See also</span></span>

- [<span data-ttu-id="117bc-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="117bc-113">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="117bc-114">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="117bc-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
