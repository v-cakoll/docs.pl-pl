---
title: Podawanie informacji o ułatwieniach dostępu dotyczących formantów w formularzu systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, accessibility
- controls [Windows Forms], accessibility
- accessibility [Windows Forms], Windows Forms controls
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 887dee6f-5059-4d57-957d-7c6fcd4acb10
ms.openlocfilehash: 672104db94826cfbe113a7ae0ea29546b0c3b9da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182002"
---
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a><span data-ttu-id="89a58-102">Podawanie informacji o ułatwieniach dostępu dotyczących formantów w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="89a58-102">Providing Accessibility Information for Controls on a Windows Form</span></span>
<span data-ttu-id="89a58-103">Pomoce ułatwień dostępu to specjalistyczne programy i urządzenia, które pomagają osobom niepełnosprawnym efektywniej korzystać z komputerów.</span><span class="sxs-lookup"><span data-stu-id="89a58-103">Accessibility aids are specialized programs and devices that help people with disabilities use computers more effectively.</span></span> <span data-ttu-id="89a58-104">Przykłady obejmują czytniki ekranu dla osób niewidomych i narzędzia wprowadzania głosu dla osób, które dostarczają polecenia słowne zamiast myszy lub klawiatury.</span><span class="sxs-lookup"><span data-stu-id="89a58-104">Examples include screen readers for people who are blind and voice input utilities for people who provide verbal commands instead of using the mouse or keyboard.</span></span> <span data-ttu-id="89a58-105">Te pomoce ułatwień dostępu współdziałają z właściwościami ułatwień dostępu udostępniane przez formanty formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="89a58-105">These accessibility aids interact with the accessibility properties exposed by Windows Forms controls.</span></span> <span data-ttu-id="89a58-106">Te właściwości są następujące:</span><span class="sxs-lookup"><span data-stu-id="89a58-106">These properties are:</span></span>  
  
- <span data-ttu-id="89a58-107">**Accessibilityobject**</span><span class="sxs-lookup"><span data-stu-id="89a58-107">**AccessibilityObject**</span></span>  
  
- <span data-ttu-id="89a58-108">**Accessibledefaultactiondescription**</span><span class="sxs-lookup"><span data-stu-id="89a58-108">**AccessibleDefaultActionDescription**</span></span>  
  
- <span data-ttu-id="89a58-109">**Accessibledescription**</span><span class="sxs-lookup"><span data-stu-id="89a58-109">**AccessibleDescription**</span></span>  
  
- <span data-ttu-id="89a58-110">**Accessiblename**</span><span class="sxs-lookup"><span data-stu-id="89a58-110">**AccessibleName**</span></span>  
  
- <span data-ttu-id="89a58-111">**Accessiblerole**</span><span class="sxs-lookup"><span data-stu-id="89a58-111">**AccessibleRole**</span></span>  
  
## <a name="accessibilityobject-property"></a><span data-ttu-id="89a58-112">Właściwość AccessibilityObject</span><span class="sxs-lookup"><span data-stu-id="89a58-112">AccessibilityObject Property</span></span>  
 <span data-ttu-id="89a58-113">Ta właściwość tylko <xref:System.Windows.Forms.AccessibleObject> do odczytu zawiera wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="89a58-113">This read-only property contains an <xref:System.Windows.Forms.AccessibleObject> instance.</span></span> <span data-ttu-id="89a58-114">**AccessibleObject** implementuje <xref:Accessibility.IAccessible> interfejs, który zawiera informacje o opisie formantu, lokalizacji ekranu, zdolności nawigacyjnych i wartości.</span><span class="sxs-lookup"><span data-stu-id="89a58-114">The **AccessibleObject** implements the <xref:Accessibility.IAccessible> interface, which provides information about the control's description, screen location, navigational abilities, and value.</span></span> <span data-ttu-id="89a58-115">Projektant ustawia tę wartość po dodaniu formantu do formularza.</span><span class="sxs-lookup"><span data-stu-id="89a58-115">The designer sets this value when the control is added to the form.</span></span>  
  
## <a name="accessibledefaultactiondescription-property"></a><span data-ttu-id="89a58-116">Właściwość AccessibleDefaultActionDescription</span><span class="sxs-lookup"><span data-stu-id="89a58-116">AccessibleDefaultActionDescription Property</span></span>  
 <span data-ttu-id="89a58-117">Ten ciąg opisuje akcję formantu.</span><span class="sxs-lookup"><span data-stu-id="89a58-117">This string describes the action of the control.</span></span> <span data-ttu-id="89a58-118">Nie pojawia się w oknie Właściwości i może być ustawiony tylko w kodzie.</span><span class="sxs-lookup"><span data-stu-id="89a58-118">It does not appear in the Properties window and may only be set in code.</span></span> <span data-ttu-id="89a58-119">W poniższym przykładzie ustawia się ta właściwość dla formantu przycisku:</span><span class="sxs-lookup"><span data-stu-id="89a58-119">The following example sets this property for a button control:</span></span>  
  
