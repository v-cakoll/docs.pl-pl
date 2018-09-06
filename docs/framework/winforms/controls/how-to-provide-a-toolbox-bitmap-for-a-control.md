---
title: 'Porady: dostarczanie mapy bitowej przybornika dla formantu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
ms.openlocfilehash: aa32850b9bcd1a15a93bd6c80b2278278d12c417
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43746548"
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a>Porady: dostarczanie mapy bitowej przybornika dla formantu
Jeśli chcesz mieć specjalną ikonę kontrolki są wyświetlane w **przybornika**, należy określić określonego obrazu, za pomocą <xref:System.Drawing.ToolboxBitmapAttribute>. Ta klasa jest *atrybutu*, specjalny rodzaj klasy, można dołączyć do innych klas. Aby uzyskać więcej informacji na temat atrybutów, zobacz [atrybuty Przegląd (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) dla języka Visual Basic lub [atrybuty (C#)](../../../csharp/programming-guide/concepts/attributes/index.md) dla języka C#.  
  
 Za pomocą <xref:System.Drawing.ToolboxBitmapAttribute>, można określić ciąg, który określa ścieżkę i nazwę pliku mapy bitowej 16 na 16 pikseli. Ta mapa bitowa pojawi się obok kontrolki podczas dodawania do **przybornika**. Można również określić <xref:System.Type>, w którym to przypadku mapy bitowej skojarzony z danym typem jest ładowany. Jeśli określisz zarówno <xref:System.Type> i ciąg, formant wyszukuje zasób obrazu o nazwie określonej przez parametr ciągu w zestawie z typem określonym przez <xref:System.Type> parametru.  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a>Aby określić mapy bitowej przybornika dla kontrolki  
  
1.  Dodaj <xref:System.Drawing.ToolboxBitmapAttribute> do deklaracji klasy kontrolki przed `Class` — słowo kluczowe w języku visual Basic oraz nad deklaracją klasy dla języka Visual C#.  
  
    ```vb  
    ' Specifies the bitmap associated with the Button type.  
    <ToolboxBitmap(GetType(Button))> Class MyControl1  
    ' Specifies a bitmap file.  
    End Class  
    <ToolboxBitmap("C:\Documents and Settings\Joe\MyPics\myImage.bmp")> _  
       Class MyControl2  
    End Class  
    ' Specifies a type that indicates the assembly to search, and the name   
    ' of an image resource to look for.  
    <ToolboxBitmap(GetType(MyControl), "MyControlBitmap")> Class MyControl  
    End Class  
    ```  
  
    ```csharp  
    // Specifies the bitmap associated with the Button type.  
    [ToolboxBitmap(typeof(Button))]  
    class MyControl1 : UserControl  
    {  
    }  
    // Specifies a bitmap file.  
    [ToolboxBitmap(@"C:\Documents and Settings\Joe\MyPics\myImage.bmp")]  
    class MyControl2 : UserControl  
    {  
    }  
    // Specifies a type that indicates the assembly to search, and the name   
    // of an image resource to look for.  
    [ToolboxBitmap(typeof(MyControl), "MyControlBitmap")]  
    class MyControl : UserControl  
    {  
    }  
    ```  
  
2.  Skompiluj ponownie projekt.  
  
    > [!NOTE]
    >  Nie ma mapy bitowej przybornika dla kontrolki wygenerowany automatycznie i składników. Aby wyświetlić mapę bitową, należy ponownie załadować formantu za pomocą **wybierz elementy przybornika** okno dialogowe. Aby uzyskać więcej informacji, zobacz [wskazówki: automatyczne zapełnianie przybornika składnikami niestandardowe](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [Przewodnik: automatyczne zapełnianie Przybornika składnikami niestandardowymi](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania](developing-windows-forms-controls-at-design-time.md)
- [Omówienie atrybuty (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Atrybuty (C#)](../../../csharp/programming-guide/concepts/attributes/index.md)
