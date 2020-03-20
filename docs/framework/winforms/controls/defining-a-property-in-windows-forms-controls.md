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
# <a name="defining-a-property-in-windows-forms-controls"></a><span data-ttu-id="0fdaf-102">Definiowanie właściwości formantów formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0fdaf-102">Defining a Property in Windows Forms Controls</span></span>
<span data-ttu-id="0fdaf-103">Aby uzyskać omówienie właściwości, zobacz [Omówienie właściwości](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="0fdaf-103">For an overview of properties, see [Properties Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span></span> <span data-ttu-id="0fdaf-104">Istnieje kilka ważnych zagadnień podczas definiowania właściwości:</span><span class="sxs-lookup"><span data-stu-id="0fdaf-104">There are a few important considerations when defining a property:</span></span>  
  
- <span data-ttu-id="0fdaf-105">Należy zastosować atrybuty do zdefiniowanych właściwości.</span><span class="sxs-lookup"><span data-stu-id="0fdaf-105">You must apply attributes to the properties you define.</span></span> <span data-ttu-id="0fdaf-106">Atrybuty określają, jak projektant powinien wyświetlać właściwość.</span><span class="sxs-lookup"><span data-stu-id="0fdaf-106">Attributes specify how the designer should display a property.</span></span> <span data-ttu-id="0fdaf-107">Aby uzyskać szczegółowe informacje, zobacz [Atrybuty czasu projektowania dla składników](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="0fdaf-107">For details, see [Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span></span>  
  
- <span data-ttu-id="0fdaf-108">Jeśli zmiana właściwości wpływa na wizualne wyświetlanie <xref:System.Windows.Forms.Control.Invalidate%2A> formantu, wywołać <xref:System.Windows.Forms.Control>metodę (która jest dziedziczona z formantu) z `set` akcesora.</span><span class="sxs-lookup"><span data-stu-id="0fdaf-108">If changing the property affects the visual display of the control, call the <xref:System.Windows.Forms.Control.Invalidate%2A> method (that your control inherits from <xref:System.Windows.Forms.Control>) from the `set` accessor.</span></span> <span data-ttu-id="0fdaf-109"><xref:System.Windows.Forms.Control.Invalidate%2A>z kolei <xref:System.Windows.Forms.Control.OnPaint%2A> wywołuje metodę, która przerysowuje formant.</span><span class="sxs-lookup"><span data-stu-id="0fdaf-109"><xref:System.Windows.Forms.Control.Invalidate%2A> in turn calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which redraws the control.</span></span> <span data-ttu-id="0fdaf-110">Wiele wywołań, aby <xref:System.Windows.Forms.Control.Invalidate%2A> spowodować <xref:System.Windows.Forms.Control.OnPaint%2A> jedno wywołanie wydajności.</span><span class="sxs-lookup"><span data-stu-id="0fdaf-110">Multiple calls to <xref:System.Windows.Forms.Control.Invalidate%2A> result in a single call to <xref:System.Windows.Forms.Control.OnPaint%2A> for efficiency.</span></span>  
  
- <span data-ttu-id="0fdaf-111">Biblioteka klas .NET Framework zawiera konwertery typów dla typowych typów danych, takich jak liczby całkowite, liczby dziesiętne, wartości logiczne i inne.</span><span class="sxs-lookup"><span data-stu-id="0fdaf-111">The .NET Framework class library provides type converters for common data types such as integers, decimal numbers, Boolean values, and others.</span></span> <span data-ttu-id="0fdaf-112">Celem konwertera typów jest zazwyczaj zapewnienie konwersji ciąg do wartości (z danych ciągu do innych typów danych).</span><span class="sxs-lookup"><span data-stu-id="0fdaf-112">The purpose of a type converter is generally to provide string-to-value conversion (from string data to other data types).</span></span> <span data-ttu-id="0fdaf-113">Typowe typy danych są skojarzone z domyślnymi konwerterami typów, które konwertują wartości na ciągi i ciągi na odpowiednie typy danych.</span><span class="sxs-lookup"><span data-stu-id="0fdaf-113">Common data types are associated with default type converters that convert values into strings and strings into the appropriate data types.</span></span> <span data-ttu-id="0fdaf-114">Jeśli zdefiniujesz właściwość, która jest typem danych niestandardowym (czyli niestandardowym), należy zastosować atrybut, który określa konwerter typów do skojarzenia z tą właściwością.</span><span class="sxs-lookup"><span data-stu-id="0fdaf-114">If you define a property that is a custom (that is, nonstandard) data type, you will have to apply an attribute that specifies the type converter to associate with that property.</span></span> <span data-ttu-id="0fdaf-115">Można również użyć atrybutu do skojarzenia niestandardowego edytora typów interfejsu użytkownika z właściwością.</span><span class="sxs-lookup"><span data-stu-id="0fdaf-115">You can also use an attribute to associate a custom UI type editor with a property.</span></span> <span data-ttu-id="0fdaf-116">Edytor typów interfejsu użytkownika udostępnia interfejs użytkownika do edycji właściwości lub typu danych.</span><span class="sxs-lookup"><span data-stu-id="0fdaf-116">A UI type editor provides a user interface for editing a property or data type.</span></span> <span data-ttu-id="0fdaf-117">Selektor kolorów jest przykładem edytora typów interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0fdaf-117">A color picker is an example of a UI type editor.</span></span> <span data-ttu-id="0fdaf-118">Przykłady atrybutów są podane na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="0fdaf-118">Examples of attributes are given at the end of this topic.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0fdaf-119">Jeśli konwerter typów lub edytor typów interfejsu użytkownika nie jest dostępny dla właściwości niestandardowej, można go zaimplementować zgodnie z opisem w [opisie w funkcji Rozszerzanie obsługi czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="0fdaf-119">If a type converter or a UI type editor is not available for your custom property, you can implement one as described in [Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)).</span></span>  
  
 <span data-ttu-id="0fdaf-120">Poniższy fragment kodu definiuje niestandardową właściwość o nazwie `EndColor` formantu `FlashTrackBar`niestandardowego .</span><span class="sxs-lookup"><span data-stu-id="0fdaf-120">The following code fragment defines a custom property named `EndColor` for the custom control `FlashTrackBar`.</span></span>  
  
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
  
 <span data-ttu-id="0fdaf-121">Poniższy fragment kodu kojarzy konwerter typów i edytor `Value`typów interfejsu użytkownika z właściwością .</span><span class="sxs-lookup"><span data-stu-id="0fdaf-121">The following code fragment associates a type converter and a UI type editor with the property `Value`.</span></span> <span data-ttu-id="0fdaf-122">W tym `Value` przypadku jest liczą całkowitą i ma <xref:System.ComponentModel.TypeConverterAttribute> domyślny konwerter typów,`FlashTrackBarValueConverter`ale atrybut stosuje konwerter typów niestandardowych ( ), który umożliwia projektantowi wyświetlanie go jako procent.</span><span class="sxs-lookup"><span data-stu-id="0fdaf-122">In this case `Value` is an integer and has a default type converter, but the <xref:System.ComponentModel.TypeConverterAttribute> attribute applies a custom type converter (`FlashTrackBarValueConverter`) that enables the designer to display it as a percentage.</span></span> <span data-ttu-id="0fdaf-123">Edytor typów interfejsu `FlashTrackBarValueEditor`użytkownika umożliwia wizualne wyświetlanie wartości procentowej.</span><span class="sxs-lookup"><span data-stu-id="0fdaf-123">The UI type editor, `FlashTrackBarValueEditor`, allows the percentage to be displayed visually.</span></span> <span data-ttu-id="0fdaf-124">W tym przykładzie pokazano również, że <xref:System.ComponentModel.TypeConverterAttribute> konwerter typów lub edytor określony przez lub <xref:System.ComponentModel.EditorAttribute> atrybut zastępuje konwerter domyślny.</span><span class="sxs-lookup"><span data-stu-id="0fdaf-124">This example also shows that the type converter or editor specified by the <xref:System.ComponentModel.TypeConverterAttribute> or <xref:System.ComponentModel.EditorAttribute> attribute overrides the default converter.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0fdaf-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0fdaf-125">See also</span></span>

- [<span data-ttu-id="0fdaf-126">Właściwości kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0fdaf-126">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="0fdaf-127">Definiowanie wartości domyślnych za pomocą metod ShouldSerialize i Reset</span><span class="sxs-lookup"><span data-stu-id="0fdaf-127">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](defining-default-values-with-the-shouldserialize-and-reset-methods.md)
- [<span data-ttu-id="0fdaf-128">Zdarzenia zmiany właściwości</span><span class="sxs-lookup"><span data-stu-id="0fdaf-128">Property-Changed Events</span></span>](property-changed-events.md)
- [<span data-ttu-id="0fdaf-129">Atrybuty w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0fdaf-129">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)
