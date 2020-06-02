---
title: <value> — Przewodnik programowania w języku C#
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: bd6630a8d5894fda39ad289c8dd584f6d84e5490
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287197"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="0ceb4-102">\<value>(Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="0ceb4-102">\<value> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="0ceb4-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ceb4-103">Syntax</span></span>

```xml
<value>property-description</value>
```

## <a name="parameters"></a><span data-ttu-id="0ceb4-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ceb4-104">Parameters</span></span>

- `property-description`

  <span data-ttu-id="0ceb4-105">Opis właściwości.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-105">A description for the property.</span></span>

## <a name="remarks"></a><span data-ttu-id="0ceb4-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ceb4-106">Remarks</span></span>

<span data-ttu-id="0ceb4-107">`<value>`Tag umożliwia opisanie wartości reprezentowanej przez właściwość.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-107">The `<value>` tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="0ceb4-108">Po dodaniu właściwości za pośrednictwem Kreatora kodu w środowisku deweloperskim Visual Studio .NET dodaje [\<summary>](./summary.md) tag nowej właściwości.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-108">When you add a property via code wizard in the Visual Studio .NET development environment, it adds a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="0ceb4-109">Następnie należy ręcznie dodać tag, `<value>` aby opisać wartość, którą reprezentuje właściwość.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-109">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>

<span data-ttu-id="0ceb4-110">Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="0ceb4-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="0ceb4-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a><span data-ttu-id="0ceb4-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ceb4-112">See also</span></span>

- [<span data-ttu-id="0ceb4-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0ceb4-113">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="0ceb4-114">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="0ceb4-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
