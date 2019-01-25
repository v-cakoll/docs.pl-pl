---
title: '&lt;param&gt; - C# Programming Guide'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: fb31e1d4c39888765fe3e55674d5b6d18b9d5b65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641021"
---
# <a name="ltparamgt-c-programming-guide"></a><span data-ttu-id="e5efe-102">&lt;param&gt; (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="e5efe-102">&lt;param&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="e5efe-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5efe-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e5efe-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5efe-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="e5efe-105">Nazwa parametru metody.</span><span class="sxs-lookup"><span data-stu-id="e5efe-105">The name of a method parameter.</span></span> <span data-ttu-id="e5efe-106">Nazwę należy ująć w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="e5efe-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="e5efe-107">Opis parametru.</span><span class="sxs-lookup"><span data-stu-id="e5efe-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5efe-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5efe-108">Remarks</span></span>  
 <span data-ttu-id="e5efe-109">\<Param > używany tag w komentarzu do deklaracji metody do opisania jeden z parametrów dla metody.</span><span class="sxs-lookup"><span data-stu-id="e5efe-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="e5efe-110">Dokumentowanie wiele parametrów, należy użyć wielu \<param > tagów.</span><span class="sxs-lookup"><span data-stu-id="e5efe-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="e5efe-111">Tekst dla \<param > będą wyświetlane w IntelliSense, przeglądarki obiektów i w raporcie Web komentarz kodu.</span><span class="sxs-lookup"><span data-stu-id="e5efe-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="e5efe-112">Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="e5efe-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5efe-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="e5efe-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e5efe-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5efe-114">See also</span></span>

- [<span data-ttu-id="e5efe-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e5efe-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e5efe-116">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="e5efe-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
