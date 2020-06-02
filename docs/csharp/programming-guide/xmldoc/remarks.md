---
title: <remarks> — Przewodnik programowania w języku C#
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: 739027786e02e559d86f990bf614e261b497c76f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287288"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="86a0a-102">\<remarks>(Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="86a0a-102">\<remarks> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="86a0a-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="86a0a-103">Syntax</span></span>

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a><span data-ttu-id="86a0a-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="86a0a-104">Parameters</span></span>

- `Description`

  <span data-ttu-id="86a0a-105">Opis elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="86a0a-105">A description of the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="86a0a-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86a0a-106">Remarks</span></span>

<span data-ttu-id="86a0a-107">`<remarks>`Tag służy do dodawania informacji o typie, uzupełniając informacje określone za pomocą [\<summary>](./summary.md) .</span><span class="sxs-lookup"><span data-stu-id="86a0a-107">The `<remarks>` tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="86a0a-108">Te informacje są wyświetlane w oknie Przeglądarka obiektów.</span><span class="sxs-lookup"><span data-stu-id="86a0a-108">This information is displayed in the Object Browser window.</span></span>

<span data-ttu-id="86a0a-109">Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="86a0a-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="86a0a-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="86a0a-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a><span data-ttu-id="86a0a-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86a0a-111">See also</span></span>

- [<span data-ttu-id="86a0a-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="86a0a-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="86a0a-113">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="86a0a-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
