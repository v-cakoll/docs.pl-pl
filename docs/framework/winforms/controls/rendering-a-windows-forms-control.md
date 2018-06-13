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
ms.openlocfilehash: a2d7a02e725e3f8065b80a6b30ea21158be43ea8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541391"
---
# <a name="rendering-a-windows-forms-control"></a>Renderowanie formantu formularzy systemu Windows
Renderowanie odwołuje się do procesu tworzenia wizualną reprezentację na ekranie użytkownika. Formularze systemu Windows używa [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] (nowej bibliotece systemu Windows grafiki) do renderowania. Klasy zarządzane, które zapewniają dostęp do [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] w <xref:System.Drawing?displayProperty=nameWithType> przestrzeni nazw i jego podobszary nazw.  
  
 W przypadku renderowania formantu obejmuje następujące elementy:  
  
-   Rysowanie funkcje udostępniane przez klasę podstawową <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
-   Istotne elementy [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] bibliotekę grafiki.  
  
-   Geometria obszaru rysowania.  
  
-   Procedurę zwalnianie zasobów graficznych.  
  
## <a name="drawing-functionality-provided-by-control"></a>Rysowanie funkcje udostępniane przez formant  
 Klasa podstawowa <xref:System.Windows.Forms.Control> rysowania funkcje za pośrednictwem jego <xref:System.Windows.Forms.Control.Paint> zdarzeń. Formant zgłasza <xref:System.Windows.Forms.Control.Paint> zdarzenia przy każdym musi zaktualizować jej wyświetlania. Aby uzyskać więcej informacji o zdarzeniach w programie .NET Framework, zobacz [Obsługa i wywoływanie zdarzeń](../../../../docs/standard/events/index.md).  
  
 Dane zdarzenia klasy dla <xref:System.Windows.Forms.Control.Paint> zdarzenia <xref:System.Windows.Forms.PaintEventArgs>, przechowuje dane potrzebne do rysowania formantu — dojścia do obiektu graphics i obiekt prostokąt, który reprezentuje obszar do rysowania. Te obiekty są wyświetlane w pogrubioną następującego fragmentu kodu.  
  
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
  
 <xref:System.Drawing.Graphics> jest zarządzanej klasy, który hermetyzuje funkcjonalność rysowania, zgodnie z opisem w dyskusji [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] dalszej części tego tematu. <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> Jest wystąpieniem <xref:System.Drawing.Rectangle> struktury i definiuje dostępnego obszaru, w którym można narysować kontrolkę. Można obliczyć dewelopera kontrolek <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> przy użyciu <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> właściwości formantu, zgodnie z opisem w omówieniu geometrii w dalszej części tego tematu.  
  
 Formant musi dostarczyć logiki renderowania przez zastąpienie <xref:System.Windows.Forms.Control.OnPaint%2A> metodę, która dziedziczy on z <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control.OnPaint%2A> uzyskuje dostęp do obiektu graphics i prostokąta do rysowania za pomocą <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> i <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> właściwości <xref:System.Windows.Forms.PaintEventArgs> wystąpienia przekazane do niej.  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A> Metody podstawowej <xref:System.Windows.Forms.Control> klasa nie implementuje żadnych funkcji rysowania, ale tylko wywołuje obiektów delegowanych zdarzeń, które są zarejestrowane w usłudze <xref:System.Windows.Forms.Control.Paint> zdarzeń. Jeśli zastąpienie <xref:System.Windows.Forms.Control.OnPaint%2A>, zazwyczaj należy wywołać <xref:System.Windows.Forms.Control.OnPaint%2A> odbierania metody klasy podstawowej, która zarejestrowana delegatów <xref:System.Windows.Forms.Control.Paint> zdarzeń. Jednak formantów, które ich całej powierzchni rysowania nie należy wywołać klasy podstawowej <xref:System.Windows.Forms.Control.OnPaint%2A>, jak to przedstawiono migotania. Przykład zastępowanie <xref:System.Windows.Forms.Control.OnPaint%2A> zdarzeń, zobacz [porady: tworzenie systemu Windows Forms kontroli czy pokazuje postępu](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
> [!NOTE]
>  Nie wywołuj <xref:System.Windows.Forms.Control.OnPaint%2A> bezpośrednio z formantu; zamiast tego wywołać <xref:System.Windows.Forms.Control.Invalidate%2A> — metoda (dziedziczone z <xref:System.Windows.Forms.Control>) lub innej metody, która wywołuje <xref:System.Windows.Forms.Control.Invalidate%2A>. <xref:System.Windows.Forms.Control.Invalidate%2A> Metoda z kolei wywołuje <xref:System.Windows.Forms.Control.OnPaint%2A>. <xref:System.Windows.Forms.Control.Invalidate%2A> Metody jest przeciążona i, w zależności od argumentów dostarczony do <xref:System.Windows.Forms.Control.Invalidate%2A> `e`, formantu ponownie rysuje niektórych lub wszystkich jego obszar ekranu.  
  
 Podstawowym <xref:System.Windows.Forms.Control> klasa definiuje innej metody, które są przydatne do rysowania — <xref:System.Windows.Forms.Control.OnPaintBackground%2A> metody.  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> Umożliwia malowanie tła (i tym samym kształtu) okna i gwarantuje to szybkie podczas <xref:System.Windows.Forms.Control.OnPaint%2A> malowanie szczegóły i może przebiegać wolniej, ponieważ paint poszczególnych żądań są połączone w jedną <xref:System.Windows.Forms.Control.Paint> zdarzenie, które obejmuje wszystkie obszary, które muszą być narysowany ponownie. Należy wywołać <xref:System.Windows.Forms.Control.OnPaintBackground%2A> Jeśli na przykład chcesz narysować kolorze gradientu tła formantu.  
  
 Podczas <xref:System.Windows.Forms.Control.OnPaintBackground%2A> ma nomenklaturę zdarzenia podobne i ma ten sam argument co `OnPaint` metody <xref:System.Windows.Forms.Control.OnPaintBackground%2A> nie jest metodą zdarzeń wartość true. Brak nie `PaintBackground` zdarzeń i <xref:System.Windows.Forms.Control.OnPaintBackground%2A> nie wywoła zdarzeń delegatów. W przypadku przesłaniania <xref:System.Windows.Forms.Control.OnPaintBackground%2A> — metoda, klasa pochodna nie jest wymagana do wywołania <xref:System.Windows.Forms.Control.OnPaintBackground%2A> metody klasy podstawowej.  
  
## <a name="gdi-basics"></a>Podstawowe informacje dotyczące interfejsu GDI +  
 <xref:System.Drawing.Graphics> Klasa zawiera metody służące do rysowania różnych kształtów, np. okręgi, trójkąty łuki i wielokropek, a także metod do wyświetlania tekstu. <xref:System.Drawing?displayProperty=nameWithType> Przestrzeni nazw i jego podobszary nazw zawiera klasy, które hermetyzują elementów graficznych, takich jak kształtów (okręgi, prostokąty, łuki i inne), kolory, czcionki, pędzle i tak dalej. Aby uzyskać więcej informacji na temat [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], zobacz [za pomocą zarządzanych klas grafiki](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md). Podstawowe informacje o [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] są także opisane w [porady: tworzenie systemu Windows Forms kontroli czy pokazuje postępu](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="geometry-of-the-drawing-region"></a>Geometria regionie rysowania  
 <xref:System.Windows.Forms.Control.ClientRectangle%2A> Właściwości formantu określa prostokątny obszar dostępne do kontroli na ekranie użytkownika, gdy <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> właściwość <xref:System.Windows.Forms.PaintEventArgs> określa obszaru faktycznie jest rysowane. (Należy pamiętać, że malowanie odbywa się <xref:System.Windows.Forms.Control.Paint> metoda zdarzenia, który pobiera <xref:System.Windows.Forms.PaintEventArgs> wystąpienia jako jej argument). Formant może być konieczne malowanie tylko części obszaru dostępne, tak jak w przypadku gdy małych sekcji zmiany wyświetlania formantu. W takiej sytuacji dewelopera kontrolek obliczyć rzeczywiste prostokąta do rysowania i że w celu przekazania <xref:System.Windows.Forms.Control.Invalidate%2A>. Przeciążone wersje <xref:System.Windows.Forms.Control.Invalidate%2A> które trwają <xref:System.Drawing.Rectangle> lub <xref:System.Drawing.Region> jako argument, użyj tego argumentu można wygenerować <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> właściwość <xref:System.Windows.Forms.PaintEventArgs>.  
  
 Następujący kod fragmentu pokazuje sposób `FlashTrackBar` prostokątny obszar do rysowania oblicza kontrolki niestandardowej. `client` Zmienna oznacza <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> właściwości. Dla kompletnego przykładu, zobacz [porady: tworzenie systemu Windows Forms kontroli czy pokazuje postępu](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>Zwalnianie zasobów graficznych  
 Obiektów graficznych są kosztowne, ponieważ jest używany przez zasoby systemowe. Takie obiekty obejmują wystąpienia <xref:System.Drawing.Graphics?displayProperty=nameWithType> klasy, a także wystąpień <xref:System.Drawing.Brush?displayProperty=nameWithType>, <xref:System.Drawing.Pen?displayProperty=nameWithType>i innych klas grafiki. Należy utworzyć zasobów grafiki, tylko wtedy, gdy potrzebny i zwolnij go wkrótce zakończeniu korzystania z niego. W przypadku utworzenia typu, który implementuje <xref:System.IDisposable> interfejsu, należy wywołać jej <xref:System.IDisposable.Dispose%2A> metody po zakończeniu z nim w celu zwolnienia zasobów.  
  
 Poniższy kod fragmentu pokazuje sposób `FlashTrackBar` kontrolki niestandardowej tworzy i zwalnia <xref:System.Drawing.Brush> zasobów. Kodu źródłowego pełną, zobacz [jak: utworzyć Windows formularze kontroli czy pokazuje postępu](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: tworzenie kontrolki formularzy Windows Forms pokazującej postęp](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)
