---
title: <paramref>- Przewodnik programowania C#
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 12df257271369dc7f0a5c066b712a8d8e6c38761
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793403"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="76804-102">\<paramref> (przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="76804-102">\<paramref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="76804-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="76804-103">Syntax</span></span>

```xml
<paramref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="76804-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="76804-104">Parameters</span></span>

- `name`

  <span data-ttu-id="76804-105">Nazwa parametru, do który ma się odwoływać.</span><span class="sxs-lookup"><span data-stu-id="76804-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="76804-106">Nazwę ująć w podwójne cudzysłowy (" ").</span><span class="sxs-lookup"><span data-stu-id="76804-106">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="76804-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="76804-107">Remarks</span></span>

<span data-ttu-id="76804-108">Tag \<> paramref umożliwia wskazanie, że słowo w komentarzach do \<kodu, \<na przykład w> podsumowującym lub uwagi> bloku odnosi się do parametru.</span><span class="sxs-lookup"><span data-stu-id="76804-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="76804-109">Plik XML można przetworzyć w celu sformatowania tego wyrazu w różny sposób, na przykład czcionką pogrubioną lub kursywą.</span><span class="sxs-lookup"><span data-stu-id="76804-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>

<span data-ttu-id="76804-110">Skompiluj za pomocą [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) aby przetworzyć komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="76804-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="76804-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="76804-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a><span data-ttu-id="76804-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76804-112">See also</span></span>

- [<span data-ttu-id="76804-113">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="76804-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="76804-114">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="76804-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
