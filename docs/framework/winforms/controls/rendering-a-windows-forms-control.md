---
title: Renderowanie kontrolki
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- OnPaintBackground method [Windows Forms], invoking in Windows Forms custom controls
- custom controls [Windows Forms], graphics resources
- custom controls [Windows Forms], invalidation and painting
ms.assetid: aae8e1e6-4786-432b-a15e-f4c44760d302
ms.openlocfilehash: 0e1a7ca5dc0414d518c081b1db2dca5477d4f743
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742387"
---
# <a name="rendering-a-windows-forms-control"></a>Renderowanie formantu formularzy systemu Windows
Renderowanie odnosi się do procesu tworzenia reprezentacji wizualizacji na ekranie użytkownika. Windows Forms używa interfejsu GDI (nowej biblioteki grafiki systemu Windows) do renderowania. Zarządzane klasy, które zapewniają dostęp do interfejsu GDI, znajdują się w przestrzeni nazw <xref:System.Drawing?displayProperty=nameWithType> i jej podobszarach nazw.  
  
 Następujące elementy są objęte renderowaniem kontroli:  
  
- Funkcje rysowania dostarczone przez klasę bazową <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
- Najważniejsze elementy biblioteki grafiki GDI.  
  
- Geometria regionu rysowania.  
  
- Procedura zwalniania zasobów graficznych.  
  
