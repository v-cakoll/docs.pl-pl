---
title: <paramref>— Przewodnik programowania w języku C#
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 4f3b521d24c8b4677a05b0b145cb36c31b2793f2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287314"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="62f1a-102">\<paramref>(Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="62f1a-102">\<paramref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="62f1a-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="62f1a-103">Syntax</span></span>

```xml
<paramref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="62f1a-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="62f1a-104">Parameters</span></span>

- `name`

  <span data-ttu-id="62f1a-105">Nazwa parametru, do którego się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="62f1a-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="62f1a-106">Ujmij nazwę w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="62f1a-106">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="62f1a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62f1a-107">Remarks</span></span>

<span data-ttu-id="62f1a-108">`<paramref>`Tag umożliwia wskazanie, że słowo w komentarzach do kodu, na przykład w `<summary>` `<remarks>` bloku lub odwołuje się do parametru.</span><span class="sxs-lookup"><span data-stu-id="62f1a-108">The `<paramref>` tag gives you a way to indicate that a word in the code comments, for example in a `<summary>` or `<remarks>` block refers to a parameter.</span></span> <span data-ttu-id="62f1a-109">Plik XML można przetworzyć, aby sformatować ten wyraz w sposób niezależny, na przykład za pomocą czcionki pogrubionej lub kursywy.</span><span class="sxs-lookup"><span data-stu-id="62f1a-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>

<span data-ttu-id="62f1a-110">Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="62f1a-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="62f1a-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="62f1a-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a><span data-ttu-id="62f1a-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62f1a-112">See also</span></span>

- [<span data-ttu-id="62f1a-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="62f1a-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="62f1a-114">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="62f1a-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
