---
title: 'Instrukcje: ustawienie formatu dla kontrolki NumericUpDown formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
ms.openlocfilehash: 6db7a1b2aeb7282c3ac827cb8319706ed348fc22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949160"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a>Instrukcje: ustawienie formatu dla kontrolki NumericUpDown formularzy systemu Windows
Można skonfigurować sposób wyświetlania wartości w kontrolce Windows Forms <xref:System.Windows.Forms.NumericUpDown> . Właściwość <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> określa, ile liczb pojawia się po przecinku dziesiętnym; wartość domyślna to 0. Właściwość <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> określa, czy separator zostanie wstawiony między każdą trzema cyframi dziesiętnymi; wartość domyślna `false`to. Kontrolka może wyświetlać wartości w formacie szesnastkowym, a nie dziesiętnym <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> , jeśli właściwość jest `true`ustawiona na; wartość `false`domyślna to.  
  
### <a name="to-format-the-numeric-value"></a>Aby sformatować wartość liczbową  
  
- Wyświetl wartość dziesiętną <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> , ustawiając właściwość na liczbę całkowitą i <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> ustawiając właściwość na `true` lub `false`.  
  
    ```vb  
    NumericUpDown1.DecimalPlaces = 2  
    NumericUpDown1.ThousandsSeparator = True  
    ```  
  
    ```csharp  
    numericUpDown1.DecimalPlaces = 2;  
    numericUpDown1.ThousandsSeparator = true;  
    ```  
  
    ```cpp  
    numericUpDown1->DecimalPlaces = 2;  
    numericUpDown1->ThousandsSeparator = true;  
    ```  
  
     —lub—  
  
- Wyświetl wartość szesnastkową, ustawiając <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> właściwość na. `true`  
  
    ```vb  
    NumericUpDown1.Hexadecimal = True  
    ```  
  
    ```csharp  
    numericUpDown1.Hexadecimal = true;  
    ```  
  
    ```cpp  
    numericUpDown1->Hexadecimal = true;  
    ```  
  
    > [!NOTE]
    > Nawet jeśli wartość jest wyświetlana w postaci szesnastkowej, wszystkie testy wykonywane na <xref:System.Windows.Forms.NumericUpDown.Value%2A> właściwości będą testowanie wartości dziesiętnej.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.NumericUpDown>
- [NumericUpDown, kontrolka](numericupdown-control-windows-forms.md)
- [NumericUpDown, kontrolka — omówienie](numericupdown-control-overview-windows-forms.md)
