---
title: '&lt;Podsumowanie&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 899a3343d9758aab79f5aaa77ede26e92f8c07ae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54551013"
---
# <a name="ltsummarygt-visual-basic"></a><span data-ttu-id="7c80d-102">&lt;Podsumowanie&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c80d-102">&lt;summary&gt; (Visual Basic)</span></span>
<span data-ttu-id="7c80d-103">Określa podsumowanie elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="7c80d-103">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c80d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c80d-104">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7c80d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c80d-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="7c80d-106">Podsumowanie obiektu.</span><span class="sxs-lookup"><span data-stu-id="7c80d-106">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c80d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c80d-107">Remarks</span></span>  
 <span data-ttu-id="7c80d-108">Użyj `<summary>` znaczników do opisu typu lub składowej typu.</span><span class="sxs-lookup"><span data-stu-id="7c80d-108">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="7c80d-109">Użyj [ \<Uwagi >](../../../visual-basic/language-reference/xmldoc/remarks.md) można dodać dodatkowe informacje do opisu typu.</span><span class="sxs-lookup"><span data-stu-id="7c80d-109">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="7c80d-110">Tekst dla `<summary>` tagu to jedyne źródło informacji o typie w technologii IntelliSense i jest wyświetlany w przeglądarce obiektów.</span><span class="sxs-lookup"><span data-stu-id="7c80d-110">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="7c80d-111">Aby uzyskać informacje o przeglądarce obiektów, zobacz [wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="7c80d-111">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="7c80d-112">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="7c80d-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c80d-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c80d-113">Example</span></span>  
 <span data-ttu-id="7c80d-114">W tym przykładzie użyto `<summary>` tag do opisania `ResetCounter` metody i `Counter` właściwości.</span><span class="sxs-lookup"><span data-stu-id="7c80d-114">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7c80d-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c80d-115">See also</span></span>
- [<span data-ttu-id="7c80d-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="7c80d-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
