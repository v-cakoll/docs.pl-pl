---
title: <inheritdoc>- Przewodnik programowania C#
ms.date: 01/21/2020
f1_keywords:
- inheritdoc
- <inheritdoc>
helpviewer_keywords:
- <inheritdoc> C# XML tag
- inheritdoc C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 6f42462f21d045428577cd2123e2180d866f1e1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156951"
---
# <a name="inheritdoc-c-programming-guide"></a><span data-ttu-id="92cbb-102">\<> (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="92cbb-102">\<inheritdoc> (C# Programming Guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="92cbb-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="92cbb-103">Syntax</span></span>  
  
```xml  
<inheritdoc/>
```  

## <a name="inheritdoc"></a><span data-ttu-id="92cbb-104">InheritDoc</span><span class="sxs-lookup"><span data-stu-id="92cbb-104">InheritDoc</span></span>

<span data-ttu-id="92cbb-105">Dziedzicz komentarze XML z klas podstawowych, interfejsów i podobnych metod.</span><span class="sxs-lookup"><span data-stu-id="92cbb-105">Inherit XML comments from base classes, interfaces, and similar methods.</span></span> <span data-ttu-id="92cbb-106">Eliminuje to niepożądane kopiowanie i wklejanie zduplikowanych komentarzy XML i automatycznie synchronizuje komentarze XML.</span><span class="sxs-lookup"><span data-stu-id="92cbb-106">This eliminates unwanted copying and pasting of duplicate XML comments and automatically keeps XML comments synchronized.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="92cbb-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="92cbb-107">Remarks</span></span>  
<span data-ttu-id="92cbb-108">Dodaj komentarze XML w klasach podstawowych lub interfejsach i pozwól InheritDoc skopiować komentarze do klasy implementującej.</span><span class="sxs-lookup"><span data-stu-id="92cbb-108">Add your XML comments in base classes or interfaces and let InheritDoc copy the comments to implementing classes.</span></span>

<span data-ttu-id="92cbb-109">Dodaj komentarze XML do metod synchronicznych i pozwól InheritDoc skopiować komentarze do asynchronicznych wersji tych samych metod.</span><span class="sxs-lookup"><span data-stu-id="92cbb-109">Add your XML comments to your synchronous methods and let InheritDoc copy the comments to your asynchronous versions of the same methods.</span></span>  

<span data-ttu-id="92cbb-110">Jeśli chcesz skopiować komentarze od określonego członka, `cref` możesz użyć atrybutu, aby określić element członkowski.</span><span class="sxs-lookup"><span data-stu-id="92cbb-110">If you want to copy the comments from a specific member you can use the `cref` attribute to specify the member.</span></span>
  
## <a name="examples"></a><span data-ttu-id="92cbb-111">Przykłady</span><span class="sxs-lookup"><span data-stu-id="92cbb-111">Examples</span></span>
[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a><span data-ttu-id="92cbb-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="92cbb-112">See also</span></span>

- [<span data-ttu-id="92cbb-113">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="92cbb-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="92cbb-114">Zalecane tagi do komentarzy do dokumentacji</span><span class="sxs-lookup"><span data-stu-id="92cbb-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
