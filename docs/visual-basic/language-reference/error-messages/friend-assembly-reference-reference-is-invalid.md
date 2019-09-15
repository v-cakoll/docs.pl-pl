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
# <a name="friend-assembly-reference-reference-is-invalid"></a>Odwołanie do odwołania \<do zestawu zaprzyjaźnionego > jest nieprawidłowe
Odwołanie do odwołania \<do zestawu zaprzyjaźnionego > jest nieprawidłowe. Zestawy podpisane silnymi nazwami muszą określać klucz publiczny w swoich deklaracjach InternalsVisibleTo.  
  
 Nazwa zestawu przeniesiona do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> konstruktora atrybutu identyfikuje zestaw o silnej nazwie, ale nie `PublicKey` zawiera atrybutu.  
  
 **Identyfikator błędu:** BC31535  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Określ klucz publiczny dla zestawu o silnej nazwie zaprzyjaźnionej. Dołącz klucz publiczny jako część nazwy zestawu przesłanej do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> konstruktora atrybutu przy `PublicKey` użyciu atrybutu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection.AssemblyName>
- [Przyjazne zestawy](../../../standard/assembly/friend.md)
