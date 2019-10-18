---
title: <see> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: e3ae5fb63540e47e5b8da2e2d60d5bd736e019d7
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524660"
---
# <a name="see-visual-basic"></a><span data-ttu-id="05b58-102">> \<see (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05b58-102">\<see> (Visual Basic)</span></span>
<span data-ttu-id="05b58-103">Określa łącze do innego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="05b58-103">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05b58-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="05b58-104">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="05b58-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05b58-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="05b58-106">Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji.</span><span class="sxs-lookup"><span data-stu-id="05b58-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="05b58-107">Kompilator sprawdza, czy dany element kodu istnieje i przekazuje `member` do nazwy elementu w wyjściowym kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="05b58-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="05b58-108">`member` musi znajdować się w podwójnym cudzysłowie ("").</span><span class="sxs-lookup"><span data-stu-id="05b58-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05b58-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05b58-109">Remarks</span></span>  
 <span data-ttu-id="05b58-110">Użyj znacznika `<see>`, aby określić łącze z tekstu.</span><span class="sxs-lookup"><span data-stu-id="05b58-110">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="05b58-111">Użyj [> \<seealso](../../../visual-basic/language-reference/xmldoc/seealso.md) , aby wskazać tekst, który może być wyświetlany w sekcji "Zobacz też".</span><span class="sxs-lookup"><span data-stu-id="05b58-111">Use [\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="05b58-112">Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="05b58-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05b58-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="05b58-113">Example</span></span>  
 <span data-ttu-id="05b58-114">W tym przykładzie zastosowano tag `<see>` w sekcji `UpdateRecord` uwagi, aby odwołać się do metody `DoesRecordExist`.</span><span class="sxs-lookup"><span data-stu-id="05b58-114">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="05b58-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05b58-115">See also</span></span>

- [<span data-ttu-id="05b58-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="05b58-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
