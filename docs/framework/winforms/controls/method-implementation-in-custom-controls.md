---
title: Implementacja metody w formantach niestandardowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user controls [Windows Forms], method implementation
- custom controls [Windows Forms], overloading methods
- custom controls [Windows Forms], method implementation
- methods [Windows Forms]
- methods [Windows Forms], custom controls
ms.assetid: 35d14fca-4bb4-4a27-8211-1f7a98ea27de
ms.openlocfilehash: 9df2bc9257c3f697f30cbe8c679ffc88ec34517b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538116"
---
# <a name="method-implementation-in-custom-controls"></a>Implementacja metody w formantach niestandardowych
Metoda jest zaimplementowana w formancie w taki sam sposób, które metody są realizowane w innych składników.  
  
 W języku Visual Basic, jeśli metoda jest wymagane w celu zwrócenia wartości, są one zaimplementowane jako `Public Function`. Jeśli wartość nie zostanie zwrócone, jest zaimplementowany jako `Public Sub`. Metody zadeklarowane za pomocą następującej składni:  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 Ponieważ funkcje zwracają wartość, musi określić typ zwracany, takie jak liczba całkowita, ciąg, obiekt i tak dalej. Argumenty `Function` lub `Sub` wykonać procedury, jeśli istnieje, należy także określić.  
  
 C# nie rozróżnia między funkcje i procedury, tak jak w języku Visual Basic. Metoda zwraca wartość lub zwraca `void`. Składnia deklaracji publiczną metodę C# jest:  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 W deklaracji metody, należy zadeklarować wszystkie argumenty jako typy danych jawne, jeśli to możliwe. Argumenty, które przyjmują odwołania do obiektów powinien być zadeklarowany jako klasa określonych typów — na przykład `As Widget` zamiast `As Object`. W języku Visual Basic, domyślne ustawienie `Option Strict` automatycznie wymusza tej reguły.  
  
 Argumenty typu Zezwalaj na wiele błędów developer wychwycony przez kompilator, a nie w czasie wykonywania. Kompilator zawsze połowy błędów, natomiast czasu wykonywania testów jest tylko zestaw testów.  
  
## <a name="overloaded-methods"></a>Metody przeciążane  
 Jeśli chcesz umożliwić użytkownikom formantu umożliwiają określanie kombinacji parametrów do metody, zawierają wiele przeciążenia metody, przy użyciu jawnych typów. Unikaj tworzenia parametrami zadeklarowanymi jako `As Object` który może zawierać dowolny typ danych, ponieważ może to prowadzić do błędów, które nie mogą być przechwycono testowania.  
  
> [!NOTE]
>  Typ danych uniwersalnych w środowisku uruchomieniowym języka jest `Object` zamiast `Variant`. `Variant` została usunięta z języka.  
  
 Na przykład `Spin` metody hipotetyczny `Widget` formant może zezwala na bezpośrednie specyfikacji pokrętła kierunek i szybkość lub specyfikacji innego `Widget` obiektu, z którym pędu jest pochłanianej:  
  
```vb  
Overloads Public Sub Spin( _  
   ByVal SpinDirection As SpinDirectionsEnum, _  
   ByVal RevolutionsPerSecond As Double)  
   ' Implementation code here.  
End Sub  
Overloads Public Sub Spin(ByVal Driver As Widget) _  
   ' Implementation code here.  
End Sub  
```  
  
```csharp  
public void Spin(SpinDirectionsEnum spinDirection, double revolutionsPerSecond)  
{  
   // Implementation code here.  
}  
  
public void Spin(Widget driver)  
{  
   // Implementation code here.  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia](../../../../docs/standard/events/index.md)  
 [Właściwości kontrolek formularzy Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
