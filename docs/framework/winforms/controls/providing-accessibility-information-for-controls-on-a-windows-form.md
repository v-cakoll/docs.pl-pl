---
title: "Podawanie informacji o ułatwieniach dostępu dotyczących formantów w formularzu systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, accessibility
- controls [Windows Forms], accessibility
- accessibility [Windows Forms], Windows Forms controls
ms.assetid: 887dee6f-5059-4d57-957d-7c6fcd4acb10
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d7afc8cc67dc3a428e4995230345938075fbcc0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a><span data-ttu-id="0687d-102">Podawanie informacji o ułatwieniach dostępu dotyczących formantów w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0687d-102">Providing Accessibility Information for Controls on a Windows Form</span></span>
<span data-ttu-id="0687d-103">Narzędzi ułatwień dostępu są programy specjalistyczne i urządzenia, które pomagają osób niepełnosprawnych komputerów wydajniej wykorzystywać.</span><span class="sxs-lookup"><span data-stu-id="0687d-103">Accessibility aids are specialized programs and devices that help people with disabilities use computers more effectively.</span></span> <span data-ttu-id="0687d-104">Przykładami czytników ekranu dla osób blind i głos wejściowych narzędzi dla osób, które udostępniają ustne polecenia zamiast za pomocą klawiatury lub myszy.</span><span class="sxs-lookup"><span data-stu-id="0687d-104">Examples include screen readers for people who are blind and voice input utilities for people who provide verbal commands instead of using the mouse or keyboard.</span></span> <span data-ttu-id="0687d-105">Tych narzędzi ułatwień dostępu w interakcje z właściwości dostępu udostępnianych przez formanty formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="0687d-105">These accessibility aids interact with the accessibility properties exposed by Windows Forms controls.</span></span> <span data-ttu-id="0687d-106">Te właściwości są:</span><span class="sxs-lookup"><span data-stu-id="0687d-106">These properties are:</span></span>  
  
-   <span data-ttu-id="0687d-107">**AccessibilityObject**</span><span class="sxs-lookup"><span data-stu-id="0687d-107">**AccessibilityObject**</span></span>  
  
-   <span data-ttu-id="0687d-108">**AccessibleDefaultActionDescription**</span><span class="sxs-lookup"><span data-stu-id="0687d-108">**AccessibleDefaultActionDescription**</span></span>  
  
-   <span data-ttu-id="0687d-109">**AccessibleDescription**</span><span class="sxs-lookup"><span data-stu-id="0687d-109">**AccessibleDescription**</span></span>  
  
-   <span data-ttu-id="0687d-110">**AccessibleName**</span><span class="sxs-lookup"><span data-stu-id="0687d-110">**AccessibleName**</span></span>  
  
-   <span data-ttu-id="0687d-111">**AccessibleRole**</span><span class="sxs-lookup"><span data-stu-id="0687d-111">**AccessibleRole**</span></span>  
  
## <a name="accessibilityobject-property"></a><span data-ttu-id="0687d-112">Właściwość AccessibilityObject</span><span class="sxs-lookup"><span data-stu-id="0687d-112">AccessibilityObject Property</span></span>  
 <span data-ttu-id="0687d-113">Ta właściwość tylko do odczytu zawiera <xref:System.Windows.Forms.AccessibleObject> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="0687d-113">This read-only property contains an <xref:System.Windows.Forms.AccessibleObject> instance.</span></span> <span data-ttu-id="0687d-114">**Element AccessibleObject** implementuje <xref:Accessibility.IAccessible> interfejsu, która dostarcza informacji na temat formantu opisu, lokalizacji ekranu możliwości nawigacji i wartość.</span><span class="sxs-lookup"><span data-stu-id="0687d-114">The **AccessibleObject** implements the <xref:Accessibility.IAccessible> interface, which provides information about the control's description, screen location, navigational abilities, and value.</span></span> <span data-ttu-id="0687d-115">Projektant konfiguruje tę wartość, gdy formant został dodany do formularza.</span><span class="sxs-lookup"><span data-stu-id="0687d-115">The designer sets this value when the control is added to the form.</span></span>  
  
## <a name="accessibledefaultactiondescription-property"></a><span data-ttu-id="0687d-116">Właściwość AccessibleDefaultActionDescription</span><span class="sxs-lookup"><span data-stu-id="0687d-116">AccessibleDefaultActionDescription Property</span></span>  
 <span data-ttu-id="0687d-117">Ten ciąg zawiera opis akcji formantu.</span><span class="sxs-lookup"><span data-stu-id="0687d-117">This string describes the action of the control.</span></span> <span data-ttu-id="0687d-118">Nie są wyświetlane w oknie właściwości, a można ustawić tylko w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0687d-118">It does not appear in the Properties window and may only be set in code.</span></span> <span data-ttu-id="0687d-119">Poniższy przykład ustawia tę właściwość formantu przycisku:</span><span class="sxs-lookup"><span data-stu-id="0687d-119">The following example sets this property for a button control:</span></span>  
  
