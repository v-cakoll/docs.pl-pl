---
title: Podawanie informacji o ułatwieniach dostępu dotyczących formantów w formularzu systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, accessibility
- controls [Windows Forms], accessibility
- accessibility [Windows Forms], Windows Forms controls
ms.assetid: 887dee6f-5059-4d57-957d-7c6fcd4acb10
ms.openlocfilehash: 3067c90978e6ebd680d10c1c4f9db131f19c9e44
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614744"
---
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a><span data-ttu-id="e05f5-102">Podawanie informacji o ułatwieniach dostępu dotyczących formantów w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e05f5-102">Providing Accessibility Information for Controls on a Windows Form</span></span>
<span data-ttu-id="e05f5-103">Narzędzi ułatwień dostępu są programy specjalistyczne i urządzenia, które pomagają osobom niepełnosprawnym bardziej efektywne wykorzystanie komputerów.</span><span class="sxs-lookup"><span data-stu-id="e05f5-103">Accessibility aids are specialized programs and devices that help people with disabilities use computers more effectively.</span></span> <span data-ttu-id="e05f5-104">Przykłady obejmują czytniki zawartości ekranu dla osób, które są blind i głosu narzędzia danych wejściowych dla osób, które udostępniają ustnej polecenia zamiast przy użyciu myszy lub klawiatury.</span><span class="sxs-lookup"><span data-stu-id="e05f5-104">Examples include screen readers for people who are blind and voice input utilities for people who provide verbal commands instead of using the mouse or keyboard.</span></span> <span data-ttu-id="e05f5-105">Tych narzędzi ułatwień dostępu w interakcje z właściwości ułatwień dostępu, udostępnianych przez kontrolek formularzy Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e05f5-105">These accessibility aids interact with the accessibility properties exposed by Windows Forms controls.</span></span> <span data-ttu-id="e05f5-106">Te właściwości są:</span><span class="sxs-lookup"><span data-stu-id="e05f5-106">These properties are:</span></span>  
  
- <span data-ttu-id="e05f5-107">**AccessibilityObject**</span><span class="sxs-lookup"><span data-stu-id="e05f5-107">**AccessibilityObject**</span></span>  
  
- <span data-ttu-id="e05f5-108">**AccessibleDefaultActionDescription**</span><span class="sxs-lookup"><span data-stu-id="e05f5-108">**AccessibleDefaultActionDescription**</span></span>  
  
- <span data-ttu-id="e05f5-109">**AccessibleDescription**</span><span class="sxs-lookup"><span data-stu-id="e05f5-109">**AccessibleDescription**</span></span>  
  
- <span data-ttu-id="e05f5-110">**AccessibleName**</span><span class="sxs-lookup"><span data-stu-id="e05f5-110">**AccessibleName**</span></span>  
  
- <span data-ttu-id="e05f5-111">**AccessibleRole**</span><span class="sxs-lookup"><span data-stu-id="e05f5-111">**AccessibleRole**</span></span>  
  
## <a name="accessibilityobject-property"></a><span data-ttu-id="e05f5-112">Właściwość AccessibilityObject</span><span class="sxs-lookup"><span data-stu-id="e05f5-112">AccessibilityObject Property</span></span>  
 <span data-ttu-id="e05f5-113">Ta właściwość tylko do odczytu zawiera <xref:System.Windows.Forms.AccessibleObject> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e05f5-113">This read-only property contains an <xref:System.Windows.Forms.AccessibleObject> instance.</span></span> <span data-ttu-id="e05f5-114">**Element AccessibleObject** implementuje <xref:Accessibility.IAccessible> interfejs, który zawiera informacje dotyczące opis kontrolki, położenie na ekranie, możliwości nawigacji i wartości.</span><span class="sxs-lookup"><span data-stu-id="e05f5-114">The **AccessibleObject** implements the <xref:Accessibility.IAccessible> interface, which provides information about the control's description, screen location, navigational abilities, and value.</span></span> <span data-ttu-id="e05f5-115">Projektant ustawia tę wartość, gdy formant został dodany do formularza.</span><span class="sxs-lookup"><span data-stu-id="e05f5-115">The designer sets this value when the control is added to the form.</span></span>  
  
## <a name="accessibledefaultactiondescription-property"></a><span data-ttu-id="e05f5-116">AccessibleDefaultActionDescription Property</span><span class="sxs-lookup"><span data-stu-id="e05f5-116">AccessibleDefaultActionDescription Property</span></span>  
 <span data-ttu-id="e05f5-117">Ten ciąg w tym artykule opisano działanie sterowania.</span><span class="sxs-lookup"><span data-stu-id="e05f5-117">This string describes the action of the control.</span></span> <span data-ttu-id="e05f5-118">Go nie jest wyświetlana w oknie dialogowym właściwości i może być ustawiony tylko w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e05f5-118">It does not appear in the Properties window and may only be set in code.</span></span> <span data-ttu-id="e05f5-119">W poniższym przykładzie ustawiono tej właściwości dla kontrolki przycisku:</span><span class="sxs-lookup"><span data-stu-id="e05f5-119">The following example sets this property for a button control:</span></span>  
  
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
  
