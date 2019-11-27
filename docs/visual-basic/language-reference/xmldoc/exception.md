---
title: <exception>
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: e1e7f2d0fb06599f83ba224ed52a10429d9b11fe
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346959"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="40a59-101">> \<wyjątków (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40a59-101">\<exception> (Visual Basic)</span></span>
<span data-ttu-id="40a59-102">Określa, które wyjątki mogą być zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="40a59-102">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40a59-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="40a59-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="40a59-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="40a59-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="40a59-105">Odwołanie do wyjątku, które jest dostępne w bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="40a59-105">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="40a59-106">Kompilator sprawdza, czy dany wyjątek istnieje i tłumaczy `member` na nazwę elementu kanonicznego w wyjściowym kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="40a59-106">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="40a59-107">`member` musi znajdować się w podwójnym cudzysłowie ("").</span><span class="sxs-lookup"><span data-stu-id="40a59-107">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="40a59-108">Opis.</span><span class="sxs-lookup"><span data-stu-id="40a59-108">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40a59-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="40a59-109">Remarks</span></span>  
 <span data-ttu-id="40a59-110">Użyj znacznika `<exception>`, aby określić, które wyjątki mogą być zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="40a59-110">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="40a59-111">Ten tag jest stosowany do definicji metody.</span><span class="sxs-lookup"><span data-stu-id="40a59-111">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="40a59-112">Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="40a59-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40a59-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="40a59-113">Example</span></span>  
 <span data-ttu-id="40a59-114">W tym przykładzie używa znacznika `<exception>`, aby opisać wyjątek, który może zgłosić funkcja `IntDivide`.</span><span class="sxs-lookup"><span data-stu-id="40a59-114">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="40a59-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40a59-115">See also</span></span>

- [<span data-ttu-id="40a59-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="40a59-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
