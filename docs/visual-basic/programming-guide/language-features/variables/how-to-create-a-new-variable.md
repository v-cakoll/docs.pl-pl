---
title: 'Porady: tworzenie nowej zmiennej (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aff160584d3d1fe382020d5b8c25ac57dab66d92
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-new-variable-visual-basic"></a>Porady: tworzenie nowej zmiennej (Visual Basic)
Utwórz zmienną z [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).  
  
### <a name="to-create-a-new-variable"></a>Aby utworzyć nową zmienną  
  
1.  Deklarowanie zmiennej w `Dim` instrukcji.  
  
    ```  
    Dim newCustomer  
    ```  
  
2.  Uwzględnić wymagania dotyczące cech zmiennej, takie jak [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md), [statycznych](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md), lub [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md). Aby uzyskać więcej informacji, zobacz [zadeklarowana Charakterystyka elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).  
  
    ```  
    Public Static newCustomer  
    ```  
  
     Nie trzeba `Dim` — słowo kluczowe, jeśli używasz innych słów kluczowych w deklaracji.  
  
3.  Wykonaj specyfikacji z nazwę zmiennej, która musi następować po reguły Visual Basic i Konwencji. Aby uzyskać więcej informacji, zobacz [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) (Deklarowane nazwy elementów).  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  Po nazwie [jako](../../../../visual-basic/language-reference/statements/as-clause.md) klauzuli, aby określić typ danych zmiennej.  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     Jeśli nie określisz typu danych, używa domyślnie: `Object`.  
  
5.  Postępuj zgodnie z `As` klauzuli znakiem równości (`=`) i postępuj zgodnie z znaku równości w początkowej wartości zmiennej.  
  
     Visual Basic przypisuje określona wartość do zmiennej w każdym uruchomieniu `Dim` instrukcji. Jeśli nie określisz wartości początkowej, Visual Basic najpierw wprowadza kod, który zawiera, przypisuje początkową wartością domyślną dla typu danych `Dim` instrukcji.  
  
     Jeśli zmienna jest typem referencyjnym, umieszczając w niej można utworzyć wystąpienia klasy jego [operatora New](../../../../visual-basic/language-reference/operators/new-operator.md) — słowo kluczowe w `As` klauzuli. Jeśli nie używasz `New`, początkowej wartości zmiennej jest [nic](../../../../visual-basic/language-reference/nothing.md).  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Zmienne](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Nazwy zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Charakterystyka zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Instrukcje](../../../../visual-basic/language-reference/statements/index.md)  
 [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Infer, instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
