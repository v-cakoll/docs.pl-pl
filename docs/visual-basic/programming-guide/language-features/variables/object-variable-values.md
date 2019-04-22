---
title: Wartości zmiennej obiektu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: c17c5f85952596f0a080ca473e8f792740e66b8f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58840396"
---
# <a name="object-variable-values-visual-basic"></a>Wartości zmiennej obiektu (Visual Basic)
Zmienna [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md) mogą odwoływać się do danych dowolnego typu. Wartości są przechowywane w `Object` zmiennej jest przechowywana gdzie indziej w pamięci, a sama zmienna przechowuje wskaźnik do danych.  
  
## <a name="object-classifier-functions"></a>Funkcje klasyfikatora obiektu  
 Visual Basic dostarcza funkcje, które zwracają informacje o tym, co `Object` zmienna odwołuje się do, jak pokazano w poniższej tabeli.  
  
|Funkcja|Zwraca wartość PRAWDA, jeśli odnosi się zmienna obiektu|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|Tablica wartości, a nie wartość typu single|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|A [Date — typ danych](../../../../visual-basic/language-reference/data-types/date-data-type.md) wartość lub ciąg, który może być interpretowana jako wartość daty i godziny|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|Obiekt typu <xref:System.DBNull>, który reprezentuje dane brakujące lub nie istnieje|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|Obiekt wyjątku, który pochodzi od klasy <xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[Nic nie](../../../../visual-basic/language-reference/nothing.md), oznacza to, że żaden obiekt nie jest aktualnie przypisana do zmiennej|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|Liczba lub ciąg, który może być interpretowana jako numer|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|Typ odwołania (na przykład ciąg, macierz, delegata lub typu klasy)|  
  
 Aby uniknąć przesyłania nieprawidłową wartość operacji lub procedury, można użyć tych funkcji.  
  
## <a name="typeof-operator"></a>TypeOf — Operator  
 Można również użyć [TypeOf — Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) do określenia, czy obecnie odnosi się zmienna obiektu określonego typu danych. `TypeOf`... `Is` wyrażenie daje w wyniku `True` czy typu run-time operandu jest tworzony na podstawie implementuje określonego typu.  
  
 W poniższym przykładzie użyto `TypeOf` na zmienne odwołujące się do typu wartości i odwołań do obiektu.  
  
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
  
 Poprzedni przykład zapisuje następujące wiersze do **debugowania** okna:  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 Zmienna obiektu `num` odnosi się do danych typu `Integer`, i `frm` odwołuje się do obiektu klasy <xref:System.Windows.Forms.Form>.  
  
## <a name="object-arrays"></a>Tablice obiektów  
 Można zadeklarować i używać tablicy `Object` zmiennych. Jest to przydatne, gdy wymagana jest obsługa różnych typów danych i klas obiektów. Wszystkie elementy w tablicy musi mieć ten sam typ danych zadeklarowany. Deklarowanie ten typ danych jako `Object` pozwala przechowywać obiekty i klasy wystąpienia wraz z innymi typami danych w tablicy.  
  
## <a name="see-also"></a>Zobacz także

- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Deklaracja zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Przypisanie zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Instrukcje: Odwoływanie się do bieżącego wystąpienia obiektu](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [Instrukcje: Wyznaczyć, jakiego typu odnosi się zmienna obiektu](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)
- [Instrukcje: Określanie, czy dwa obiekty są powiązane](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Instrukcje: Określanie, czy dwa obiekty są jednakowe](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
