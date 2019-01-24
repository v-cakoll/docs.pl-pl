---
title: 'Instrukcje: Wyznaczyć, jakiego typu odnosi się zmienna obiektu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 149af116f2b848082367b33d826bace8345cee05
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571181"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>Instrukcje: Wyznaczyć, jakiego typu odnosi się zmienna obiektu (Visual Basic)
Zmienna obiektu zawiera wskaźnik do danych przechowywanych w różnych miejscach. Typ danych można zmienić w czasie wykonywania. W każdej chwili możesz użyć <xref:System.Type.GetTypeCode%2A> metodę pozwala ustalić bieżącego typu run-time lub [TypeOf — Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) można sprawdzić, czy bieżący typu run-time jest zgodny z określonym typem.  
  
### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>Można określić konkretny typ zmiennej obiektu obecnie odwołuje się do  
  
1.  Na zmienną obiektu, wywołaj <xref:System.Object.GetType%2A> metodę, która pobierze <xref:System.Type?displayProperty=nameWithType> obiektu.  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2.  Na <xref:System.Type?displayProperty=nameWithType> klasy, wywołaj metodę udostępnionego <xref:System.Type.GetTypeCode%2A> można pobrać <xref:System.TypeCode> wartość wyliczenia typu obiektu.  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     Możesz przetestować <xref:System.TypeCode> wartość wyliczenia dla jednego z tych elementów członkowskich wyliczenia są interesujące, takie jak `Double`.  
  
### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>Aby określić, czy obiekt jest zgodny z określonym typem Typ zmiennej  
  
-   Użyj `TypeOf` operatora w połączeniu z [operatora Is](../../../../visual-basic/language-reference/operators/is-operator.md) do testowania obiekt z `TypeOf`... `Is` wyrażenia.  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     `TypeOf`... `Is` zwraca wyrażenie `True` Jeśli obiekt środowiska wykonawczego typ jest zgodny z określonym typem.  
  
     Dla zgodności kryterium zależy od tego, czy określony typ jest klasy, struktury lub interfejsu. Ogólnie rzecz biorąc typy są zgodne, jeśli obiekt jest taki sam jak, dziedziczy lub implementuje określonego typu. Aby uzyskać więcej informacji, zobacz [TypeOf — Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Należy pamiętać, że określony typ nie może być zmiennej lub wyrażenia. Musi to być nazwa zdefiniowanego typu, takich jak klasy, struktury lub interfejsu. Obejmuje to typy wewnętrzne takie jak `Integer` i `String`.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Wartości zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Object, typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)
