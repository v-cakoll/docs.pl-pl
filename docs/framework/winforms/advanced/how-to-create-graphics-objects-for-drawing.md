---
title: 'Porady: tworzenie obiektów graficznych do rysowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating
- images [Windows Forms], creating
- GDI+, creating images
ms.assetid: 162861f9-f050-445e-8abb-b2c43a918b8b
ms.openlocfilehash: 3c25ddcfb3a566055afd5e233c2a69b3b7a8c66e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-graphics-objects-for-drawing"></a>Porady: tworzenie obiektów graficznych do rysowania
Przed może wykonywać Rysowanie linii i kształtów, renderowania tekstu, lub wyświetlania i modyfikowania obrazów za pomocą [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], należy utworzyć <xref:System.Drawing.Graphics> obiektu. <xref:System.Drawing.Graphics> Obiekt reprezentuje [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] powierzchni rysowania i jest obiekt, który służy do tworzenia obrazów graficznego.  
  
 Istnieją dwa kroki pracy z grafiki:  
  
1.  Tworzenie <xref:System.Drawing.Graphics> obiektu.  
  
2.  Przy użyciu <xref:System.Drawing.Graphics> obiekt do rysowania linii i kształtów, renderowanie tekstu, lub wyświetlanie obrazów i manipulowania nimi.  
  
## <a name="creating-a-graphics-object"></a>Tworzenie obiektów graficznych  
 Obiekt grafiki można tworzyć wiele sposobów.  
  
#### <a name="to-create-a-graphics-object"></a>Aby utworzyć obiekt grafiki  
  
-   Odbieranie odwołanie do obiektu graphics jako część <xref:System.Windows.Forms.PaintEventArgs> w <xref:System.Windows.Forms.Control.Paint> zdarzeń formularza lub kontrolki. Jest to zwykle, jak uzyskać odwołania do obiektu grafiki podczas tworzenia kodu malowanie kontrolki. Podobnie, możesz również uzyskać obiekt graphics jako właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> podczas obsługi <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenia dla <xref:System.Drawing.Printing.PrintDocument>.  
  
     —lub—  
  
-   Wywołanie <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody formantu lub formularza, aby uzyskać odwołania do <xref:System.Drawing.Graphics> obiekt, który reprezentuje powierzchni rysowania tego formantu lub formularza. Użyj tej metody, jeśli chcesz narysować na formularz lub formant, który już istnieje.  
  
     —lub—  
  
-   Utwórz <xref:System.Drawing.Graphics> obiektu z dowolnych obiektów, która dziedziczy <xref:System.Drawing.Image>. Takie rozwiązanie jest przydatne, jeśli chcesz zmienić już istniejącego obrazu.  
  
     W poniższych sekcjach znajdują się szczegółowe informacje o każdym z tych procesów.  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>PaintEventArgs w obsłudze zdarzeń malowania  
 Programowania <xref:System.Windows.Forms.PaintEventHandler> dla formantów lub <xref:System.Drawing.Printing.PrintDocument.PrintPage> dla <xref:System.Drawing.Printing.PrintDocument>, obiekt graphics jest dostępna jako jedna z właściwości obiektu <xref:System.Windows.Forms.PaintEventArgs> lub <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>Aby uzyskać odwołanie do obiektu Graphics z PaintEventArgs w zdarzenie malowania  
  
1.  Deklarowanie <xref:System.Drawing.Graphics> obiektu.  
  
2.  Przypisz do odwoływania się do zmiennej <xref:System.Drawing.Graphics> przekazano obiekt jako część <xref:System.Windows.Forms.PaintEventArgs>.  
  
3.  Wstawianie kodu do malowania formularza lub kontrolki.  
  
     Poniższy przykład przedstawia sposób odwoływania się do <xref:System.Drawing.Graphics> obiekt z <xref:System.Windows.Forms.PaintEventArgs> w <xref:System.Windows.Forms.Control.Paint> zdarzeń:  
  
    ```vb  
    Private Sub Form1_Paint(sender As Object, pe As PaintEventArgs) Handles _  
       MyBase.Paint  
       ' Declares the Graphics object and sets it to the Graphics object  
       ' supplied in the PaintEventArgs.  
       Dim g As Graphics = pe.Graphics  
       ' Insert code to paint the form here.  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Paint(object sender,   
       System.Windows.Forms.PaintEventArgs pe)   
    {  
       // Declares the Graphics object and sets it to the Graphics object  
       // supplied in the PaintEventArgs.  
       Graphics g = pe.Graphics;  
       // Insert code to paint the form here.  
    }  
    ```  
  
    ```cpp  
    private:  
       void Form1_Paint(System::Object ^ sender,  
          System::Windows::Forms::PaintEventArgs ^ pe)  
       {  
          // Declares the Graphics object and sets it to the Graphics object  
          // supplied in the PaintEventArgs.  
          Graphics ^ g = pe->Graphics;  
          // Insert code to paint the form here.  
       }  
    ```  
  
