---
title: <seealso>
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 5999a4ebcc90f21ee8331b96ffb2a50f7905b1b6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411515"
---
# <a name="seealso-visual-basic"></a><span data-ttu-id="84c24-101">\<seealso> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84c24-101">\<seealso> (Visual Basic)</span></span>
<span data-ttu-id="84c24-102">Określa łącze, które pojawia się w sekcji Zobacz też.</span><span class="sxs-lookup"><span data-stu-id="84c24-102">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84c24-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="84c24-103">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="84c24-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="84c24-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="84c24-105">Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji.</span><span class="sxs-lookup"><span data-stu-id="84c24-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="84c24-106">Kompilator sprawdza, czy dany element kodu istnieje i przekazuje `member` do nazwy elementu w wyjściowym kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="84c24-106">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="84c24-107">`member`musi znajdować się w podwójnym cudzysłowie ("").</span><span class="sxs-lookup"><span data-stu-id="84c24-107">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84c24-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="84c24-108">Remarks</span></span>  
 <span data-ttu-id="84c24-109">Użyj `<seealso>` znacznika, aby określić tekst, który ma być wyświetlany w sekcji Zobacz też.</span><span class="sxs-lookup"><span data-stu-id="84c24-109">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="84c24-110">Służy [\<see>](see.md) do określania linku w tekście.</span><span class="sxs-lookup"><span data-stu-id="84c24-110">Use [\<see>](see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="84c24-111">Kompiluj z [-doc](../../reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="84c24-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84c24-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="84c24-112">Example</span></span>  
 <span data-ttu-id="84c24-113">Ten przykład używa `<seealso>` znacznika w `DoesRecordExist` sekcji uwagi, aby odwołać się do `UpdateRecord` metody.</span><span class="sxs-lookup"><span data-stu-id="84c24-113">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="84c24-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="84c24-114">See also</span></span>

- [<span data-ttu-id="84c24-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="84c24-115">XML Comment Tags</span></span>](index.md)
