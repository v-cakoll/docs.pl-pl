---
title: "Definiowanie właściwości formantów formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [Windows Forms], defining in code
- custom controls [Windows Forms], defining properties in code
ms.assetid: c2eb8277-a842-4d99-89a9-647b901a0434
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8c3c25b9c408e5b8f0b76cdf87375875cdb06a13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="defining-a-property-in-windows-forms-controls"></a>Definiowanie właściwości formantów formularzy systemu Windows
Omówienie właściwości, zobacz [Przegląd właściwości](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52). Istnieje kilka istotnych kwestii, definiując właściwość:  
  
-   Należy zastosować atrybutów do właściwości, które należy zdefiniować. Atrybuty Określ, jak powinien być wyświetlany właściwości projektanta. Aby uzyskać więcej informacji, zobacz [atrybuty czasu projektowania dla składników](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).  
  
-   Jeśli zmiana właściwości dotyczy wyświetlania kontrolki, wywołaj <xref:System.Windows.Forms.Control.Invalidate%2A> — metoda (dziedziczący formantu <xref:System.Windows.Forms.Control>) z `set` metody dostępu. <xref:System.Windows.Forms.Control.Invalidate%2A>z kolei wywołuje <xref:System.Windows.Forms.Control.OnPaint%2A> metodę, która ponownie rysuje formantu. Wiele wywołań <xref:System.Windows.Forms.Control.Invalidate%2A> powoduje wywołanie <xref:System.Windows.Forms.Control.OnPaint%2A> w celu zwiększenia wydajności.  
  
-   Biblioteka klas programu .NET Framework zapewnia konwertery typu standardowe typy danych, takich jak liczby całkowite, liczby dziesiętne wartości logiczne i inne. Celem konwertera typów jest zwykle zapewnienie konwersji wartość ciągu (na podstawie danych ciągu na inne typy danych). Standardowe typy danych są skojarzone z konwertery typu domyślnego konwersji wartości do ciągów i ciągi do typów danych. W przypadku definiowania właściwości, która jest niestandardowy (to znaczy niestandardowe) typu danych, należy zastosować atrybut określający konwerter typów do skojarzenia z tą właściwością. Umożliwia także atrybutu do skojarzenia z właściwością niestandardowy Edytor typów interfejsu użytkownika. Edytor typów interfejsu użytkownika udostępnia interfejs użytkownika do edycji właściwości lub typu danych. Przykładem Edytor typów interfejsu użytkownika jest próbnika kolorów. Przykłady atrybutów znajdują się na końcu tego tematu.  
  
    > [!NOTE]
    >  Jeśli konwerter typów lub Edytor typów interfejsu użytkownika nie są dostępne dla właściwości niestandardowej, można zaimplementować jedną zgodnie z opisem w [rozszerzenie obsługi w czasie projektowania](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
 Poniższy fragment kodu definiuje właściwość niestandardowa o nazwie `EndColor` dla kontrolki niestandardowej `FlashTrackBar`.  
  
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
  
 Poniższy fragment kodu kojarzy konwertera typów i Edytor typów interfejsu użytkownika z właściwością `Value`. W takim przypadku `Value` jest liczbą całkowitą i domyślne konwerterem typów, ale <xref:System.ComponentModel.TypeConverterAttribute> atrybut jest stosowany konwertera typu niestandardowego (`FlashTrackBarValueConverter`), który umożliwia projektanta, aby wyświetlić go jako procent. Edytor typów interfejsu użytkownika, `FlashTrackBarValueEditor`, umożliwia procent będzie wyświetlany. W tym przykładzie pokazano, że również konwerter typów lub określony przez edytor <xref:System.ComponentModel.TypeConverterAttribute> lub <xref:System.ComponentModel.EditorAttribute> atrybutu zastępuje domyślną konwertera.  
  
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
 [Właściwości formantów formularzy systemu Windows](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [Definiowanie wartości domyślnych z metod ShouldSerialize i Reset](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 [Zdarzenia zmiany właściwości](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 [Atrybuty w formantach formularzy systemu Windows](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)
