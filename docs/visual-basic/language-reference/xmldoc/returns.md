---
title: <returns> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 5a0ff0da7cf26a1cea75a5b2e4678593d9b72f54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940793"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="06b77-102">\<Zwraca > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06b77-102">\<returns> (Visual Basic)</span></span>
<span data-ttu-id="06b77-103">Określa wartość zwracaną właściwości lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="06b77-103">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06b77-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="06b77-104">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="06b77-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06b77-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="06b77-106">Opis wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="06b77-106">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06b77-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06b77-107">Remarks</span></span>  
 <span data-ttu-id="06b77-108">Użyj `<returns>` tagu w komentarzu do deklaracji metody opisać wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="06b77-108">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="06b77-109">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="06b77-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06b77-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="06b77-110">Example</span></span>  
 <span data-ttu-id="06b77-111">W tym przykładzie użyto `<returns>` tag, aby wyjaśnić, co `DoesRecordExist` funkcja zwraca.</span><span class="sxs-lookup"><span data-stu-id="06b77-111">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="06b77-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06b77-112">See also</span></span>

- [<span data-ttu-id="06b77-113">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="06b77-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
