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
ms.openlocfilehash: dc47d7152419d55b3e52aec70257e2b39e9aaca0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528326"
---
# <a name="defining-a-property-in-windows-forms-controls"></a><span data-ttu-id="cd7ca-102">Definiowanie właściwości formantów formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="cd7ca-102">Defining a Property in Windows Forms Controls</span></span>
<span data-ttu-id="cd7ca-103">Omówienie właściwości, zobacz [Przegląd właściwości](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span><span class="sxs-lookup"><span data-stu-id="cd7ca-103">For an overview of properties, see [Properties Overview](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span></span> <span data-ttu-id="cd7ca-104">Istnieje kilka istotnych kwestii, definiując właściwość:</span><span class="sxs-lookup"><span data-stu-id="cd7ca-104">There are a few important considerations when defining a property:</span></span>  
  
-   <span data-ttu-id="cd7ca-105">Należy zastosować atrybutów do właściwości, które należy zdefiniować.</span><span class="sxs-lookup"><span data-stu-id="cd7ca-105">You must apply attributes to the properties you define.</span></span> <span data-ttu-id="cd7ca-106">Atrybuty Określ, jak powinien być wyświetlany właściwości projektanta.</span><span class="sxs-lookup"><span data-stu-id="cd7ca-106">Attributes specify how the designer should display a property.</span></span> <span data-ttu-id="cd7ca-107">Aby uzyskać więcej informacji, zobacz [atrybuty czasu projektowania dla składników](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).</span><span class="sxs-lookup"><span data-stu-id="cd7ca-107">For details, see [Design-Time Attributes for Components](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).</span></span>  
  
-   <span data-ttu-id="cd7ca-108">Jeśli zmiana właściwości dotyczy wyświetlania kontrolki, wywołaj <xref:System.Windows.Forms.Control.Invalidate%2A> — metoda (dziedziczący formantu <xref:System.Windows.Forms.Control>) z `set` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="cd7ca-108">If changing the property affects the visual display of the control, call the <xref:System.Windows.Forms.Control.Invalidate%2A> method (that your control inherits from <xref:System.Windows.Forms.Control>) from the `set` accessor.</span></span> <span data-ttu-id="cd7ca-109"><xref:System.Windows.Forms.Control.Invalidate%2A> z kolei wywołuje <xref:System.Windows.Forms.Control.OnPaint%2A> metodę, która ponownie rysuje formantu.</span><span class="sxs-lookup"><span data-stu-id="cd7ca-109"><xref:System.Windows.Forms.Control.Invalidate%2A> in turn calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which redraws the control.</span></span> <span data-ttu-id="cd7ca-110">Wiele wywołań <xref:System.Windows.Forms.Control.Invalidate%2A> powoduje wywołanie <xref:System.Windows.Forms.Control.OnPaint%2A> w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="cd7ca-110">Multiple calls to <xref:System.Windows.Forms.Control.Invalidate%2A> result in a single call to <xref:System.Windows.Forms.Control.OnPaint%2A> for efficiency.</span></span>  
  
-   <span data-ttu-id="cd7ca-111">Biblioteka klas programu .NET Framework zapewnia konwertery typu standardowe typy danych, takich jak liczby całkowite, liczby dziesiętne wartości logiczne i inne.</span><span class="sxs-lookup"><span data-stu-id="cd7ca-111">The .NET Framework class library provides type converters for common data types such as integers, decimal numbers, Boolean values, and others.</span></span> <span data-ttu-id="cd7ca-112">Celem konwertera typów jest zwykle zapewnienie konwersji wartość ciągu (na podstawie danych ciągu na inne typy danych).</span><span class="sxs-lookup"><span data-stu-id="cd7ca-112">The purpose of a type converter is generally to provide string-to-value conversion (from string data to other data types).</span></span> <span data-ttu-id="cd7ca-113">Standardowe typy danych są skojarzone z konwertery typu domyślnego konwersji wartości do ciągów i ciągi do typów danych.</span><span class="sxs-lookup"><span data-stu-id="cd7ca-113">Common data types are associated with default type converters that convert values into strings and strings into the appropriate data types.</span></span> <span data-ttu-id="cd7ca-114">W przypadku definiowania właściwości, która jest niestandardowy (to znaczy niestandardowe) typu danych, należy zastosować atrybut określający konwerter typów do skojarzenia z tą właściwością.</span><span class="sxs-lookup"><span data-stu-id="cd7ca-114">If you define a property that is a custom (that is, nonstandard) data type, you will have to apply an attribute that specifies the type converter to associate with that property.</span></span> <span data-ttu-id="cd7ca-115">Umożliwia także atrybutu do skojarzenia z właściwością niestandardowy Edytor typów interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cd7ca-115">You can also use an attribute to associate a custom UI type editor with a property.</span></span> <span data-ttu-id="cd7ca-116">Edytor typów interfejsu użytkownika udostępnia interfejs użytkownika do edycji właściwości lub typu danych.</span><span class="sxs-lookup"><span data-stu-id="cd7ca-116">A UI type editor provides a user interface for editing a property or data type.</span></span> <span data-ttu-id="cd7ca-117">Przykładem Edytor typów interfejsu użytkownika jest próbnika kolorów.</span><span class="sxs-lookup"><span data-stu-id="cd7ca-117">A color picker is an example of a UI type editor.</span></span> <span data-ttu-id="cd7ca-118">Przykłady atrybutów znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="cd7ca-118">Examples of attributes are given at the end of this topic.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cd7ca-119">Jeśli konwerter typów lub Edytor typów interfejsu użytkownika nie są dostępne dla właściwości niestandardowej, można zaimplementować jedną zgodnie z opisem w [rozszerzenie obsługi w czasie projektowania](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).</span><span class="sxs-lookup"><span data-stu-id="cd7ca-119">If a type converter or a UI type editor is not available for your custom property, you can implement one as described in [Extending Design-Time Support](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).</span></span>  
  
 <span data-ttu-id="cd7ca-120">Poniższy fragment kodu definiuje właściwość niestandardowa o nazwie `EndColor` dla kontrolki niestandardowej `FlashTrackBar`.</span><span class="sxs-lookup"><span data-stu-id="cd7ca-120">The following code fragment defines a custom property named `EndColor` for the custom control `FlashTrackBar`.</span></span>  
  
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
  
 <span data-ttu-id="cd7ca-121">Poniższy fragment kodu kojarzy konwertera typów i Edytor typów interfejsu użytkownika z właściwością `Value`.</span><span class="sxs-lookup"><span data-stu-id="cd7ca-121">The following code fragment associates a type converter and a UI type editor with the property `Value`.</span></span> <span data-ttu-id="cd7ca-122">W takim przypadku `Value` jest liczbą całkowitą i domyślne konwerterem typów, ale <xref:System.ComponentModel.TypeConverterAttribute> atrybut jest stosowany konwertera typu niestandardowego (`FlashTrackBarValueConverter`), który umożliwia projektanta, aby wyświetlić go jako procent.</span><span class="sxs-lookup"><span data-stu-id="cd7ca-122">In this case `Value` is an integer and has a default type converter, but the <xref:System.ComponentModel.TypeConverterAttribute> attribute applies a custom type converter (`FlashTrackBarValueConverter`) that enables the designer to display it as a percentage.</span></span> <span data-ttu-id="cd7ca-123">Edytor typów interfejsu użytkownika, `FlashTrackBarValueEditor`, umożliwia procent będzie wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="cd7ca-123">The UI type editor, `FlashTrackBarValueEditor`, allows the percentage to be displayed visually.</span></span> <span data-ttu-id="cd7ca-124">W tym przykładzie pokazano, że również konwerter typów lub określony przez edytor <xref:System.ComponentModel.TypeConverterAttribute> lub <xref:System.ComponentModel.EditorAttribute> atrybutu zastępuje domyślną konwertera.</span><span class="sxs-lookup"><span data-stu-id="cd7ca-124">This example also shows that the type converter or editor specified by the <xref:System.ComponentModel.TypeConverterAttribute> or <xref:System.ComponentModel.EditorAttribute> attribute overrides the default converter.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cd7ca-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd7ca-125">See Also</span></span>  
 [<span data-ttu-id="cd7ca-126">Właściwości kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cd7ca-126">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [<span data-ttu-id="cd7ca-127">Definiowanie wartości domyślnych za pomocą metod ShouldSerialize i Reset</span><span class="sxs-lookup"><span data-stu-id="cd7ca-127">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 [<span data-ttu-id="cd7ca-128">Zdarzenia zmiany właściwości</span><span class="sxs-lookup"><span data-stu-id="cd7ca-128">Property-Changed Events</span></span>](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 [<span data-ttu-id="cd7ca-129">Atrybuty w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cd7ca-129">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)
