---
title: <remarks> - Przewodnik programowania C#
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: e37dac9cb9fed1df6ca027f09f2c95dbbc8ea66d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793375"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="8c7f7-102">\<uwagi> (przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="8c7f7-102">\<remarks> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="8c7f7-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="8c7f7-103">Syntax</span></span>

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a><span data-ttu-id="8c7f7-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c7f7-104">Parameters</span></span>

- `Description`

  <span data-ttu-id="8c7f7-105">Opis elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="8c7f7-105">A description of the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="8c7f7-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8c7f7-106">Remarks</span></span>

<span data-ttu-id="8c7f7-107">Uwagi \<> tag użyje do dania informacji o typie, uzupełniając informacje określone [ \<>podsumowania ](./summary.md).</span><span class="sxs-lookup"><span data-stu-id="8c7f7-107">The \<remarks> tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="8c7f7-108">Informacje te są wyświetlane w oknie Przeglądarka obiektów.</span><span class="sxs-lookup"><span data-stu-id="8c7f7-108">This information is displayed in the Object Browser window.</span></span>

<span data-ttu-id="8c7f7-109">Skompiluj za pomocą [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) aby przetworzyć komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="8c7f7-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="8c7f7-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="8c7f7-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a><span data-ttu-id="8c7f7-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c7f7-111">See also</span></span>

- [<span data-ttu-id="8c7f7-112">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="8c7f7-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8c7f7-113">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="8c7f7-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
