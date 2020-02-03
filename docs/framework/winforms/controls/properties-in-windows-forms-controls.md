---
title: Właściwości kontrolek
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
ms.openlocfilehash: 82bfab15cef4946661a37d2d88fbe1b797f3d816
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741180"
---
# <a name="properties-in-windows-forms-controls"></a><span data-ttu-id="06742-102">Właściwości formantów formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="06742-102">Properties in Windows Forms Controls</span></span>
<span data-ttu-id="06742-103">Formant Windows Forms dziedziczy wiele właściwości w klasie bazowej <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="06742-103">A Windows Forms control inherits many properties form the base class <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="06742-104">Obejmują one takie właściwości, jak <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>i wielu innych.</span><span class="sxs-lookup"><span data-stu-id="06742-104">These include properties such as <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>, and many others.</span></span> <span data-ttu-id="06742-105">Aby uzyskać szczegółowe informacje na temat właściwości dziedziczonych, zobacz <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="06742-105">For details about inherited properties, see <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="06742-106">Dziedziczone właściwości można przesłonić w kontrolce, a także definiować nowe właściwości.</span><span class="sxs-lookup"><span data-stu-id="06742-106">You can override inherited properties in your control as well as define new properties.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="06742-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="06742-107">In This Section</span></span>  
 [<span data-ttu-id="06742-108">Definiowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="06742-108">Defining a Property</span></span>](defining-a-property-in-windows-forms-controls.md)  
 <span data-ttu-id="06742-109">Pokazuje, jak zaimplementować Właściwość niestandardowego formantu lub składnika oraz pokazuje, jak zintegrować właściwość w środowisku projektowym.</span><span class="sxs-lookup"><span data-stu-id="06742-109">Shows how to implement a property for a custom control or component and shows how to integrate the property into the design environment.</span></span>  
  
 [<span data-ttu-id="06742-110">Definiowanie wartości domyślnych za pomocą metod ShouldSerialize i Reset</span><span class="sxs-lookup"><span data-stu-id="06742-110">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 <span data-ttu-id="06742-111">Pokazuje, w jaki sposób definiować domyślne wartości właściwości dla niestandardowego formantu lub składnika.</span><span class="sxs-lookup"><span data-stu-id="06742-111">Shows how to define default property values for a custom control or component.</span></span>  
  
 [<span data-ttu-id="06742-112">Zdarzenia zmiany właściwości</span><span class="sxs-lookup"><span data-stu-id="06742-112">Property-Changed Events</span></span>](property-changed-events.md)  
 <span data-ttu-id="06742-113">Opisuje sposób włączania powiadomień o zmianach właściwości w przypadku zmiany wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="06742-113">Describes how to enable property-change notifications when a property value changes.</span></span>  
  
 [<span data-ttu-id="06742-114">Instrukcje: udostępnianie właściwości kontrolek składowych</span><span class="sxs-lookup"><span data-stu-id="06742-114">How to: Expose Properties of Constituent Controls</span></span>](how-to-expose-properties-of-constituent-controls.md)  
 <span data-ttu-id="06742-115">Pokazuje, jak uwidocznić właściwości formantów składników w niestandardowej kontrolce złożonej.</span><span class="sxs-lookup"><span data-stu-id="06742-115">Shows how to expose properties of constituent controls in a custom composite control.</span></span>  
  
 [<span data-ttu-id="06742-116">Implementacja metody w kontrolkach niestandardowych</span><span class="sxs-lookup"><span data-stu-id="06742-116">Method Implementation in Custom Controls</span></span>](method-implementation-in-custom-controls.md)  
 <span data-ttu-id="06742-117">Opisuje sposób implementowania metod w niestandardowych kontrolkach i składnikach.</span><span class="sxs-lookup"><span data-stu-id="06742-117">Describes how to implement methods in custom controls and components.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="06742-118">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="06742-118">Reference</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 <span data-ttu-id="06742-119">Dokumentuje klasę bazową do implementowania formantów złożonych.</span><span class="sxs-lookup"><span data-stu-id="06742-119">Documents the base class for implementing composite controls.</span></span>  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 <span data-ttu-id="06742-120">Dokumentuje atrybut, który określa <xref:System.ComponentModel.TypeConverter> do użycia dla niestandardowego typu właściwości.</span><span class="sxs-lookup"><span data-stu-id="06742-120">Documents the attribute that specifies the <xref:System.ComponentModel.TypeConverter> to use for a custom property type.</span></span>  
  
 <xref:System.ComponentModel.EditorAttribute>  
 <span data-ttu-id="06742-121">Dokumentuje atrybut, który określa <xref:System.Drawing.Design.UITypeEditor> do użycia dla właściwości niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="06742-121">Documents the attribute that specifies the <xref:System.Drawing.Design.UITypeEditor> to use for a custom property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="06742-122">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="06742-122">Related Sections</span></span>  
 [<span data-ttu-id="06742-123">Atrybuty w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="06742-123">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="06742-124">Opisuje atrybuty, które można zastosować do właściwości lub innych elementów niestandardowych formantów i składników.</span><span class="sxs-lookup"><span data-stu-id="06742-124">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 <span data-ttu-id="06742-125">[Atrybuty czasu projektowania dla składników](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="06742-125">[Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span></span>  
 <span data-ttu-id="06742-126">Wyświetla listę atrybutów metadanych, które mają zostać zastosowane do składników i formantów, aby były wyświetlane prawidłowo w czasie projektowania w projektantach wizualizacji.</span><span class="sxs-lookup"><span data-stu-id="06742-126">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 <span data-ttu-id="06742-127">[Rozszerzanie obsługi czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="06742-127">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>  
 <span data-ttu-id="06742-128">Opisuje sposób implementacji klas, takich jak redaktorzy i projektanci, które zapewniają obsługę czasu projektowania.</span><span class="sxs-lookup"><span data-stu-id="06742-128">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>
