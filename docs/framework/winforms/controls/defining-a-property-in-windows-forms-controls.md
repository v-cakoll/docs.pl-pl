---
title: Definiowanie właściwości formantu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [Windows Forms], defining in code
- custom controls [Windows Forms], defining properties in code
ms.assetid: c2eb8277-a842-4d99-89a9-647b901a0434
ms.openlocfilehash: 7223f8c88bee4ee9c1db621cc39bbcf70d0c4589
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182375"
---
# <a name="defining-a-property-in-windows-forms-controls"></a>Definiowanie właściwości formantów formularzy systemu Windows
Aby uzyskać omówienie właściwości, zobacz [Omówienie właściwości](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)). Istnieje kilka ważnych zagadnień podczas definiowania właściwości:  
  
- Należy zastosować atrybuty do zdefiniowanych właściwości. Atrybuty określają, jak projektant powinien wyświetlać właściwość. Aby uzyskać szczegółowe informacje, zobacz [Atrybuty czasu projektowania dla składników](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).  
  
- Jeśli zmiana właściwości wpływa na wizualne wyświetlanie <xref:System.Windows.Forms.Control.Invalidate%2A> formantu, wywołać <xref:System.Windows.Forms.Control>metodę (która jest dziedziczona z formantu) z `set` akcesora. <xref:System.Windows.Forms.Control.Invalidate%2A>z kolei <xref:System.Windows.Forms.Control.OnPaint%2A> wywołuje metodę, która przerysowuje formant. Wiele wywołań, aby <xref:System.Windows.Forms.Control.Invalidate%2A> spowodować <xref:System.Windows.Forms.Control.OnPaint%2A> jedno wywołanie wydajności.  
  
- Biblioteka klas .NET Framework zawiera konwertery typów dla typowych typów danych, takich jak liczby całkowite, liczby dziesiętne, wartości logiczne i inne. Celem konwertera typów jest zazwyczaj zapewnienie konwersji ciąg do wartości (z danych ciągu do innych typów danych). Typowe typy danych są skojarzone z domyślnymi konwerterami typów, które konwertują wartości na ciągi i ciągi na odpowiednie typy danych. Jeśli zdefiniujesz właściwość, która jest typem danych niestandardowym (czyli niestandardowym), należy zastosować atrybut, który określa konwerter typów do skojarzenia z tą właściwością. Można również użyć atrybutu do skojarzenia niestandardowego edytora typów interfejsu użytkownika z właściwością. Edytor typów interfejsu użytkownika udostępnia interfejs użytkownika do edycji właściwości lub typu danych. Selektor kolorów jest przykładem edytora typów interfejsu użytkownika. Przykłady atrybutów są podane na końcu tego tematu.  
  
    > [!NOTE]
    > Jeśli konwerter typów lub edytor typów interfejsu użytkownika nie jest dostępny dla właściwości niestandardowej, można go zaimplementować zgodnie z opisem w [opisie w funkcji Rozszerzanie obsługi czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)).  
  
 Poniższy fragment kodu definiuje niestandardową właściwość o nazwie `EndColor` formantu `FlashTrackBar`niestandardowego .  
  
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
  
 Poniższy fragment kodu kojarzy konwerter typów i edytor `Value`typów interfejsu użytkownika z właściwością . W tym `Value` przypadku jest liczą całkowitą i ma <xref:System.ComponentModel.TypeConverterAttribute> domyślny konwerter typów,`FlashTrackBarValueConverter`ale atrybut stosuje konwerter typów niestandardowych ( ), który umożliwia projektantowi wyświetlanie go jako procent. Edytor typów interfejsu `FlashTrackBarValueEditor`użytkownika umożliwia wizualne wyświetlanie wartości procentowej. W tym przykładzie pokazano również, że <xref:System.ComponentModel.TypeConverterAttribute> konwerter typów lub edytor określony przez lub <xref:System.ComponentModel.EditorAttribute> atrybut zastępuje konwerter domyślny.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Właściwości kontrolek formularzy Windows Forms](properties-in-windows-forms-controls.md)
- [Definiowanie wartości domyślnych za pomocą metod ShouldSerialize i Reset](defining-default-values-with-the-shouldserialize-and-reset-methods.md)
- [Zdarzenia zmiany właściwości](property-changed-events.md)
- [Atrybuty w kontrolkach formularzy Windows Forms](attributes-in-windows-forms-controls.md)