## <a name="drawing-functionality-provided-by-control"></a>Funkcje rysowania zapewniane przez kontrolę  
 Klasa bazowa <xref:System.Windows.Forms.Control> udostępnia funkcje rysowania za pomocą <xref:System.Windows.Forms.Control.Paint> zdarzenia. Kontrolka wywołuje zdarzenie <xref:System.Windows.Forms.Control.Paint>, gdy trzeba zaktualizować jego wyświetlanie. Aby uzyskać więcej informacji na temat zdarzeń w .NET Framework, zobacz [Obsługa i](../../../standard/events/index.md)wywoływanie zdarzeń.  
  
 Klasa danych zdarzenia dla zdarzenia <xref:System.Windows.Forms.Control.Paint>, <xref:System.Windows.Forms.PaintEventArgs>, przechowuje dane, które są konieczne do rysowania kontrolki — dojście do obiektu graficznego i obiekt prostokąta, który reprezentuje region do rysowania. Te obiekty są pokazane pogrubioną czcionką w poniższym fragmencie kodu.  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   Implements IDisposable  
  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property  
   ' Other properties and methods.  
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs, IDisposable {  
public System.Drawing.Rectangle ClipRectangle {get;}  
public System.Drawing.Graphics Graphics {get;}  
// Other properties and methods.  
...  
}  
```  
  
 <xref:System.Drawing.Graphics> jest klasą zarządzaną, która hermetyzuje funkcje rysowania, zgodnie z opisem w omówieniu GDI w dalszej części tego tematu. <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> jest wystąpieniem struktury <xref:System.Drawing.Rectangle> i definiuje dostępny obszar, w którym formant może być rysowany. Deweloper kontroli może obliczyć <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> przy użyciu właściwości <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> kontrolki, zgodnie z opisem w omówieniu geometrii w dalszej części tego tematu.  
  
 Formant musi zapewniać logikę renderowania przez zastąpienie metody <xref:System.Windows.Forms.Control.OnPaint%2A>, która dziedziczy z <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control.OnPaint%2A> uzyskuje dostęp do obiektu graficznego oraz prostokąta do rysowania przez <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> i właściwości <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> wystąpienia <xref:System.Windows.Forms.PaintEventArgs> przekazywać do niego.  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 Metoda <xref:System.Windows.Forms.Control.OnPaint%2A> klasy podstawowej <xref:System.Windows.Forms.Control> nie implementuje żadnych funkcji rysowania, ale tylko wywołuje delegatów zdarzeń zarejestrowanych w zdarzeniu <xref:System.Windows.Forms.Control.Paint>. Podczas przesłonięcia <xref:System.Windows.Forms.Control.OnPaint%2A>, zazwyczaj należy wywołać metodę <xref:System.Windows.Forms.Control.OnPaint%2A> klasy bazowej, aby zarejestrowani pełnomocnicy otrzymywali zdarzenie <xref:System.Windows.Forms.Control.Paint>. Jednak kontrolki, które malują całą powierzchnię nie należy wywoływać <xref:System.Windows.Forms.Control.OnPaint%2A>klasy bazowej, ponieważ wprowadzają migotanie. Przykład zastępowania zdarzenia <xref:System.Windows.Forms.Control.OnPaint%2A> można znaleźć w temacie How to [: Create an Windows Forms Control, który pokazuje postęp](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
> [!NOTE]
> Nie wywołuj <xref:System.Windows.Forms.Control.OnPaint%2A> bezpośrednio z formantu; Zamiast tego wywołaj metodę <xref:System.Windows.Forms.Control.Invalidate%2A> (Odziedziczone po <xref:System.Windows.Forms.Control>) lub inną metodę, która wywołuje <xref:System.Windows.Forms.Control.Invalidate%2A>. Metoda <xref:System.Windows.Forms.Control.Invalidate%2A> z kolei wywołuje <xref:System.Windows.Forms.Control.OnPaint%2A>. Metoda <xref:System.Windows.Forms.Control.Invalidate%2A> jest przeciążona i, w zależności od argumentów dostarczonych do <xref:System.Windows.Forms.Control.Invalidate%2A> `e`, formant ponownie narysuje część lub wszystkie jego obszar ekranu.  
  
 Klasa bazowa <xref:System.Windows.Forms.Control> definiuje inną metodę, która jest przydatna do rysowania — <xref:System.Windows.Forms.Control.OnPaintBackground%2A> metody.  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> maluje tło (a tym samym kształt) okna i gwarantuje, że jest to szybkie, a <xref:System.Windows.Forms.Control.OnPaint%2A> maluje szczegóły i mogą być wolniejsze, ponieważ poszczególne żądania programu Paint są łączone w jedno <xref:System.Windows.Forms.Control.Paint> zdarzenie, które obejmuje wszystkie obszary, które muszą zostać narysowane ponownie. Możesz chcieć wywołać <xref:System.Windows.Forms.Control.OnPaintBackground%2A>, jeśli na przykład chcesz narysować tło kolorowe gradientowe dla kontrolki.  
  
 Chociaż <xref:System.Windows.Forms.Control.OnPaintBackground%2A> ma nomenklaturę podobną do zdarzeń i przyjmuje ten sam argument co Metoda `OnPaint`, <xref:System.Windows.Forms.Control.OnPaintBackground%2A> nie jest rzeczywistą metodą zdarzenia. Brak zdarzenia `PaintBackground` i <xref:System.Windows.Forms.Control.OnPaintBackground%2A> nie wywoła delegatów zdarzeń. Podczas zastępowania metody <xref:System.Windows.Forms.Control.OnPaintBackground%2A> Klasa pochodna nie jest wymagana do wywołania metody <xref:System.Windows.Forms.Control.OnPaintBackground%2A> jej klasy bazowej.  
  
## <a name="gdi-basics"></a>Podstawowe informacje o GDI+  
 Klasa <xref:System.Drawing.Graphics> udostępnia metody rysowania różnych kształtów, takich jak koła, Trójkąty, łuki i elipsy, a także metody wyświetlania tekstu. Przestrzeń nazw <xref:System.Drawing?displayProperty=nameWithType> i jej podobszar nazw zawierają klasy, które hermetyzują elementy graficzne, takie jak kształty (okręgi, prostokąty, łuki i inne), kolory, czcionki, pędzle i tak dalej. Aby uzyskać więcej informacji na temat interfejsu GDI, zobacz [Używanie zarządzanych klas graficznych](../advanced/using-managed-graphics-classes.md). Podstawowe informacje o usłudze GDI są również opisane w temacie [How to: Create a Windows Forms Control, który pokazuje postęp](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="geometry-of-the-drawing-region"></a>Geometria regionu rysowania  
 Właściwość <xref:System.Windows.Forms.Control.ClientRectangle%2A> kontrolki określa prostokątny region dostępny dla formantu na ekranie użytkownika, podczas gdy właściwość <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> <xref:System.Windows.Forms.PaintEventArgs> określa obszar, który jest rzeczywiście malowany. (Należy pamiętać, że malowanie odbywa się w metodzie zdarzenia <xref:System.Windows.Forms.Control.Paint>, która przyjmuje jako argument wystąpienie <xref:System.Windows.Forms.PaintEventArgs>). Kontrolka może być konieczna do malowania tylko częścią dostępnego obszaru, tak jak w przypadku, gdy mała sekcja ekranu kontrolki jest zmieniana. W takich sytuacjach deweloper kontroli musi obliczyć rzeczywisty prostokąt do rysowania i przekazać go do <xref:System.Windows.Forms.Control.Invalidate%2A>. Przeciążone wersje <xref:System.Windows.Forms.Control.Invalidate%2A>, które pobierają <xref:System.Drawing.Rectangle> lub <xref:System.Drawing.Region> jako argument, używają tego argumentu do generowania właściwości <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> <xref:System.Windows.Forms.PaintEventArgs>.  
  
 Poniższy fragment kodu przedstawia sposób, w jaki formant niestandardowy `FlashTrackBar` oblicza prostokątny obszar do narysowania. Zmienna `client` oznacza Właściwość <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>. Pełny przykład można znaleźć w temacie [How to: Create a Windows Forms Control, który pokazuje postęp](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>Zwalnianie zasobów graficznych  
 Obiekty graficzne są kosztowne, ponieważ korzystają z zasobów systemowych. Takie obiekty obejmują wystąpienia klasy <xref:System.Drawing.Graphics?displayProperty=nameWithType>, a także wystąpienia <xref:System.Drawing.Brush?displayProperty=nameWithType>, <xref:System.Drawing.Pen?displayProperty=nameWithType>i innych klas graficznych. Ważne jest, aby utworzyć zasób grafiki tylko wtedy, gdy jest potrzebny, i wydać go wkrótce po zakończeniu korzystania z niego. Jeśli tworzysz typ, który implementuje interfejs <xref:System.IDisposable>, wywołaj jego metodę <xref:System.IDisposable.Dispose%2A> po zakończeniu pracy z nim w celu zwolnienia zasobów.  
  
 Poniższy fragment kodu przedstawia sposób, w jaki `FlashTrackBar` kontrolka niestandardowa tworzy i zwalnia zasób <xref:System.Drawing.Brush>. Aby uzyskać pełny kod źródłowy, zobacz [How to: Create a Windows Forms Control, który pokazuje postęp](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: tworzenie kontrolki formularzy Windows Forms pokazującej postęp](how-to-create-a-windows-forms-control-that-shows-progress.md)
