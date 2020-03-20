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
ms.openlocfilehash: d591d65904484e33285e5db7aa99760f3e1909d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142436"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a>Porady: tworzenie obiektów graficznych do rysowania
Aby można było rysować linie i kształty, renderować tekst lub wyświetlać i <xref:System.Drawing.Graphics> manipulować obrazami za pomocą GDI+, należy utworzyć obiekt. Obiekt <xref:System.Drawing.Graphics> reprezentuje powierzchnię rysunku GDI+ i jest obiektem używanym do tworzenia obrazów graficznych.  
  
 Istnieją dwa kroki pracy z grafiką:  
  
1. Tworzenie <xref:System.Drawing.Graphics> obiektu.  
  
2. Używanie <xref:System.Drawing.Graphics> obiektu do rysowania linii i kształtów, renderowania tekstu lub wyświetlania i manipulowania obrazami.  
  
## <a name="creating-a-graphics-object"></a>Tworzenie obiektu graficznego  
 Obiekt graficzny można utworzyć na różne sposoby.  
  
#### <a name="to-create-a-graphics-object"></a>Aby utworzyć obiekt graficzny  
  
- Odbierz odwołanie do obiektu graficznego <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> jako część w przypadku formularza lub formantu. Jest to zwykle sposób uzyskania odwołania do obiektu graficznego podczas tworzenia kodu malowania formantu. Podobnie można również uzyskać obiekt graficzny jako właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> podczas <xref:System.Drawing.Printing.PrintDocument.PrintPage> obsługi <xref:System.Drawing.Printing.PrintDocument>zdarzenia dla .  
  
     — lub —  
  
- Wywołanie <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody formantu lub formularza, <xref:System.Drawing.Graphics> aby uzyskać odwołanie do obiektu, który reprezentuje powierzchnię rysunku tego formantu lub formularza. Tej metody należy użyć, jeśli chcesz narysować formularz lub formant, który już istnieje.  
  
     — lub —  
  
- Utwórz <xref:System.Drawing.Graphics> obiekt z dowolnego obiektu, który dziedziczy z . <xref:System.Drawing.Image> Takie podejście jest przydatne, gdy chcesz zmienić już istniejący obraz.  
  
     W poniższych sekcjach podano szczegółowe informacje na temat każdego z tych procesów.  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>PaintEventArgs w programie obsługi zdarzeń malowania  
 Podczas programowania <xref:System.Windows.Forms.PaintEventHandler> formanty <xref:System.Drawing.Printing.PrintDocument.PrintPage> lub <xref:System.Drawing.Printing.PrintDocument>fora obiekt graficzny jest dostarczany jako <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Drawing.Printing.PrintPageEventArgs>jedna z właściwości lub .  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>Aby uzyskać odwołanie do obiektu Graphics z PaintEventArgs w paint zdarzenia zdarzenia  
  
1. Zadeklaruj <xref:System.Drawing.Graphics> obiekt.  
  
2. Przypisz zmienną, <xref:System.Drawing.Graphics> aby odwoływać się <xref:System.Windows.Forms.PaintEventArgs>do obiektu przekazanego jako część pliku .  
  
3. Wstaw kod, aby pomalować formularz lub formant.  
  
     Poniższy przykład pokazuje, <xref:System.Drawing.Graphics> jak odwoływać się do obiektu z <xref:System.Windows.Forms.PaintEventArgs> w zdarzeniu: <xref:System.Windows.Forms.Control.Paint>  
  
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
  
## <a name="creategraphics-method"></a>Metoda CreateGraphics  
 Można również użyć <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody formantu lub formularza, <xref:System.Drawing.Graphics> aby uzyskać odwołanie do obiektu, który reprezentuje powierzchnię rysunku tego formantu lub formularza.  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>Aby utworzyć obiekt Graphics za pomocą metody CreateGraphics  
  
- Wywołanie <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody formularza lub formantu, na którym chcesz renderować grafikę.  
  
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
  
## <a name="create-from-an-image-object"></a>Tworzenie z obiektu obrazu  
 Ponadto można utworzyć obiekt graficzny z dowolnego obiektu, <xref:System.Drawing.Image> który pochodzi z klasy.  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>Aby utworzyć obiekt Graphics na podstawie obrazu  
  
- Wywołanie <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> metody, podając nazwę Zmiennej Image, z <xref:System.Drawing.Graphics> której chcesz utworzyć obiekt.  
  
     W poniższym <xref:System.Drawing.Bitmap> przykładzie pokazano, jak używać obiektu:  
  
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
> Można tworzyć <xref:System.Drawing.Graphics> tylko obiekty z plików bmp nieindeksowanych, takie jak pliki 16-bitowe, 24-bitowe i 32-bitowe .bmp. Każdy piksel plików .bmp nonindexed posiada kolor, w przeciwieństwie do pikseli indeksowanych plików .bmp, które posiadają indeks do tabeli kolorów.  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>Rysowanie i manipulowanie kształtami i obrazami  
 Po utworzeniu <xref:System.Drawing.Graphics> obiektu można użyć obiektu do rysowania linii i kształtów, renderowania tekstu lub wyświetlania i manipulowania obrazami. Głównymi obiektami, które <xref:System.Drawing.Graphics> są używane z obiektem są:  
  
- Klasa <xref:System.Drawing.Pen> — służy do rysowania linii, tworzenia kształtów lub renderowania innych reprezentacji geometrycznych.  
  
- Klasa <xref:System.Drawing.Brush> — służy do wypełniania obszarów grafiki, takich jak wypełnione kształty, obrazy lub tekst.  
  
- Klasa <xref:System.Drawing.Font> — zawiera opis kształtów, których należy używać podczas renderowania tekstu.  
  
- Struktura <xref:System.Drawing.Color> — reprezentuje różne kolory do wyświetlenia.  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>Aby użyć utworzonego obiektu Graphics  
  
- Pracuj z odpowiednim obiektem wymienionym powyżej, aby narysować to, czego potrzebujesz.  
  
     Aby uzyskać więcej informacji, zobacz następujące tematy:  
  
    |Aby renderować|Zobacz|  
    |---------------|---------|  
    |Linie|[Instrukcje: rysowanie linii w formularzu systemu Windows](how-to-draw-a-line-on-a-windows-form.md)|  
    |Kształty|[Porady: rysowanie konturu kształtu](how-to-draw-an-outlined-shape.md)|  
    |Tekst|[Porady: rysowanie tekstu w formularzu systemu Windows](how-to-draw-text-on-a-windows-form.md)|  
    |Obrazy|[Instrukcje: renderowanie obrazów za pomocą GDI+](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do programowania grafiki](getting-started-with-graphics-programming.md)
- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Linie, krzywe i kształty](lines-curves-and-shapes.md)
- [Instrukcje: renderowanie obrazów za pomocą GDI+](how-to-render-images-with-gdi.md)
