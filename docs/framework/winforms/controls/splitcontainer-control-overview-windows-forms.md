---
title: SplitContainer — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- SplitContainer
helpviewer_keywords:
- SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
ms.openlocfilehash: 4afdd764b2f6ef7f15e8bd26459f0fa4c7d345e1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971993"
---
# <a name="splitcontainer-control-overview-windows-forms"></a>SplitContainer — Informacje o formancie [Formularze systemu Windows]
Formularze Windows <xref:System.Windows.Forms.SplitContainer> kontrolki mogą być uważane za złożonego, a dwa panele rozdzielone ruchome paska. Gdy wskaźnik myszy znajduje się nad paskiem, kursor zmienia kształt, aby pokazać, że pasek jest ruchomy.  
  
> [!IMPORTANT]
>  W **przybornika**, <xref:System.Windows.Forms.SplitContainer> kontrolować zastępuje <xref:System.Windows.Forms.Splitter> formant, który był w poprzedniej wersji programu Visual Studio. <xref:System.Windows.Forms.SplitContainer> Formant jest znacznie preferowany nad <xref:System.Windows.Forms.Splitter> kontroli. <xref:System.Windows.Forms.Splitter> Klasy nadal znajduje się w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] potrzeby utrzymywania zgodności z istniejącymi aplikacjami, ale zdecydowanie zachęcamy do użycia <xref:System.Windows.Forms.SplitContainer> kontroli dla nowych projektów.  
  
 Za pomocą <xref:System.Windows.Forms.SplitContainer> formantu, mogą tworzyć interfejsy użytkownika złożonych; często wybór w jeden panel Określa, jakie obiekty są wyświetlane w innych panelu. Taki układ jest bardzo skuteczny sposób na wyświetlanie i informacji o przeglądaniu. Istnienie dwa panele pozwala agregować informacje zawarte w obszarach i słupka lub "podziału," ułatwia użytkownikom zmieniać rozmiar paneli.  
  
 Więcej niż jeden <xref:System.Windows.Forms.SplitContainer> kontrolki mogą być zagnieżdżone, drugi <xref:System.Windows.Forms.SplitContainer> kontroli zorientowanej na poziomie, do utworzenia górny i dolny paneli.  
  
 Należy pamiętać, że <xref:System.Windows.Forms.SplitContainer> kontroli dostępnej klawiatury — domyślne; użytkownicy, można nacisnąć klawisze strzałek, aby przenieść rozdzielacza, jeśli <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> właściwość jest ustawiona na `false`.  
  
 <xref:System.Windows.Forms.SplitContainer.Orientation%2A> Właściwość <xref:System.Windows.Forms.SplitContainer> kontroli określa kierunek rozdzielacza, a nie sam formant. Dzięki temu, jeśli ta właściwość jest równa <xref:System.Windows.Forms.Orientation.Vertical>, rozdzielacza działa od góry do dołu, tworząc panele po lewej i prawej stronie.  
  
 Ponadto należy pamiętać, że wartość <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> właściwość różni się w zależności od wartości <xref:System.Windows.Forms.SplitContainer.Orientation%2A> właściwości. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> właściwości.  
  
 Można również ograniczyć rozmiaru i przenoszenie <xref:System.Windows.Forms.SplitContainer> kontroli. <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> Właściwość określa, który panel pozostanie taki sam rozmiar po <xref:System.Windows.Forms.SplitContainer> zmieni się rozmiar kontrolki, a <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> właściwość określa, czy rozdzielacza ruchome, klawiatury i myszy.  
  
> [!NOTE]
>  Nawet wtedy, gdy <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> właściwość jest ustawiona na `true`, rozdzielacza mogą nadal być przemieszczane programowo, na przykład za pomocą <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> właściwości.  
  
 Na koniec każdego panelu <xref:System.Windows.Forms.SplitContainer> kontrolka ma właściwości w celu określenia rozmiaru poszczególnych.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Często używanych właściwości, metody i zdarzenia  
  
|Nazwa|Opis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> Właściwość|Określa, który panel pozostanie taki sam rozmiar po <xref:System.Windows.Forms.SplitContainer> zmieni się rozmiar kontrolki.|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> Właściwość|Określa, czy można przenieść rozdzielacza za pomocą klawiatury lub myszy.|  
|<xref:System.Windows.Forms.SplitContainer.Orientation%2A> Właściwość|Określa, jeśli rozdzielacz są rozmieszczone w pionie lub poziomie.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> Właściwość|Określa odległość w pikselach pasek podziału ruchome z lewej lub górnej krawędzi.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> Właściwość|Określa minimalną odległość w pikselach, że rozdzielacza mogą być przenoszone przez użytkownika.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A> Właściwość|Określa grubość, w pikselach rozdzielacza.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoving> Zdarzenia|Występuje, gdy porusza się rozdzielacza.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoved> Zdarzenia|Występuje, gdy został przeniesiony rozdzielacza.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer, kontrolka](splitcontainer-control-windows-forms.md)
- [Przykładowe SplitContainer, kontrolka](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/0ffz7d1b(v=vs.90))
