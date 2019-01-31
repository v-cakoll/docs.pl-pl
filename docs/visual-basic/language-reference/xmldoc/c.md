---
title: <c> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 2fa6e66771ac854421d07a5f33e116f12516dad6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260207"
---
# <a name="c-visual-basic"></a><span data-ttu-id="32bca-102">\<c > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32bca-102">\<c> (Visual Basic)</span></span>
<span data-ttu-id="32bca-103">Wskazuje, że tekst w ciągu opisu jest kod.</span><span class="sxs-lookup"><span data-stu-id="32bca-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32bca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32bca-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32bca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32bca-105">Parameters</span></span>  
  
|<span data-ttu-id="32bca-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="32bca-106">Parameter</span></span>|<span data-ttu-id="32bca-107">Opis</span><span class="sxs-lookup"><span data-stu-id="32bca-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="32bca-108">Tekst, który chcesz wskazać jako kod.</span><span class="sxs-lookup"><span data-stu-id="32bca-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32bca-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="32bca-109">Remarks</span></span>  
 <span data-ttu-id="32bca-110">`<c>` Tag zapewnia sposób, aby wskazać, że tekst w opis powinien być oznaczony jako kod.</span><span class="sxs-lookup"><span data-stu-id="32bca-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="32bca-111">Użyj [ \<kodu >](../../../visual-basic/language-reference/xmldoc/code.md) aby wskazać wiele wierszy, jako kod.</span><span class="sxs-lookup"><span data-stu-id="32bca-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="32bca-112">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="32bca-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32bca-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="32bca-113">Example</span></span>  
 <span data-ttu-id="32bca-114">W tym przykładzie użyto `<c>` tagu w sekcji podsumowania w celu wskazania, że `Counter` jest kod.</span><span class="sxs-lookup"><span data-stu-id="32bca-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/c_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="32bca-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32bca-115">See also</span></span>
- [<span data-ttu-id="32bca-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="32bca-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
