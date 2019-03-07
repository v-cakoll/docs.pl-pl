---
title: <param> - C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: ffa3bd066ce753f2b953f2d6d0a70a3bf65293ff
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468036"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="5d880-102">\<param > (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="5d880-102">\<param> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="5d880-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d880-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d880-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d880-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="5d880-105">Nazwa parametru metody.</span><span class="sxs-lookup"><span data-stu-id="5d880-105">The name of a method parameter.</span></span> <span data-ttu-id="5d880-106">Nazwę należy ująć w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="5d880-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="5d880-107">Opis parametru.</span><span class="sxs-lookup"><span data-stu-id="5d880-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d880-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d880-108">Remarks</span></span>  
 <span data-ttu-id="5d880-109">\<Param > używany tag w komentarzu do deklaracji metody do opisania jeden z parametrów dla metody.</span><span class="sxs-lookup"><span data-stu-id="5d880-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="5d880-110">Dokumentowanie wiele parametrów, należy użyć wielu \<param > tagów.</span><span class="sxs-lookup"><span data-stu-id="5d880-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="5d880-111">Tekst dla \<param > będą wyświetlane w IntelliSense, przeglądarki obiektów i w raporcie Web komentarz kodu.</span><span class="sxs-lookup"><span data-stu-id="5d880-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="5d880-112">Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="5d880-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d880-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d880-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5d880-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d880-114">See also</span></span>

- [<span data-ttu-id="5d880-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5d880-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="5d880-116">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="5d880-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
