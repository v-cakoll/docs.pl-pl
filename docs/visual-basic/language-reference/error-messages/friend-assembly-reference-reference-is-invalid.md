---
title: Odwołanie do przyjaznego zestawu „<reference>” jest nieprawidłowe
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: 796c16e912283d86496a4ccbd3b675ac1433f02d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356406"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a>Odwołanie do przyjaznego zestawu \<odwołanie > jest nieprawidłowy
Odwołanie do przyjaznego zestawu \<odwołanie > jest nieprawidłowy. Zestawy podpisane silnymi nazwami muszą określać klucz publiczny w swoich deklaracjach InternalsVisibleTo.  
  
 Nazwa zestawu jest przekazywany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut konstruktora identyfikuje zestawu z silną nazwą, ale nie obejmuje `PublicKey` atrybutu.  
  
 **Identyfikator błędu:** BC31535  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Określ klucz publiczny dla zestawu o silnej nazwie przyjaciela. Dołącz klucz publiczny, jako część nazwy zestawu przekazywany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut konstruktora przy użyciu `PublicKey` atrybutu.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Reflection.AssemblyName>
- [Przyjazne zestawy](../../../standard/assembly/friend-assemblies.md)


