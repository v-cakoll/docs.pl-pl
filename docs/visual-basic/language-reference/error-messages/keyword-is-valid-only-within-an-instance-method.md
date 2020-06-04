---
title: Element „<keyword>” jest prawidłowy tylko wewnątrz metody wystąpienia
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 537689405ea30bdd7c075320eba58a8723a93cdb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397405"
---
# <a name="keyword-is-valid-only-within-an-instance-method"></a>Element „\<keyword>” jest prawidłowy tylko wewnątrz metody wystąpienia
`Me` `MyClass` Słowa kluczowe, i `MyBase` odwołują się do określonych wystąpień klasy. Nie można ich używać wewnątrz wspólnej `Function` procedury lub `Sub` .  
  
 **Identyfikator błędu:** BC30043  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Usuń słowo kluczowe z procedury lub Usuń `Shared` słowo kluczowe z deklaracji procedury.  
  
## <a name="see-also"></a>Zobacz też

- [Przypisanie zmiennej obiektu](../../programming-guide/language-features/variables/object-variable-assignment.md)
- [Me, My, MyBase i MyClass](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Podstawowe informacje o dziedziczeniu](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
