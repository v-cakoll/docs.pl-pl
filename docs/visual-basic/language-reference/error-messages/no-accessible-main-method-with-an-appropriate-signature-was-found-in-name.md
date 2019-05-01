---
title: W elemencie „<name>” nie odnaleziono dostępnej metody „Main” z odpowiednim podpisem.
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: f5053bddf4b9ba791ad6d0733e1dd89c4ded91bd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918271"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a>Brak metody dostępne "Main" z odpowiednim podpisem został znaleziony w "\<name >"
Aplikacje wiersza poleceń jest posiadanie `Sub Main` zdefiniowane. `Main` musi być zadeklarowany jako `Public Shared` Jeśli jest zdefiniowana w klasie lub jako `Public` Jeśli zdefiniowany w module.  
  
 **Identyfikator błędu:** BC30737  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Zdefiniuj `Public Sub Main` procedury dla Twojego projektu. Zadeklaruj go jako `Shared` tylko wtedy, gdy zdefiniujesz wewnątrz klasy.  
  
## <a name="see-also"></a>Zobacz także

- [Struktura programu w języku Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
