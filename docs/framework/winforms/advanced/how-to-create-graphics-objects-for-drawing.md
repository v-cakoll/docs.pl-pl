---
title: 'Instrukcje: Tworzenie obiektów graficznych do rysowania'
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
ms.openlocfilehash: a21e049cb91ec29bcd46eb04efd78487da9a6317
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497035"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a>Instrukcje: Tworzenie obiektów graficznych do rysowania
Zanim można narysować linie i kształty, renderowanie tekstu, lub wyświetlanie obrazów i manipulowania nimi za pomocą [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], musisz utworzyć <xref:System.Drawing.Graphics> obiektu. <xref:System.Drawing.Graphics> Obiekt reprezentuje [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] rysowania powierzchni i jest obiekt, który jest używany do tworzenia obrazów graficznych.  
  
 W pracy z grafikami znajdują się dwa kroki:  
  
1.  Tworzenie <xref:System.Drawing.Graphics> obiektu.  
  
2.  Za pomocą <xref:System.Drawing.Graphics> obiektu rysowanie linii i kształtów, tekstu, renderowanie lub wyświetlania obrazów i manipulowania nimi.  
  
## <a name="creating-a-graphics-object"></a>Tworzenie obiektów graficznych  
 Obiekt grafiki można utworzyć na wiele sposobów.  
  
#### <a name="to-create-a-graphics-object"></a>Aby utworzyć obiekt grafiki  
  
-   Odbieranie odwołanie do obiektu grafiki jako część <xref:System.Windows.Forms.PaintEventArgs> w <xref:System.Windows.Forms.Control.Paint> zdarzeń formularza lub formantu. Jest to zazwyczaj, jak uzyskać odwołanie do obiektu grafiki podczas tworzenia kodu rysowania dla formantu. Podobnie, można również uzyskać obiekt graficzny jako właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> podczas obsługi <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenie <xref:System.Drawing.Printing.PrintDocument>.  
  
     —lub—  
  
-   Wywołaj <xref:System.Windows.Forms.Control.CreateGraphics%2A> metoda formantu lub formularz, aby uzyskać odwołanie do <xref:System.Drawing.Graphics> obiekt, który reprezentuje powierzchni do rysowania tego formularza lub formantu. Użyj tej metody, jeśli chcesz rysować na formularza lub formantu, który już istnieje.  
  
     —lub—  
  
-   Tworzenie <xref:System.Drawing.Graphics> obiekt z dowolnego obiektu, który dziedziczy z <xref:System.Drawing.Image>. Takie podejście jest przydatne, jeśli chcesz zmienić istniejącego obrazu.  
  
     Poniższe sekcje zawierają szczegółowe informacje o każdej z tych procesów.  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>PaintEventArgs w obsłudze zdarzeń malowania  
 Podczas programowania <xref:System.Windows.Forms.PaintEventHandler> dla formantów lub <xref:System.Drawing.Printing.PrintDocument.PrintPage> dla <xref:System.Drawing.Printing.PrintDocument>, obiekt graficzny jest dostarczana jako jedna z właściwości obiektu <xref:System.Windows.Forms.PaintEventArgs> lub <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>Aby uzyskać odwołanie do obiektu grafiki z PaintEventArgs w zdarzenie malowania  
  
1.  Zadeklaruj <xref:System.Drawing.Graphics> obiektu.  
  
2.  Przypisz zmienną do odwoływania się do <xref:System.Drawing.Graphics> przekazano obiekt jako część <xref:System.Windows.Forms.PaintEventArgs>.  
  
3.  Wstaw kod do malowania formularza lub formantu.  
  
     Poniższy przykład pokazuje, jak utworzyć odwołanie do <xref:System.Drawing.Graphics> obiektu z <xref:System.Windows.Forms.PaintEventArgs> w <xref:System.Windows.Forms.Control.Paint> zdarzeń:  
  
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
 Można również użyć <xref:System.Windows.Forms.Control.CreateGraphics%2A> metoda formantu lub formularz, aby uzyskać odwołanie do <xref:System.Drawing.Graphics> obiekt, który reprezentuje powierzchni do rysowania tego formularza lub formantu.  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>Aby utworzyć obiekt graficzny z metodę CreateGraphics  
  
-   Wywołaj <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody formularza lub formantu, na którym ma być renderowany grafiki.  
  
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
  
## <a name="create-from-an-image-object"></a>Tworzenie na podstawie obiektu obrazu  
 Ponadto można utworzyć obiekt grafiki z dowolnych obiektów, która pochodzi od klasy <xref:System.Drawing.Image> klasy.  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>Aby utworzyć obiekt grafiki z obrazu  
  
-   Wywołaj <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> metody, podając nazwę zmiennej obrazu, z którego chcesz utworzyć <xref:System.Drawing.Graphics> obiektu.  
  
     Poniższy przykład pokazuje, jak używać <xref:System.Drawing.Bitmap> obiektu:  
  
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
>  Można tworzyć tylko <xref:System.Drawing.Graphics> obiektów z nieindeksowanym .bmp — pliki, takie jak pliki .bmp 16-bitowych, 24-bitowego i 32-bitowych. Każdego piksela nieindeksowanych .bmp — pliki zawiera kolor, w przeciwieństwie do pikseli .bmp indeksowane pliki, które przechowywania indeksu tabeli kolorów.  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>Rysowanie i manipulowanie nimi kształtów i obrazów  
 Po jego utworzeniu <xref:System.Drawing.Graphics> obiekt może służyć do rysowania linii i kształtów, renderowanie tekstu, lub wyświetlanie obrazów i manipulowania nimi. Obiekty główne, które są używane z <xref:System.Drawing.Graphics> obiekt są:  
  
-   <xref:System.Drawing.Pen> Klasy — Rysowanie linii, kształtów lub renderowania inne oświadczenia geometrycznych.  
  
-   <xref:System.Drawing.Brush> Klasy — używany do wypełniania obszarów grafiki, takie jak wypełnione kształty, obrazy i tekst.  
  
-   <xref:System.Drawing.Font> Klasy — zawiera opis co kształty do użycia podczas renderowania tekstu.  
  
-   <xref:System.Drawing.Color> Struktury — reprezentuje różne kolory do wyświetlenia.  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>Aby użyć obiektu grafiki, utworzonych przez użytkownika  
  
-   Praca z odpowiedniego obiektu wymienionych powyżej, aby narysować, co jest potrzebne.  
  
     Więcej informacji znajduje się w następujących tematach:  
  
    |Do renderowania|Zobacz|  
    |---------------|---------|  
    |wiersze|[Instrukcje: Rysuj linię w formularzu Windows](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-on-a-windows-form.md)|  
    |Kształty|[Instrukcje: Rysowanie konturu kształtu](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)|  
    |Tekst|[Instrukcje: Rysowanie tekstu w formularzu Windows](../../../../docs/framework/winforms/advanced/how-to-draw-text-on-a-windows-form.md)|  
    |Obrazy|[Instrukcje: Renderowanie obrazów za pomocą GDI +](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a>Zobacz także
- [Wprowadzenie do programowania grafiki](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)
- [Grafika i rysowanie w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [Linie, krzywe i kształty](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [Instrukcje: Renderowanie obrazów za pomocą GDI +](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)
