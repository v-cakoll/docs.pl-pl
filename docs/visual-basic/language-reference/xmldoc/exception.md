---
title: <exception> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 16ffb4f6b57dabb3650376c913a7d7608a00646d
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523919"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="aa646-102">> \<exception (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa646-102">\<exception> (Visual Basic)</span></span>
<span data-ttu-id="aa646-103">Określa, które wyjątki mogą być zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="aa646-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa646-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aa646-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa646-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa646-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="aa646-106">Odwołanie do wyjątku, które jest dostępne w bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="aa646-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="aa646-107">Kompilator sprawdza, czy dany wyjątek istnieje i tłumaczy `member` na nazwę elementu kanonicznego w wyjściowym kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="aa646-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="aa646-108">`member` musi znajdować się w podwójnym cudzysłowie ("").</span><span class="sxs-lookup"><span data-stu-id="aa646-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="aa646-109">Opis.</span><span class="sxs-lookup"><span data-stu-id="aa646-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa646-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aa646-110">Remarks</span></span>  
 <span data-ttu-id="aa646-111">Użyj znacznika `<exception>`, aby określić, które wyjątki mogą być zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="aa646-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="aa646-112">Ten tag jest stosowany do definicji metody.</span><span class="sxs-lookup"><span data-stu-id="aa646-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="aa646-113">Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="aa646-113">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa646-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa646-114">Example</span></span>  
 <span data-ttu-id="aa646-115">W tym przykładzie używa znacznika `<exception>`, aby opisać wyjątek, który może zgłosić funkcja `IntDivide`.</span><span class="sxs-lookup"><span data-stu-id="aa646-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="aa646-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa646-116">See also</span></span>

- [<span data-ttu-id="aa646-117">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="aa646-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
