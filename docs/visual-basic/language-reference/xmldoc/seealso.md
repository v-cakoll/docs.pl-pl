---
title: '&lt;SeeAlso —&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: a792bbea108bcdf33d430c47773466ef3dccdb0c
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46539995"
---
# <a name="ltseealsogt-visual-basic"></a><span data-ttu-id="9a8f9-102">&lt;SeeAlso —&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a8f9-102">&lt;seealso&gt; (Visual Basic)</span></span>
<span data-ttu-id="9a8f9-103">Określa łącze, które pojawia się w sekcji Zobacz też.</span><span class="sxs-lookup"><span data-stu-id="9a8f9-103">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a8f9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a8f9-104">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a8f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a8f9-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="9a8f9-106">Odwołanie do elementu członkowskiego lub pola, które są dostępne do wywoływania z bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9a8f9-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="9a8f9-107">Kompilator sprawdza, czy dany element kodu istnieje i przekazuje `member` do nazwy elementu w danych wyjściowych XML.</span><span class="sxs-lookup"><span data-stu-id="9a8f9-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="9a8f9-108">`member` musi znajdować się w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="9a8f9-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a8f9-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a8f9-109">Remarks</span></span>  
 <span data-ttu-id="9a8f9-110">Użyj `<seealso>` tag, aby określić tekst, który ma być wyświetlany w sekcji Zobacz też.</span><span class="sxs-lookup"><span data-stu-id="9a8f9-110">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="9a8f9-111">Użyj [ \<zobacz >](../../../visual-basic/language-reference/xmldoc/see.md) określić łącze między w tekście.</span><span class="sxs-lookup"><span data-stu-id="9a8f9-111">Use [\<see>](../../../visual-basic/language-reference/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="9a8f9-112">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="9a8f9-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a8f9-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a8f9-113">Example</span></span>  
 <span data-ttu-id="9a8f9-114">W tym przykładzie użyto `<seealso>` tagów w `DoesRecordExist` uwagi sekcji do odwoływania się do `UpdateRecord` metody.</span><span class="sxs-lookup"><span data-stu-id="9a8f9-114">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/seealso_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9a8f9-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9a8f9-115">See Also</span></span>  
 [<span data-ttu-id="9a8f9-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="9a8f9-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
