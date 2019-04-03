---
title: <see> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 828e55e0ddb0382c16c60ae3d9e5958c18e42c10
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821340"
---
# <a name="see-visual-basic"></a><span data-ttu-id="0e0ab-102">\<zobacz > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e0ab-102">\<see> (Visual Basic)</span></span>
<span data-ttu-id="0e0ab-103">Określa łącze do innego członka.</span><span class="sxs-lookup"><span data-stu-id="0e0ab-103">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e0ab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0e0ab-104">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e0ab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0e0ab-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="0e0ab-106">Odwołanie do elementu członkowskiego lub pola, które są dostępne do wywoływania z bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0e0ab-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="0e0ab-107">Kompilator sprawdza, czy dany element kodu istnieje i przekazuje `member` do nazwy elementu w danych wyjściowych XML.</span><span class="sxs-lookup"><span data-stu-id="0e0ab-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="0e0ab-108">`member` musi znajdować się w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="0e0ab-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e0ab-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0e0ab-109">Remarks</span></span>  
 <span data-ttu-id="0e0ab-110">Użyj `<see>` tag, aby określić link z w tekście.</span><span class="sxs-lookup"><span data-stu-id="0e0ab-110">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="0e0ab-111">Użyj [ \<SeeAlso — >](../../../visual-basic/language-reference/xmldoc/seealso.md) do wskazania tekst, który ma być wyświetlane w sekcji "Zobacz też".</span><span class="sxs-lookup"><span data-stu-id="0e0ab-111">Use [\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="0e0ab-112">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="0e0ab-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e0ab-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="0e0ab-113">Example</span></span>  
 <span data-ttu-id="0e0ab-114">W tym przykładzie użyto `<see>` tagów w `UpdateRecord` uwagi sekcji do odwoływania się do `DoesRecordExist` metody.</span><span class="sxs-lookup"><span data-stu-id="0e0ab-114">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="0e0ab-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e0ab-115">See also</span></span>

- [<span data-ttu-id="0e0ab-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="0e0ab-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
