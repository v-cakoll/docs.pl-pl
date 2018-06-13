---
title: '&lt;Podsumowanie&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: cf320b61a2ca1c54b22e3c3d31ae51d003366efd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602655"
---
# <a name="ltsummarygt-visual-basic"></a><span data-ttu-id="e1cc7-102">&lt;Podsumowanie&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1cc7-102">&lt;summary&gt; (Visual Basic)</span></span>
<span data-ttu-id="e1cc7-103">Określa podsumowanie elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="e1cc7-103">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1cc7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1cc7-104">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1cc7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1cc7-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="e1cc7-106">Podsumowanie obiektu.</span><span class="sxs-lookup"><span data-stu-id="e1cc7-106">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1cc7-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e1cc7-107">Remarks</span></span>  
 <span data-ttu-id="e1cc7-108">Użyj `<summary>` tag do opisu typu lub członka typu.</span><span class="sxs-lookup"><span data-stu-id="e1cc7-108">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="e1cc7-109">Użyj [ \<Uwagi >](../../../visual-basic/language-reference/xmldoc/remarks.md) można dodać dodatkowe informacje do opisu typu.</span><span class="sxs-lookup"><span data-stu-id="e1cc7-109">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="e1cc7-110">Tekst dla `<summary>` tag jest jedynym źródłem informacji o typie w IntelliSense i jest wyświetlany w przeglądarce obiektów.</span><span class="sxs-lookup"><span data-stu-id="e1cc7-110">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="e1cc7-111">Informacje o przeglądarce obiektów, zobacz [wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="e1cc7-111">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="e1cc7-112">Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="e1cc7-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1cc7-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1cc7-113">Example</span></span>  
 <span data-ttu-id="e1cc7-114">W tym przykładzie użyto `<summary>` tag do opisywania `ResetCounter` — metoda i `Counter` właściwości.</span><span class="sxs-lookup"><span data-stu-id="e1cc7-114">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e1cc7-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1cc7-115">See Also</span></span>  
 [<span data-ttu-id="e1cc7-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="e1cc7-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
