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
# <a name="defining-a-property-in-windows-forms-controls"></a><span data-ttu-id="70213-102">Definiowanie właściwości formantów formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="70213-102">Defining a Property in Windows Forms Controls</span></span>
<span data-ttu-id="70213-103">Aby zapoznać się z omówieniem właściwości, zobacz [Omówienie właściwości](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="70213-103">For an overview of properties, see [Properties Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span></span> <span data-ttu-id="70213-104">Podczas definiowania właściwości należy wziąć pod uwagę kilka istotnych kwestii:</span><span class="sxs-lookup"><span data-stu-id="70213-104">There are a few important considerations when defining a property:</span></span>  
  
- <span data-ttu-id="70213-105">Należy zastosować atrybuty do zdefiniowanych właściwości.</span><span class="sxs-lookup"><span data-stu-id="70213-105">You must apply attributes to the properties you define.</span></span> <span data-ttu-id="70213-106">Atrybuty określają sposób wyświetlania właściwości przez projektanta.</span><span class="sxs-lookup"><span data-stu-id="70213-106">Attributes specify how the designer should display a property.</span></span> <span data-ttu-id="70213-107">Aby uzyskać szczegółowe informacje, zobacz [atrybuty czasu projektowania dla składników](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="70213-107">For details, see [Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span></span>  
  
- <span data-ttu-id="70213-108">Jeśli zmiana właściwości ma wpływ na wyświetlanie wizualizacji kontrolki, wywołaj metodę <xref:System.Windows.Forms.Control.Invalidate%2A> (formant dziedziczy po <xref:System.Windows.Forms.Control>) z metody dostępu `set`.</span><span class="sxs-lookup"><span data-stu-id="70213-108">If changing the property affects the visual display of the control, call the <xref:System.Windows.Forms.Control.Invalidate%2A> method (that your control inherits from <xref:System.Windows.Forms.Control>) from the `set` accessor.</span></span> <span data-ttu-id="70213-109"><xref:System.Windows.Forms.Control.Invalidate%2A> z kolei wywołuje metodę <xref:System.Windows.Forms.Control.OnPaint%2A>, która ponownie Rysuje formant.</span><span class="sxs-lookup"><span data-stu-id="70213-109"><xref:System.Windows.Forms.Control.Invalidate%2A> in turn calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which redraws the control.</span></span> <span data-ttu-id="70213-110">Wiele wywołań do <xref:System.Windows.Forms.Control.Invalidate%2A> skutkuje pojedynczym wywołaniem <xref:System.Windows.Forms.Control.OnPaint%2A> w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="70213-110">Multiple calls to <xref:System.Windows.Forms.Control.Invalidate%2A> result in a single call to <xref:System.Windows.Forms.Control.OnPaint%2A> for efficiency.</span></span>  
  
- <span data-ttu-id="70213-111">Biblioteka klas .NET Framework udostępnia konwertery typów dla wspólnych typów danych, takich jak liczby całkowite, liczby dziesiętne, wartości logiczne i inne.</span><span class="sxs-lookup"><span data-stu-id="70213-111">The .NET Framework class library provides type converters for common data types such as integers, decimal numbers, Boolean values, and others.</span></span> <span data-ttu-id="70213-112">Przeznaczenie konwertera typów zwykle zapewnia konwersję typu ciąg-do-wartości (od danych ciągu do innych typów danych).</span><span class="sxs-lookup"><span data-stu-id="70213-112">The purpose of a type converter is generally to provide string-to-value conversion (from string data to other data types).</span></span> <span data-ttu-id="70213-113">Typy wspólnych danych są skojarzone z domyślnymi konwerterami typów, które konwertują wartości na ciągi i ciągi do odpowiednich typów danych.</span><span class="sxs-lookup"><span data-stu-id="70213-113">Common data types are associated with default type converters that convert values into strings and strings into the appropriate data types.</span></span> <span data-ttu-id="70213-114">W przypadku zdefiniowania właściwości, która jest niestandardowym typem danych (czyli niestandardowym), należy zastosować atrybut określający konwerter typów do skojarzenia z tą właściwością.</span><span class="sxs-lookup"><span data-stu-id="70213-114">If you define a property that is a custom (that is, nonstandard) data type, you will have to apply an attribute that specifies the type converter to associate with that property.</span></span> <span data-ttu-id="70213-115">Można również użyć atrybutu, aby skojarzyć niestandardowy Edytor typów interfejsu użytkownika z właściwością.</span><span class="sxs-lookup"><span data-stu-id="70213-115">You can also use an attribute to associate a custom UI type editor with a property.</span></span> <span data-ttu-id="70213-116">Edytor typów interfejsu użytkownika udostępnia interfejs użytkowników do edycji właściwości lub typu danych.</span><span class="sxs-lookup"><span data-stu-id="70213-116">A UI type editor provides a user interface for editing a property or data type.</span></span> <span data-ttu-id="70213-117">Selektor kolorów jest przykładem edytora typów interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="70213-117">A color picker is an example of a UI type editor.</span></span> <span data-ttu-id="70213-118">Przykłady atrybutów są podane na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="70213-118">Examples of attributes are given at the end of this topic.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="70213-119">Jeśli konwerter typu lub Edytor typów interfejsu użytkownika nie jest dostępny dla właściwości niestandardowej, można zaimplementować jedną zgodnie z opisem w temacie [rozszerzanie obsługi czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="70213-119">If a type converter or a UI type editor is not available for your custom property, you can implement one as described in [Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)).</span></span>  
  
 <span data-ttu-id="70213-120">Poniższy fragment kodu definiuje właściwość niestandardową o nazwie `EndColor` dla `FlashTrackBar`kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="70213-120">The following code fragment defines a custom property named `EndColor` for the custom control `FlashTrackBar`.</span></span>  
  
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
  
 <span data-ttu-id="70213-121">Poniższy fragment kodu kojarzy konwerter typów i Edytor typów interfejsu użytkownika z właściwością `Value`.</span><span class="sxs-lookup"><span data-stu-id="70213-121">The following code fragment associates a type converter and a UI type editor with the property `Value`.</span></span> <span data-ttu-id="70213-122">W tym przypadku `Value` jest liczbą całkowitą i ma konwerter typu domyślnego, ale atrybut <xref:System.ComponentModel.TypeConverterAttribute> ma zastosowanie niestandardowego konwertera typów (`FlashTrackBarValueConverter`), który umożliwia projektantowi wyświetlenie go jako wartości procentowej.</span><span class="sxs-lookup"><span data-stu-id="70213-122">In this case `Value` is an integer and has a default type converter, but the <xref:System.ComponentModel.TypeConverterAttribute> attribute applies a custom type converter (`FlashTrackBarValueConverter`) that enables the designer to display it as a percentage.</span></span> <span data-ttu-id="70213-123">Edytor typów interfejsu użytkownika `FlashTrackBarValueEditor`, umożliwia wizualne Wyświetlanie wartości procentowej.</span><span class="sxs-lookup"><span data-stu-id="70213-123">The UI type editor, `FlashTrackBarValueEditor`, allows the percentage to be displayed visually.</span></span> <span data-ttu-id="70213-124">Ten przykład pokazuje również, że konwerter typu lub Edytor określony przez atrybut <xref:System.ComponentModel.TypeConverterAttribute> lub <xref:System.ComponentModel.EditorAttribute> przesłania domyślny konwerter.</span><span class="sxs-lookup"><span data-stu-id="70213-124">This example also shows that the type converter or editor specified by the <xref:System.ComponentModel.TypeConverterAttribute> or <xref:System.ComponentModel.EditorAttribute> attribute overrides the default converter.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="70213-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70213-125">See also</span></span>

- [<span data-ttu-id="70213-126">Właściwości kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="70213-126">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="70213-127">Definiowanie wartości domyślnych za pomocą metod ShouldSerialize i Reset</span><span class="sxs-lookup"><span data-stu-id="70213-127">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](defining-default-values-with-the-shouldserialize-and-reset-methods.md)
- [<span data-ttu-id="70213-128">Zdarzenia zmiany właściwości</span><span class="sxs-lookup"><span data-stu-id="70213-128">Property-Changed Events</span></span>](property-changed-events.md)
- [<span data-ttu-id="70213-129">Atrybuty w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="70213-129">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)
