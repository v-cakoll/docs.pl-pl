---
title: <exception>
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 3a2452ec60a2182adfee365777d9824001ff006a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400127"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="d55ab-101">\<exception> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d55ab-101">\<exception> (Visual Basic)</span></span>
<span data-ttu-id="d55ab-102">Określa, które wyjątki mogą być zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="d55ab-102">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d55ab-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="d55ab-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="d55ab-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="d55ab-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="d55ab-105">Odwołanie do wyjątku, które jest dostępne w bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d55ab-105">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="d55ab-106">Kompilator sprawdza, czy dany wyjątek istnieje i tłumaczy `member` na nazwę elementu kanonicznego w wyjściowym kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="d55ab-106">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="d55ab-107">`member`musi znajdować się w podwójnym cudzysłowie ("").</span><span class="sxs-lookup"><span data-stu-id="d55ab-107">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="d55ab-108">Opis.</span><span class="sxs-lookup"><span data-stu-id="d55ab-108">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d55ab-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d55ab-109">Remarks</span></span>  
 <span data-ttu-id="d55ab-110">Użyj `<exception>` znacznika, aby określić, które wyjątki mogą być zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="d55ab-110">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="d55ab-111">Ten tag jest stosowany do definicji metody.</span><span class="sxs-lookup"><span data-stu-id="d55ab-111">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="d55ab-112">Kompiluj z [-doc](../../reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="d55ab-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d55ab-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="d55ab-113">Example</span></span>  
 <span data-ttu-id="d55ab-114">W tym przykładzie używa `<exception>` znacznika do opisywania wyjątku, który `IntDivide` Funkcja może zgłosić.</span><span class="sxs-lookup"><span data-stu-id="d55ab-114">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="d55ab-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d55ab-115">See also</span></span>

- [<span data-ttu-id="d55ab-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="d55ab-116">XML Comment Tags</span></span>](index.md)
