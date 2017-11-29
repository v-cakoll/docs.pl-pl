---
title: "&lt;wyjątek&gt; (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8d718a7c2213a61f7f60ed80a04f9bd03f6c770a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltexceptiongt-visual-basic"></a><span data-ttu-id="4e8cf-102">&lt;wyjątek&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e8cf-102">&lt;exception&gt; (Visual Basic)</span></span>
<span data-ttu-id="4e8cf-103">Określa, które wyjątki może zostać wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="4e8cf-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e8cf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e8cf-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4e8cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4e8cf-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="4e8cf-106">Odwołanie do wyjątek, który jest dostępny w bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4e8cf-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="4e8cf-107">Kompilator sprawdza, czy dany wyjątek istnieje i czy tłumaczy `member` nazwę kanoniczną element wyjściowy element XML.</span><span class="sxs-lookup"><span data-stu-id="4e8cf-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="4e8cf-108">`member`musi występować w podwójny cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="4e8cf-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="4e8cf-109">Opis.</span><span class="sxs-lookup"><span data-stu-id="4e8cf-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e8cf-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4e8cf-110">Remarks</span></span>  
 <span data-ttu-id="4e8cf-111">Użyj `<exception>` tag, aby określić, które wyjątki może zostać wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="4e8cf-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="4e8cf-112">Ten tag jest stosowany do definicji metody.</span><span class="sxs-lookup"><span data-stu-id="4e8cf-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="4e8cf-113">Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="4e8cf-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e8cf-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="4e8cf-114">Example</span></span>  
 <span data-ttu-id="4e8cf-115">W tym przykładzie użyto `<exception>` tag opisujący wyjątek który `IntDivide` może zgłosić funkcji.</span><span class="sxs-lookup"><span data-stu-id="4e8cf-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/exception_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4e8cf-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4e8cf-116">See Also</span></span>  
 [<span data-ttu-id="4e8cf-117">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="4e8cf-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
