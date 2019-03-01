---
title: <seealso> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 9f857be6d0bd46233a49c7d2ff0931670baa95a6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965306"
---
# <a name="seealso-visual-basic"></a><span data-ttu-id="93003-102">\<seealso> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93003-102">\<seealso> (Visual Basic)</span></span>
<span data-ttu-id="93003-103">Określa łącze, które pojawia się w sekcji Zobacz też.</span><span class="sxs-lookup"><span data-stu-id="93003-103">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93003-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="93003-104">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93003-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="93003-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="93003-106">Odwołanie do elementu członkowskiego lub pola, które są dostępne do wywoływania z bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="93003-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="93003-107">Kompilator sprawdza, czy dany element kodu istnieje i przekazuje `member` do nazwy elementu w danych wyjściowych XML.</span><span class="sxs-lookup"><span data-stu-id="93003-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="93003-108">`member` musi znajdować się w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="93003-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93003-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93003-109">Remarks</span></span>  
 <span data-ttu-id="93003-110">Użyj `<seealso>` tag, aby określić tekst, który ma być wyświetlany w sekcji Zobacz też.</span><span class="sxs-lookup"><span data-stu-id="93003-110">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="93003-111">Użyj [ \<zobacz >](../../../visual-basic/language-reference/xmldoc/see.md) określić łącze między w tekście.</span><span class="sxs-lookup"><span data-stu-id="93003-111">Use [\<see>](../../../visual-basic/language-reference/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="93003-112">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="93003-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93003-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="93003-113">Example</span></span>  
 <span data-ttu-id="93003-114">W tym przykładzie użyto `<seealso>` tagów w `DoesRecordExist` uwagi sekcji do odwoływania się do `UpdateRecord` metody.</span><span class="sxs-lookup"><span data-stu-id="93003-114">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="93003-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93003-115">See also</span></span>
- [<span data-ttu-id="93003-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="93003-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
