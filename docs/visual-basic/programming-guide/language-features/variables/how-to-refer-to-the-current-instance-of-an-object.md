---
title: "Porady: odwoływanie się do bieżącego wystąpienia obiektu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33ea612253b00e12f47258189da4ac7d8d98ade5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>Porady: odwoływanie się do bieżącego wystąpienia obiektu (Visual Basic)
*Bieżącego wystąpienia* obiektu jest wystąpienie, w którym kod jest aktualnie wykonywany.  
  
 Możesz użyć `Me` — słowo kluczowe do odwoływania się do bieżącego wystąpienia.  
  
### <a name="to-refer-to-the-current-instance"></a>Aby odwołać się do bieżącego wystąpienia  
  
-   Użyj `Me` — słowo kluczowe zwykle użycia nazwę zmiennej obiektu.  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     Mimo że `Me` zachowuje się jak obiekt zmiennej, nie można zadeklarować go lub niczego przypisać do niej. `Me`zawsze odwołuje się do bieżącego wystąpienia.  
  
## <a name="see-also"></a>Zobacz też  
 [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Przypisanie zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Me, My, MyBase i MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