## <a name="accessibledescription-property"></a><span data-ttu-id="e05f5-120">Właściwość AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="e05f5-120">AccessibleDescription Property</span></span>  
 <span data-ttu-id="e05f5-121">Ten ciąg opisuje kontrolki.</span><span class="sxs-lookup"><span data-stu-id="e05f5-121">This string describes the control.</span></span> <span data-ttu-id="e05f5-122">Może zostać ustawiony w oknie dialogowym właściwości lub w kodzie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e05f5-122">It may be set in the Properties window, or in code as follows:</span></span>  
  
```  
' Visual Basic  
Button1.AccessibleDescription = "A button with text 'Exit'."  
  
// C#  
Button1.AccessibleDescription = "A button with text 'Exit'";  
  
// C++  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a><span data-ttu-id="e05f5-123">Właściwość AccessibleName</span><span class="sxs-lookup"><span data-stu-id="e05f5-123">AccessibleName Property</span></span>  
 <span data-ttu-id="e05f5-124">Jest to nazwa kontrolki zgłoszonych narzędzi ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="e05f5-124">This is the name of a control reported to accessibility aids.</span></span> <span data-ttu-id="e05f5-125">Może zostać ustawiony w oknie dialogowym właściwości lub w kodzie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e05f5-125">It may be set in the Properties window, or in code as follows:</span></span>  
  
```  
' Visual Basic  
Button1.AccessibleName = "Order"  
  
// C#  
Button1.AccessibleName = "Order";  
  
// C++  
button1->AccessibleName = "Order";  
```  
  
## <a name="accessiblerole-property"></a><span data-ttu-id="e05f5-126">Właściwość AccessibleRole</span><span class="sxs-lookup"><span data-stu-id="e05f5-126">AccessibleRole Property</span></span>  
 <span data-ttu-id="e05f5-127">Tę właściwość, która zawiera <xref:System.Windows.Forms.AccessibleRole> wyliczenia, w tym artykule opisano rolę interfejsu użytkownika formantu.</span><span class="sxs-lookup"><span data-stu-id="e05f5-127">This property, which contains an <xref:System.Windows.Forms.AccessibleRole> enumeration, describes the user interface role of the control.</span></span> <span data-ttu-id="e05f5-128">Nowy formant jest ustawione na wartość `Default`.</span><span class="sxs-lookup"><span data-stu-id="e05f5-128">A new control has the value set to `Default`.</span></span> <span data-ttu-id="e05f5-129">To oznacza, że domyślnie **przycisk** kontroli działa jako **przycisk**.</span><span class="sxs-lookup"><span data-stu-id="e05f5-129">This would mean that by default, a **Button** control acts as a **Button**.</span></span> <span data-ttu-id="e05f5-130">Możesz zresetować tę właściwość, jeśli kontrolka ma inną rolą.</span><span class="sxs-lookup"><span data-stu-id="e05f5-130">You may want to reset this property if a control has another role.</span></span> <span data-ttu-id="e05f5-131">Na przykład używasz **PictureBox** powinna być kontrolka **wykresu**, i może być narzędzi ułatwień dostępu, aby zgłosić rolę **wykresu**, nie jako **PictureBox** .</span><span class="sxs-lookup"><span data-stu-id="e05f5-131">For example, you may be using a **PictureBox** control as a **Chart**, and you may want accessibility aids to report the role as a **Chart**, not as a **PictureBox**.</span></span> <span data-ttu-id="e05f5-132">Można również określić tę właściwość w przypadku kontrolek niestandardowych, które zostały opracowane.</span><span class="sxs-lookup"><span data-stu-id="e05f5-132">You may also want to specify this property for custom controls you have developed.</span></span> <span data-ttu-id="e05f5-133">Ta właściwość może ustawiać w oknie dialogowym właściwości lub w kodzie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e05f5-133">This property may be set in the Properties window, or in code as follows:</span></span>  
  
```  
' Visual Basic  
PictureBox1.AccessibleRole = AccessibleRole.Chart  
  
// C#  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
  
// C++  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## <a name="see-also"></a><span data-ttu-id="e05f5-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e05f5-134">See also</span></span>

- <xref:System.Windows.Forms.AccessibleObject>
- <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.AccessibleRole>
