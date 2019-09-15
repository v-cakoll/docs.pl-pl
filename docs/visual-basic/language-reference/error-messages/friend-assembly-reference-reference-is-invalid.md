---
title: Odwołanie do przyjaznego zestawu „<reference>” jest nieprawidłowe
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: 6eb46c6479adc69eaf65b34c69aa69977b4d62ef
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972395"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a><span data-ttu-id="fd5cc-102">Odwołanie do odwołania \<do zestawu zaprzyjaźnionego > jest nieprawidłowe</span><span class="sxs-lookup"><span data-stu-id="fd5cc-102">Friend assembly reference \<reference> is invalid</span></span>
<span data-ttu-id="fd5cc-103">Odwołanie do odwołania \<do zestawu zaprzyjaźnionego > jest nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="fd5cc-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="fd5cc-104">Zestawy podpisane silnymi nazwami muszą określać klucz publiczny w swoich deklaracjach InternalsVisibleTo.</span><span class="sxs-lookup"><span data-stu-id="fd5cc-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="fd5cc-105">Nazwa zestawu przeniesiona do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> konstruktora atrybutu identyfikuje zestaw o silnej nazwie, ale nie `PublicKey` zawiera atrybutu.</span><span class="sxs-lookup"><span data-stu-id="fd5cc-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="fd5cc-106">**Identyfikator błędu:** BC31535</span><span class="sxs-lookup"><span data-stu-id="fd5cc-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fd5cc-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="fd5cc-107">To correct this error</span></span>  
  
1. <span data-ttu-id="fd5cc-108">Określ klucz publiczny dla zestawu o silnej nazwie zaprzyjaźnionej.</span><span class="sxs-lookup"><span data-stu-id="fd5cc-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="fd5cc-109">Dołącz klucz publiczny jako część nazwy zestawu przesłanej do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> konstruktora atrybutu przy `PublicKey` użyciu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="fd5cc-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd5cc-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd5cc-110">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="fd5cc-111">Przyjazne zestawy</span><span class="sxs-lookup"><span data-stu-id="fd5cc-111">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
