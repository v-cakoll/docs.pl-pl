---
title: Odwołanie do przyjaznego zestawu „<reference>” jest nieprawidłowe
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: ff2cdbebe13f6224209ef8da62600c99348c911b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55286822"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a><span data-ttu-id="a0c92-102">Odwołanie do przyjaznego zestawu \<odwołanie > jest nieprawidłowy</span><span class="sxs-lookup"><span data-stu-id="a0c92-102">Friend assembly reference \<reference> is invalid</span></span>
<span data-ttu-id="a0c92-103">Odwołanie do przyjaznego zestawu \<odwołanie > jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="a0c92-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="a0c92-104">Zestawy podpisane silnymi nazwami muszą określać klucz publiczny w swoich deklaracjach InternalsVisibleTo.</span><span class="sxs-lookup"><span data-stu-id="a0c92-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="a0c92-105">Nazwa zestawu jest przekazywany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut konstruktora identyfikuje zestawu z silną nazwą, ale nie obejmuje `PublicKey` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a0c92-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="a0c92-106">**Identyfikator błędu:** BC31535</span><span class="sxs-lookup"><span data-stu-id="a0c92-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a0c92-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a0c92-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="a0c92-108">Określ klucz publiczny dla zestawu o silnej nazwie przyjaciela.</span><span class="sxs-lookup"><span data-stu-id="a0c92-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="a0c92-109">Dołącz klucz publiczny, jako część nazwy zestawu przekazywany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut konstruktora przy użyciu `PublicKey` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a0c92-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0c92-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0c92-110">See also</span></span>
- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="a0c92-111">Przyjazne zestawy</span><span class="sxs-lookup"><span data-stu-id="a0c92-111">Friend Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)


