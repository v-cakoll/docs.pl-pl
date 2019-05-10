---
title: W elemencie „<name>” nie odnaleziono dostępnej metody „Main” z odpowiednim podpisem.
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 559c905d1e2e2de4500771a93d6116f9630011ba
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591972"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a>Brak metody dostępne "Main" z odpowiednim podpisem został znaleziony w "\<name >"
Aplikacje wiersza poleceń jest posiadanie `Sub Main` zdefiniowane. `Main` musi być zadeklarowany jako `Public Shared` Jeśli jest zdefiniowana w klasie lub jako `Public` Jeśli zdefiniowany w module.  
  
 **Identyfikator błędu:** BC30737  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Zdefiniuj `Public Sub Main` procedury dla Twojego projektu. Zadeklaruj go jako `Shared` tylko wtedy, gdy zdefiniujesz wewnątrz klasy.  
  
## <a name="see-also"></a>Zobacz także

- [Struktura programu w języku Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
