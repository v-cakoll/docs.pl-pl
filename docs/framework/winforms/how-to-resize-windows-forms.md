---
title: 'Porady: zmienianie rozmiarów formularzy systemu Windows'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 22f1c829257f8cd23379de54063ae88802908fe0
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-resize-windows-forms"></a>Porady: zmienianie rozmiarów formularzy systemu Windows
Można określić rozmiar formularza systemu Windows na kilka sposobów. Można zmienić wysokość i szerokość formularza programowo, ustawiając nową wartość dla <xref:System.Windows.Forms.Form.Size%2A> właściwości, lub Dostosuj <xref:System.Windows.Forms.Control.Height%2A> lub <xref:System.Windows.Forms.Control.Width%2A> właściwości pojedynczo. Jeśli używasz programu Visual Studio, można zmienić rozmiar przy użyciu narzędzia Projektant formularzy systemu Windows. Zobacz też [porady: Zmienianie rozmiaru Windows Forms przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/37k2zkwx\(v=vs.110\)).  
  
### <a name="to-resize-a-form-programmatically"></a>Aby programowo zmienić rozmiar formularza  
  
-   Zdefiniuj rozmiar formularza w czasie wykonywania, ustawiając <xref:System.Windows.Forms.Form.Size%2A> właściwości formularza.  
  
     Poniższy przykład kodu pokazuje rozmiar formularza ustawiona na 100 x 100 pikseli.  
  
    ```vb  
    Form1.Size = New System.Drawing.Size(100, 100)  
    ```  
  
    ```csharp  
    Form1.Size = new System.Drawing.Size(100, 100);  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(100, 100);  
    ```  
  
### <a name="to-change-form-width-and-height-programmatically"></a>Aby zmienić programowo formularza szerokości i wysokości.  
  
-   Po <xref:System.Windows.Forms.Form.Size%2A> jest zdefiniowany, zmienić za pomocą formularza wysokość lub szerokość <xref:System.Windows.Forms.Control.Width%2A> lub <xref:System.Windows.Forms.Control.Height%2A> właściwości.  
  
     Poniższy przykład kodu pokazuje szerokość formularza ustawioną 300 pikseli od lewej krawędzi formularza, natomiast wysokość pozostaje stała.  
  
    ```vb  
    Form1.Width = 300  
    ```  
  
    ```csharp  
    Form1.Width = 300;  
    ```  
  
    ```cpp  
    Form1->Width = 300;  
    ```  
  
     —lub—  
  
     Zmień <xref:System.Drawing.Size.Width%2A> lub <xref:System.Drawing.Size.Height%2A> przez ustawienie <xref:System.Windows.Forms.Form.Size%2A> właściwości.  
  
     Jednakże, jak pokazano w poniższym przykładzie kodu, ta metoda jest bardziej skomplikowane niż ustawienie tylko <xref:System.Windows.Forms.Control.Width%2A> lub <xref:System.Windows.Forms.Control.Height%2A> właściwości.  
  
    ```vb  
    Form1.Size = New Size(300, Form1.Size.Height)  
    ```  
  
    ```csharp  
    Form1.Size = new Size(300, Form1.Size.Height);  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(300, Form1->Size.Height);  
    ```  
  
### <a name="to-change-form-size-by-increments-programmatically"></a>Aby zmienić rozmiar formularza krokami programowo  
  
-   Aby zwiększyć rozmiar formularza, ustaw <xref:System.Drawing.Size.Width%2A> i <xref:System.Drawing.Size.Height%2A> właściwości.  
  
     Poniższy przykład kodu pokazuje szerokość formularza ustawiona na większą niż bieżące ustawienie 200 pikseli.  
  
    ```vb  
    Form1.Width += 200  
    ```  
  
    ```csharp  
    Form1.Width += 200;  
    ```  
  
    ```cpp  
    Form1->Width += 200;  
    ```  
  
    > [!CAUTION]
    >  Zawsze używaj <xref:System.Drawing.Size.Height%2A> lub <xref:System.Drawing.Size.Width%2A> zmienić wymiaru formularza, chyba że ustawiasz szerokość i wysokość wymiarów w tym samym czasie, ustawiając dla właściwości <xref:System.Windows.Forms.Form.Size%2A> właściwości na nowy <xref:System.Drawing.Size> struktury. <xref:System.Windows.Forms.Form.Size%2A> Zwraca <xref:System.Drawing.Size> struktury, która jest typem wartości. Nie można przypisać nową wartość dla właściwości typu wartości. W związku z tym Poniższy przykładowy kod nie zostanie skompilowany.  
  
    ```vb  
    ' NOTE: CODE WILL NOT COMPILE  
    Dim f As New Form()  
    f.Size.Width += 100  
    ```  
  
    ```csharp  
    // NOTE: CODE WILL NOT COMPILE  
    Form f = new Form();  
    f.Size.Width += 100;  
    ```  
  
    ```cpp  
    // NOTE: CODE WILL NOT COMPILE  
    Form^ f = gcnew Form();  
    f->Size->X += 100;  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do formularzy Windows Forms](../../../docs/framework/winforms/getting-started-with-windows-forms.md)  
 [Rozszerzanie aplikacji Windows Forms](../../../docs/framework/winforms/advanced/index.md)
