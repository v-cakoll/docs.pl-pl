---
title: '&lt;param&gt; (C# przewodnik programowania w języku)'
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 3d89637e5b1238c582390750e8eef30960fa90b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338016"
---
# <a name="ltparamgt-c-programming-guide"></a><span data-ttu-id="86d4e-102">&lt;param&gt; (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="86d4e-102">&lt;param&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="86d4e-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="86d4e-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="86d4e-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="86d4e-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="86d4e-105">Nazwa parametru metody.</span><span class="sxs-lookup"><span data-stu-id="86d4e-105">The name of a method parameter.</span></span> <span data-ttu-id="86d4e-106">Nazwę należy ująć w podwójny cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="86d4e-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="86d4e-107">Opis parametru.</span><span class="sxs-lookup"><span data-stu-id="86d4e-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86d4e-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86d4e-108">Remarks</span></span>  
 <span data-ttu-id="86d4e-109">\<Param > tag powinny być używane w komentarz dla deklaracji metody opisujący jeden z parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="86d4e-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="86d4e-110">Aby udokumentować wiele parametrów, używanych jest wiele \<param > tagów.</span><span class="sxs-lookup"><span data-stu-id="86d4e-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="86d4e-111">Tekst dla \<param > będą wyświetlane w funkcji IntelliSense, przeglądarka obiektów i w raporcie Web komentarz kodu.</span><span class="sxs-lookup"><span data-stu-id="86d4e-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="86d4e-112">Kompiluj z użyciem [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="86d4e-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86d4e-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="86d4e-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="86d4e-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="86d4e-114">See Also</span></span>  
 [<span data-ttu-id="86d4e-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="86d4e-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="86d4e-116">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="86d4e-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
