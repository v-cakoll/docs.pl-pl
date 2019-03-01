---
title: <returns> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 96b9754332b7b9c6c7823aecab6a93b0aa7ffd21
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975462"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="bf39d-102">\<Zwraca > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf39d-102">\<returns> (Visual Basic)</span></span>
<span data-ttu-id="bf39d-103">Określa wartość zwracaną właściwości lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="bf39d-103">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf39d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf39d-104">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bf39d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf39d-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="bf39d-106">Opis wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="bf39d-106">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf39d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf39d-107">Remarks</span></span>  
 <span data-ttu-id="bf39d-108">Użyj `<returns>` tagu w komentarzu do deklaracji metody opisać wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="bf39d-108">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="bf39d-109">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="bf39d-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf39d-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="bf39d-110">Example</span></span>  
 <span data-ttu-id="bf39d-111">W tym przykładzie użyto `<returns>` tag, aby wyjaśnić, co `DoesRecordExist` funkcja zwraca.</span><span class="sxs-lookup"><span data-stu-id="bf39d-111">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="bf39d-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf39d-112">See also</span></span>
- [<span data-ttu-id="bf39d-113">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="bf39d-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
