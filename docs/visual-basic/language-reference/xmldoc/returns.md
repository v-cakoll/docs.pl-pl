---
title: '&lt;Zwraca&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 47debcef2c6ce56fda4c4a0818c8e813b41ebad1
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925021"
---
# <a name="ltreturnsgt-visual-basic"></a><span data-ttu-id="4ea24-102">&lt;Zwraca&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ea24-102">&lt;returns&gt; (Visual Basic)</span></span>
<span data-ttu-id="4ea24-103">Określa wartość zwracaną właściwości lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="4ea24-103">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ea24-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ea24-104">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4ea24-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4ea24-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="4ea24-106">Opis wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="4ea24-106">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ea24-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ea24-107">Remarks</span></span>  
 <span data-ttu-id="4ea24-108">Użyj `<returns>` tagu w komentarzu do deklaracji metody opisać wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="4ea24-108">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="4ea24-109">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="4ea24-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ea24-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ea24-110">Example</span></span>  
 <span data-ttu-id="4ea24-111">W tym przykładzie użyto `<returns>` tag, aby wyjaśnić, co `DoesRecordExist` funkcja zwraca.</span><span class="sxs-lookup"><span data-stu-id="4ea24-111">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/returns_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4ea24-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ea24-112">See Also</span></span>  
 [<span data-ttu-id="4ea24-113">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="4ea24-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
