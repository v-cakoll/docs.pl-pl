---
title: <c> — C# Przewodnik programowania
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
ms.openlocfilehash: d5b28ee6db52d191f8454592d792ac0a1e1dc73b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793457"
---
# <a name="c-c-programming-guide"></a><span data-ttu-id="08caf-102">\<c > (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="08caf-102">\<c> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="08caf-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="08caf-103">Syntax</span></span>

```xml
<c>text</c>
```

## <a name="parameters"></a><span data-ttu-id="08caf-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="08caf-104">Parameters</span></span>

- `text`

  <span data-ttu-id="08caf-105">Tekst, który ma być wskazywany jako kod.</span><span class="sxs-lookup"><span data-stu-id="08caf-105">The text you would like to indicate as code.</span></span>

## <a name="remarks"></a><span data-ttu-id="08caf-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="08caf-106">Remarks</span></span>

<span data-ttu-id="08caf-107">Tag \<c > umożliwia wskazanie, że tekst w opisie powinien być oznaczony jako kod.</span><span class="sxs-lookup"><span data-stu-id="08caf-107">The \<c> tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="08caf-108">Użyj [\<kodu >](./code.md) , aby wskazać wiele wierszy jako kod.</span><span class="sxs-lookup"><span data-stu-id="08caf-108">Use [\<code>](./code.md) to indicate multiple lines as code.</span></span>

<span data-ttu-id="08caf-109">Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="08caf-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="08caf-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="08caf-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a><span data-ttu-id="08caf-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="08caf-111">See also</span></span>

- [<span data-ttu-id="08caf-112">C#Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="08caf-112">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="08caf-113">Zalecane Tagi dla komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="08caf-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
