---
title: <summary> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 531cac9bfec24577c22cb52962b2ac1eb740c5c8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975501"
---
# <a name="summary-visual-basic"></a><span data-ttu-id="07b94-102">\<Podsumowanie > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07b94-102">\<summary> (Visual Basic)</span></span>
<span data-ttu-id="07b94-103">Określa podsumowanie elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="07b94-103">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07b94-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="07b94-104">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="07b94-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="07b94-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="07b94-106">Podsumowanie obiektu.</span><span class="sxs-lookup"><span data-stu-id="07b94-106">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07b94-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="07b94-107">Remarks</span></span>  
 <span data-ttu-id="07b94-108">Użyj `<summary>` znaczników do opisu typu lub składowej typu.</span><span class="sxs-lookup"><span data-stu-id="07b94-108">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="07b94-109">Użyj [ \<Uwagi >](../../../visual-basic/language-reference/xmldoc/remarks.md) można dodać dodatkowe informacje do opisu typu.</span><span class="sxs-lookup"><span data-stu-id="07b94-109">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="07b94-110">Tekst dla `<summary>` tagu to jedyne źródło informacji o typie w technologii IntelliSense i jest wyświetlany w przeglądarce obiektów.</span><span class="sxs-lookup"><span data-stu-id="07b94-110">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="07b94-111">Aby uzyskać informacje o przeglądarce obiektów, zobacz [wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="07b94-111">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="07b94-112">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="07b94-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07b94-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="07b94-113">Example</span></span>  
 <span data-ttu-id="07b94-114">W tym przykładzie użyto `<summary>` tag do opisania `ResetCounter` metody i `Counter` właściwości.</span><span class="sxs-lookup"><span data-stu-id="07b94-114">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="07b94-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07b94-115">See also</span></span>
- [<span data-ttu-id="07b94-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="07b94-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
