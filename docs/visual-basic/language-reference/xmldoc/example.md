---
title: "&lt;przykład&gt; (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e34b75f4ce924a35dd5396b449730316025a9f35
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltexamplegt-visual-basic"></a><span data-ttu-id="2cb37-102">&lt;przykład&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cb37-102">&lt;example&gt; (Visual Basic)</span></span>
<span data-ttu-id="2cb37-103">Określa przykład elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="2cb37-103">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cb37-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2cb37-104">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2cb37-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2cb37-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="2cb37-106">Opis przykładowego kodu.</span><span class="sxs-lookup"><span data-stu-id="2cb37-106">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cb37-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2cb37-107">Remarks</span></span>  
 <span data-ttu-id="2cb37-108">`<example>` Należy określić przykładem przedstawiającym sposób użycia metody lub innego członka biblioteki.</span><span class="sxs-lookup"><span data-stu-id="2cb37-108">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="2cb37-109">Obejmuje to zwykle, za pomocą [ \<kod >](../../../visual-basic/language-reference/xmldoc/code.md) tagu.</span><span class="sxs-lookup"><span data-stu-id="2cb37-109">This commonly involves using the [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) tag.</span></span>  
  
 <span data-ttu-id="2cb37-110">Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="2cb37-110">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cb37-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="2cb37-111">Example</span></span>  
 <span data-ttu-id="2cb37-112">W tym przykładzie użyto `<example>` tag do uwzględnienia na przykład za pomocą `ID` pola.</span><span class="sxs-lookup"><span data-stu-id="2cb37-112">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/example_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2cb37-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2cb37-113">See Also</span></span>  
 [<span data-ttu-id="2cb37-114">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="2cb37-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