```vb  
Button1.AccessibleDefaultActionDescription = _  
   "Closes the application."  
```

```csharp  
Button1.AccessibleDefaultActionDescription =
   "Closes the application.";  
```

```cpp  
button1->AccessibleDefaultActionDescription =  
   "Closes the application.";  
```  
  
## <a name="accessibledescription-property"></a><span data-ttu-id="89a58-120">Właściwość AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="89a58-120">AccessibleDescription Property</span></span>  
 <span data-ttu-id="89a58-121">Ten ciąg opisuje formant.</span><span class="sxs-lookup"><span data-stu-id="89a58-121">This string describes the control.</span></span> <span data-ttu-id="89a58-122">Może być ustawiona w oknie Właściwości lub w kodzie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="89a58-122">It may be set in the Properties window, or in code as follows:</span></span>  
  
```vb  
Button1.AccessibleDescription = "A button with text 'Exit'."  
```

```csharp  
Button1.AccessibleDescription = "A button with text 'Exit'";  
```

```cpp  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a><span data-ttu-id="89a58-123">Właściwość AccessibleName</span><span class="sxs-lookup"><span data-stu-id="89a58-123">AccessibleName Property</span></span>  
 <span data-ttu-id="89a58-124">Jest to nazwa formantu zgłaszane do pomocy ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="89a58-124">This is the name of a control reported to accessibility aids.</span></span> <span data-ttu-id="89a58-125">Może być ustawiona w oknie Właściwości lub w kodzie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="89a58-125">It may be set in the Properties window, or in code as follows:</span></span>  
  
```vb  
Button1.AccessibleName = "Order"  
```

```csharp  
Button1.AccessibleName = "Order";  
```

```cpp  
button1->AccessibleName = "Order";  
```  
  
## <a name="accessiblerole-property"></a><span data-ttu-id="89a58-126">Właściwość AccessibleRole</span><span class="sxs-lookup"><span data-stu-id="89a58-126">AccessibleRole Property</span></span>  
 <span data-ttu-id="89a58-127">Ta właściwość, <xref:System.Windows.Forms.AccessibleRole> która zawiera wyliczenie, opisuje rolę interfejsu użytkownika formantu.</span><span class="sxs-lookup"><span data-stu-id="89a58-127">This property, which contains an <xref:System.Windows.Forms.AccessibleRole> enumeration, describes the user interface role of the control.</span></span> <span data-ttu-id="89a58-128">Nowy formant ma ustawioną wartość `Default`.</span><span class="sxs-lookup"><span data-stu-id="89a58-128">A new control has the value set to `Default`.</span></span> <span data-ttu-id="89a58-129">Oznaczałoby to, że domyślnie **button** kontroli działa jako **Przycisk**.</span><span class="sxs-lookup"><span data-stu-id="89a58-129">This would mean that by default, a **Button** control acts as a **Button**.</span></span> <span data-ttu-id="89a58-130">Można zresetować tę właściwość, jeśli formant ma inną rolę.</span><span class="sxs-lookup"><span data-stu-id="89a58-130">You may want to reset this property if a control has another role.</span></span> <span data-ttu-id="89a58-131">Na przykład może być używany **picturebox** kontrolki jako **wykresu**i może chcesz pomocy ułatwień dostępu do zgłaszania roli jako **wykres,** a nie jako **PictureBox**.</span><span class="sxs-lookup"><span data-stu-id="89a58-131">For example, you may be using a **PictureBox** control as a **Chart**, and you may want accessibility aids to report the role as a **Chart**, not as a **PictureBox**.</span></span> <span data-ttu-id="89a58-132">Można również określić tę właściwość dla formantów niestandardowych, które zostały opracowane.</span><span class="sxs-lookup"><span data-stu-id="89a58-132">You may also want to specify this property for custom controls you have developed.</span></span> <span data-ttu-id="89a58-133">Ta właściwość może być ustawiona w oknie Właściwości lub w kodzie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="89a58-133">This property may be set in the Properties window, or in code as follows:</span></span>  
  
```vb
PictureBox1.AccessibleRole = AccessibleRole.Chart  
```

```csharp  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
```

```cpp  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## <a name="see-also"></a><span data-ttu-id="89a58-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89a58-134">See also</span></span>

- <xref:System.Windows.Forms.AccessibleObject>
- <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.AccessibleRole>
