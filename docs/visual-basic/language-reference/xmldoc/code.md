---
title: <code> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: d4e887e3bbbc01e4cef5278f67b8c4afe273bf28
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524033"
---
# <a name="code-visual-basic"></a><span data-ttu-id="e6ba5-101">> \<code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6ba5-101">\<code> (Visual Basic)</span></span>
<span data-ttu-id="e6ba5-102">Wskazuje, że tekst jest wieloma wierszami kodu.</span><span class="sxs-lookup"><span data-stu-id="e6ba5-102">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6ba5-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="e6ba5-103">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6ba5-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="e6ba5-104">Parameters</span></span>  
 `content`  
 <span data-ttu-id="e6ba5-105">Tekst, który ma zostać oznaczony jako kod.</span><span class="sxs-lookup"><span data-stu-id="e6ba5-105">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6ba5-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e6ba5-106">Remarks</span></span>  
 <span data-ttu-id="e6ba5-107">Użyj znacznika `<code>`, aby wskazać wiele wierszy jako kod.</span><span class="sxs-lookup"><span data-stu-id="e6ba5-107">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="e6ba5-108">Użyj [> \<c](../../../visual-basic/language-reference/xmldoc/c.md) , aby wskazać, że tekst w opisie powinien być oznaczony jako kod.</span><span class="sxs-lookup"><span data-stu-id="e6ba5-108">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="e6ba5-109">Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="e6ba5-109">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6ba5-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="e6ba5-110">Example</span></span>  
 <span data-ttu-id="e6ba5-111">W tym przykładzie użyto znacznika > \<code, aby dołączyć przykładowy kod do użycia pola `ID`.</span><span class="sxs-lookup"><span data-stu-id="e6ba5-111">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e6ba5-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6ba5-112">See also</span></span>

- [<span data-ttu-id="e6ba5-113">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="e6ba5-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
