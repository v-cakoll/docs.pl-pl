---
title: Wartości zmiennej obiektu
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: 8b93063d2d97802b1a7fdbc93e01040ff3337753
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351800"
---
# <a name="object-variable-values-visual-basic"></a>Wartości zmiennej obiektu (Visual Basic)
Zmienna [typu danych obiektu](../../../../visual-basic/language-reference/data-types/object-data-type.md) może odwoływać się do danych dowolnego typu. Wartość przechowywana w zmiennej `Object` jest przechowywana w innym miejscu w pamięci, podczas gdy zmienna sama zawiera wskaźnik do danych.  
  
## <a name="object-classifier-functions"></a>Funkcje klasyfikatora obiektów  
 Visual Basic dostarcza funkcje, które zwracają informacje o tym, do czego odnosi się `Object` zmienna, jak pokazano w poniższej tabeli.  
  
|Funkcja|Zwraca wartość PRAWDA, jeśli zmienna obiektu odwołuje się do|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|Tablica wartości, a nie pojedyncza wartość|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|Wartość [typu danych Data](../../../../visual-basic/language-reference/data-types/date-data-type.md) lub ciąg, który może być interpretowany jako wartość daty i godziny.|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|Obiekt typu <xref:System.DBNull>, który reprezentuje brakujące lub nieistniejące dane|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|Obiekt wyjątku, który pochodzi od <xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[Nic](../../../../visual-basic/language-reference/nothing.md), oznacza to, że żaden obiekt nie jest obecnie przypisany do zmiennej|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|Liczba lub ciąg, który może być interpretowany jako liczba|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|Typ referencyjny (na przykład ciąg, tablica, delegat lub typ klasy)|  
  
 Tych funkcji można użyć, aby uniknąć przesyłania nieprawidłowej wartości do operacji lub procedury.  
  
## <a name="typeof-operator"></a>TypeOf — Operator  
 Można również użyć [operatora typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md) , aby określić, czy zmienna obiektu aktualnie odwołuje się do określonego typu danych. Wyrażenie `TypeOf`...`Is` daje w wyniku `True`, jeśli typ czasu wykonywania operandu jest pochodną lub implementuje określony typ.  
  
 Poniższy przykład używa `TypeOf` w zmiennych obiektu odnoszących się do typów wartości i referencyjnych.  
  
```vb  
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
  
 Powyższy przykład zapisuje następujące wiersze do okna **debugowania** :  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 Zmienna obiektu `num` odwołuje się do danych typu `Integer`, a `frm` odwołuje się do obiektu klasy <xref:System.Windows.Forms.Form>.  
  
## <a name="object-arrays"></a>Tablice obiektów  
 Można zadeklarować tablicę `Object` zmiennych i używać jej. Jest to przydatne, gdy konieczne jest obsługę różnych typów danych i klas obiektów. Wszystkie elementy w tablicy muszą mieć ten sam zadeklarowany typ danych. Deklarowanie tego typu danych jako `Object` umożliwia przechowywanie obiektów i wystąpień klas wraz z innymi typami danych w tablicy.  
  
## <a name="see-also"></a>Zobacz także

- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Deklaracja zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Przypisanie zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Instrukcje: odwoływanie się do bieżącego wystąpienia obiektu](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [Instrukcje: określanie, do jakiego typu odnosi się zmienna obiektu](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)
- [Instrukcje: określanie, czy dwa obiekty są powiązane](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Instrukcje: określanie, czy dwa obiekty są jednakowe](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
