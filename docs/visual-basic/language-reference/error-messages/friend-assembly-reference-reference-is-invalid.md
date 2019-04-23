---
title: Odwołanie do przyjaznego zestawu „<reference>” jest nieprawidłowe
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: 0c1526e32ddc64cb4124c6f8205d58deef911dd6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59298997"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a>Odwołanie do przyjaznego zestawu \<odwołanie > jest nieprawidłowy
Odwołanie do przyjaznego zestawu \<odwołanie > jest nieprawidłowy. Zestawy podpisane silnymi nazwami muszą określać klucz publiczny w swoich deklaracjach InternalsVisibleTo.  
  
 Nazwa zestawu jest przekazywany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut konstruktora identyfikuje zestawu z silną nazwą, ale nie obejmuje `PublicKey` atrybutu.  
  
 **Identyfikator błędu:** BC31535  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Określ klucz publiczny dla zestawu o silnej nazwie przyjaciela. Dołącz klucz publiczny, jako część nazwy zestawu przekazywany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut konstruktora przy użyciu `PublicKey` atrybutu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection.AssemblyName>
- [Przyjazne zestawy](../../../standard/assembly/friend-assemblies.md)
