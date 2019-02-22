---
title: Właściwości formantów formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
ms.openlocfilehash: b1f7e0f5c1c9a01e47d0d972c56db8da922d2d0b
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56664578"
---
# <a name="properties-in-windows-forms-controls"></a><span data-ttu-id="f5e6e-102">Właściwości formantów formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f5e6e-102">Properties in Windows Forms Controls</span></span>
<span data-ttu-id="f5e6e-103">Formant programu Windows Forms dziedziczy wiele formularza właściwości klasy bazowej <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f5e6e-103">A Windows Forms control inherits many properties form the base class <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f5e6e-104">Obejmują one właściwości takich jak <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>i wiele innych.</span><span class="sxs-lookup"><span data-stu-id="f5e6e-104">These include properties such as <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>, and many others.</span></span> <span data-ttu-id="f5e6e-105">Aby uzyskać szczegółowe informacje o właściwości dziedziczonych, zobacz <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f5e6e-105">For details about inherited properties, see <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="f5e6e-106">Można zastąpić właściwości dziedziczonych w kontrolce i jak definiowania nowych właściwości.</span><span class="sxs-lookup"><span data-stu-id="f5e6e-106">You can override inherited properties in your control as well as define new properties.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f5e6e-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="f5e6e-107">In This Section</span></span>  
 [<span data-ttu-id="f5e6e-108">Definiowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="f5e6e-108">Defining a Property</span></span>](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 <span data-ttu-id="f5e6e-109">Pokazuje, jak implementować właściwość kontrolkę niestandardową lub składnika i pokazuje, jak zintegrować właściwość środowisko projektowania.</span><span class="sxs-lookup"><span data-stu-id="f5e6e-109">Shows how to implement a property for a custom control or component and shows how to integrate the property into the design environment.</span></span>  
  
 [<span data-ttu-id="f5e6e-110">Definiowanie wartości domyślnych za pomocą metod ShouldSerialize i Reset</span><span class="sxs-lookup"><span data-stu-id="f5e6e-110">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 <span data-ttu-id="f5e6e-111">Pokazuje jak zdefiniować domyślne wartości właściwości dla składnika lub kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="f5e6e-111">Shows how to define default property values for a custom control or component.</span></span>  
  
 [<span data-ttu-id="f5e6e-112">Zdarzenia zmiany właściwości</span><span class="sxs-lookup"><span data-stu-id="f5e6e-112">Property-Changed Events</span></span>](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 <span data-ttu-id="f5e6e-113">W tym artykule opisano, jak włączyć powiadomienia o zmianie właściwości po zmianie wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="f5e6e-113">Describes how to enable property-change notifications when a property value changes.</span></span>  
  
 [<span data-ttu-id="f5e6e-114">Instrukcje: Udostępnianie właściwości formantów składowych</span><span class="sxs-lookup"><span data-stu-id="f5e6e-114">How to: Expose Properties of Constituent Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md)  
 <span data-ttu-id="f5e6e-115">Pokazuje, jak udostępnianie właściwości formantów składowych w złożonego formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="f5e6e-115">Shows how to expose properties of constituent controls in a custom composite control.</span></span>  
  
 [<span data-ttu-id="f5e6e-116">Implementacja metody w kontrolkach niestandardowych</span><span class="sxs-lookup"><span data-stu-id="f5e6e-116">Method Implementation in Custom Controls</span></span>](../../../../docs/framework/winforms/controls/method-implementation-in-custom-controls.md)  
 <span data-ttu-id="f5e6e-117">Opisuje sposób implementacji metody w kontrolkach niestandardowych i składników.</span><span class="sxs-lookup"><span data-stu-id="f5e6e-117">Describes how to implement methods in custom controls and components.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f5e6e-118">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="f5e6e-118">Reference</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 <span data-ttu-id="f5e6e-119">Dokumenty klasę bazową dla implementacji formanty złożone.</span><span class="sxs-lookup"><span data-stu-id="f5e6e-119">Documents the base class for implementing composite controls.</span></span>  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 <span data-ttu-id="f5e6e-120">Dokumenty atrybut, który określa <xref:System.ComponentModel.TypeConverter> do użycia w przypadku typu właściwości niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="f5e6e-120">Documents the attribute that specifies the <xref:System.ComponentModel.TypeConverter> to use for a custom property type.</span></span>  
  
 <xref:System.ComponentModel.EditorAttribute>  
 <span data-ttu-id="f5e6e-121">Dokumenty atrybut, który określa <xref:System.Drawing.Design.UITypeEditor> do użycia dla właściwości niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="f5e6e-121">Documents the attribute that specifies the <xref:System.Drawing.Design.UITypeEditor> to use for a custom property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f5e6e-122">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="f5e6e-122">Related Sections</span></span>  
 [<span data-ttu-id="f5e6e-123">Atrybuty w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f5e6e-123">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="f5e6e-124">W tym artykule opisano atrybuty, które można zastosować do właściwości lub innym członkom swojej niestandardowych kontrolek i składników.</span><span class="sxs-lookup"><span data-stu-id="f5e6e-124">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 <span data-ttu-id="f5e6e-125">[Atrybuty czasu projektowania dla składników](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="f5e6e-125">[Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span></span>  
 <span data-ttu-id="f5e6e-126">Wyświetla listę atrybutów metadanych, które mają zastosowanie do składników i formantów, aby były wyświetlane poprawnie w czasie projektowania w projektantów wizualnych.</span><span class="sxs-lookup"><span data-stu-id="f5e6e-126">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 <span data-ttu-id="f5e6e-127">[Rozszerzenie obsługi w czasie projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="f5e6e-127">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>  
 <span data-ttu-id="f5e6e-128">Opisuje sposób implementacji klas, takich jak edytorach i projektantach, które zapewniają obsługę projektowania.</span><span class="sxs-lookup"><span data-stu-id="f5e6e-128">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>
