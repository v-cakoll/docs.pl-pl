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
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a>Odwołanie do przyjaznego zestawu &lt;odwołania&gt; jest nieprawidłowy
Odwołanie do przyjaznego zestawu \<odwołanie > jest nieprawidłowy. Zestawy podpisane silnymi nazwami muszą określać klucz publiczny w swoich deklaracjach InternalsVisibleTo.  
  
 Nazwa zestawu jest przekazywany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut konstruktora identyfikuje zestawu z silną nazwą, ale nie obejmuje `PublicKey` atrybutu.  
  
 **Identyfikator błędu:** BC31535  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Określ klucz publiczny dla zestawu o silnej nazwie przyjaciela. Dołącz klucz publiczny, jako część nazwy zestawu przekazywany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut konstruktora przy użyciu `PublicKey` atrybutu.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Reflection.AssemblyName>
- [Przyjazne zestawy](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)


