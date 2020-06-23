---
title: 'Porady: tworzenie obiektów graficznych do rysowania'
description: Zapoznaj się teraz, aby utworzyć obiekt graficzny, który jest potrzebny do rysowania linii i kształtów, renderowania tekstu lub wyświetlania obrazów i manipulowania nimi przy użyciu interfejsu GDI+.
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
ms.openlocfilehash: 1a0884c1e9956dc6f4608e32372deeea24ef4670
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903210"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a>Porady: tworzenie obiektów graficznych do rysowania
Aby można było rysować linie i kształty, renderować tekst lub wyświetlać i manipulować obrazami za pomocą interfejsu GDI+, należy utworzyć <xref:System.Drawing.Graphics> obiekt. <xref:System.Drawing.Graphics>Obiekt reprezentuje powierzchnię rysowania GDI+ i jest obiektem, który jest używany do tworzenia obrazów graficznych.  
  
 Istnieją dwa kroki pracy z grafiką:  
  
1. Tworzenie <xref:System.Drawing.Graphics> obiektu.  
  
2. Używanie <xref:System.Drawing.Graphics> obiektu do rysowania linii i kształtów, renderowania tekstu lub wyświetlania obrazów i manipulowania nimi.  
  
## <a name="creating-a-graphics-object"></a>Tworzenie obiektu graficznego  
 Obiekt grafiki można utworzyć na różne sposoby.  
  
#### <a name="to-create-a-graphics-object"></a>Aby utworzyć obiekt grafiki  
  
- Odbierz odwołanie do obiektu grafiki <xref:System.Windows.Forms.PaintEventArgs> w ramach <xref:System.Windows.Forms.Control.Paint> zdarzenia formularza lub kontrolki. Jest to zazwyczaj sposób uzyskiwania odwołania do obiektu grafiki podczas tworzenia kodu rysowania dla kontrolki. Podobnie, można również uzyskać obiekt grafiki jako właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> podczas obsługi <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenia dla elementu <xref:System.Drawing.Printing.PrintDocument> .  
  
     -lub-  
  
- Wywołaj <xref:System.Windows.Forms.Control.CreateGraphics%2A> metodę kontrolki lub formularza, aby uzyskać odwołanie do <xref:System.Drawing.Graphics> obiektu, który reprezentuje powierzchnię rysowania tego formantu lub formularza. Użyj tej metody, jeśli chcesz rysować na formularzu lub kontrolce, która już istnieje.  
  
     -lub-  
  
- Utwórz <xref:System.Drawing.Graphics> obiekt z dowolnego obiektu, który dziedziczy z <xref:System.Drawing.Image> . Takie podejście jest przydatne, gdy chcesz zmienić już istniejący obraz.  
  
     Poniższe sekcje zawierają szczegółowe informacje o każdym z tych procesów.  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>PaintEventArgs w programie obsługi zdarzeń programu Paint  
 Gdy programowanie <xref:System.Windows.Forms.PaintEventHandler> dla kontrolek lub <xref:System.Drawing.Printing.PrintDocument.PrintPage> dla obiektu a <xref:System.Drawing.Printing.PrintDocument> , obiekt grafiki jest udostępniany jako jedna z właściwości <xref:System.Windows.Forms.PaintEventArgs> lub <xref:System.Drawing.Printing.PrintPageEventArgs> .  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>Aby uzyskać odwołanie do obiektu grafiki z PaintEventArgs w zdarzeniu Paint  
  
1. Zadeklaruj <xref:System.Drawing.Graphics> obiekt.  
  
2. Przypisz zmienną, aby odwołać się do <xref:System.Drawing.Graphics> obiektu przesyłanego jako część elementu <xref:System.Windows.Forms.PaintEventArgs> .  
  
3. Wstaw kod, aby malować formularz lub kontrolkę.  
  
     Poniższy przykład pokazuje, jak odwoływać się do <xref:System.Drawing.Graphics> obiektu ze <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> zdarzenia:  
  
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
  
## <a name="creategraphics-method"></a>Metoda xmlgraphics  
 Można również użyć <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody kontrolki lub formularza, aby uzyskać odwołanie do <xref:System.Drawing.Graphics> obiektu, który reprezentuje powierzchnię rysowania tego formantu lub formularza.  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>Aby utworzyć obiekt grafiki przy użyciu metody xmlgraphics  
  
- Wywołaj <xref:System.Windows.Forms.Control.CreateGraphics%2A> metodę formularza lub kontrolki, na której chcesz renderować grafikę.  
  
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
 Ponadto można utworzyć obiekt grafiki z dowolnego obiektu, który pochodzi od <xref:System.Drawing.Image> klasy.  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>Aby utworzyć obiekt grafiki z obrazu  
  
- Wywołaj <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> metodę, podając nazwę zmiennej obrazu, z której chcesz utworzyć <xref:System.Drawing.Graphics> obiekt.  
  
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
> Można tworzyć tylko <xref:System.Drawing.Graphics> obiekty z nieindeksowanych plików BMP, takich jak 16-bitowe, 24-bitowe i 32-bitowe pliki BMP. Każdy piksel nieindeksowanych plików BMP posiada kolor, w przeciwieństwie do pikseli indeksowanych plików BMP, które przechowują indeks tabeli koloru.  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>Rysowanie i manipulowanie kształtami i obrazami  
 Po jego utworzeniu <xref:System.Drawing.Graphics> obiekt może być używany do rysowania linii i kształtów, renderowania tekstu lub wyświetlania obrazów i manipulowania nimi. Obiekty główne, które są używane z <xref:System.Drawing.Graphics> obiektem:  
  
- <xref:System.Drawing.Pen>Klasa — używana do rysowania linii, tworzenia konspektów kształtów lub renderowania innych reprezentacji geometrycznych.  
  
- <xref:System.Drawing.Brush>Klasa — używana do wypełniania obszarów grafiki, takich jak wypełnione kształty, obrazy lub tekst.  
  
- <xref:System.Drawing.Font>Klasa — zawiera opis kształtów, które mają być używane podczas renderowania tekstu.  
  
- <xref:System.Drawing.Color>Struktura — reprezentuje różne kolory do wyświetlenia.  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>Aby użyć utworzonego obiektu graficznego  
  
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
