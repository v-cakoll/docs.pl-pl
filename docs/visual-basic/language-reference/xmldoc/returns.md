---
title: '&lt;Zwraca&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6130a6fabe450900fe19ef4d361654508f907ea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltreturnsgt-visual-basic"></a><span data-ttu-id="00d96-102">&lt;Zwraca&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00d96-102">&lt;returns&gt; (Visual Basic)</span></span>
<span data-ttu-id="00d96-103">Określa wartość zwracaną właściwości lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="00d96-103">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00d96-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="00d96-104">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00d96-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00d96-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="00d96-106">Opis wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="00d96-106">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00d96-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="00d96-107">Remarks</span></span>  
 <span data-ttu-id="00d96-108">Użyj `<returns>` tag w komentarz dla deklaracji metody do opisywania wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="00d96-108">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="00d96-109">Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="00d96-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00d96-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="00d96-110">Example</span></span>  
 <span data-ttu-id="00d96-111">W tym przykładzie użyto `<returns>` tag, aby wyjaśnić, co `DoesRecordExist` funkcja zwraca.</span><span class="sxs-lookup"><span data-stu-id="00d96-111">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/returns_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="00d96-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="00d96-112">See Also</span></span>  
 [<span data-ttu-id="00d96-113">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="00d96-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
