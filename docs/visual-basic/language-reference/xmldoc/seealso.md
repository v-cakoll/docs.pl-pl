---
title: <seealso> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 0231ff748949874f4b477cac15d891d313b25f4f
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524647"
---
# <a name="seealso-visual-basic"></a><span data-ttu-id="6028e-102">> \<seealso (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6028e-102">\<seealso> (Visual Basic)</span></span>
<span data-ttu-id="6028e-103">Określa łącze, które pojawia się w sekcji Zobacz też.</span><span class="sxs-lookup"><span data-stu-id="6028e-103">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6028e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6028e-104">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="6028e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6028e-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="6028e-106">Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6028e-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="6028e-107">Kompilator sprawdza, czy dany element kodu istnieje i przekazuje `member` do nazwy elementu w wyjściowym kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="6028e-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="6028e-108">`member` musi znajdować się w podwójnym cudzysłowie ("").</span><span class="sxs-lookup"><span data-stu-id="6028e-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6028e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6028e-109">Remarks</span></span>  
 <span data-ttu-id="6028e-110">Użyj znacznika `<seealso>`, aby określić tekst, który ma być wyświetlany w sekcji Zobacz też.</span><span class="sxs-lookup"><span data-stu-id="6028e-110">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="6028e-111">Użyj [> \<see](../../../visual-basic/language-reference/xmldoc/see.md) , aby określić łącze z poziomu tekstu.</span><span class="sxs-lookup"><span data-stu-id="6028e-111">Use [\<see>](../../../visual-basic/language-reference/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="6028e-112">Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="6028e-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6028e-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="6028e-113">Example</span></span>  
 <span data-ttu-id="6028e-114">W tym przykładzie zastosowano tag `<seealso>` w sekcji `DoesRecordExist` uwagi, aby odwołać się do metody `UpdateRecord`.</span><span class="sxs-lookup"><span data-stu-id="6028e-114">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="6028e-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6028e-115">See also</span></span>

- [<span data-ttu-id="6028e-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="6028e-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
