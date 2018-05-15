---
title: '&lt;zobacz&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: e790f8abd216e198ff5077beab6f857e39981d2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ltseegt-visual-basic"></a><span data-ttu-id="21497-102">&lt;zobacz&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21497-102">&lt;see&gt; (Visual Basic)</span></span>
<span data-ttu-id="21497-103">Określa łącze do innego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="21497-103">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21497-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="21497-104">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21497-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="21497-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="21497-106">Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywoływania z bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="21497-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="21497-107">Kompilator sprawdza, czy element podanego kodu istnieje i przekazuje `member` do nazwy elementu w danych wyjściowych XML.</span><span class="sxs-lookup"><span data-stu-id="21497-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="21497-108">`member` musi występować w podwójny cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="21497-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21497-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="21497-109">Remarks</span></span>  
 <span data-ttu-id="21497-110">Użyj `<see>` tag, aby określić łącze od w tekście.</span><span class="sxs-lookup"><span data-stu-id="21497-110">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="21497-111">Użyj [ \<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) wskazująca tekst, który ma być wyświetlany w sekcji "Zobacz też".</span><span class="sxs-lookup"><span data-stu-id="21497-111">Use [\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="21497-112">Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="21497-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21497-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="21497-113">Example</span></span>  
 <span data-ttu-id="21497-114">W tym przykładzie użyto `<see>` tagów w `UpdateRecord` uwagi sekcji, aby odwołać się do `DoesRecordExist` metody.</span><span class="sxs-lookup"><span data-stu-id="21497-114">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/see_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="21497-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="21497-115">See Also</span></span>  
 [<span data-ttu-id="21497-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="21497-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
