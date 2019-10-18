---
title: <typeparam> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: dbd99997fed33c192a2160fb45a739addbae254a
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524621"
---
# <a name="typeparam-visual-basic"></a><span data-ttu-id="c75b4-102">> \<typeparam (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c75b4-102">\<typeparam> (Visual Basic)</span></span>
<span data-ttu-id="c75b4-103">Definiuje nazwę i opis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="c75b4-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c75b4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c75b4-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="c75b4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c75b4-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="c75b4-106">Nazwa parametru typu.</span><span class="sxs-lookup"><span data-stu-id="c75b4-106">The name of the type parameter.</span></span> <span data-ttu-id="c75b4-107">Ujmij nazwę w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="c75b4-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="c75b4-108">Opis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="c75b4-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c75b4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c75b4-109">Remarks</span></span>  
 <span data-ttu-id="c75b4-110">Użyj znacznika `<typeparam>` w komentarzu dla typu ogólnego lub ogólnej deklaracji elementu członkowskiego, aby opisać jeden z parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="c75b4-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="c75b4-111">Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="c75b4-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c75b4-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="c75b4-112">Example</span></span>  
 <span data-ttu-id="c75b4-113">W tym przykładzie za pomocą tagu `<typeparam>` można opisać parametr `id`.</span><span class="sxs-lookup"><span data-stu-id="c75b4-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="c75b4-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c75b4-114">See also</span></span>

- [<span data-ttu-id="c75b4-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="c75b4-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
