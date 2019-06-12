---
title: Utworzono odwołanie do osadzonego zestawu międzyoperacyjnego „<assembly1>' z powodu pośredniego odwołania do tego zestawu z zestawu „<assembly2>'.
ms.date: 07/20/2015
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
ms.openlocfilehash: 36ae9d8257c8265b813bba446f685428bbf0b1e7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64646880"
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-assembly1-because-of-an-indirect-reference-to-that-assembly-from-assembly-assembly2"></a><span data-ttu-id="32c8e-102">Utworzono odwołanie do osadzonego zestawu międzyoperacyjnego '\<assembly1 >' z powodu pośredniego odwołania do tego zestawu z zestawu '\<assembly2 >'</span><span class="sxs-lookup"><span data-stu-id="32c8e-102">A reference was created to embedded interop assembly '\<assembly1>' because of an indirect reference to that assembly from assembly '\<assembly2>'</span></span>
<span data-ttu-id="32c8e-103">Utworzono odwołanie do osadzonego zestawu międzyoperacyjnego '\<assembly1 >' z powodu pośredniego odwołania do tego zestawu z zestawu '\<assembly2 >'.</span><span class="sxs-lookup"><span data-stu-id="32c8e-103">A reference was created to embedded interop assembly '\<assembly1>' because of an indirect reference to that assembly from assembly '\<assembly2>'.</span></span> <span data-ttu-id="32c8e-104">Rozważ zmianę właściwości 'Embed Interop Types' na jednym z zestawów.</span><span class="sxs-lookup"><span data-stu-id="32c8e-104">Consider changing the 'Embed Interop Types' property on either assembly.</span></span>  
  
 <span data-ttu-id="32c8e-105">Dodano odwołanie do zestawu (assembly1), który ma `Embed Interop Types` właściwością `True`.</span><span class="sxs-lookup"><span data-stu-id="32c8e-105">You have added a reference to an assembly (assembly1) that has the `Embed Interop Types` property set to `True`.</span></span> <span data-ttu-id="32c8e-106">To powoduje, że kompilator, aby osadzić typu międzyoperacyjnego informacje z tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="32c8e-106">This instructs the compiler to embed interop type information from that assembly.</span></span> <span data-ttu-id="32c8e-107">Jednak kompilator nie można osadzić typu międzyoperacyjnego informacje z tego zestawu, ponieważ także innego zestawu, że masz przywoływane (zależność assembly2) odwołuje się do tego zestawu (assembly1) i ma `Embed Interop Types` właściwością `False`.</span><span class="sxs-lookup"><span data-stu-id="32c8e-107">However, the compiler cannot embed interop type information from that assembly because another assembly that you have referenced (assembly2) also references that assembly (assembly1) and has the `Embed Interop Types` property set to `False`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32c8e-108">Ustawienie `Embed Interop Types` właściwość odwołanie do zestawu `True` jest odpowiednikiem odwołanie do zestawu przy użyciu `/link` opcję kompilatora wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="32c8e-108">Setting the `Embed Interop Types` property on an assembly reference to `True` is equivalent to referencing the assembly by using the `/link` option for the command-line compiler.</span></span>  
  
 <span data-ttu-id="32c8e-109">**Identyfikator błędu:** BC40059</span><span class="sxs-lookup"><span data-stu-id="32c8e-109">**Error ID:** BC40059</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="32c8e-110">Aby rozwiązać tego ostrzeżenia</span><span class="sxs-lookup"><span data-stu-id="32c8e-110">To address this warning</span></span>  
  
- <span data-ttu-id="32c8e-111">Aby osadzić typu międzyoperacyjnego informacje dla obu zestawów, należy ustawić `Embed Interop Types` właściwość wszystkie odwołania do assembly1 do `True`.</span><span class="sxs-lookup"><span data-stu-id="32c8e-111">To embed interop type information for both assemblies, set the `Embed Interop Types` property on all references to assembly1 to `True`.</span></span>  
  
- <span data-ttu-id="32c8e-112">Aby usunąć to ostrzeżenie, można ustawić `Embed Interop Types` właściwość assembly1 do `False`.</span><span class="sxs-lookup"><span data-stu-id="32c8e-112">To remove the warning, you can set the `Embed Interop Types` property of assembly1 to `False`.</span></span> <span data-ttu-id="32c8e-113">W tym przypadku typu międzyoperacyjnego informacje są udostępniane przez podstawowego zestawu międzyoperacyjnego (PIA).</span><span class="sxs-lookup"><span data-stu-id="32c8e-113">In this case, interop type information is provided by a primary interop assembly (PIA).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32c8e-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32c8e-114">See also</span></span>

- [<span data-ttu-id="32c8e-115">/ Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32c8e-115">/link (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="32c8e-116">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="32c8e-116">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
