---
title: 'Instrukcje: Renderowanie obrazów za pomocą GDI +'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], creating
- GDI+, rendering existing images
ms.assetid: c128b79a-3e31-47d8-9e66-3470f570a056
ms.openlocfilehash: d2c626f46862e5fdc7c51b509a6419a3d67c4102
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702831"
---
# <a name="how-to-render-images-with-gdi"></a>Instrukcje: Renderowanie obrazów za pomocą GDI +
Możesz użyć [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] renderowanie obrazów, które istnieją w postaci plików w aplikacjach. Można to zrobić, tworząc nowy obiekt <xref:System.Drawing.Image> klasy (takie jak <xref:System.Drawing.Bitmap>), tworzenie <xref:System.Drawing.Graphics> obiekt, który odwołuje się do powierzchni rysowania, którego chcesz użyć, a podczas wywoływania <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> obiektu. Obraz będą rysowane na powierzchnię rysunku, reprezentowane przez klasę grafiki. Można użyć edytora obrazów, aby tworzyć i edytować pliki obrazów w czasie projektowania i renderowania je za pomocą [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [edytor obrazów dla ikon](/cpp/windows/image-editor-for-icons).  
  
### <a name="to-render-an-image-with-gdi"></a>Aby renderować obraz za pomocą GDI +  
  
1.  Utwórz obiekt reprezentujący obraz, który chcesz wyświetlić. Ten obiekt musi należeć do klasy, która dziedziczy po elemencie <xref:System.Drawing.Image>, takich jak <xref:System.Drawing.Bitmap> lub <xref:System.Drawing.Imaging.Metafile>. Przykład przedstawiono:  
  
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
  
2.  Utwórz <xref:System.Drawing.Graphics> obiekt, który reprezentuje powierzchnię rysunku, którego chcesz użyć. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie obiektów graficznych do rysowania](how-to-create-graphics-objects-for-drawing.md).  
  
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
  
3.  Wywołaj <xref:System.Drawing.Graphics.DrawImage%2A> obiektów graficznych do renderowania obrazu. Należy określić obraz, który ma być rysowany oraz współrzędne, w którym ma być rysowany.  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a>Zobacz także
- [Wprowadzenie do programowania grafiki](getting-started-with-graphics-programming.md)
- [Instrukcje: Tworzenie obiektów graficznych do rysowania](how-to-create-graphics-objects-for-drawing.md)
- [Pióra, linie i prostokąty w GDI+](pens-lines-and-rectangles-in-gdi.md)
- [Instrukcje: Rysowanie tekstu w formularzu Windows](how-to-draw-text-on-a-windows-form.md)
- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Linie rysunku lub zamkniętych figur](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)
- [Edytor obrazów dla ikon](/cpp/windows/image-editor-for-icons)
