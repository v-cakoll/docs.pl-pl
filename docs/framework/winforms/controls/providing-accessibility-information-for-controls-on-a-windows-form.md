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
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a>Podawanie informacji o ułatwieniach dostępu dotyczących formantów w formularzu systemu Windows
Ułatwienia dostępu są wyspecjalizowanymi programami i urządzeniami, które ułatwiają osobom niepełnosprawnym korzystanie z komputerów. Przykłady obejmują czytniki zawartości ekranu dla osób, które są narzędziami do wprowadzania ustnego i głosowego dla osób, które udostępniają werbalne polecenia zamiast korzystać z myszy lub klawiatury. Te ułatwienia dostępu współdziałają z właściwościami dostępności dostępnymi w kontrolkach Windows Forms. Te właściwości są następujące:  
  
- **Ułatwienia dostępu**  
  
- **AccessibleDefaultActionDescription**  
  
- **AccessibleDescription**  
  
- **AccessibleName**  
  
- **AccessibleRole**  
  
## <a name="accessibilityobject-property"></a>AccessibilityObject — Właściwość  
 Ta właściwość tylko do odczytu zawiera <xref:System.Windows.Forms.AccessibleObject> wystąpienie. Element **AccessibleObject** implementuje <xref:Accessibility.IAccessible> interfejs, który zawiera informacje o opisie kontrolki, lokalizacji ekranu, możliwościach nawigacyjnych i wartości. Projektant ustawia tę wartość, gdy kontrolka jest dodawana do formularza.  
  
## <a name="accessibledefaultactiondescription-property"></a>AccessibleDefaultActionDescription Property  
 Ten ciąg opisuje akcję formantu. Nie jest on wyświetlany w okno Właściwości i może być ustawiony tylko w kodzie. Poniższy przykład ustawia tę właściwość dla kontrolki Button:  
  
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
 Ten ciąg opisuje formant. Można ją ustawić w okno Właściwości lub w kodzie w następujący sposób:  
  
```vb  
Button1.AccessibleDescription = "A button with text 'Exit'."  
```

```csharp  
Button1.AccessibleDescription = "A button with text 'Exit'";  
```

```cpp  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a>Właściwość accessibleName  
 Jest to nazwa kontrolki raportowanej do pomocy ułatwień dostępu. Można ją ustawić w okno Właściwości lub w kodzie w następujący sposób:  
  
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
 Ta właściwość, która zawiera <xref:System.Windows.Forms.AccessibleRole> Wyliczenie, opisuje rolę interfejsu użytkownika formantu. Nowa kontrolka ma ustawioną `Default`wartość. Oznacza to, że domyślnie formant **Button** działa jako **przycisk**. Możesz chcieć zresetować tę właściwość, Jeśli kontrolka ma inną rolę. Na przykład można użyć formantu **PictureBox** jako **wykresu**i można chcieć, aby pomoc ułatwień dostępu mogła zgłosić rolę jako **Wykres**, a nie jako element **PictureBox**. Możesz również określić tę właściwość dla utworzonych formantów niestandardowych. Tę właściwość można ustawić w okno Właściwości lub w kodzie w następujący sposób:  
  
```vb 
PictureBox1.AccessibleRole = AccessibleRole.Chart  
```

```csharp  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
```

```cpp  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.AccessibleObject>
- <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.AccessibleRole>
