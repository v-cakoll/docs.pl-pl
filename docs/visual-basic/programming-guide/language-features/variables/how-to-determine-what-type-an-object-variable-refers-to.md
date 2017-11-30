---
title: "Porady: określanie, do jakiego typu odnosi się zmienna obiektu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5dd6785ecd48be3f0455de63b9e3f13a485ddbb2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>Porady: określanie, do jakiego typu odnosi się zmienna obiektu (Visual Basic)
Zmienna obiektu zawiera wskaźnik do danych przechowywanych w innym miejscu. Typ danych można zmienić w czasie wykonywania. W dowolnym momencie można użyć <xref:System.Type.GetTypeCode%2A> metody w celu określenia bieżącego typu czasu wykonywania, lub [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) można sprawdzić, czy bieżący typu run-time jest zgodny z określonym typem.  
  
### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>W celu określenia dokładnie typu zmienną obiektu obecnie odwołuje się do  
  
1.  Zmiennej obiektu wywołania <xref:System.Object.GetType%2A> metoda pobierania <xref:System.Type?displayProperty=nameWithType> obiektu.  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2.  Na <xref:System.Type?displayProperty=nameWithType> klasy, należy wywołać metodę udostępnionego <xref:System.Type.GetTypeCode%2A> można pobrać <xref:System.TypeCode> wartość wyliczenia dla typu obiektu.  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     Możesz przetestować <xref:System.TypeCode> wartość wyliczenia z dowolną wskazaną wyliczane elementy Członkowskie mogą być przydatne, takich jak `Double`.  
  
### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>Aby określić, czy obiekt jest zgodny z określonym typem Typ zmiennej  
  
-   Użyj `TypeOf` operatora w połączeniu z [operatora Is](../../../../visual-basic/language-reference/operators/is-operator.md) do testowania obiektu o `TypeOf`... `Is` wyrażenia.  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     `TypeOf`... `Is` zwraca wyrażenie `True` Jeśli obiektu środowiska wykonawczego typ jest zgodny z określonym typem.  
  
     Kryterium zgodności zależy od tego, czy określony typ jest klasy, struktury lub interfejsu. Ogólnie rzecz biorąc typy są zgodne, jeśli obiekt jest taki sam typ jak dziedziczy i implementuje określonego typu. Aby uzyskać więcej informacji, zobacz [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Należy pamiętać, że określony typ nie może być zmiennej lub wyrażenie. Musi to być nazwa zdefiniowanego typu, takich jak klasy, struktury lub interfejsu. Obejmuje to typy wewnętrzne takich jak `Integer` i `String`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Object.GetType%2A>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Type.GetTypeCode%2A>  
 <xref:System.TypeCode>  
 [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Wartości zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)
