---
title: <see>
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 3c149b8ff60bcc2aba06856ad95f461fb18da4b6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352226"
---
# <a name="see-visual-basic"></a><span data-ttu-id="0ce31-101">\<Zobacz > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ce31-101">\<see> (Visual Basic)</span></span>
<span data-ttu-id="0ce31-102">Określa łącze do innego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="0ce31-102">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ce31-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ce31-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ce31-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ce31-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="0ce31-105">Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0ce31-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="0ce31-106">Kompilator sprawdza, czy dany element kodu istnieje i przekazuje `member` do nazwy elementu w wyjściowym kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="0ce31-106">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="0ce31-107">`member` musi znajdować się w podwójnym cudzysłowie ("").</span><span class="sxs-lookup"><span data-stu-id="0ce31-107">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ce31-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ce31-108">Remarks</span></span>  
 <span data-ttu-id="0ce31-109">Użyj znacznika `<see>`, aby określić łącze z tekstu.</span><span class="sxs-lookup"><span data-stu-id="0ce31-109">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="0ce31-110">Użyj [\<seealso — >](../../../visual-basic/language-reference/xmldoc/seealso.md) , aby wskazać tekst, który może być wyświetlany w sekcji "Zobacz też".</span><span class="sxs-lookup"><span data-stu-id="0ce31-110">Use [\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="0ce31-111">Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="0ce31-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ce31-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="0ce31-112">Example</span></span>  
 <span data-ttu-id="0ce31-113">W tym przykładzie zastosowano tag `<see>` w sekcji `UpdateRecord` uwagi, aby odwołać się do metody `DoesRecordExist`.</span><span class="sxs-lookup"><span data-stu-id="0ce31-113">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="0ce31-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ce31-114">See also</span></span>

- [<span data-ttu-id="0ce31-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="0ce31-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
