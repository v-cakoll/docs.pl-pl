---
title: <returns> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 0463d1b489fdad5e6af2d8eb20a1e68c77f57b4d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254967"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="4f556-102">\<Zwraca > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f556-102">\<returns> (Visual Basic)</span></span>
<span data-ttu-id="4f556-103">Określa wartość zwracaną właściwości lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="4f556-103">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f556-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4f556-104">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4f556-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4f556-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="4f556-106">Opis wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="4f556-106">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f556-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4f556-107">Remarks</span></span>  
 <span data-ttu-id="4f556-108">Użyj `<returns>` tagu w komentarzu do deklaracji metody opisać wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="4f556-108">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="4f556-109">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="4f556-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f556-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="4f556-110">Example</span></span>  
 <span data-ttu-id="4f556-111">W tym przykładzie użyto `<returns>` tag, aby wyjaśnić, co `DoesRecordExist` funkcja zwraca.</span><span class="sxs-lookup"><span data-stu-id="4f556-111">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/returns_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4f556-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f556-112">See also</span></span>
- [<span data-ttu-id="4f556-113">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="4f556-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
