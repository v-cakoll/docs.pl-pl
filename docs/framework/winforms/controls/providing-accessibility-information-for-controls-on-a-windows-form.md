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
ms.workload: dotnet
ms.openlocfilehash: 9b7c0d570dbb6389ef22dba635bbbc2885c5f3a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a>Podawanie informacji o ułatwieniach dostępu dotyczących formantów w formularzu systemu Windows
Narzędzi ułatwień dostępu są programy specjalistyczne i urządzenia, które pomagają osób niepełnosprawnych komputerów wydajniej wykorzystywać. Przykładami czytników ekranu dla osób blind i głos wejściowych narzędzi dla osób, które udostępniają ustne polecenia zamiast za pomocą klawiatury lub myszy. Tych narzędzi ułatwień dostępu w interakcje z właściwości dostępu udostępnianych przez formanty formularzy systemu Windows. Te właściwości są:  
  
-   **AccessibilityObject**  
  
-   **AccessibleDefaultActionDescription**  
  
-   **AccessibleDescription**  
  
-   **AccessibleName**  
  
-   **AccessibleRole**  
  
## <a name="accessibilityobject-property"></a>Właściwość AccessibilityObject  
 Ta właściwość tylko do odczytu zawiera <xref:System.Windows.Forms.AccessibleObject> wystąpienia. **Element AccessibleObject** implementuje <xref:Accessibility.IAccessible> interfejsu, która dostarcza informacji na temat formantu opisu, lokalizacji ekranu możliwości nawigacji i wartość. Projektant konfiguruje tę wartość, gdy formant został dodany do formularza.  
  
## <a name="accessibledefaultactiondescription-property"></a>Właściwość AccessibleDefaultActionDescription  
 Ten ciąg zawiera opis akcji formantu. Nie są wyświetlane w oknie właściwości, a można ustawić tylko w kodzie. Poniższy przykład ustawia tę właściwość formantu przycisku:  
  
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
  
## <a name="accessibledescription-property"></a>Właściwość AccessibleDescription  
 Ten ciąg opisuje formantu. Może zostać ustawiony w oknie właściwości lub w kodzie w następujący sposób:  
  
```  
' Visual Basic  
Button1.AccessibleDescription = "A button with text 'Exit'."  
  
// C#  
Button1.AccessibleDescription = "A button with text 'Exit'";  
  
// C++  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a>Właściwość AccessibleName  
 Jest to nazwa formantu zgłaszane do narzędzi ułatwień dostępu. Może zostać ustawiony w oknie właściwości lub w kodzie w następujący sposób:  
  
```  
' Visual Basic  
Button1.AccessibleName = "Order"  
  
// C#  
Button1.AccessibleName = "Order";  
  
// C++  
button1->AccessibleName = "Order";  
```  
  
## <a name="accessiblerole-property"></a>Właściwość AccessibleRole  
 Ta właściwość zawiera <xref:System.Windows.Forms.AccessibleRole> wyliczenia, zawiera opis roli użytkownika interfejsu formantu. Nowy formant jest ustawione na wartość `Default`. To spowoduje oznaczają, że domyślnie **przycisk** formant zachowuje się jak **przycisk**. Możesz zresetować tę właściwość, jeśli formant ma inną rolą. Na przykład używasz **PictureBox** kontrolować jako **wykresu**, i narzędzi ułatwień dostępu, aby zgłosić roli może być **wykresu**, nie jako **PictureBox** . Można również określić tę właściwość w przypadku kontrolek niestandardowych, które zostały opracowane. Tej właściwości można ustawić w oknie właściwości lub w kodzie w następujący sposób:  
  
```  
' Visual Basic  
PictureBox1.AccessibleRole = AccessibleRole.Chart  
  
// C#  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
  
// C++  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.AccessibleObject>  
 <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.AccessibleRole>
