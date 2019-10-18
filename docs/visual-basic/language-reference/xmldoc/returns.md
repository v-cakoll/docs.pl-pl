---
title: <returns> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: b220c2a9aa544413c3692485f6c1eb2b64e54389
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524681"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="01357-102">> \<returns (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01357-102">\<returns> (Visual Basic)</span></span>
<span data-ttu-id="01357-103">Określa wartość zwracaną przez właściwość lub funkcję.</span><span class="sxs-lookup"><span data-stu-id="01357-103">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01357-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="01357-104">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="01357-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01357-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="01357-106">Opis wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="01357-106">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01357-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01357-107">Remarks</span></span>  
 <span data-ttu-id="01357-108">Użyj znacznika `<returns>` w komentarzu dla deklaracji metody, aby opisać wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="01357-108">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="01357-109">Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="01357-109">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01357-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="01357-110">Example</span></span>  
 <span data-ttu-id="01357-111">W tym przykładzie używa znacznika `<returns>`, aby wyjaśnić, co zwraca funkcja `DoesRecordExist`.</span><span class="sxs-lookup"><span data-stu-id="01357-111">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="01357-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01357-112">See also</span></span>

- [<span data-ttu-id="01357-113">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="01357-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
