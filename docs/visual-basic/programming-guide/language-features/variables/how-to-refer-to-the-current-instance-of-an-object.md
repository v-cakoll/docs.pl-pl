---
title: 'Instrukcje: Odwoływanie się do bieżącego wystąpienia obiektu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 70955cd55dfb91d4111e59ae58bfe409a4470433
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663530"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>Instrukcje: Odwoływanie się do bieżącego wystąpienia obiektu (Visual Basic)
*Bieżącego wystąpienia* obiektu zasady jest wystąpienie, w którym aktualnie wykonuje kod.  
  
 Możesz użyć `Me` — słowo kluczowe do odwoływania się do bieżącego wystąpienia.  
  
### <a name="to-refer-to-the-current-instance"></a>Aby odwołać się do bieżącego wystąpienia  
  
- Użyj `Me` — słowo kluczowe, których nazwa zmiennej obiektu zwykle są używane.  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     Mimo że `Me` zachowuje się jak obiekt zmiennej, nie można zadeklarować ją lub przypisać niczego do niej. `Me` zawsze odwołuje się do bieżącego wystąpienia.  
  
## <a name="see-also"></a>Zobacz także

- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Przypisanie zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Me, My, MyBase i MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
