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
ms.openlocfilehash: 38dcad25af31b87afc1cc6ef4f89a1f7903bc0ed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117420"
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

- [Zdarzenia](../../../standard/events/index.md)
- [Właściwości formantów formularzy systemu Windows](properties-in-windows-forms-controls.md)
