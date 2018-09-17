---
title: '&lt;wyjątek&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 047805ad91d87550da80448fd10883ae58647bd6
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45687416"
---
# <a name="ltexceptiongt-visual-basic"></a><span data-ttu-id="dbc9f-102">&lt;wyjątek&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbc9f-102">&lt;exception&gt; (Visual Basic)</span></span>
<span data-ttu-id="dbc9f-103">Określa, które wyjątki mogą zostać wygenerowane.</span><span class="sxs-lookup"><span data-stu-id="dbc9f-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbc9f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dbc9f-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dbc9f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dbc9f-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="dbc9f-106">Odwołanie do wyjątek, który jest dostępny w bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="dbc9f-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="dbc9f-107">Kompilator sprawdza, czy dany wyjątek istnieje i czy tłumaczy `member` nazwę kanoniczną element w danych wyjściowych XML.</span><span class="sxs-lookup"><span data-stu-id="dbc9f-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="dbc9f-108">`member` musi znajdować się w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="dbc9f-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="dbc9f-109">Opis.</span><span class="sxs-lookup"><span data-stu-id="dbc9f-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbc9f-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dbc9f-110">Remarks</span></span>  
 <span data-ttu-id="dbc9f-111">Użyj `<exception>` tag, aby określić, które wyjątki mogą zostać wygenerowane.</span><span class="sxs-lookup"><span data-stu-id="dbc9f-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="dbc9f-112">Ten tag jest stosowany do definicji metody.</span><span class="sxs-lookup"><span data-stu-id="dbc9f-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="dbc9f-113">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="dbc9f-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbc9f-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="dbc9f-114">Example</span></span>  
 <span data-ttu-id="dbc9f-115">W tym przykładzie użyto `<exception>` znaczników do opisu wyjątku, `IntDivide` funkcja może zgłosić.</span><span class="sxs-lookup"><span data-stu-id="dbc9f-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/exception_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="dbc9f-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dbc9f-116">See Also</span></span>  
 [<span data-ttu-id="dbc9f-117">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="dbc9f-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
