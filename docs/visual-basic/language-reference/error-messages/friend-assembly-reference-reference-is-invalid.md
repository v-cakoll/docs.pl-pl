---
title: Odwołanie do przyjaznego zestawu &lt;odwołania&gt; jest nieprawidłowy
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: c47fae9c60dc04ee02b1ff015d3dde87b8920c02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a><span data-ttu-id="c9a15-102">Odwołanie do przyjaznego zestawu &lt;odwołania&gt; jest nieprawidłowy</span><span class="sxs-lookup"><span data-stu-id="c9a15-102">Friend assembly reference &lt;reference&gt; is invalid</span></span>
<span data-ttu-id="c9a15-103">Odwołanie do przyjaznego zestawu \<odwołania > jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="c9a15-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="c9a15-104">Zestawy podpisane silnymi nazwami muszą określać klucz publiczny w swoich deklaracjach InternalsVisibleTo.</span><span class="sxs-lookup"><span data-stu-id="c9a15-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="c9a15-105">Nazwa zestawu przekazany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Konstruktor atrybutu identyfikuje zestawu z silną nazwą, ale nie obejmuje `PublicKey` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c9a15-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="c9a15-106">**Identyfikator błędu:** BC31535</span><span class="sxs-lookup"><span data-stu-id="c9a15-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c9a15-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="c9a15-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="c9a15-108">Określ klucz publiczny zestawu o silnej nazwie friend.</span><span class="sxs-lookup"><span data-stu-id="c9a15-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="c9a15-109">Dołącz klucz publiczny, jako część nazwy zestawu przekazany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Konstruktor atrybutu przy użyciu `PublicKey` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c9a15-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9a15-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9a15-110">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 [<span data-ttu-id="c9a15-111">Przyjazne zestawy</span><span class="sxs-lookup"><span data-stu-id="c9a15-111">Friend Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 

