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
ms.openlocfilehash: 791944bd9e8f5520a571e6fb415d69022aa0bead
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991712"
---
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a><span data-ttu-id="22eba-102">Podawanie informacji o ułatwieniach dostępu dotyczących formantów w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="22eba-102">Providing Accessibility Information for Controls on a Windows Form</span></span>
<span data-ttu-id="22eba-103">Ułatwienia dostępu są wyspecjalizowanymi programami i urządzeniami, które ułatwiają osobom niepełnosprawnym korzystanie z komputerów.</span><span class="sxs-lookup"><span data-stu-id="22eba-103">Accessibility aids are specialized programs and devices that help people with disabilities use computers more effectively.</span></span> <span data-ttu-id="22eba-104">Przykłady obejmują czytniki zawartości ekranu dla osób, które są narzędziami do wprowadzania ustnego i głosowego dla osób, które udostępniają werbalne polecenia zamiast korzystać z myszy lub klawiatury.</span><span class="sxs-lookup"><span data-stu-id="22eba-104">Examples include screen readers for people who are blind and voice input utilities for people who provide verbal commands instead of using the mouse or keyboard.</span></span> <span data-ttu-id="22eba-105">Te ułatwienia dostępu współdziałają z właściwościami dostępności dostępnymi w kontrolkach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="22eba-105">These accessibility aids interact with the accessibility properties exposed by Windows Forms controls.</span></span> <span data-ttu-id="22eba-106">Te właściwości są następujące:</span><span class="sxs-lookup"><span data-stu-id="22eba-106">These properties are:</span></span>  
  
- <span data-ttu-id="22eba-107">**Ułatwienia dostępu**</span><span class="sxs-lookup"><span data-stu-id="22eba-107">**AccessibilityObject**</span></span>  
  
- <span data-ttu-id="22eba-108">**AccessibleDefaultActionDescription**</span><span class="sxs-lookup"><span data-stu-id="22eba-108">**AccessibleDefaultActionDescription**</span></span>  
  
- <span data-ttu-id="22eba-109">**AccessibleDescription**</span><span class="sxs-lookup"><span data-stu-id="22eba-109">**AccessibleDescription**</span></span>  
  
- <span data-ttu-id="22eba-110">**AccessibleName**</span><span class="sxs-lookup"><span data-stu-id="22eba-110">**AccessibleName**</span></span>  
  
- <span data-ttu-id="22eba-111">**AccessibleRole**</span><span class="sxs-lookup"><span data-stu-id="22eba-111">**AccessibleRole**</span></span>  
  
## <a name="accessibilityobject-property"></a><span data-ttu-id="22eba-112">AccessibilityObject — Właściwość</span><span class="sxs-lookup"><span data-stu-id="22eba-112">AccessibilityObject Property</span></span>  
 <span data-ttu-id="22eba-113">Ta właściwość tylko do odczytu zawiera <xref:System.Windows.Forms.AccessibleObject> wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="22eba-113">This read-only property contains an <xref:System.Windows.Forms.AccessibleObject> instance.</span></span> <span data-ttu-id="22eba-114">Element **AccessibleObject** implementuje <xref:Accessibility.IAccessible> interfejs, który zawiera informacje o opisie kontrolki, lokalizacji ekranu, możliwościach nawigacyjnych i wartości.</span><span class="sxs-lookup"><span data-stu-id="22eba-114">The **AccessibleObject** implements the <xref:Accessibility.IAccessible> interface, which provides information about the control's description, screen location, navigational abilities, and value.</span></span> <span data-ttu-id="22eba-115">Projektant ustawia tę wartość, gdy kontrolka jest dodawana do formularza.</span><span class="sxs-lookup"><span data-stu-id="22eba-115">The designer sets this value when the control is added to the form.</span></span>  
  
## <a name="accessibledefaultactiondescription-property"></a><span data-ttu-id="22eba-116">AccessibleDefaultActionDescription Property</span><span class="sxs-lookup"><span data-stu-id="22eba-116">AccessibleDefaultActionDescription Property</span></span>  
 <span data-ttu-id="22eba-117">Ten ciąg opisuje akcję formantu.</span><span class="sxs-lookup"><span data-stu-id="22eba-117">This string describes the action of the control.</span></span> <span data-ttu-id="22eba-118">Nie jest on wyświetlany w okno Właściwości i może być ustawiony tylko w kodzie.</span><span class="sxs-lookup"><span data-stu-id="22eba-118">It does not appear in the Properties window and may only be set in code.</span></span> <span data-ttu-id="22eba-119">Poniższy przykład ustawia tę właściwość dla kontrolki Button:</span><span class="sxs-lookup"><span data-stu-id="22eba-119">The following example sets this property for a button control:</span></span>  
  
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
  
