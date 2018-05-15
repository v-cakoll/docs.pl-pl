---
title: '&lt;param&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: c992c96303eb1441eaf667693b7aefb5361b196c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ltparamgt-visual-basic"></a><span data-ttu-id="ab308-102">&lt;param&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab308-102">&lt;param&gt; (Visual Basic)</span></span>
<span data-ttu-id="ab308-103">Określa nazwę parametru i opis.</span><span class="sxs-lookup"><span data-stu-id="ab308-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab308-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab308-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab308-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab308-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="ab308-106">Nazwa parametru metody.</span><span class="sxs-lookup"><span data-stu-id="ab308-106">The name of a method parameter.</span></span> <span data-ttu-id="ab308-107">Nazwę należy ująć w podwójny cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="ab308-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="ab308-108">Opis parametru.</span><span class="sxs-lookup"><span data-stu-id="ab308-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab308-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab308-109">Remarks</span></span>  
 <span data-ttu-id="ab308-110">`<param>` Tag powinny być używane w komentarz dla deklaracji metody opisujący jeden z parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="ab308-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="ab308-111">Tekst dla `<param>` tag pojawi się w następujących lokalizacjach:</span><span class="sxs-lookup"><span data-stu-id="ab308-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
-   <span data-ttu-id="ab308-112">Informacje o parametrach IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="ab308-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="ab308-113">Aby uzyskać więcej informacji, zobacz [za pomocą funkcji IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="ab308-113">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
-   <span data-ttu-id="ab308-114">Przeglądarka obiektów.</span><span class="sxs-lookup"><span data-stu-id="ab308-114">Object Browser.</span></span> <span data-ttu-id="ab308-115">Aby uzyskać więcej informacji, zobacz [wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="ab308-115">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="ab308-116">Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="ab308-116">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab308-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab308-117">Example</span></span>  
 <span data-ttu-id="ab308-118">W tym przykładzie użyto `<param>` tag do opisywania `id` parametru.</span><span class="sxs-lookup"><span data-stu-id="ab308-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ab308-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab308-119">See Also</span></span>  
 [<span data-ttu-id="ab308-120">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="ab308-120">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
