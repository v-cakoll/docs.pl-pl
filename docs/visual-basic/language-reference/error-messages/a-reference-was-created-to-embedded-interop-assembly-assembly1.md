---
title: "Utworzono odwołanie do osadzonego zestawu międzyoperacyjnego &#39; &lt;zestaw1&gt;&#39; z powodu pośredniego odwołania do tego zestawu z zestawu &#39;&lt; assembly2&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bc2fbb044fc839aa24abf3dc1ea864457efb0653
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-39ltassembly1gt39-because-of-an-indirect-reference-to-that-assembly-from-assembly-39ltassembly2gt39"></a><span data-ttu-id="4eb0f-102">Utworzono odwołanie do osadzonego zestawu międzyoperacyjnego &#39; &lt;zestaw1&gt;&#39; z powodu pośredniego odwołania do tego zestawu z zestawu &#39;&lt; assembly2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="4eb0f-102">A reference was created to embedded interop assembly &#39;&lt;assembly1&gt;&#39; because of an indirect reference to that assembly from assembly &#39;&lt;assembly2&gt;&#39;</span></span>
<span data-ttu-id="4eb0f-103">Utworzono odwołanie do osadzonego zestawu międzyoperacyjnego "\<zestaw1 >" z powodu pośredniego odwołania do tego zestawu z zestawu "\<assembly2 >".</span><span class="sxs-lookup"><span data-stu-id="4eb0f-103">A reference was created to embedded interop assembly '\<assembly1>' because of an indirect reference to that assembly from assembly '\<assembly2>'.</span></span> <span data-ttu-id="4eb0f-104">Rozważ zmianę właściwości "Osadź typy międzyoperacyjne" na jednym z zestawów.</span><span class="sxs-lookup"><span data-stu-id="4eb0f-104">Consider changing the 'Embed Interop Types' property on either assembly.</span></span>  
  
 <span data-ttu-id="4eb0f-105">Dodano odwołanie do zestawu (zestaw1), który ma `Embed Interop Types` ustawioną właściwość `True`.</span><span class="sxs-lookup"><span data-stu-id="4eb0f-105">You have added a reference to an assembly (assembly1) that has the `Embed Interop Types` property set to `True`.</span></span> <span data-ttu-id="4eb0f-106">To instruuje kompilator, aby osadzić typu międzyoperacyjnego informacje z tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="4eb0f-106">This instructs the compiler to embed interop type information from that assembly.</span></span> <span data-ttu-id="4eb0f-107">Jednak kompilator nie można osadzić typu międzyoperacyjnego informacje z tego zestawu, ponieważ inny zestaw czy zdefiniowano odwołania (assembly2) również odwołuje się do tego zestawu (zestaw1) i ma `Embed Interop Types` ustawioną właściwość `False`.</span><span class="sxs-lookup"><span data-stu-id="4eb0f-107">However, the compiler cannot embed interop type information from that assembly because another assembly that you have referenced (assembly2) also references that assembly (assembly1) and has the `Embed Interop Types` property set to `False`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4eb0f-108">Ustawienie `Embed Interop Types` właściwości na odwołanie do zestawu `True` jest odpowiednikiem odwołanie do zestawu przy użyciu `/link` opcji dla kompilatora wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="4eb0f-108">Setting the `Embed Interop Types` property on an assembly reference to `True` is equivalent to referencing the assembly by using the `/link` option for the command-line compiler.</span></span>  
  
 <span data-ttu-id="4eb0f-109">**Identyfikator błędu:** BC40059</span><span class="sxs-lookup"><span data-stu-id="4eb0f-109">**Error ID:** BC40059</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="4eb0f-110">W celu rozwiązania tego ostrzeżenia</span><span class="sxs-lookup"><span data-stu-id="4eb0f-110">To address this warning</span></span>  
  
-   <span data-ttu-id="4eb0f-111">Aby osadzić typu międzyoperacyjnego informacje dla obu zestawów, ustaw `Embed Interop Types` właściwości na wszystkich odwołań do zestaw1 do `True`.</span><span class="sxs-lookup"><span data-stu-id="4eb0f-111">To embed interop type information for both assemblies, set the `Embed Interop Types` property on all references to assembly1 to `True`.</span></span>  
  
-   <span data-ttu-id="4eb0f-112">Aby usunąć to ostrzeżenie, można ustawić `Embed Interop Types` właściwości zestaw1 do `False`.</span><span class="sxs-lookup"><span data-stu-id="4eb0f-112">To remove the warning, you can set the `Embed Interop Types` property of assembly1 to `False`.</span></span> <span data-ttu-id="4eb0f-113">W takim przypadku informacje typu międzyoperacyjnego są udostępniane przez podstawowy zestaw międzyoperacyjny (PIA).</span><span class="sxs-lookup"><span data-stu-id="4eb0f-113">In this case, interop type information is provided by a primary interop assembly (PIA).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eb0f-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4eb0f-114">See Also</span></span>  
 [<span data-ttu-id="4eb0f-115">/ Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4eb0f-115">/link (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/link.md)  
 [<span data-ttu-id="4eb0f-116">Programowanie za pomocą podstawowe zestawy międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="4eb0f-116">Programming with Primary Interop Assemblies</span></span>](http://msdn.microsoft.com/en-us/306fa1d6-0703-4004-9e93-d0a57f1be81e)
