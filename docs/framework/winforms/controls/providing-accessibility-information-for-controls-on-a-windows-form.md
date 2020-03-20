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
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a>Podawanie informacji o ułatwieniach dostępu dotyczących formantów w formularzu systemu Windows
Pomoce ułatwień dostępu to specjalistyczne programy i urządzenia, które pomagają osobom niepełnosprawnym efektywniej korzystać z komputerów. Przykłady obejmują czytniki ekranu dla osób niewidomych i narzędzia wprowadzania głosu dla osób, które dostarczają polecenia słowne zamiast myszy lub klawiatury. Te pomoce ułatwień dostępu współdziałają z właściwościami ułatwień dostępu udostępniane przez formanty formularzy systemu Windows. Te właściwości są następujące:  
  
- **Accessibilityobject**  
  
- **Accessibledefaultactiondescription**  
  
- **Accessibledescription**  
  
- **Accessiblename**  
  
- **Accessiblerole**  
  
## <a name="accessibilityobject-property"></a>Właściwość AccessibilityObject  
 Ta właściwość tylko <xref:System.Windows.Forms.AccessibleObject> do odczytu zawiera wystąpienie. **AccessibleObject** implementuje <xref:Accessibility.IAccessible> interfejs, który zawiera informacje o opisie formantu, lokalizacji ekranu, zdolności nawigacyjnych i wartości. Projektant ustawia tę wartość po dodaniu formantu do formularza.  
  
## <a name="accessibledefaultactiondescription-property"></a>Właściwość AccessibleDefaultActionDescription  
 Ten ciąg opisuje akcję formantu. Nie pojawia się w oknie Właściwości i może być ustawiony tylko w kodzie. W poniższym przykładzie ustawia się ta właściwość dla formantu przycisku:  
  
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
  
## <a name="accessibledescription-property"></a>Właściwość AccessibleDescription  
 Ten ciąg opisuje formant. Może być ustawiona w oknie Właściwości lub w kodzie w następujący sposób:  
  
```vb  
Button1.AccessibleDescription = "A button with text 'Exit'."  
```

```csharp  
Button1.AccessibleDescription = "A button with text 'Exit'";  
```

```cpp  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a>Właściwość AccessibleName  
 Jest to nazwa formantu zgłaszane do pomocy ułatwień dostępu. Może być ustawiona w oknie Właściwości lub w kodzie w następujący sposób:  
  
```vb  
Button1.AccessibleName = "Order"  
```

```csharp  
Button1.AccessibleName = "Order";  
```

```cpp  
button1->AccessibleName = "Order";  
```  
  
## <a name="accessiblerole-property"></a>Właściwość AccessibleRole  
 Ta właściwość, <xref:System.Windows.Forms.AccessibleRole> która zawiera wyliczenie, opisuje rolę interfejsu użytkownika formantu. Nowy formant ma ustawioną wartość `Default`. Oznaczałoby to, że domyślnie **button** kontroli działa jako **Przycisk**. Można zresetować tę właściwość, jeśli formant ma inną rolę. Na przykład może być używany **picturebox** kontrolki jako **wykresu**i może chcesz pomocy ułatwień dostępu do zgłaszania roli jako **wykres,** a nie jako **PictureBox**. Można również określić tę właściwość dla formantów niestandardowych, które zostały opracowane. Ta właściwość może być ustawiona w oknie Właściwości lub w kodzie w następujący sposób:  
  
```vb
PictureBox1.AccessibleRole = AccessibleRole.Chart  
```

```csharp  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
```

```cpp  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.AccessibleObject>
- <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.AccessibleRole>
