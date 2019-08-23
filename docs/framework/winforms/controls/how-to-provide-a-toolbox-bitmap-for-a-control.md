---
title: 'Instrukcje: dostarczanie mapy bitowej przybornika dla kontrolki'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
ms.openlocfilehash: 428af7e4396fde8ac29046d73adda95dbe2182f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910469"
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a>Instrukcje: dostarczanie mapy bitowej przybornika dla kontrolki
Jeśli chcesz mieć specjalną ikonę kontrolki w przyborniku, możesz określićkonkretny obraz przy użyciu <xref:System.Drawing.ToolboxBitmapAttribute>. Ta klasa jest *atrybutem*, specjalnym rodzajem klasy, którą można dołączyć do innych klas. Aby uzyskać więcej informacji na temat atrybutów, zobacz [Omówienie atrybutów (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) dla Visual Basic lub [atrybutówC#()](../../../csharp/programming-guide/concepts/attributes/index.md) dla. C#  
  
 Przy użyciu <xref:System.Drawing.ToolboxBitmapAttribute>, można określić ciąg, który wskazuje ścieżkę i nazwę pliku dla mapy bitowej 16 x 16 pikseli. Ta mapa bitowa pojawia się obok formantu po dodaniu do **przybornika**. Można również określić <xref:System.Type>, w którym przypadku zostanie załadowana Mapa bitowa skojarzona z tym typem. Jeśli określono zarówno <xref:System.Type> ciąg a, jak i, formant wyszukuje zasób obrazu o nazwie określonej przez parametr ciągu w zestawie zawierający typ określony <xref:System.Type> przez parametr.  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a>Aby określić mapę bitową przybornika dla kontrolki  
  
1. Dodaj do deklaracji klasy kontrolki `Class` przed słowem kluczowym dla języka Visual Basic i powyżej deklaracji klasy dla wizualizacji C# <xref:System.Drawing.ToolboxBitmapAttribute>  
  
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
  
2. Ponownie skompiluj projekt.  
  
    > [!NOTE]
    > Mapa bitowa nie jest wyświetlana w przyborniku dla automatycznie generowanych kontrolek i składników. Aby wyświetlić mapę bitową, Załaduj ponownie formant przy użyciu okna dialogowego **Wybierz elementy przybornika** . Aby uzyskać więcej informacji, [zobacz Przewodnik: Automatyczne wypełnianie przybornika składnikami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)niestandardowymi.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [Przewodnik: Automatyczne zapełnianie przybornika składnikami niestandardowymi](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania](developing-windows-forms-controls-at-design-time.md)
- [Omówienie atrybutów (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Atrybuty (C#)](../../../csharp/programming-guide/concepts/attributes/index.md)
