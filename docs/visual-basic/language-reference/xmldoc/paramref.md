---
title: '&lt;paramref&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3bf3d4f04997a03f442cf7fd2a1586604198d3fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltparamrefgt-visual-basic"></a><span data-ttu-id="35349-102">&lt;paramref&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35349-102">&lt;paramref&gt; (Visual Basic)</span></span>
<span data-ttu-id="35349-103">Formatuje wyraz jako parametr.</span><span class="sxs-lookup"><span data-stu-id="35349-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35349-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="35349-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="35349-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="35349-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="35349-106">Nazwa parametru do odwoływania się do.</span><span class="sxs-lookup"><span data-stu-id="35349-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="35349-107">Nazwę należy ująć w podwójny cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="35349-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35349-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="35349-108">Remarks</span></span>  
 <span data-ttu-id="35349-109">`<paramref>` Tag udostępnia sposób wskazują, że wyraz jest parametrem.</span><span class="sxs-lookup"><span data-stu-id="35349-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="35349-110">Aby sformatować ten parametr w jakiś sposób różne mogą być przetwarzane plik XML.</span><span class="sxs-lookup"><span data-stu-id="35349-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="35349-111">Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="35349-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35349-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="35349-112">Example</span></span>  
 <span data-ttu-id="35349-113">W tym przykładzie użyto `<paramref>` tag do odwoływania się do `id` parametru.</span><span class="sxs-lookup"><span data-stu-id="35349-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="35349-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="35349-114">See Also</span></span>  
 [<span data-ttu-id="35349-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="35349-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
