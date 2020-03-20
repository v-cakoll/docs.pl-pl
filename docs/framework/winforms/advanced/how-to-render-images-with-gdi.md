---
title: 'Porady: renderowanie obrazów za pomocą GDI+'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], creating
- GDI+, rendering existing images
ms.assetid: c128b79a-3e31-47d8-9e66-3470f570a056
ms.openlocfilehash: fffe1f1052d7323d234985b7e752866f2e89657d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182502"
---
# <a name="how-to-render-images-with-gdi"></a>Porady: renderowanie obrazów za pomocą GDI+
Za pomocą GDI+ można renderować obrazy, które istnieją jako pliki w aplikacjach. Można to zrobić, tworząc nowy <xref:System.Drawing.Image> obiekt klasy <xref:System.Drawing.Bitmap>(na przykład <xref:System.Drawing.Graphics> ), tworząc obiekt, który odwołuje się do <xref:System.Drawing.Graphics.DrawImage%2A> powierzchni rysunku, której chcesz użyć, i wywołując metodę <xref:System.Drawing.Graphics> obiektu. Obraz zostanie pomalowany na powierzchni rysunku reprezentowanej przez klasę grafiki. Za pomocą Edytora obrazów można tworzyć i edytować pliki obrazów w czasie projektowania oraz renderować je za pomocą interfejsu GDI+ w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Edytor obrazów ikon](/cpp/windows/image-editor-for-icons).  
  
### <a name="to-render-an-image-with-gdi"></a>Aby renderować obraz za pomocą GDI+  
  
1. Utwórz obiekt reprezentujący obraz, który ma być wyświetlany. Ten obiekt musi być członkiem klasy, <xref:System.Drawing.Image>która <xref:System.Drawing.Bitmap> dziedziczy po , takich jak lub <xref:System.Drawing.Imaging.Metafile>. Pokazany jest przykład:  
  
    ```vb  
    ' Uses the System.Environment.GetFolderPath to get the path to the
    ' current user's MyPictures folder.  
    Dim myBitmap as New Bitmap _  
       (System.Environment.GetFolderPath _  
          (System.Environment.SpecialFolder.MyPictures))  
    ```  
  
    ```csharp  
    // Uses the System.Environment.GetFolderPath to get the path to the
    // current user's MyPictures folder.  
    Bitmap myBitmap = new Bitmap  
       (System.Environment.GetFolderPath  
          (System.Environment.SpecialFolder.MyPictures));  
    ```  
  
    ```cpp  
    // Uses the System.Environment.GetFolderPath to get the path to the
    // current user's MyPictures folder.  
    Bitmap^ myBitmap = gcnew Bitmap  
       (System::Environment::GetFolderPath  
          (System::Environment::SpecialFolder::MyPictures));  
    ```  
  
2. Utwórz <xref:System.Drawing.Graphics> obiekt reprezentujący powierzchnię rysunku, której chcesz użyć. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie obiektów graficznych do rysowania](how-to-create-graphics-objects-for-drawing.md).  
  
    ```vb  
    ' Creates a Graphics object that represents the drawing surface of
    ' Button1.  
    Dim g as Graphics = Button1.CreateGraphics  
    ```  
  
    ```csharp  
    // Creates a Graphics object that represents the drawing surface of
    // Button1.  
    Graphics g = Button1.CreateGraphics();  
    ```  
  
    ```cpp  
    // Creates a Graphics object that represents the drawing surface of
    // Button1.  
    Graphics^ g = button1->CreateGraphics();  
    ```  
  
3. Wywołanie <xref:System.Drawing.Graphics.DrawImage%2A> obiektu graficznego, aby renderować obraz. Należy określić zarówno obraz, który ma zostać narysowany, jak i współrzędne, w których ma zostać narysowany.  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do programowania grafiki](getting-started-with-graphics-programming.md)
- [Instrukcje: tworzenie obiektów graficznych do rysowania](how-to-create-graphics-objects-for-drawing.md)
- [Pióra, linie i prostokąty w GDI+](pens-lines-and-rectangles-in-gdi.md)
- [Porady: rysowanie tekstu w formularzu systemu Windows](how-to-draw-text-on-a-windows-form.md)
- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Linie rysunku lub liczby zamknięte](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)
- [Edytor obrazów dla ikon](/cpp/windows/image-editor-for-icons)
