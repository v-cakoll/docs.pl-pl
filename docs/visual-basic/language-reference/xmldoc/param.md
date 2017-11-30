---
title: '&lt;param&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 09c7473cd88a701d8e46251be9b1c268c2dc8805
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltparamgt-visual-basic"></a><span data-ttu-id="3e1fa-102">&lt;param&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e1fa-102">&lt;param&gt; (Visual Basic)</span></span>
<span data-ttu-id="3e1fa-103">Określa nazwę parametru i opis.</span><span class="sxs-lookup"><span data-stu-id="3e1fa-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e1fa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e1fa-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3e1fa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3e1fa-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="3e1fa-106">Nazwa parametru metody.</span><span class="sxs-lookup"><span data-stu-id="3e1fa-106">The name of a method parameter.</span></span> <span data-ttu-id="3e1fa-107">Nazwę należy ująć w podwójny cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="3e1fa-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="3e1fa-108">Opis parametru.</span><span class="sxs-lookup"><span data-stu-id="3e1fa-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e1fa-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3e1fa-109">Remarks</span></span>  
 <span data-ttu-id="3e1fa-110">`<param>` Tag powinny być używane w komentarz dla deklaracji metody opisujący jeden z parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="3e1fa-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="3e1fa-111">Tekst dla `<param>` tag pojawi się w następujących lokalizacjach:</span><span class="sxs-lookup"><span data-stu-id="3e1fa-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
-   <span data-ttu-id="3e1fa-112">Informacje o parametrach IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="3e1fa-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="3e1fa-113">Aby uzyskać więcej informacji, zobacz [za pomocą funkcji IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="3e1fa-113">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
-   <span data-ttu-id="3e1fa-114">Przeglądarka obiektów.</span><span class="sxs-lookup"><span data-stu-id="3e1fa-114">Object Browser.</span></span> <span data-ttu-id="3e1fa-115">Aby uzyskać więcej informacji, zobacz [wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="3e1fa-115">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="3e1fa-116">Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="3e1fa-116">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e1fa-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e1fa-117">Example</span></span>  
 <span data-ttu-id="3e1fa-118">W tym przykładzie użyto `<param>` tag do opisywania `id` parametru.</span><span class="sxs-lookup"><span data-stu-id="3e1fa-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3e1fa-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e1fa-119">See Also</span></span>  
 [<span data-ttu-id="3e1fa-120">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="3e1fa-120">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
