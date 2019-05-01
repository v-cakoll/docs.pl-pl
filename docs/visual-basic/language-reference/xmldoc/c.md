---
title: <c> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 9be9f9e96fc1b79ea97d54c54352da63b93ef264
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938596"
---
# <a name="c-visual-basic"></a><span data-ttu-id="345d9-102">\<c > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="345d9-102">\<c> (Visual Basic)</span></span>
<span data-ttu-id="345d9-103">Wskazuje, że tekst w ciągu opisu jest kod.</span><span class="sxs-lookup"><span data-stu-id="345d9-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="345d9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="345d9-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="345d9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="345d9-105">Parameters</span></span>  
  
|<span data-ttu-id="345d9-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="345d9-106">Parameter</span></span>|<span data-ttu-id="345d9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="345d9-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="345d9-108">Tekst, który chcesz wskazać jako kod.</span><span class="sxs-lookup"><span data-stu-id="345d9-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="345d9-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="345d9-109">Remarks</span></span>  
 <span data-ttu-id="345d9-110">`<c>` Tag zapewnia sposób, aby wskazać, że tekst w opis powinien być oznaczony jako kod.</span><span class="sxs-lookup"><span data-stu-id="345d9-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="345d9-111">Użyj [ \<kodu >](../../../visual-basic/language-reference/xmldoc/code.md) aby wskazać wiele wierszy, jako kod.</span><span class="sxs-lookup"><span data-stu-id="345d9-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="345d9-112">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="345d9-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="345d9-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="345d9-113">Example</span></span>  
 <span data-ttu-id="345d9-114">W tym przykładzie użyto `<c>` tagu w sekcji podsumowania w celu wskazania, że `Counter` jest kod.</span><span class="sxs-lookup"><span data-stu-id="345d9-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="345d9-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="345d9-115">See also</span></span>

- [<span data-ttu-id="345d9-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="345d9-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
