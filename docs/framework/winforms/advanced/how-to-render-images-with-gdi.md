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
ms.openlocfilehash: 6f5b139c6831a065c85e9d9889c259c859a649cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524609"
---
# <a name="how-to-render-images-with-gdi"></a>Porady: renderowanie obrazów za pomocą GDI+
Można użyć [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] renderowanie obrazów, które istnieje jako pliki w aplikacji. Można to zrobić, tworząc nowy obiekt <xref:System.Drawing.Image> klasy (takich jak <xref:System.Drawing.Bitmap>), tworzenie <xref:System.Drawing.Graphics> obiekt, który odwołuje się do powierzchni rysowania, którego chcesz użyć i wywoływania <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> obiektu. Obraz będą rysowane na powierzchni rysowania reprezentowany przez klasę grafiki. Użyj edytora obrazów do tworzenia i edytowania plików obrazów w czasie projektowania i renderowania je za pomocą [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [edytor obrazów dla ikon](/cpp/windows/image-editor-for-icons).  
  
### <a name="to-render-an-image-with-gdi"></a>Aby renderować obraz z GDI +  
  
1.  Utwórz obiekt reprezentujący obraz, który chcesz wyświetlić. Ten obiekt musi być elementem członkowskim klasy, która dziedziczy po <xref:System.Drawing.Image>, takich jak <xref:System.Drawing.Bitmap> lub <xref:System.Drawing.Imaging.Metafile>. Przykład przedstawiono:  
  
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
  
2.  Utwórz <xref:System.Drawing.Graphics> obiekt, który reprezentuje powierzchni rysowania, którego chcesz użyć. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie obiektów graficznych do rysowania](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).  
  
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
  
3.  Wywołanie <xref:System.Drawing.Graphics.DrawImage%2A> grafiki obiektu do renderowania obrazu. Należy określić obraz, który ma być rysowany i współrzędne, w którym ma być rysowany.  
  
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
 [Wprowadzenie do programowania grafiki](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [Instrukcje: tworzenie obiektów graficznych do rysowania](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Pióra, linie i prostokąty w GDI+](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)  
 [Instrukcje: rysowanie tekstu w formularzu systemu Windows](../../../../docs/framework/winforms/advanced/how-to-draw-text-on-a-windows-form.md)  
 [Grafika i rysowanie w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Linie rysunku lub zamkniętych figur](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)  
 [Edytor obrazów dla ikon](/cpp/windows/image-editor-for-icons)
