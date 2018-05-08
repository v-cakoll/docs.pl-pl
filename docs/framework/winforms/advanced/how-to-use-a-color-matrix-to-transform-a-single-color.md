---
title: 'Porady: stosowanie macierzy kolorów do przekształcenia pojedynczego koloru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image colors [Windows Forms], transforming
- color matrices [Windows Forms], using
ms.assetid: 44df4556-a433-49c0-ac0f-9a12063a5860
ms.openlocfilehash: 741259fcf853c82dfd13b43edc92e50d8767887b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-color-matrix-to-transform-a-single-color"></a>Porady: stosowanie macierzy kolorów do przekształcenia pojedynczego koloru
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] udostępnia <xref:System.Drawing.Image> i <xref:System.Drawing.Bitmap> klasy do przechowywania i manipulowanie obrazów. <xref:System.Drawing.Image> i <xref:System.Drawing.Bitmap> obiektów przechowywania koloru każdego piksela jako 32-bitową liczbą: 8, usługa bits dla czerwony, zielony, niebieski i alfa. Każdy z czterech składników jest liczba z przedziału od 0 do 255, gdzie 0 reprezentujący natężenie i 255 reprezentujący intensywność pełna. Określa przezroczystość koloru, składnika alfa: 0 jest w pełni przezroczyste, i jest całkowicie nieprzezroczyste 255.  
  
 Wektor kolor jest 4-krotka formularza (czerwony, zielony, niebieski, alfa). Na przykład wektor kolor (0, 255, 0, 255) reprezentuje nieprzezroczyste kolor, który nie ma czerwony ani blue, ale ma zielony pełna intensywność.  
  
 Inny Konwencji reprezentujący kolorów używa numer 1 intensywność pełna. Przy użyciu Konwencji, kolor opisane w poprzednim akapicie jest przedstawiany wektor (0, 1, 0, 1). [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] używa konwencji 1 jako pełna intensywność podczas wykonywania transformacji kolorów.  
  
 Linear — przekształcenia (obrót, skalowanie i podobne) można zastosować do wektorów kolor przez pomnożenie wektory kolor przez macierz 4 x 4. Jednak macierzy 4 x 4 nie można używać do wykonywania tłumaczenia (rożne). Jeśli dodasz fikcyjnymi współrzędnych piąty (na przykład numer 1) do każdego z kierunków kolor umożliwia macierzy 5 x 5 zastosować dowolną kombinację linear — przekształcenia i tłumaczeń. Przekształcenie składające się z transformację liniowej następuje translacja jest nazywany affine — przekształcenia.  
  
 Na przykład załóżmy, że chcesz uruchomić z kolorem (0,2, 0.0, 0,4, 1.0) i stosuje się następujące przekształcenia:  
  
1.  Podwójna składnika czerwony  
  
2.  Dodaj 0,2 czerwony, zielonemu i niebieskiemu składników  
  
 Następujące mnożenie macierzy wykona pary przekształcenia w podanej kolejności.  
  
 ![Ponowne kolorowanie](../../../../docs/framework/winforms/advanced/media/recoloring01.gif "recoloring01")  
  
 Elementy tablicy kolorów są indeksowane (liczony od zera) wiersza i kolumny. Na przykład wpis w wierszu piątym i trzecia kolumna macierzy M jest oznaczona M [4] [2].  
  
 5 x 5 macierzą (pokazano na poniższej ilustracji) ma 1s na przekątnej i 0s wszędzie else. Jeśli wektor kolor pomnożenia macierzą, vector kolor nie zmienia się. To wygodny sposób na formularzu macierzy transformacji kolorów jest rozpocząć z macierzą i wprowadzić niewielkie zmiany tworzącego żądaną transformacji.  
  
 ![Ponowne kolorowanie](../../../../docs/framework/winforms/advanced/media/recoloring02.gif "recoloring02")  
  
 Bardziej szczegółowe omówienie macierzy i przekształcenia, zobacz [systemy i transformacje współrzędnych](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przyjmuje obrazu, który jest jeden kolor (0,2, 0.0, 0,4, 1.0) i stosuje transformację opisane w poprzednim akapicie.  
  
 Na poniższej ilustracji przedstawiono oryginalnego obrazu po lewej stronie i przekształcony obraz po prawej stronie.  
  
 ![Kolory](../../../../docs/framework/winforms/advanced/media/colortrans1.png "colortrans1")  
  
 Kod w poniższym przykładzie przeprowadzić ponowne kolorowanie korzysta z następujące czynności:  
  
1.  Inicjowanie <xref:System.Drawing.Imaging.ColorMatrix> obiektu.  
  
2.  Utwórz <xref:System.Drawing.Imaging.ImageAttributes> obiektu i przekazać <xref:System.Drawing.Imaging.ColorMatrix> do obiektu <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> metody <xref:System.Drawing.Imaging.ImageAttributes> obiektu.  
  
3.  Przekaż <xref:System.Drawing.Imaging.ImageAttributes> do obiektu <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> obiektu.  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Ponowne kolorowanie obrazów](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 [Systemy i przekształcenia współrzędnych](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)
