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
ms.openlocfilehash: 43bfd54592fb1d26cbf7f268b7e098e01e3745d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410428"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>Porady: odwoływanie się do bieżącego wystąpienia obiektu (Visual Basic)
*Bieżące wystąpienie* obiektu to wystąpienie, w którym kod jest aktualnie wykonywany.  
  
 Użyj `Me` słowa kluczowego, aby odwołać się do bieżącego wystąpienia.  
  
### <a name="to-refer-to-the-current-instance"></a>Aby odwołać się do bieżącego wystąpienia  
  
- Użyj `Me` słowa kluczowego, gdzie normalnie używać nazwy zmiennej obiektu.  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     Chociaż `Me` zachowuje się jak zmienna obiektu, nie można jej zadeklarować ani przypisać do niej niczego. `Me`zawsze odwołuje się do bieżącego wystąpienia.  
  
## <a name="see-also"></a>Zobacz też

- [Zmienne obiektów](object-variables.md)
- [Przypisanie zmiennej obiektu](object-variable-assignment.md)
- [Me, My, MyBase i MyClass](../../program-structure/me-my-mybase-and-myclass.md)
