---
title: "Wartości zmiennej obiektu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ccab22920923500a2332db2372e52813c890e5e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="object-variable-values-visual-basic"></a>Wartości zmiennej obiektu (Visual Basic)
Zmienna [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md) mogą odwoływać się do danych dowolnego typu. Wartości są przechowywane w `Object` zmiennej jest przechowywany w innym miejscu w pamięci, gdy samej zmiennej zawiera wskaźnik do danych.  
  
## <a name="object-classifier-functions"></a>Funkcje klasyfikatora obiektu  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]udostępnia funkcje, które zwracają informacje o tym, co `Object` zmienna odwołuje się do, jak pokazano w poniższej tabeli.  
  
|Funkcja|Zwraca wartość PRAWDA, jeśli odnosi się zmienna obiektu|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|Tablica wartości, a nie pojedynczą wartość|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|A [Date — typ danych](../../../../visual-basic/language-reference/data-types/date-data-type.md) wartość lub ciąg, który może zostać zinterpretowany jako wartość daty i godziny|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|Obiekt typu <xref:System.DBNull>, reprezentuje brakujące lub nieistniejącą dane|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|Obiekt wyjątku, który jest pochodną<xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[Nic](../../../../visual-basic/language-reference/nothing.md), oznacza to, obiekt nie jest aktualnie przypisany do zmiennej|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|Liczba lub ciąg, który może zostać zinterpretowany jako liczba|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|Typ odwołania (na przykład ciąg, tablicy, delegata lub typ klasy)|  
  
 Funkcje te można użyć w celu uniknięcia przesyłania nieprawidłową wartość do operacji lub procedury.  
  
## <a name="typeof-operator"></a>TypeOf — Operator  
 Można również użyć [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) ustalenie, czy obecnie odnosi się zmienna obiektu określonego typu danych. `TypeOf`... `Is` wyrażenie ma `True` typu run-time operandu jest pochodną lub implementuje określonego typu.  
  
 W poniższym przykładzie użyto `TypeOf` na zmienne obiektów odwołujących się do typów wartości i odwołania.  
  
```  
' The following statement puts a value type (Integer) in an Object variable.  
Dim num As Object = 10  
' The following statement puts a reference type (Form) in an Object variable.  
Dim frm As Object = New Form()  
If TypeOf num Is Long Then Debug.WriteLine("num is Long")  
If TypeOf num Is Integer Then Debug.WriteLine("num is Integer")  
If TypeOf num Is Short Then Debug.WriteLine("num is Short")  
If TypeOf num Is Object Then Debug.WriteLine("num is Object")  
If TypeOf frm Is Form Then Debug.WriteLine("frm is Form")  
If TypeOf frm Is Label Then Debug.WriteLine("frm is Label")  
If TypeOf frm Is Object Then Debug.WriteLine("frm is Object")  
```  
  
 Powyższy przykład zapisuje następujące wiersze do **debugowania** okno:  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 Zmienna obiektu `num` odnosi się do danych typu `Integer`, i `frm` odwołuje się do obiektu klasy <xref:System.Windows.Forms.Form>.  
  
## <a name="object-arrays"></a>Tablice obiektów  
 Można zadeklarować i użyj tablicy `Object` zmiennych. Jest to przydatne, gdy potrzebne do obsługi różnych typów danych i klas obiektów. Wszystkie elementy w tablicy muszą mieć ten sam zadeklarowany typ danych. Deklarowanie tego typu danych jako `Object` pozwala przechowywać obiekty i klasy wystąpień równolegle z innymi typami danych w tablicy.  
  
## <a name="see-also"></a>Zobacz też  
 [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Deklaracja zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Przypisanie zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Porady: odwoływanie się do bieżącego wystąpienia obiektu](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)  
 [Porady: wyznaczyć, jakiego typu odnosi się zmienna obiektu](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)  
 [Porady: Określanie, czy dwa obiekty są powiązane](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [Porady: Określanie, czy dwa obiekty są identyczne](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)  
 [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
