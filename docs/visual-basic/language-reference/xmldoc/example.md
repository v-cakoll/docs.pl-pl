---
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 42f40581d252956433165789d6674234a295867c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400149"
---
# <a name="example-visual-basic"></a><span data-ttu-id="508d6-101">\<example> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="508d6-101">\<example> (Visual Basic)</span></span>
<span data-ttu-id="508d6-102">Określa przykład dla elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="508d6-102">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="508d6-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="508d6-103">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a><span data-ttu-id="508d6-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="508d6-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="508d6-105">Opis przykładu kodu.</span><span class="sxs-lookup"><span data-stu-id="508d6-105">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="508d6-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="508d6-106">Remarks</span></span>  
 <span data-ttu-id="508d6-107">`<example>`Tag pozwala określić przykład użycia metody lub innego elementu członkowskiego biblioteki.</span><span class="sxs-lookup"><span data-stu-id="508d6-107">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="508d6-108">Zwykle obejmuje to użycie [\<code>](code.md) znacznika.</span><span class="sxs-lookup"><span data-stu-id="508d6-108">This commonly involves using the [\<code>](code.md) tag.</span></span>  
  
 <span data-ttu-id="508d6-109">Kompiluj z [-doc](../../reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="508d6-109">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="508d6-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="508d6-110">Example</span></span>  
 <span data-ttu-id="508d6-111">W tym przykładzie użyto `<example>` znacznika, aby dołączyć przykład do użycia `ID` pola.</span><span class="sxs-lookup"><span data-stu-id="508d6-111">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="508d6-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="508d6-112">See also</span></span>

- [<span data-ttu-id="508d6-113">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="508d6-113">XML Comment Tags</span></span>](index.md)
