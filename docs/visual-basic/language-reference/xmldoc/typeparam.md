---
title: <typeparam> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 014623be84f9d7eb8a25ac4aadcce450f158c154
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827240"
---
# <a name="typeparam-visual-basic"></a><span data-ttu-id="a5722-102">\<typeparam > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5722-102">\<typeparam> (Visual Basic)</span></span>
<span data-ttu-id="a5722-103">Definiuje typ parametru nazwę i opis.</span><span class="sxs-lookup"><span data-stu-id="a5722-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5722-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5722-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5722-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5722-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="a5722-106">Nazwa parametru typu.</span><span class="sxs-lookup"><span data-stu-id="a5722-106">The name of the type parameter.</span></span> <span data-ttu-id="a5722-107">Nazwę należy ująć w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="a5722-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="a5722-108">Opis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="a5722-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5722-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5722-109">Remarks</span></span>  
 <span data-ttu-id="a5722-110">Użyj `<typeparam>` tagu w komentarz dla typu ogólnego lub deklaracji ogólnej składowej, opisujący jeden z parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="a5722-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="a5722-111">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="a5722-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5722-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5722-112">Example</span></span>  
 <span data-ttu-id="a5722-113">W tym przykładzie użyto `<typeparam>` tag do opisania `id` parametru.</span><span class="sxs-lookup"><span data-stu-id="a5722-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="a5722-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5722-114">See also</span></span>

- [<span data-ttu-id="a5722-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="a5722-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
