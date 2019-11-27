---
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 1cbac2162bd39cdc8af9a55dfd6e2f90bc40b08a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354323"
---
# <a name="code-visual-basic"></a><span data-ttu-id="ff623-101">> kodu \<(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff623-101">\<code> (Visual Basic)</span></span>
<span data-ttu-id="ff623-102">Wskazuje, że tekst jest wieloma wierszami kodu.</span><span class="sxs-lookup"><span data-stu-id="ff623-102">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff623-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff623-103">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff623-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff623-104">Parameters</span></span>  
 `content`  
 <span data-ttu-id="ff623-105">Tekst, który ma zostać oznaczony jako kod.</span><span class="sxs-lookup"><span data-stu-id="ff623-105">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff623-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ff623-106">Remarks</span></span>  
 <span data-ttu-id="ff623-107">Użyj znacznika `<code>`, aby wskazać wiele wierszy jako kod.</span><span class="sxs-lookup"><span data-stu-id="ff623-107">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="ff623-108">Użyj [\<c >](../../../visual-basic/language-reference/xmldoc/c.md) , aby wskazać, że tekst w opisie powinien być oznaczony jako kod.</span><span class="sxs-lookup"><span data-stu-id="ff623-108">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="ff623-109">Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="ff623-109">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff623-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="ff623-110">Example</span></span>  
 <span data-ttu-id="ff623-111">W tym przykładzie użyto tagu \<Code >, aby dołączyć przykładowy kod do użycia pola `ID`.</span><span class="sxs-lookup"><span data-stu-id="ff623-111">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ff623-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff623-112">See also</span></span>

- [<span data-ttu-id="ff623-113">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="ff623-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
