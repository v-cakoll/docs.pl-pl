---
title: "Porady: renderowanie obrazów za pomocą GDI+"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], creating
- GDI+, rendering existing images
ms.assetid: c128b79a-3e31-47d8-9e66-3470f570a056
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9c0b4c128667cab04ca8ed015b44dae60d11b474
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Porady: Tworzenie obiektów graficznych do rysowania](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Pióra, linie i prostokąty w GDI +](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)  
 [Porady: Rysowanie tekstu w formularzu systemu Windows](../../../../docs/framework/winforms/advanced/how-to-draw-text-on-a-windows-form.md)  
 [Grafika i rysowanie w formularzach systemu Windows](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Linie rysunku lub zamkniętych figur](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)  
 [Edytor obrazów dla ikon](/cpp/windows/image-editor-for-icons)
