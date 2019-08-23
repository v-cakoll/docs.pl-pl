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
ms.openlocfilehash: 867bf97ea13654de6f9c0209c64b9320824f9665
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931751"
---
# <a name="method-implementation-in-custom-controls"></a>Implementacja metody w formantach niestandardowych
Metoda jest implementowana w kontrolce w taki sam sposób, jak metoda zostanie zaimplementowana w innym składniku.  
  
 W Visual Basic, jeśli metoda jest wymagana do zwrócenia wartości, zostanie zaimplementowana jako `Public Function`. Jeśli żadna wartość nie zostanie zwrócona, zostanie zaimplementowana jako `Public Sub`. Metody są deklarowane przy użyciu następującej składni:  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 Ponieważ funkcje zwracają wartość, muszą określić zwracany typ, taki jak Integer, String, Object i tak dalej. Należy również `Function` określić `Sub` argumenty lub procedury, jeśli istnieją.  
  
 C#nie wykonuje rozróżnienia między funkcjami i procedurami, jak Visual Basic. Metoda zwraca wartość lub zwraca `void`. Składnia do deklarowania metody C# publicznej to:  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 Podczas deklarowania metody należy zadeklarować wszystkie jej argumenty jako jawne typy danych zawsze wtedy, gdy jest to możliwe. Argumenty, które przyjmują odwołania do obiektów, powinny być deklarowane jako określone typy `As Widget` klas — `As Object`na przykład, zamiast. W Visual Basic domyślne ustawienie `Option Strict` automatycznie wymusza tę regułę.  
  
 Wpisane argumenty umożliwiają przechwycić wiele błędów dewelopera przez kompilator, a nie w czasie wykonywania. Kompilator zawsze przechwytuje błędy, podczas gdy testowanie w czasie wykonywania jest dobrym warunkiem jako zestaw testów.  
  
## <a name="overloaded-methods"></a>Przeciążone metody  
 Jeśli chcesz zezwolić użytkownikom formantu na dostarczanie różnych kombinacji parametrów do metody, podaj wiele przeciążeń metody przy użyciu jawnych typów danych. Unikaj tworzenia zadeklarowanych `As Object` parametrów, które mogą zawierać dowolny typ danych, ponieważ może to prowadzić do błędów, które mogą nie zostać przechwycone podczas testowania.  
  
> [!NOTE]
> Uniwersalny typ danych w środowisku uruchomieniowym języka wspólnego jest `Object` `Variant`zamiast. `Variant`został usunięty z języka.  
  
 Na przykład `Spin` Metoda hipotetycznej `Widget` kontrolki może zezwalać na bezpośrednią specyfikację kierunku i szybkości pokrętła lub specyfikacją innego `Widget` obiektu, z którego ma być pochłaniana wartość kąta kątowego:  
  
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
- [Właściwości kontrolek formularzy Windows Forms](properties-in-windows-forms-controls.md)