```  
' Visual Basic  
Button1.AccessibleDefaultActionDescription = _  
   "Closes the application."  
  
// C#  
Button1.AccessibleDefaultActionDescription =   
   "Closes the application.";  
  
// C++  
button1->AccessibleDefaultActionDescription =  
   "Closes the application.";  
```  
  
## <a name="accessibledescription-property"></a><span data-ttu-id="0687d-120">Właściwość AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="0687d-120">AccessibleDescription Property</span></span>  
 <span data-ttu-id="0687d-121">Ten ciąg opisuje formantu.</span><span class="sxs-lookup"><span data-stu-id="0687d-121">This string describes the control.</span></span> <span data-ttu-id="0687d-122">Może zostać ustawiony w oknie właściwości lub w kodzie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0687d-122">It may be set in the Properties window, or in code as follows:</span></span>  
  
```  
' Visual Basic  
Button1.AccessibleDescription = "A button with text 'Exit'."  
  
// C#  
Button1.AccessibleDescription = "A button with text 'Exit'";  
  
// C++  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a><span data-ttu-id="0687d-123">Właściwość AccessibleName</span><span class="sxs-lookup"><span data-stu-id="0687d-123">AccessibleName Property</span></span>  
 <span data-ttu-id="0687d-124">Jest to nazwa formantu zgłaszane do narzędzi ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="0687d-124">This is the name of a control reported to accessibility aids.</span></span> <span data-ttu-id="0687d-125">Może zostać ustawiony w oknie właściwości lub w kodzie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0687d-125">It may be set in the Properties window, or in code as follows:</span></span>  
  
```  
' Visual Basic  
Button1.AccessibleName = "Order"  
  
// C#  
Button1.AccessibleName = "Order";  
  
// C++  
button1->AccessibleName = "Order";  
```  
  
## <a name="accessiblerole-property"></a><span data-ttu-id="0687d-126">Właściwość AccessibleRole</span><span class="sxs-lookup"><span data-stu-id="0687d-126">AccessibleRole Property</span></span>  
 <span data-ttu-id="0687d-127">Ta właściwość zawiera <xref:System.Windows.Forms.AccessibleRole> wyliczenia, zawiera opis roli użytkownika interfejsu formantu.</span><span class="sxs-lookup"><span data-stu-id="0687d-127">This property, which contains an <xref:System.Windows.Forms.AccessibleRole> enumeration, describes the user interface role of the control.</span></span> <span data-ttu-id="0687d-128">Nowy formant jest ustawione na wartość `Default`.</span><span class="sxs-lookup"><span data-stu-id="0687d-128">A new control has the value set to `Default`.</span></span> <span data-ttu-id="0687d-129">To spowoduje oznaczają, że domyślnie **przycisk** formant zachowuje się jak **przycisk**.</span><span class="sxs-lookup"><span data-stu-id="0687d-129">This would mean that by default, a **Button** control acts as a **Button**.</span></span> <span data-ttu-id="0687d-130">Możesz zresetować tę właściwość, jeśli formant ma inną rolą.</span><span class="sxs-lookup"><span data-stu-id="0687d-130">You may want to reset this property if a control has another role.</span></span> <span data-ttu-id="0687d-131">Na przykład używasz **PictureBox** kontrolować jako **wykresu**, i narzędzi ułatwień dostępu, aby zgłosić roli może być **wykresu**, nie jako **PictureBox** .</span><span class="sxs-lookup"><span data-stu-id="0687d-131">For example, you may be using a **PictureBox** control as a **Chart**, and you may want accessibility aids to report the role as a **Chart**, not as a **PictureBox**.</span></span> <span data-ttu-id="0687d-132">Można również określić tę właściwość w przypadku kontrolek niestandardowych, które zostały opracowane.</span><span class="sxs-lookup"><span data-stu-id="0687d-132">You may also want to specify this property for custom controls you have developed.</span></span> <span data-ttu-id="0687d-133">Tej właściwości można ustawić w oknie właściwości lub w kodzie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0687d-133">This property may be set in the Properties window, or in code as follows:</span></span>  
  
```  
' Visual Basic  
PictureBox1.AccessibleRole = AccessibleRole.Chart  
  
// C#  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
  
// C++  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## <a name="see-also"></a><span data-ttu-id="0687d-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0687d-134">See Also</span></span>  
 <xref:System.Windows.Forms.AccessibleObject>  
 <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.AccessibleRole>
