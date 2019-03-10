---
title: Definiowanie właściwości formantów formularzy systemu Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [Windows Forms], defining in code
- custom controls [Windows Forms], defining properties in code
ms.assetid: c2eb8277-a842-4d99-89a9-647b901a0434
ms.openlocfilehash: 84273d2fab36df287eaca70f5f32fd8024a9204d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712204"
---
# <a name="defining-a-property-in-windows-forms-controls"></a>Definiowanie właściwości formantów formularzy systemu Windows
Aby zapoznać się z omówieniem właściwości, zobacz [Przegląd właściwości](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)). Istnieje kilka istotnych kwestii, definiując właściwość:  
  
-   Należy najpierw zastosować atrybutów do właściwości, jaką zdefiniujesz. Atrybuty określają, jak projektant powinien być wyświetlany właściwości. Aby uzyskać więcej informacji, zobacz [atrybuty czasu projektowania dla składników](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).  
  
-   Jeśli zmiana wartości właściwości dotyczy wyświetlania kontrolki, należy wywołać <xref:System.Windows.Forms.Control.Invalidate%2A> — metoda (dziedziczący kontroli nad <xref:System.Windows.Forms.Control>) z `set` metody dostępu. <xref:System.Windows.Forms.Control.Invalidate%2A> z kolei wywołuje <xref:System.Windows.Forms.Control.OnPaint%2A> metody, która odrysowuje formantu. Wiele wywołań <xref:System.Windows.Forms.Control.Invalidate%2A> powoduje, jednokrotnego wywołania <xref:System.Windows.Forms.Control.OnPaint%2A> w celu zwiększenia wydajności.  
  
-   Biblioteka klas .NET Framework zapewnia konwerterów typów standardowe typy danych, takich jak liczby całkowite, liczby dziesiętne, wartości logicznych i innych. Celem konwertera typów jest zwykle zapewniają wartość ciągu konwersja (dane ciągu na inne typy danych). Standardowe typy danych są skojarzone z konwertery typu domyślnego, które konwertują wartości do ciągów i ciągów na typy danych. Jeśli zdefiniowano właściwość niestandardową (oznacza to, niestandardowe) typu danych, należy zastosować atrybut określający konwertera typów do skojarzenia z tej właściwości. Atrybut umożliwia również skojarzyć niestandardowego edytora typów interfejsu użytkownika z właściwością. Edytor typów interfejsu użytkownika udostępnia interfejs użytkownika do edycji właściwości lub typu danych. Selektor kolorów jest przykład edytora typów interfejsu użytkownika. Przykłady atrybutów znajdują się na końcu tego tematu.  
  
    > [!NOTE]
    >  Jeśli konwertera typów lub Edytor typów interfejsu użytkownika nie są dostępne dla właściwości niestandardowej, można zaimplementować jeden zgodnie z opisem w [rozszerzenie obsługi w czasie projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)).  
  
 Poniższy fragment kodu definiuje właściwość niestandardowa o nazwie `EndColor` dla formantu niestandardowego `FlashTrackBar`.  
  
```vb  
Public Class FlashTrackBar  
   Inherits Control  
   ...  
   ' Private data member that backs the EndColor property.  
   Private _endColor As Color = Color.LimeGreen  
  
   ' The Category attribute tells the designer to display  
   ' it in the Flash grouping.   
   ' The Description attribute provides a description of  
   ' the property.   
   <Category("Flash"), _  
   Description("The ending color of the bar.")>  _  
   Public Property EndColor() As Color  
      ' The public property EndColor accesses _endColor.  
      Get  
         Return _endColor  
      End Get  
      Set  
         _endColor = value  
         If Not (baseBackground Is Nothing) And showGradient Then  
            baseBackground.Dispose()  
            baseBackground = Nothing  
         End If  
         ' The Invalidate method calls the OnPaint method, which redraws    
         ' the control.  
         Invalidate()  
      End Set  
   End Property  
   ...  
End Class  
```  
  
```csharp  
public class FlashTrackBar : Control {  
   ...  
   // Private data member that backs the EndColor property.  
   private Color endColor = Color.LimeGreen;  
   // The Category attribute tells the designer to display  
   // it in the Flash grouping.   
   // The Description attribute provides a description of  
   // the property.   
   [  
   Category("Flash"),  
   Description("The ending color of the bar.")  
   ]  
   // The public property EndColor accesses endColor.  
   public Color EndColor {  
      get {  
         return endColor;  
      }  
      set {  
         endColor = value;  
         if (baseBackground != null && showGradient) {  
            baseBackground.Dispose();  
            baseBackground = null;  
         }  
         // The Invalidate method calls the OnPaint method, which redraws   
         // the control.  
         Invalidate();  
      }  
   }  
   ...  
}  
```  
  
 Poniższy fragment kodu tworzy skojarzenia między konwertera typów i Edytor typów interfejsu użytkownika za pomocą właściwości `Value`. W tym przypadku `Value` jest liczbą całkowitą, a ma konwertera typów domyślnego, ale <xref:System.ComponentModel.TypeConverterAttribute> atrybutu, dotyczy konwertera typów niestandardowych (`FlashTrackBarValueConverter`), który umożliwia projektanta Aby wyświetlić go jako procent. Edytor typów interfejsu użytkownika, `FlashTrackBarValueEditor`, umożliwia procent, które mają być wyświetlane wizualnie. Ten przykład pokazuje, że również konwertera typów lub editor określona przez <xref:System.ComponentModel.TypeConverterAttribute> lub <xref:System.ComponentModel.EditorAttribute> konwerter domyślne przesłonięcia atrybutów.  
  
```vb  
<Category("Flash"), _  
TypeConverter(GetType(FlashTrackBarValueConverter)), _  
Editor(GetType(FlashTrackBarValueEditor), _  
GetType(UITypeEditor)), _  
Description("The current value of the track bar.  You can enter an actual value or a percentage.")>  _  
Public ReadOnly Property Value() As Integer  
...  
End Property  
```  
  
```csharp  
[  
Category("Flash"),   
TypeConverter(typeof(FlashTrackBarValueConverter)),  
Editor(typeof(FlashTrackBarValueEditor), typeof(UITypeEditor)),  
Description("The current value of the track bar.  You can enter an actual value or a percentage.")  
]  
public int Value {  
...  
}  
```  
  
## <a name="see-also"></a>Zobacz także
- [Właściwości kontrolek formularzy Windows Forms](properties-in-windows-forms-controls.md)
- [Definiowanie wartości domyślnych za pomocą metod ShouldSerialize i Reset](defining-default-values-with-the-shouldserialize-and-reset-methods.md)
- [Zdarzenia zmiany właściwości](property-changed-events.md)
- [Atrybuty w kontrolkach formularzy Windows Forms](attributes-in-windows-forms-controls.md)
