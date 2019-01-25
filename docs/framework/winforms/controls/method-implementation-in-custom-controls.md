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
ms.openlocfilehash: f65c34c965ddf19c7a287eeeaafe2583c97583ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506073"
---
# <a name="method-implementation-in-custom-controls"></a>Implementacja metody w formantach niestandardowych
Metoda jest zaimplementowana w formancie w taki sam sposób, którego metody mogą być realizowane w jakikolwiek inny składnik.  
  
 W języku Visual Basic, jeśli metoda jest wymagane w celu zwrócenia wartości, są one zaimplementowane jako `Public Function`. Jeśli jest zwracana żadna wartość, jest implementowany jako `Public Sub`. Metody są deklarowane przy użyciu następującej składni:  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 Ponieważ funkcje zwracają wartość, określać typ zwracany, takie jak liczba całkowita, ciąg, obiekt i tak dalej. Argumenty `Function` lub `Sub` wykonać procedury, jeśli istnieją, należy także określić.  
  
 C#nie rozróżnia pomiędzy funkcjami i procedur, tak jak w języku Visual Basic. Metoda zwraca wartość lub zwraca `void`. Składnia do deklarowania C# jest publiczną metodę:  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 Po użytkownik deklaruje metodę, należy zadeklarować wszystkie jej argumenty jako typy danych jawne, jeśli to możliwe. Argumenty, które przyjmują odwołania do obiektu powinien być zadeklarowany jako typu określonej klasy — na przykład `As Widget` zamiast `As Object`. W języku Visual Basic, domyślne ustawienie `Option Strict` automatycznie wymuszają tę regułę.  
  
 Argumenty wpisane zezwala na wiele błędów dla deweloperów, aby zostać przechwycony przez kompilator, a nie w czasie wykonywania. Kompilator zawsze połowy błędów, testowania w czasie wykonywania tylko jest dobrą zestawu testów.  
  
## <a name="overloaded-methods"></a>Przeciążone metody  
 Jeśli chcesz umożliwić użytkownikom kontroli nad Podaj różne kombinacje parametrów do metody, należy podać wiele przeciążeń metody, za pomocą jawnych typów. Unikaj tworzenia parametrami zadeklarowanymi jako `As Object` , może zawierać żadnego typu danych, ponieważ może to prowadzić do błędów, które nie może zostać przechwycony podczas testowania.  
  
> [!NOTE]
>  Typ danych uniwersalne środowisko uruchomieniowe języka wspólnego jest `Object` zamiast `Variant`. `Variant` Usunięto od języka.  
  
 Na przykład `Spin` metoda możesz `Widget` formant może zezwala na bezpośrednie specyfikacji pokrętła kierunku i szybkość lub specyfikacji innego `Widget` obiekt, z których pęd angular jest pochłanianej:  
  
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
  
## <a name="see-also"></a>Zobacz także
- [Zdarzenia](../../../../docs/standard/events/index.md)
- [Właściwości kontrolek formularzy Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
