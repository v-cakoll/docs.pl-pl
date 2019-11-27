---
title: <typeparam>
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 00cb62827381146c172e0d15a2c64b167c21f025
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352189"
---
# <a name="typeparam-visual-basic"></a><span data-ttu-id="f8155-101">\<typeparam > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8155-101">\<typeparam> (Visual Basic)</span></span>
<span data-ttu-id="f8155-102">Definiuje nazwę i opis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="f8155-102">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8155-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8155-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8155-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8155-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="f8155-105">Nazwa parametru typu.</span><span class="sxs-lookup"><span data-stu-id="f8155-105">The name of the type parameter.</span></span> <span data-ttu-id="f8155-106">Ujmij nazwę w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="f8155-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="f8155-107">Opis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="f8155-107">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8155-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f8155-108">Remarks</span></span>  
 <span data-ttu-id="f8155-109">Użyj znacznika `<typeparam>` w komentarzu dla typu ogólnego lub ogólnej deklaracji elementu członkowskiego, aby opisać jeden z parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="f8155-109">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="f8155-110">Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="f8155-110">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8155-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8155-111">Example</span></span>  
 <span data-ttu-id="f8155-112">W tym przykładzie za pomocą tagu `<typeparam>` można opisać parametr `id`.</span><span class="sxs-lookup"><span data-stu-id="f8155-112">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="f8155-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8155-113">See also</span></span>

- [<span data-ttu-id="f8155-114">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="f8155-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
