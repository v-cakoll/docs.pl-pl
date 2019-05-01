---
title: Podawanie informacji o ułatwieniach dostępu dotyczących formantów w formularzu systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, accessibility
- controls [Windows Forms], accessibility
- accessibility [Windows Forms], Windows Forms controls
ms.assetid: 887dee6f-5059-4d57-957d-7c6fcd4acb10
ms.openlocfilehash: 0f589f37d79c9ec8d55153aac4c846726a379055
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948023"
---
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a>Podawanie informacji o ułatwieniach dostępu dotyczących formantów w formularzu systemu Windows
Narzędzi ułatwień dostępu są programy specjalistyczne i urządzenia, które pomagają osobom niepełnosprawnym bardziej efektywne wykorzystanie komputerów. Przykłady obejmują czytniki zawartości ekranu dla osób, które są blind i głosu narzędzia danych wejściowych dla osób, które udostępniają ustnej polecenia zamiast przy użyciu myszy lub klawiatury. Tych narzędzi ułatwień dostępu w interakcje z właściwości ułatwień dostępu, udostępnianych przez kontrolek formularzy Windows Forms. Te właściwości są:  
  
- **AccessibilityObject**  
  
- **AccessibleDefaultActionDescription**  
  
- **AccessibleDescription**  
  
- **AccessibleName**  
  
- **AccessibleRole**  
  
## <a name="accessibilityobject-property"></a>Właściwość AccessibilityObject  
 Ta właściwość tylko do odczytu zawiera <xref:System.Windows.Forms.AccessibleObject> wystąpienia. **Element AccessibleObject** implementuje <xref:Accessibility.IAccessible> interfejs, który zawiera informacje dotyczące opis kontrolki, położenie na ekranie, możliwości nawigacji i wartości. Projektant ustawia tę wartość, gdy formant został dodany do formularza.  
  
## <a name="accessibledefaultactiondescription-property"></a>AccessibleDefaultActionDescription Property  
 Ten ciąg w tym artykule opisano działanie sterowania. Go nie jest wyświetlana w oknie dialogowym właściwości i może być ustawiony tylko w kodzie. W poniższym przykładzie ustawiono tej właściwości dla kontrolki przycisku:  
  
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
 Ten ciąg opisuje kontrolki. Może zostać ustawiony w oknie dialogowym właściwości lub w kodzie w następujący sposób:  
  
```  
' Visual Basic  
Button1.AccessibleDescription = "A button with text 'Exit'."  
  
// C#  
Button1.AccessibleDescription = "A button with text 'Exit'";  
  
// C++  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a>Właściwość AccessibleName  
 Jest to nazwa kontrolki zgłoszonych narzędzi ułatwień dostępu. Może zostać ustawiony w oknie dialogowym właściwości lub w kodzie w następujący sposób:  
  
```  
' Visual Basic  
Button1.AccessibleName = "Order"  
  
// C#  
Button1.AccessibleName = "Order";  
  
// C++  
button1->AccessibleName = "Order";  
```  
  
## <a name="accessiblerole-property"></a>Właściwość AccessibleRole  
 Tę właściwość, która zawiera <xref:System.Windows.Forms.AccessibleRole> wyliczenia, w tym artykule opisano rolę interfejsu użytkownika formantu. Nowy formant jest ustawione na wartość `Default`. To oznacza, że domyślnie **przycisk** kontroli działa jako **przycisk**. Możesz zresetować tę właściwość, jeśli kontrolka ma inną rolą. Na przykład używasz **PictureBox** powinna być kontrolka **wykresu**, i może być narzędzi ułatwień dostępu, aby zgłosić rolę **wykresu**, nie jako **PictureBox** . Można również określić tę właściwość w przypadku kontrolek niestandardowych, które zostały opracowane. Ta właściwość może ustawiać w oknie dialogowym właściwości lub w kodzie w następujący sposób:  
  
```  
' Visual Basic  
PictureBox1.AccessibleRole = AccessibleRole.Chart  
  
// C#  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
  
// C++  
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
