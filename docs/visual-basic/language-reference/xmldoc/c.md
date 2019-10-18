---
title: <c> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 4ea19ed5330dcbb8fcd84708d1546a81d909b04e
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523943"
---
# <a name="c-visual-basic"></a><span data-ttu-id="efc6c-102">> \<c (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efc6c-102">\<c> (Visual Basic)</span></span>
<span data-ttu-id="efc6c-103">Wskazuje, że tekst w opisie ma kod.</span><span class="sxs-lookup"><span data-stu-id="efc6c-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efc6c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="efc6c-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="efc6c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="efc6c-105">Parameters</span></span>  
  
|<span data-ttu-id="efc6c-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="efc6c-106">Parameter</span></span>|<span data-ttu-id="efc6c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="efc6c-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="efc6c-108">Tekst, który ma być wskazywany jako kod.</span><span class="sxs-lookup"><span data-stu-id="efc6c-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="efc6c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="efc6c-109">Remarks</span></span>  
 <span data-ttu-id="efc6c-110">Tag `<c>` umożliwia wskazanie, że tekst w opisie powinien być oznaczony jako kod.</span><span class="sxs-lookup"><span data-stu-id="efc6c-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="efc6c-111">Użyj [> \<code](../../../visual-basic/language-reference/xmldoc/code.md) , aby wskazać wiele wierszy jako kod.</span><span class="sxs-lookup"><span data-stu-id="efc6c-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="efc6c-112">Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="efc6c-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="efc6c-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="efc6c-113">Example</span></span>  
 <span data-ttu-id="efc6c-114">W poniższym przykładzie zastosowano tag `<c>` w sekcji Podsumowanie, aby wskazać, że `Counter` jest kodem.</span><span class="sxs-lookup"><span data-stu-id="efc6c-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="efc6c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="efc6c-115">See also</span></span>

- [<span data-ttu-id="efc6c-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="efc6c-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
