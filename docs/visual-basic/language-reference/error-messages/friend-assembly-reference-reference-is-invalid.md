---
title: "Odwołanie do przyjaznego zestawu &lt;odwołania&gt; jest nieprawidłowy"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ab1c7c5cc7a7f4ad899df7722769238e05d96e6b
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a><span data-ttu-id="6ab1c-102">Odwołanie do przyjaznego zestawu &lt;odwołania&gt; jest nieprawidłowy</span><span class="sxs-lookup"><span data-stu-id="6ab1c-102">Friend assembly reference &lt;reference&gt; is invalid</span></span>
<span data-ttu-id="6ab1c-103">Odwołanie do przyjaznego zestawu \<odwołania > jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="6ab1c-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="6ab1c-104">Zestawy podpisane silnymi nazwami muszą określać klucz publiczny w swoich deklaracjach InternalsVisibleTo.</span><span class="sxs-lookup"><span data-stu-id="6ab1c-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="6ab1c-105">Nazwa zestawu przekazany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Konstruktor atrybutu identyfikuje zestawu z silną nazwą, ale nie obejmuje `PublicKey` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6ab1c-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="6ab1c-106">**Identyfikator błędu:** BC31535</span><span class="sxs-lookup"><span data-stu-id="6ab1c-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6ab1c-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="6ab1c-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="6ab1c-108">Określ klucz publiczny zestawu o silnej nazwie friend.</span><span class="sxs-lookup"><span data-stu-id="6ab1c-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="6ab1c-109">Dołącz klucz publiczny, jako część nazwy zestawu przekazany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Konstruktor atrybutu przy użyciu `PublicKey` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6ab1c-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ab1c-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ab1c-110">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 [<span data-ttu-id="6ab1c-111">Przyjazne zestawy</span><span class="sxs-lookup"><span data-stu-id="6ab1c-111">Friend Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 

