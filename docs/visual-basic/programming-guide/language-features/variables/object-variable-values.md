---
title: Wartości zmiennej obiektu
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: 1dd3e8cd68086fe116daf0678a1a19881f1ae9c3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410351"
---
# <a name="object-variable-values-visual-basic"></a>Wartości zmiennej obiektu (Visual Basic)
Zmienna [typu danych obiektu](../../../language-reference/data-types/object-data-type.md) może odwoływać się do danych dowolnego typu. Wartość przechowywana w `Object` zmiennej jest przechowywana w innym miejscu w pamięci, podczas gdy zmienna sama zawiera wskaźnik do danych.  
  
## <a name="object-classifier-functions"></a>Funkcje klasyfikatora obiektów  
 Visual Basic dostarcza funkcje, które zwracają informacje o tym `Object` , do czego odwołuje się zmienna, jak pokazano w poniższej tabeli.  
  
|Funkcja|Zwraca wartość PRAWDA, jeśli zmienna obiektu odwołuje się do|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|Tablica wartości, a nie pojedyncza wartość|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|Wartość [typu danych Data](../../../language-reference/data-types/date-data-type.md) lub ciąg, który może być interpretowany jako wartość daty i godziny.|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|Obiekt typu <xref:System.DBNull> , który reprezentuje brakujące lub nieistniejące dane|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|Obiekt wyjątku, który pochodzi od<xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[Nic](../../../language-reference/nothing.md), oznacza to, że żaden obiekt nie jest obecnie przypisany do zmiennej|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|Liczba lub ciąg, który może być interpretowany jako liczba|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|Typ referencyjny (na przykład ciąg, tablica, delegat lub typ klasy)|  
  
 Tych funkcji można użyć, aby uniknąć przesyłania nieprawidłowej wartości do operacji lub procedury.  
  
## <a name="typeof-operator"></a>TypeOf — Operator  
 Można również użyć [operatora typeof](../../../language-reference/operators/typeof-operator.md) , aby określić, czy zmienna obiektu aktualnie odwołuje się do określonego typu danych. `TypeOf`Wyrażenie... zwraca `Is` wartość, `True` Jeśli typ czasu wykonywania operandu jest pochodną lub implementuje określony typ.  
  
 W poniższym przykładzie zastosowano `TypeOf` zmienne obiektu odwołujące się do typów wartości i referencyjnych.  
  
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
  
 Zmienna obiektu `num` odwołuje się do danych typu `Integer` i `frm` odwołuje się do obiektu klasy <xref:System.Windows.Forms.Form> .  
  
## <a name="object-arrays"></a>Tablice obiektów  
 Można zadeklarować tablicę zmiennych i używać jej `Object` . Jest to przydatne, gdy konieczne jest obsługę różnych typów danych i klas obiektów. Wszystkie elementy w tablicy muszą mieć ten sam zadeklarowany typ danych. Deklarowanie tego typu danych jako `Object` umożliwia przechowywanie obiektów i wystąpień klas wraz z innymi typami danych w tablicy.  
  
## <a name="see-also"></a>Zobacz też

- [Zmienne obiektów](object-variables.md)
- [Deklaracja zmiennej obiektu](object-variable-declaration.md)
- [Przypisanie zmiennej obiektu](object-variable-assignment.md)
- [Instrukcje: odwoływanie się do bieżącego wystąpienia obiektu](how-to-refer-to-the-current-instance-of-an-object.md)
- [Instrukcje: określanie, do jakiego typu odnosi się zmienna obiektu](how-to-determine-what-type-an-object-variable-refers-to.md)
- [Porady: określanie, czy dwa obiekty są powiązane](how-to-determine-whether-two-objects-are-related.md)
- [Porady: określanie, czy dwa obiekty są jednakowe](how-to-determine-whether-two-objects-are-identical.md)
- [Typy danych](../data-types/index.md)
