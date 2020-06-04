---
title: <returns>
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: edbc374332bdcd67b385ac3d061045664e942460
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84399998"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="7618b-101">\<returns> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7618b-101">\<returns> (Visual Basic)</span></span>
<span data-ttu-id="7618b-102">Określa wartość zwracaną przez właściwość lub funkcję.</span><span class="sxs-lookup"><span data-stu-id="7618b-102">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7618b-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="7618b-103">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="7618b-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="7618b-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="7618b-105">Opis wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="7618b-105">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7618b-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7618b-106">Remarks</span></span>  
 <span data-ttu-id="7618b-107">Użyj `<returns>` znacznika w komentarzu dla deklaracji metody, aby opisać wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="7618b-107">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="7618b-108">Kompiluj z [-doc](../../reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="7618b-108">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7618b-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="7618b-109">Example</span></span>  
 <span data-ttu-id="7618b-110">W tym przykładzie używa `<returns>` znacznika, aby wyjaśnić, co `DoesRecordExist` zwraca funkcja.</span><span class="sxs-lookup"><span data-stu-id="7618b-110">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="7618b-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7618b-111">See also</span></span>

- [<span data-ttu-id="7618b-112">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="7618b-112">XML Comment Tags</span></span>](index.md)
