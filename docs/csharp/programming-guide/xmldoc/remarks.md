---
title: <remarks> — C# Przewodnik programowania
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: e37dac9cb9fed1df6ca027f09f2c95dbbc8ea66d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793375"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="57122-102">\<uwagi > (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="57122-102">\<remarks> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="57122-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="57122-103">Syntax</span></span>

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a><span data-ttu-id="57122-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="57122-104">Parameters</span></span>

- `Description`

  <span data-ttu-id="57122-105">Opis elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="57122-105">A description of the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="57122-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="57122-106">Remarks</span></span>

<span data-ttu-id="57122-107">Tag \<uwagi > służy do dodawania informacji o typie, uzupełnienie informacji określonych za pomocą [\<podsumowania >](./summary.md).</span><span class="sxs-lookup"><span data-stu-id="57122-107">The \<remarks> tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="57122-108">Te informacje są wyświetlane w oknie Przeglądarka obiektów.</span><span class="sxs-lookup"><span data-stu-id="57122-108">This information is displayed in the Object Browser window.</span></span>

<span data-ttu-id="57122-109">Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="57122-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="57122-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="57122-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a><span data-ttu-id="57122-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57122-111">See also</span></span>

- [<span data-ttu-id="57122-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="57122-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="57122-113">Zalecane Tagi dla komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="57122-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
