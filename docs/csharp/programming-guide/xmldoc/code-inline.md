---
title: <c>— Przewodnik programowania w języku C#
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: a09bcd069e2f85f4a21736cb218c42c0e481d70b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287470"
---
# <a name="c-c-programming-guide"></a><span data-ttu-id="4bbb2-102">\<c>(Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="4bbb2-102">\<c> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="4bbb2-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="4bbb2-103">Syntax</span></span>

```xml
<c>text</c>
```

## <a name="parameters"></a><span data-ttu-id="4bbb2-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="4bbb2-104">Parameters</span></span>

- `text`

  <span data-ttu-id="4bbb2-105">Tekst, który ma być wskazywany jako kod.</span><span class="sxs-lookup"><span data-stu-id="4bbb2-105">The text you would like to indicate as code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4bbb2-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4bbb2-106">Remarks</span></span>

<span data-ttu-id="4bbb2-107">`<c>`Tag umożliwia wskazanie, że tekst w opisie powinien być oznaczony jako kod.</span><span class="sxs-lookup"><span data-stu-id="4bbb2-107">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="4bbb2-108">Użyj [\<code>](./code.md) , aby wskazać wiele wierszy jako kod.</span><span class="sxs-lookup"><span data-stu-id="4bbb2-108">Use [\<code>](./code.md) to indicate multiple lines as code.</span></span>

<span data-ttu-id="4bbb2-109">Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="4bbb2-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="4bbb2-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="4bbb2-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a><span data-ttu-id="4bbb2-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4bbb2-111">See also</span></span>

- [<span data-ttu-id="4bbb2-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4bbb2-112">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="4bbb2-113">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="4bbb2-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