## <a name="creategraphics-method"></a>Metodę CreateGraphics  
 Można również użyć <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody formantu lub formularza, aby uzyskać odwołania do <xref:System.Drawing.Graphics> obiekt, który reprezentuje powierzchni rysowania tego formantu lub formularza.  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>Aby utworzyć obiekt grafiki przy użyciu metody CreateGraphics  
  
-   Wywołanie <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody formularza lub kontrolki, na którym ma być renderowany grafiki.  
  
    ```vb  
    Dim g as Graphics  
    ' Sets g to a Graphics object representing the drawing surface of the  
    ' control or form g is a member of.  
    g = Me.CreateGraphics  
    ```  
  
    ```csharp  
    Graphics g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this.CreateGraphics();  
    ```  
  
    ```cpp  
    Graphics ^ g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this->CreateGraphics();  
    ```  
  
## <a name="create-from-an-image-object"></a>Utwórz na podstawie obiektu obrazu  
 Ponadto można utworzyć obiektu graphics z dowolnych obiektów, która jest pochodną <xref:System.Drawing.Image> klasy.  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>Aby utworzyć obiekt Graphics z obrazu  
  
-   Wywołanie <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> metody, podając nazwę zmiennej obrazu, w którym chcesz utworzyć <xref:System.Drawing.Graphics> obiektu.  
  
     Poniższy przykład przedstawia użycie <xref:System.Drawing.Bitmap> obiektu:  
  
    ```vb  
    Dim myBitmap as New Bitmap("C:\Documents and Settings\Joe\Pics\myPic.bmp")  
    Dim g as Graphics = Graphics.FromImage(myBitmap)  
    ```  
  
    ```csharp  
    Bitmap myBitmap = new Bitmap(@"C:\Documents and   
       Settings\Joe\Pics\myPic.bmp");  
    Graphics g = Graphics.FromImage(myBitmap);  
    ```  
  
    ```cpp  
    Bitmap ^ myBitmap = gcnew  
       Bitmap("D:\\Documents and Settings\\Joe\\Pics\\myPic.bmp");  
    Graphics ^ g = Graphics::FromImage(myBitmap);  
    ```  
  
> [!NOTE]
>  Można tworzyć tylko <xref:System.Drawing.Graphics> obiektów z plików nieindeksowanych bmp, takich jak pliki .bmp 16-bitowych, 24-bitowe i 32-bitowych. Każdy pikseli nieindeksowanych .bmp — pliki przechowuje kolor, w przeciwieństwie do pikseli indeksowanych .bmp plików, które mógł pomieścić indeksu tabeli kolorów.  
  
-  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>Rysowanie i operowanie nimi kształtów i obrazów  
 Po jego utworzeniu <xref:System.Drawing.Graphics> obiekt może służyć do rysowania linii i kształtów, renderowanie tekstu, lub wyświetlanie obrazów i manipulowania nimi. Obiekty główne, które są używane z <xref:System.Drawing.Graphics> obiektu są:  
  
-   <xref:System.Drawing.Pen> Klasy — Rysowanie linii, kształtów lub renderowania innych reprezentacje geometrycznej.  
  
-   <xref:System.Drawing.Brush> Klasy — używany do wypełniania obszarów grafiki, takie jak wypełnione kształty, obrazy i tekst.  
  
-   <xref:System.Drawing.Font> Klasy — zawiera opis co kształty do użycia podczas renderowania tekstu.  
  
-   <xref:System.Drawing.Color> Struktury — reprezentuje różne kolory do wyświetlenia.  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>Aby użyć obiektu Graphics został utworzony  
  
-   Współpraca z odpowiedniego obiektu wymienionych powyżej, aby narysować, co jest potrzebne.  
  
     Więcej informacji znajduje się w następujących tematach:  
  
    |Do renderowania|Zobacz|  
    |---------------|---------|  
    |wiersze|[Instrukcje: rysowanie linii w formularzu systemu Windows](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-on-a-windows-form.md)|  
    |Kształty|[Instrukcje: rysowanie konturu kształtu](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)|  
    |Tekst|[Instrukcje: rysowanie tekstu w formularzu systemu Windows](../../../../docs/framework/winforms/advanced/how-to-draw-text-on-a-windows-form.md)|  
    |Obrazy|[Instrukcje: renderowanie obrazów za pomocą GDI+](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do programowania grafiki](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [Grafika i rysowanie w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Linie, krzywe i kształty](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Instrukcje: renderowanie obrazów za pomocą GDI+](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)
