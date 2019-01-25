---
title: Odwołanie do przyjaznego zestawu &lt;odwołania&gt; jest nieprawidłowy
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: cdedcc18aa82f6efd8c52cdca5d915d7d78e269f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611933"
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a><span data-ttu-id="decc8-102">Odwołanie do przyjaznego zestawu &lt;odwołania&gt; jest nieprawidłowy</span><span class="sxs-lookup"><span data-stu-id="decc8-102">Friend assembly reference &lt;reference&gt; is invalid</span></span>
<span data-ttu-id="decc8-103">Odwołanie do przyjaznego zestawu \<odwołanie > jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="decc8-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="decc8-104">Zestawy podpisane silnymi nazwami muszą określać klucz publiczny w swoich deklaracjach InternalsVisibleTo.</span><span class="sxs-lookup"><span data-stu-id="decc8-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="decc8-105">Nazwa zestawu jest przekazywany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut konstruktora identyfikuje zestawu z silną nazwą, ale nie obejmuje `PublicKey` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="decc8-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="decc8-106">**Identyfikator błędu:** BC31535</span><span class="sxs-lookup"><span data-stu-id="decc8-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="decc8-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="decc8-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="decc8-108">Określ klucz publiczny dla zestawu o silnej nazwie przyjaciela.</span><span class="sxs-lookup"><span data-stu-id="decc8-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="decc8-109">Dołącz klucz publiczny, jako część nazwy zestawu przekazywany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut konstruktora przy użyciu `PublicKey` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="decc8-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="decc8-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="decc8-110">See also</span></span>
- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="decc8-111">Przyjazne zestawy</span><span class="sxs-lookup"><span data-stu-id="decc8-111">Friend Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)


