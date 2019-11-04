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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 61f60aaeab904dff80408a1dc46c2882fb5e22b9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458313"
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a>Porady: dostarczanie mapy bitowej przybornika dla formantu

Jeśli chcesz mieć specjalną ikonę kontrolki w **przyborniku** programu Visual Studio, możesz określić konkretny obraz przy użyciu <xref:System.Drawing.ToolboxBitmapAttribute>. Ta klasa jest *atrybutem*, specjalnym rodzajem klasy, którą można dołączyć do innych klas. Aby uzyskać więcej informacji na temat atrybutów, zobacz [Omówienie atrybutów (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) dla Visual Basic lub [atrybutówC#()](../../../csharp/programming-guide/concepts/attributes/index.md) dla. C#

Za pomocą <xref:System.Drawing.ToolboxBitmapAttribute>można określić ciąg, który wskazuje ścieżkę i nazwę pliku dla mapy bitowej 16 x 16 pikseli. Ta mapa bitowa pojawia się obok formantu po dodaniu do **przybornika**. Możesz również określić <xref:System.Type>, w którym ma zostać załadowana Mapa bitowa skojarzona z tym typem. Jeśli określisz zarówno <xref:System.Type>, jak i ciąg, formant wyszukuje zasób obrazu o nazwie określonej przez parametr ciągu w zestawie zawierający typ określony przez parametr <xref:System.Type>.

## <a name="to-specify-a-toolbox-bitmap-for-your-control"></a>Aby określić mapę bitową przybornika dla kontrolki

1. Dodaj <xref:System.Drawing.ToolboxBitmapAttribute> do deklaracji klasy kontrolki przed słowem kluczowym `Class` dla języka Visual Basic i powyżej deklaracji klasy dla wizualizacji C#.

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
    > Mapa bitowa nie jest wyświetlana w przyborniku dla automatycznie generowanych kontrolek i składników. Aby wyświetlić mapę bitową, Załaduj ponownie formant przy użyciu okna dialogowego **Wybierz elementy przybornika** . Aby uzyskać więcej informacji, zobacz [Przewodnik: automatyczne zapełnianie przybornika składnikami niestandardowymi](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [Przewodnik: automatyczne zapełnianie Przybornika składnikami niestandardowymi](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania](developing-windows-forms-controls-at-design-time.md)
- [Omówienie atrybutów (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Atrybuty (C#)](../../../csharp/programming-guide/concepts/attributes/index.md)
