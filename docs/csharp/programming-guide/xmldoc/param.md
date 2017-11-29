---
title: "&lt;param&gt; (C# przewodnik programowania w języku)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1a5325b91130623442c9cf5453e52418bb44cc34
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltparamgt-c-programming-guide"></a><span data-ttu-id="193bf-102">&lt;param&gt; (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="193bf-102">&lt;param&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="193bf-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="193bf-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="193bf-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="193bf-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="193bf-105">Nazwa parametru metody.</span><span class="sxs-lookup"><span data-stu-id="193bf-105">The name of a method parameter.</span></span> <span data-ttu-id="193bf-106">Nazwę należy ująć w podwójny cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="193bf-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="193bf-107">Opis parametru.</span><span class="sxs-lookup"><span data-stu-id="193bf-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="193bf-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="193bf-108">Remarks</span></span>  
 <span data-ttu-id="193bf-109">\<Param > tag powinny być używane w komentarz dla deklaracji metody opisujący jeden z parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="193bf-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="193bf-110">Aby udokumentować wiele parametrów, używanych jest wiele \<param > tagów.</span><span class="sxs-lookup"><span data-stu-id="193bf-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="193bf-111">Tekst dla \<param > będą wyświetlane w funkcji IntelliSense, przeglądarka obiektów i w raporcie Web komentarz kodu.</span><span class="sxs-lookup"><span data-stu-id="193bf-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="193bf-112">Kompiluj z użyciem [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="193bf-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="193bf-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="193bf-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="193bf-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="193bf-114">See Also</span></span>  
 [<span data-ttu-id="193bf-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="193bf-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="193bf-116">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="193bf-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
