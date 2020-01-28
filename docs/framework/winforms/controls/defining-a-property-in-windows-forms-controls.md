---
title: Definiowanie właściwości kontrolki
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [Windows Forms], defining in code
- custom controls [Windows Forms], defining properties in code
ms.assetid: c2eb8277-a842-4d99-89a9-647b901a0434
ms.openlocfilehash: 0fec817226a7da4b44ec992f9e384a2ad5449001
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746107"
---
# <a name="defining-a-property-in-windows-forms-controls"></a>Definiowanie właściwości formantów formularzy systemu Windows
Aby zapoznać się z omówieniem właściwości, zobacz [Omówienie właściwości](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)). Podczas definiowania właściwości należy wziąć pod uwagę kilka istotnych kwestii:  
  
- Należy zastosować atrybuty do zdefiniowanych właściwości. Atrybuty określają sposób wyświetlania właściwości przez projektanta. Aby uzyskać szczegółowe informacje, zobacz [atrybuty czasu projektowania dla składników](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).  
  
- Jeśli zmiana właściwości ma wpływ na wyświetlanie wizualizacji kontrolki, wywołaj metodę <xref:System.Windows.Forms.Control.Invalidate%2A> (formant dziedziczy po <xref:System.Windows.Forms.Control>) z metody dostępu `set`. <xref:System.Windows.Forms.Control.Invalidate%2A> z kolei wywołuje metodę <xref:System.Windows.Forms.Control.OnPaint%2A>, która ponownie Rysuje formant. Wiele wywołań do <xref:System.Windows.Forms.Control.Invalidate%2A> skutkuje pojedynczym wywołaniem <xref:System.Windows.Forms.Control.OnPaint%2A> w celu zwiększenia wydajności.  
  
- Biblioteka klas .NET Framework udostępnia konwertery typów dla wspólnych typów danych, takich jak liczby całkowite, liczby dziesiętne, wartości logiczne i inne. Przeznaczenie konwertera typów zwykle zapewnia konwersję typu ciąg-do-wartości (od danych ciągu do innych typów danych). Typy wspólnych danych są skojarzone z domyślnymi konwerterami typów, które konwertują wartości na ciągi i ciągi do odpowiednich typów danych. W przypadku zdefiniowania właściwości, która jest niestandardowym typem danych (czyli niestandardowym), należy zastosować atrybut określający konwerter typów do skojarzenia z tą właściwością. Można również użyć atrybutu, aby skojarzyć niestandardowy Edytor typów interfejsu użytkownika z właściwością. Edytor typów interfejsu użytkownika udostępnia interfejs użytkowników do edycji właściwości lub typu danych. Selektor kolorów jest przykładem edytora typów interfejsu użytkownika. Przykłady atrybutów są podane na końcu tego tematu.  
  
    > [!NOTE]
    > Jeśli konwerter typu lub Edytor typów interfejsu użytkownika nie jest dostępny dla właściwości niestandardowej, można zaimplementować jedną zgodnie z opisem w temacie [rozszerzanie obsługi czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)).  
  
 Poniższy fragment kodu definiuje właściwość niestandardową o nazwie `EndColor` dla `FlashTrackBar`kontrolki niestandardowej.  
  
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
  
 Poniższy fragment kodu kojarzy konwerter typów i Edytor typów interfejsu użytkownika z właściwością `Value`. W tym przypadku `Value` jest liczbą całkowitą i ma konwerter typu domyślnego, ale atrybut <xref:System.ComponentModel.TypeConverterAttribute> ma zastosowanie niestandardowego konwertera typów (`FlashTrackBarValueConverter`), który umożliwia projektantowi wyświetlenie go jako wartości procentowej. Edytor typów interfejsu użytkownika `FlashTrackBarValueEditor`, umożliwia wizualne Wyświetlanie wartości procentowej. Ten przykład pokazuje również, że konwerter typu lub Edytor określony przez atrybut <xref:System.ComponentModel.TypeConverterAttribute> lub <xref:System.ComponentModel.EditorAttribute> przesłania domyślny konwerter.  
  
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
