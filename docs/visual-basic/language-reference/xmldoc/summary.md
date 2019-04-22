---
title: <summary> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 0fbe07884f55b7e6f460929e54520de5f718e1af
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58815008"
---
# <a name="summary-visual-basic"></a><span data-ttu-id="e9a2b-102">\<Podsumowanie > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9a2b-102">\<summary> (Visual Basic)</span></span>
<span data-ttu-id="e9a2b-103">Określa podsumowanie elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="e9a2b-103">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9a2b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9a2b-104">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9a2b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9a2b-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="e9a2b-106">Podsumowanie obiektu.</span><span class="sxs-lookup"><span data-stu-id="e9a2b-106">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9a2b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e9a2b-107">Remarks</span></span>  
 <span data-ttu-id="e9a2b-108">Użyj `<summary>` znaczników do opisu typu lub składowej typu.</span><span class="sxs-lookup"><span data-stu-id="e9a2b-108">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="e9a2b-109">Użyj [ \<Uwagi >](../../../visual-basic/language-reference/xmldoc/remarks.md) można dodać dodatkowe informacje do opisu typu.</span><span class="sxs-lookup"><span data-stu-id="e9a2b-109">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="e9a2b-110">Tekst dla `<summary>` tagu to jedyne źródło informacji o typie w technologii IntelliSense i jest wyświetlany w przeglądarce obiektów.</span><span class="sxs-lookup"><span data-stu-id="e9a2b-110">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="e9a2b-111">Aby uzyskać informacje o przeglądarce obiektów, zobacz [wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="e9a2b-111">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="e9a2b-112">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="e9a2b-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9a2b-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9a2b-113">Example</span></span>  
 <span data-ttu-id="e9a2b-114">W tym przykładzie użyto `<summary>` tag do opisania `ResetCounter` metody i `Counter` właściwości.</span><span class="sxs-lookup"><span data-stu-id="e9a2b-114">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e9a2b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9a2b-115">See also</span></span>

- [<span data-ttu-id="e9a2b-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="e9a2b-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