## <a name="accessibledescription-property"></a><span data-ttu-id="22eba-120">Właściwość AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="22eba-120">AccessibleDescription Property</span></span>  
 <span data-ttu-id="22eba-121">Ten ciąg opisuje formant.</span><span class="sxs-lookup"><span data-stu-id="22eba-121">This string describes the control.</span></span> <span data-ttu-id="22eba-122">Można ją ustawić w okno Właściwości lub w kodzie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="22eba-122">It may be set in the Properties window, or in code as follows:</span></span>  
  
```vb  
Button1.AccessibleDescription = "A button with text 'Exit'."  
```

```csharp  
Button1.AccessibleDescription = "A button with text 'Exit'";  
```

```cpp  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a><span data-ttu-id="22eba-123">Właściwość accessibleName</span><span class="sxs-lookup"><span data-stu-id="22eba-123">AccessibleName Property</span></span>  
 <span data-ttu-id="22eba-124">Jest to nazwa kontrolki raportowanej do pomocy ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="22eba-124">This is the name of a control reported to accessibility aids.</span></span> <span data-ttu-id="22eba-125">Można ją ustawić w okno Właściwości lub w kodzie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="22eba-125">It may be set in the Properties window, or in code as follows:</span></span>  
  
```vb  
Button1.AccessibleName = "Order"  
```

```csharp  
Button1.AccessibleName = "Order";  
```

```cpp  
button1->AccessibleName = "Order";  
```  
  
## <a name="accessiblerole-property"></a><span data-ttu-id="22eba-126">Właściwość AccessibleRole</span><span class="sxs-lookup"><span data-stu-id="22eba-126">AccessibleRole Property</span></span>  
 <span data-ttu-id="22eba-127">Ta właściwość, która zawiera <xref:System.Windows.Forms.AccessibleRole> Wyliczenie, opisuje rolę interfejsu użytkownika formantu.</span><span class="sxs-lookup"><span data-stu-id="22eba-127">This property, which contains an <xref:System.Windows.Forms.AccessibleRole> enumeration, describes the user interface role of the control.</span></span> <span data-ttu-id="22eba-128">Nowa kontrolka ma ustawioną `Default`wartość.</span><span class="sxs-lookup"><span data-stu-id="22eba-128">A new control has the value set to `Default`.</span></span> <span data-ttu-id="22eba-129">Oznacza to, że domyślnie formant **Button** działa jako **przycisk**.</span><span class="sxs-lookup"><span data-stu-id="22eba-129">This would mean that by default, a **Button** control acts as a **Button**.</span></span> <span data-ttu-id="22eba-130">Możesz chcieć zresetować tę właściwość, Jeśli kontrolka ma inną rolę.</span><span class="sxs-lookup"><span data-stu-id="22eba-130">You may want to reset this property if a control has another role.</span></span> <span data-ttu-id="22eba-131">Na przykład można użyć formantu **PictureBox** jako **wykresu**i można chcieć, aby pomoc ułatwień dostępu mogła zgłosić rolę jako **Wykres**, a nie jako element **PictureBox**.</span><span class="sxs-lookup"><span data-stu-id="22eba-131">For example, you may be using a **PictureBox** control as a **Chart**, and you may want accessibility aids to report the role as a **Chart**, not as a **PictureBox**.</span></span> <span data-ttu-id="22eba-132">Możesz również określić tę właściwość dla utworzonych formantów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="22eba-132">You may also want to specify this property for custom controls you have developed.</span></span> <span data-ttu-id="22eba-133">Tę właściwość można ustawić w okno Właściwości lub w kodzie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="22eba-133">This property may be set in the Properties window, or in code as follows:</span></span>  
  
```vb 
PictureBox1.AccessibleRole = AccessibleRole.Chart  
```

```csharp  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
```

```cpp  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## <a name="see-also"></a><span data-ttu-id="22eba-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22eba-134">See also</span></span>

- <xref:System.Windows.Forms.AccessibleObject>
- <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.AccessibleRole>
