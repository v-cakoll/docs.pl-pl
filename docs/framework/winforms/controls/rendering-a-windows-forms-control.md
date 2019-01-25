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
ms.openlocfilehash: 9d2cb5041fbceb2e5c2d35d37a2001deffab40d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659374"
---
# <a name="rendering-a-windows-forms-control"></a>Renderowanie formantu formularzy systemu Windows
Renderowanie odnosi się do procesu tworzenia wizualnej reprezentacji na ekranie użytkownika. Formularze Windows używa [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] (nowe Windows biblioteki graficznej) do renderowania. Klasy zarządzane, które zapewniają dostęp do [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] znajdują się w <xref:System.Drawing?displayProperty=nameWithType> przestrzeni nazw i jego podobszary nazw.  
  
 Renderowanie kontrolki obejmuje następujące elementy:  
  
-   Rysowanie funkcje zapewniane przez klasę bazową <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
-   Istotne elementy [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] biblioteki funkcji graficznych.  
  
-   Geometria obszaru rysowania.  
  
-   Procedura zwalnianie zasobów graficznych.  
  
## <a name="drawing-functionality-provided-by-control"></a>Rysowanie funkcje udostępniane przez kontrolkę  
 Klasa bazowa <xref:System.Windows.Forms.Control> udostępnia funkcje rysowania za pośrednictwem jego <xref:System.Windows.Forms.Control.Paint> zdarzeń. Kontrolki wywołuje <xref:System.Windows.Forms.Control.Paint> zdarzenie zawsze wtedy, gdy trzeba ją zaktualizować jego wyświetlania. Aby uzyskać więcej informacji o zdarzeniach w .NET Framework, zobacz [Handling and Raising Events](../../../../docs/standard/events/index.md).  
  
 Dane zdarzenia klasy dla <xref:System.Windows.Forms.Control.Paint> zdarzenia <xref:System.Windows.Forms.PaintEventArgs>, przechowuje dane potrzebne do rysowania kontrolki — dojścia do obiektu grafiki i obiekt prostokąt, który reprezentuje region, aby narysować w. Te obiekty są wyświetlane w pogrubieniem w poniższy fragment kodu.  
  
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
  
 <xref:System.Drawing.Graphics> jest zarządzane klasa, która hermetyzuje funkcjonalność rysowania, zgodnie z opisem w dyskusji nad [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] w dalszej części tego tematu. <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> Jest wystąpieniem <xref:System.Drawing.Rectangle> struktury i definiuje dostępne obszaru, w którym można narysować kontrolkę. Można obliczyć dewelopera kontrolek <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> przy użyciu <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> właściwość kontrolki, zgodnie z opisem w dyskusji geometrii w dalszej części tego tematu.  
  
 Kontrolki musisz podać logiki renderowania przez zastąpienie <xref:System.Windows.Forms.Control.OnPaint%2A> metodę, która dziedziczy <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control.OnPaint%2A> uzyskuje dostęp do obiektów grafiki i prostokąt można narysować w za pośrednictwem <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> i <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> właściwości <xref:System.Windows.Forms.PaintEventArgs> wystąpienia przekazane do niego.  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A> Metody podstawowej <xref:System.Windows.Forms.Control> klasa nie implementuje żadnych funkcji rysowania, ale jedynie wywołuje delegatów zdarzeń, które są zarejestrowane w usłudze <xref:System.Windows.Forms.Control.Paint> zdarzeń. Gdy zastąpisz <xref:System.Windows.Forms.Control.OnPaint%2A>, zazwyczaj należy wywołać <xref:System.Windows.Forms.Control.OnPaint%2A> otrzymywać metody klasy bazowej, która jest zarejestrowana delegatów <xref:System.Windows.Forms.Control.Paint> zdarzeń. Jednak formantów, które ich całej powierzchni rysowania nie powinien wywołać klasy bazowej <xref:System.Windows.Forms.Control.OnPaint%2A>, ponieważ wprowadza migotania. Na przykład zastępowanie <xref:System.Windows.Forms.Control.OnPaint%2A> zdarzeń, zobacz [jak: Utwórz formant programu Windows Forms pokazującej postęp](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
> [!NOTE]
>  Nie wywołać <xref:System.Windows.Forms.Control.OnPaint%2A> bezpośrednio z kontroli nad; zamiast tego należy wywołać <xref:System.Windows.Forms.Control.Invalidate%2A> — metoda (odziedziczone <xref:System.Windows.Forms.Control>) lub innej metody, która wywołuje <xref:System.Windows.Forms.Control.Invalidate%2A>. <xref:System.Windows.Forms.Control.Invalidate%2A> Metoda z kolei wywołuje <xref:System.Windows.Forms.Control.OnPaint%2A>. <xref:System.Windows.Forms.Control.Invalidate%2A> Jest przeciążona metoda i, w zależności od argumentów przekazana do <xref:System.Windows.Forms.Control.Invalidate%2A> `e`, formant odrysowuje niektóre lub wszystkie z jej obszaru ekranu.  
  
 Podstawa <xref:System.Windows.Forms.Control> klasa definiuje innej metody, które są przydatne do rysowania — <xref:System.Windows.Forms.Control.OnPaintBackground%2A> metody.  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> Malowanie tła (i tym samym kształt) okna i gwarantuje szybkiego działania, podczas <xref:System.Windows.Forms.Control.OnPaint%2A> malowanie szczegółowe informacje i może być wolniejsze, ponieważ paint poszczególnych żądań są połączone w jedną <xref:System.Windows.Forms.Control.Paint> zdarzenia, które obejmuje wszystkie obszary, które muszą być narysowany ponownie. Należy wywołać <xref:System.Windows.Forms.Control.OnPaintBackground%2A> Jeśli na przykład chcemy narysować gradientów tła kontrolki.  
  
 Gdy <xref:System.Windows.Forms.Control.OnPaintBackground%2A> ma nomenklaturę zdarzenia podobne i ma ten sam argument co `OnPaint` metody <xref:System.Windows.Forms.Control.OnPaintBackground%2A> nie jest metodą true zdarzeń. Istnieje nie `PaintBackground` zdarzeń i <xref:System.Windows.Forms.Control.OnPaintBackground%2A> nie wywoła delegatów zdarzeń. Podczas zastępowania <xref:System.Windows.Forms.Control.OnPaintBackground%2A> metody, klasy pochodnej nie jest wymagane do wywołania <xref:System.Windows.Forms.Control.OnPaintBackground%2A> metody klasy bazowej.  
  
## <a name="gdi-basics"></a>Podstawy interfejsu GDI +  
 <xref:System.Drawing.Graphics> Klasa zawiera metody służące do rysowania różnych kształtów, np. okręgi, trójkąty, łuki i wielokropek, a także metody do wyświetlania tekstu. <xref:System.Drawing?displayProperty=nameWithType> Przestrzeni nazw i jego podobszary nazw zawierają klasy, które hermetyzują elementów graficznych, takich jak kształty (okręgów, prostokąty, łuki i inne), kolory, czcionki, pędzli i tak dalej. Aby uzyskać więcej informacji na temat [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], zobacz [używanie zarządzanych klas grafiki](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md). Podstawowe informacje o [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] są także opisane w [jak: Utwórz formant programu Windows Forms pokazującej postęp](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="geometry-of-the-drawing-region"></a>Geometria obszaru rysowania  
 <xref:System.Windows.Forms.Control.ClientRectangle%2A> Właściwości formantu określa prostokątny obszar, dostępna dla kontrolki na ekranie użytkownika, gdy <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> właściwość <xref:System.Windows.Forms.PaintEventArgs> określa obszar, który faktycznie jest malowane. (Należy pamiętać, że malowanie odbywa się w <xref:System.Windows.Forms.Control.Paint> metody zdarzeń, która przyjmuje <xref:System.Windows.Forms.PaintEventArgs> wystąpienie jako argument). Formant może być konieczne malowanie tylko część jej dostępnych obszarów tak jak w przypadku gdy niewielki fragment zmiany wyświetlania kontrolki. W takiej sytuacji dewelopera kontrolek obliczyć rzeczywiste prostokąt można narysować w i przekazać go do <xref:System.Windows.Forms.Control.Invalidate%2A>. Przeciążone wersje <xref:System.Windows.Forms.Control.Invalidate%2A> o <xref:System.Drawing.Rectangle> lub <xref:System.Drawing.Region> jako argument Użyj tego argumentu, aby wygenerować <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> właściwość <xref:System.Windows.Forms.PaintEventArgs>.  
  
 Poniższy kod fragment przedstawia sposób, w jaki `FlashTrackBar` kontrolki niestandardowej oblicza prostokątny obszar, aby narysować w. `client` Wskazuje zmienną <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> właściwości. Aby uzyskać pełny przykład, zobacz [jak: Utwórz formant programu Windows Forms pokazującej postęp](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>Zwalnianie zasobów graficznych  
 Obiekty graficzne są kosztowne, ponieważ używają zasobów systemowych. Takie obiekty zawierają wystąpień <xref:System.Drawing.Graphics?displayProperty=nameWithType> klasy, a także wystąpienia <xref:System.Drawing.Brush?displayProperty=nameWithType>, <xref:System.Drawing.Pen?displayProperty=nameWithType>i innych klas grafiki. Jest ważne, utwórz zasób grafiki, tylko wtedy, gdy go potrzebujesz i zwolnij go szybko po zakończeniu, korzystania z niego. W przypadku utworzenia typu, który implementuje <xref:System.IDisposable> interfejsu, wywołać jej <xref:System.IDisposable.Dispose%2A> metoda po zakończeniu z nim w celu zwolnienie zasobów.  
  
 Poniższy kod fragment przedstawia sposób, w jaki `FlashTrackBar` formant niestandardowy, tworzy i zwalnia <xref:System.Drawing.Brush> zasobów. Aby uzyskać pełnego kodu źródłowego, zobacz [jak: Utwórz formant programu Windows Forms pokazującej postęp](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Utwórz formant programu Windows Forms pokazującej postęp](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)
