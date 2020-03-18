---
title: <value> - Przewodnik programowania C#
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 120805346672738e614743ab8c98388b8dbac0f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793349"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="b5642-102">\<wartość> (przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="b5642-102">\<value> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="b5642-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5642-103">Syntax</span></span>

```xml
<value>property-description</value>
```

## <a name="parameters"></a><span data-ttu-id="b5642-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="b5642-104">Parameters</span></span>

- `property-description`

  <span data-ttu-id="b5642-105">Opis obiektu.</span><span class="sxs-lookup"><span data-stu-id="b5642-105">A description for the property.</span></span>

## <a name="remarks"></a><span data-ttu-id="b5642-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b5642-106">Remarks</span></span>

<span data-ttu-id="b5642-107">Wartość \<> tag pozwala opisać wartość, która reprezentuje właściwość.</span><span class="sxs-lookup"><span data-stu-id="b5642-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="b5642-108">Należy zauważyć, że po dodaniu właściwości za pomocą kreatora kodu w środowisku programistycznym programu Visual Studio .NET doda [ \<podsumowanie>](./summary.md) tag dla nowej właściwości.</span><span class="sxs-lookup"><span data-stu-id="b5642-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="b5642-109">Następnie należy ręcznie \<dodać wartość> tag, aby opisać wartość, która reprezentuje właściwość.</span><span class="sxs-lookup"><span data-stu-id="b5642-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>

<span data-ttu-id="b5642-110">Skompiluj za pomocą [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) aby przetworzyć komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="b5642-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="b5642-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="b5642-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a><span data-ttu-id="b5642-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b5642-112">See also</span></span>

- [<span data-ttu-id="b5642-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b5642-113">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="b5642-114">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="b5642-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
