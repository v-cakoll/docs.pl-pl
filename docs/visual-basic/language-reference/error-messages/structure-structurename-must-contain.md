---
title: Struktura „<structurename>" musi zawierać co najmniej jedną zmienną elementu członkowskiego lub co najmniej jedną deklarację wystąpienia zdarzenia, która nie jest oznaczona „Custom"
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: a8a85f4f089de9be6f2ecadac05256b30d3014b0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267459"
---
# <a name="structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a>Struktura "\<structurename >" musi zawierać co najmniej jedną zmienną elementu członkowskiego wystąpienia lub co najmniej jedną deklarację wystąpienia zdarzenia nie jest oznaczona "Custom"
Definicja struktury nie ma żadnych zmiennych nieudostępnionych lub nieudostępnionych, niestandardowych zdarzeń.  
  
 Co struktura musi być zmienną lub zdarzenie, które mają zastosowanie do każdego wystąpienia określonych (udostępniana), a nie do wszystkich wystąpień zbiorczo ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)). Stałe nieudostępnionych, właściwości i procedury nie spełniają tego wymagania. Ponadto w przypadku żadnych zmiennych nieudostępnionych i tylko jedno zdarzenie nieudostępnionych, to zdarzenie nie może być `Custom` zdarzeń.  
  
 **Identyfikator błędu:** BC30941  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zdefiniuj co najmniej jedną zmienną lub zdarzeń, który nie jest `Shared`. Jeśli zdefiniujesz tylko jedno zdarzenie, musi ona standardowych, jak również nieudostępnionych.  
  
## <a name="see-also"></a>Zobacz także
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Instrukcje: deklarowanie struktury](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)
