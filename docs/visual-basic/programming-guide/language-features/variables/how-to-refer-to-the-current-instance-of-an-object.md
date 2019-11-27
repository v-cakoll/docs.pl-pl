---
title: 'Porady: odwoływanie się do bieżącego wystąpienia obiektu'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 62b22a54904a45380052d3d81d9415517d4f8d3b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346881"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>Porady: odwoływanie się do bieżącego wystąpienia obiektu (Visual Basic)
*Bieżące wystąpienie* obiektu to wystąpienie, w którym kod jest aktualnie wykonywany.  
  
 Użyj słowa kluczowego `Me`, aby odwołać się do bieżącego wystąpienia.  
  
### <a name="to-refer-to-the-current-instance"></a>Aby odwołać się do bieżącego wystąpienia  
  
- Użyj słowa kluczowego `Me`, gdzie zwykle używasz nazwy zmiennej obiektu.  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     Chociaż `Me` zachowuje się jak zmienna obiektu, nie można jej zadeklarować ani przypisać do niej niczego. `Me` zawsze odwołuje się do bieżącego wystąpienia.  
  
## <a name="see-also"></a>Zobacz także

- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Przypisanie zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Me, My, MyBase i MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
