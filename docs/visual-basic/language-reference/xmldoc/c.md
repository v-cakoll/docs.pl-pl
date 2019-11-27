---
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 857ea1ccca4d74daf65bba03845004561afefd55
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348509"
---
# <a name="c-visual-basic"></a><span data-ttu-id="41131-101">> \<c (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41131-101">\<c> (Visual Basic)</span></span>
<span data-ttu-id="41131-102">Wskazuje, że tekst w opisie ma kod.</span><span class="sxs-lookup"><span data-stu-id="41131-102">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41131-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="41131-103">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="41131-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="41131-104">Parameters</span></span>  
  
|<span data-ttu-id="41131-105">Parametr</span><span class="sxs-lookup"><span data-stu-id="41131-105">Parameter</span></span>|<span data-ttu-id="41131-106">Opis</span><span class="sxs-lookup"><span data-stu-id="41131-106">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="41131-107">Tekst, który ma być wskazywany jako kod.</span><span class="sxs-lookup"><span data-stu-id="41131-107">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41131-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41131-108">Remarks</span></span>  
 <span data-ttu-id="41131-109">Tag `<c>` umożliwia wskazanie, że tekst w opisie powinien być oznaczony jako kod.</span><span class="sxs-lookup"><span data-stu-id="41131-109">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="41131-110">Użyj [\<kodu >](../../../visual-basic/language-reference/xmldoc/code.md) , aby wskazać wiele wierszy jako kod.</span><span class="sxs-lookup"><span data-stu-id="41131-110">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="41131-111">Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="41131-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41131-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="41131-112">Example</span></span>  
 <span data-ttu-id="41131-113">W poniższym przykładzie zastosowano tag `<c>` w sekcji Podsumowanie, aby wskazać, że `Counter` jest kodem.</span><span class="sxs-lookup"><span data-stu-id="41131-113">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="41131-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41131-114">See also</span></span>

- [<span data-ttu-id="41131-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="41131-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
