---
title: Renderowanie formantu formularzy systemu Windows
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
ms.openlocfilehash: b24fbefac0dcfb666e25ad1d1726ef2cf8a5d84e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968272"
---
# <a name="rendering-a-windows-forms-control"></a>Renderowanie formantu formularzy systemu Windows
Renderowanie odnosi się do procesu tworzenia reprezentacji wizualizacji na ekranie użytkownika. Windows Forms używa interfejsu GDI (nowej biblioteki grafiki systemu Windows) do renderowania. Zarządzane klasy, które zapewniają dostęp do interfejsu GDI, znajdują się w <xref:System.Drawing?displayProperty=nameWithType> przestrzeni nazw i jej podobszarach nazw.  
  
 Następujące elementy są objęte renderowaniem kontroli:  
  
- Funkcje rysowania udostępniane przez klasę <xref:System.Windows.Forms.Control?displayProperty=nameWithType>bazową.  
  
- Najważniejsze elementy biblioteki grafiki GDI.  
  
- Geometria regionu rysowania.  
  
- Procedura zwalniania zasobów graficznych.  
  
## <a name="drawing-functionality-provided-by-control"></a>Funkcje rysowania zapewniane przez kontrolę  
 Klasa <xref:System.Windows.Forms.Control> bazowa udostępnia funkcje rysowania za pomocą swojego <xref:System.Windows.Forms.Control.Paint> zdarzenia. Kontrolka wywołuje zdarzenie <xref:System.Windows.Forms.Control.Paint> za każdym razem, gdy musi zaktualizować jego wyświetlanie. Aby uzyskać więcej informacji na temat zdarzeń w .NET Framework, zobacz [Obsługa i](../../../standard/events/index.md)wywoływanie zdarzeń.  
  
 Klasa danych zdarzenia dla <xref:System.Windows.Forms.Control.Paint> zdarzenia, <xref:System.Windows.Forms.PaintEventArgs>zawiera dane, które są konieczne do rysowania kontrolki — uchwytu do obiektu grafiki i obiektu prostokąta, który reprezentuje region do rysowania. Te obiekty są pokazane pogrubioną czcionką w poniższym fragmencie kodu.  
  
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
  
 <xref:System.Drawing.Graphics>jest klasą zarządzaną, która hermetyzuje funkcje rysowania, zgodnie z opisem w omówieniu GDI w dalszej części tego tematu. Jest wystąpieniem <xref:System.Drawing.Rectangle> struktury i definiuje dostępny obszar, w którym formant może być rysowany. <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> Deweloper kontroli może obliczyć <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> przy użyciu właściwości kontrolki, zgodnie z opisem w omówieniu geometrii w dalszej części tego tematu.  
  
 Kontrolka musi zapewniać logikę renderowania przez <xref:System.Windows.Forms.Control.OnPaint%2A> zastąpienie metody, z <xref:System.Windows.Forms.Control>której dziedziczy. <xref:System.Windows.Forms.Control.OnPaint%2A>uzyskuje dostęp do obiektu graficznego oraz prostokąta do rysowania przy użyciu <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> i właściwości <xref:System.Windows.Forms.PaintEventArgs> wystąpienia, do którego została przeniesiona.  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 Metoda klasy bazowej <xref:System.Windows.Forms.Control> nie implementuje żadnych funkcji rysowania, ale tylko wywołuje delegatów zdarzeń zarejestrowanych w <xref:System.Windows.Forms.Control.Paint> zdarzeniu. <xref:System.Windows.Forms.Control.OnPaint%2A> Podczas przesłonięcia <xref:System.Windows.Forms.Control.OnPaint%2A>należy zwykle <xref:System.Windows.Forms.Control.OnPaint%2A> wywołać metodę klasy bazowej, tak aby zarejestrowane Delegaty otrzymywały <xref:System.Windows.Forms.Control.Paint> zdarzenie. Jednak kontrolki, które malują całą powierzchnię nie należy wywoływać klasy <xref:System.Windows.Forms.Control.OnPaint%2A>bazowej, ponieważ wprowadzają migotanie. Przykład zastępowania <xref:System.Windows.Forms.Control.OnPaint%2A> zdarzenia można znaleźć w [temacie How to: Utwórz formant Windows Forms, który pokazuje postęp](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
> [!NOTE]
> Nie wywołuj <xref:System.Windows.Forms.Control.OnPaint%2A> bezpośrednio z formantu; zamiast tego <xref:System.Windows.Forms.Control.Invalidate%2A> Wywołaj metodę (Odziedziczone z <xref:System.Windows.Forms.Control>) lub inną metodę, która wywołuje <xref:System.Windows.Forms.Control.Invalidate%2A>. Metoda z kolei wywołuje <xref:System.Windows.Forms.Control.OnPaint%2A>metodę. <xref:System.Windows.Forms.Control.Invalidate%2A> Metoda jest przeciążona i, w zależności od argumentów dostarczonych do <xref:System.Windows.Forms.Control.Invalidate%2A> `e`, formant ponownie rysuje część lub cały jego obszar ekranu. <xref:System.Windows.Forms.Control.Invalidate%2A>  
  
 Klasa bazowa <xref:System.Windows.Forms.Control> definiuje inną metodę, która jest przydatna do rysowania <xref:System.Windows.Forms.Control.OnPaintBackground%2A> — Metoda.  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A>maluje tło (a tym samym kształt) okna i gwarantuje szybkie przewinięcie szczegółów i może być wolniejsze, <xref:System.Windows.Forms.Control.OnPaint%2A> ponieważ poszczególne żądania programu Paint są łączone w jedno <xref:System.Windows.Forms.Control.Paint> zdarzenie, które obejmuje wszystkie obszary, które muszą być narysowany ponownie. Możesz chcieć wywołać <xref:System.Windows.Forms.Control.OnPaintBackground%2A> polecenie IF, na przykład, aby narysować kolorowe tło dla kontrolki.  
  
 Chociaż <xref:System.Windows.Forms.Control.OnPaintBackground%2A> ma nomenklaturę przypominającą zdarzenia i przyjmuje ten sam argument `OnPaint` co metoda, <xref:System.Windows.Forms.Control.OnPaintBackground%2A> nie jest to prawdziwa Metoda zdarzenia. Nie ma <xref:System.Windows.Forms.Control.OnPaintBackground%2A> zdarzenia i nie wywołuje delegatów zdarzeń. `PaintBackground` Podczas zastępowania <xref:System.Windows.Forms.Control.OnPaintBackground%2A> metody Klasa pochodna nie jest wymagana do <xref:System.Windows.Forms.Control.OnPaintBackground%2A> wywołania metody jej klasy bazowej.  
  
## <a name="gdi-basics"></a>Podstawowe informacje o GDI+  
 <xref:System.Drawing.Graphics> Klasa udostępnia metody rysowania różnych kształtów, takich jak koła, Trójkąty, łuki i elipsy, a także metody wyświetlania tekstu. <xref:System.Drawing?displayProperty=nameWithType> Przestrzeń nazw i jej podobszar nazw zawierają klasy, które hermetyzują elementy graficzne, takie jak kształty (okręgi, prostokąty, łuki i inne), kolory, czcionki, pędzle i tak dalej. Aby uzyskać więcej informacji na temat interfejsu GDI, zobacz [Używanie zarządzanych klas graficznych](../advanced/using-managed-graphics-classes.md). Podstawowe [informacje o usłudze GDI są również opisane w temacie How to: Utwórz formant Windows Forms, który pokazuje postęp](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="geometry-of-the-drawing-region"></a>Geometria regionu rysowania  
 Właściwość kontrolki określa prostokątny region dostępny dla formantu na ekranie użytkownika, <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> podczas gdy właściwość <xref:System.Windows.Forms.PaintEventArgs> określa obszar, który jest rzeczywiście malowany. <xref:System.Windows.Forms.Control.ClientRectangle%2A> (Należy pamiętać, że malowanie jest <xref:System.Windows.Forms.Control.Paint> wykonywane w metodzie zdarzenia <xref:System.Windows.Forms.PaintEventArgs> , która przyjmuje wystąpienie jako argument). Kontrolka może być konieczna do malowania tylko częścią dostępnego obszaru, tak jak w przypadku, gdy mała sekcja ekranu kontrolki jest zmieniana. W takich sytuacjach deweloper kontroli musi obliczyć rzeczywisty prostokąt, aby narysować i przekazać do <xref:System.Windows.Forms.Control.Invalidate%2A>. <xref:System.Windows.Forms.Control.Invalidate%2A> Przeciążone wersje <xref:System.Windows.Forms.PaintEventArgs>, które <xref:System.Drawing.Rectangle> przyjmują lub <xref:System.Drawing.Region> jako argument używają tego argumentu do generowania <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> właściwości.  
  
 Poniższy fragment kodu przedstawia sposób, `FlashTrackBar` w jaki formant niestandardowy oblicza prostokątny obszar do rysowania. `client` Zmienna oznacza<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> właściwość. Pełny przykład można znaleźć w temacie [How to: Utwórz formant Windows Forms, który pokazuje postęp](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>Zwalnianie zasobów graficznych  
 Obiekty graficzne są kosztowne, ponieważ korzystają z zasobów systemowych. Takie obiekty obejmują wystąpienia <xref:System.Drawing.Graphics?displayProperty=nameWithType> klasy, a także <xref:System.Drawing.Brush?displayProperty=nameWithType>wystąpienia, <xref:System.Drawing.Pen?displayProperty=nameWithType>i innych klas graficznych. Ważne jest, aby utworzyć zasób grafiki tylko wtedy, gdy jest potrzebny, i wydać go wkrótce po zakończeniu korzystania z niego. Jeśli tworzysz typ, który implementuje <xref:System.IDisposable> interfejs, wywołaj jego <xref:System.IDisposable.Dispose%2A> metodę po zakończeniu pracy z nim w celu zwolnienia zasobów.  
  
 Poniższy fragment kodu przedstawia sposób, w `FlashTrackBar` jaki formant niestandardowy tworzy i <xref:System.Drawing.Brush> zwalnia zasób. Aby uzyskać pełny kod źródłowy, zobacz [How to: Utwórz formant Windows Forms, który pokazuje postęp](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie kontrolki Windows Forms, która pokazuje postęp](how-to-create-a-windows-forms-control-that-shows-progress.md)
