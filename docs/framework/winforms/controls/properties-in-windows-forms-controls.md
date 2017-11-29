---
title: "Właściwości formantów formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d5de09635fb92b46a2c0f89427ad03449de6bd53
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="properties-in-windows-forms-controls"></a><span data-ttu-id="287d5-102">Właściwości formantów formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="287d5-102">Properties in Windows Forms Controls</span></span>
<span data-ttu-id="287d5-103">Formant formularzy systemu Windows dziedziczy wiele formularza właściwości klasy podstawowej <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="287d5-103">A Windows Forms control inherits many properties form the base class <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="287d5-104">Te właściwości obejmują takie jak <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>i wiele innych.</span><span class="sxs-lookup"><span data-stu-id="287d5-104">These include properties such as <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>, and many others.</span></span> <span data-ttu-id="287d5-105">Aby uzyskać szczegółowe informacje o właściwości dziedziczone, zobacz <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="287d5-105">For details about inherited properties, see <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="287d5-106">Można zastąpić właściwości dziedziczone formantu oraz jak definiowania nowych właściwości.</span><span class="sxs-lookup"><span data-stu-id="287d5-106">You can override inherited properties in your control as well as define new properties.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="287d5-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="287d5-107">In This Section</span></span>  
 [<span data-ttu-id="287d5-108">Definiowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="287d5-108">Defining a Property</span></span>](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 <span data-ttu-id="287d5-109">Pokazuje, jak implementować właściwość dla kontrolek niestandardowych lub składnik oraz sposób integracji właściwość w środowisku projektowania.</span><span class="sxs-lookup"><span data-stu-id="287d5-109">Shows how to implement a property for a custom control or component and shows how to integrate the property into the design environment.</span></span>  
  
 [<span data-ttu-id="287d5-110">Definiowanie wartości domyślnych z metod ShouldSerialize i Reset</span><span class="sxs-lookup"><span data-stu-id="287d5-110">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 <span data-ttu-id="287d5-111">Pokazuje, jak można definiować wartości właściwości domyślnej dla składnika lub kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="287d5-111">Shows how to define default property values for a custom control or component.</span></span>  
  
 [<span data-ttu-id="287d5-112">Zdarzenia zmiany właściwości</span><span class="sxs-lookup"><span data-stu-id="287d5-112">Property-Changed Events</span></span>](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 <span data-ttu-id="287d5-113">Opisuje sposób włączenia powiadomień zmiany właściwości, gdy wartość właściwości zostanie zmieniona.</span><span class="sxs-lookup"><span data-stu-id="287d5-113">Describes how to enable property-change notifications when a property value changes.</span></span>  
  
 [<span data-ttu-id="287d5-114">Porady: udostępnianie właściwości formantów składowych</span><span class="sxs-lookup"><span data-stu-id="287d5-114">How to: Expose Properties of Constituent Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md)  
 <span data-ttu-id="287d5-115">Pokazuje, jak do udostępnienia właściwości formantów składowych w złożonych kontrolek niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="287d5-115">Shows how to expose properties of constituent controls in a custom composite control.</span></span>  
  
 [<span data-ttu-id="287d5-116">Implementacja metody w formantach niestandardowych</span><span class="sxs-lookup"><span data-stu-id="287d5-116">Method Implementation in Custom Controls</span></span>](../../../../docs/framework/winforms/controls/method-implementation-in-custom-controls.md)  
 <span data-ttu-id="287d5-117">Zawiera opis sposobu implementacji metod w niestandardowych kontrolek i składników.</span><span class="sxs-lookup"><span data-stu-id="287d5-117">Describes how to implement methods in custom controls and components.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="287d5-118">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="287d5-118">Reference</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 <span data-ttu-id="287d5-119">Dokumenty klasę podstawową dla implementacji formanty złożone.</span><span class="sxs-lookup"><span data-stu-id="287d5-119">Documents the base class for implementing composite controls.</span></span>  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 <span data-ttu-id="287d5-120">Dokumenty atrybut, który określa <xref:System.ComponentModel.TypeConverter> do użycia w przypadku typu właściwości niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="287d5-120">Documents the attribute that specifies the <xref:System.ComponentModel.TypeConverter> to use for a custom property type.</span></span>  
  
 <xref:System.ComponentModel.EditorAttribute>  
 <span data-ttu-id="287d5-121">Dokumenty atrybut, który określa <xref:System.Drawing.Design.UITypeEditor> dla właściwości niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="287d5-121">Documents the attribute that specifies the <xref:System.Drawing.Design.UITypeEditor> to use for a custom property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="287d5-122">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="287d5-122">Related Sections</span></span>  
 [<span data-ttu-id="287d5-123">Atrybuty w formantach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="287d5-123">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="287d5-124">Zawiera opis atrybutów, które można zastosować do właściwości lub innych elementach członkowskich niestandardowe formanty i składniki.</span><span class="sxs-lookup"><span data-stu-id="287d5-124">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="287d5-125">Atrybuty czasu projektowania dla składników</span><span class="sxs-lookup"><span data-stu-id="287d5-125">Design-Time Attributes for Components</span></span>](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)  
 <span data-ttu-id="287d5-126">Wyświetla listę atrybutów metadanych do zastosowania do składników i formantów, dzięki czemu są wyświetlane poprawnie w czasie projektowania w wizualnych projektantów.</span><span class="sxs-lookup"><span data-stu-id="287d5-126">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 [<span data-ttu-id="287d5-127">Rozszerzenie obsługi w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="287d5-127">Extending Design-Time Support</span></span>](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 <span data-ttu-id="287d5-128">Zawiera opis sposobu implementacji klasy, takie jak edytory i projektantów, które zapewniają obsługę w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="287d5-128">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>
