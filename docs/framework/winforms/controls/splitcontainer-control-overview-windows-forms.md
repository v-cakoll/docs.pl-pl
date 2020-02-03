---
title: SplitContainer — Informacje o formancie
ms.date: 03/30/2017
f1_keywords:
- SplitContainer
helpviewer_keywords:
- SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
ms.openlocfilehash: 5cb5240ed4ebe3e27c20844681068711c222e9a9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742925"
---
# <a name="splitcontainer-control-overview-windows-forms"></a>SplitContainer — Informacje o formancie [Formularze systemu Windows]
Formant Windows Forms <xref:System.Windows.Forms.SplitContainer> może być uważany za złożony; jest to dwa panele oddzielone przez ruchomy pasek. Gdy wskaźnik myszy znajduje się nad paskiem, wskaźnik zmieni kształt, aby pokazać, że pasek jest przenośny.  
  
> [!IMPORTANT]
> W **przyborniku**<xref:System.Windows.Forms.SplitContainer> formant zastępuje formant <xref:System.Windows.Forms.Splitter>, który znajdował się w poprzedniej wersji programu Visual Studio. Formant <xref:System.Windows.Forms.SplitContainer> jest dużo preferowany nad formantem <xref:System.Windows.Forms.Splitter>. Klasa <xref:System.Windows.Forms.Splitter> nadal jest dołączona do .NET Framework w celu zapewnienia zgodności z istniejącymi aplikacjami, ale zdecydowanie zachęcamy do używania kontrolki <xref:System.Windows.Forms.SplitContainer> dla nowych projektów.  
  
 Za pomocą kontrolki <xref:System.Windows.Forms.SplitContainer> można tworzyć złożone interfejsy użytkownika. często wybór w jednym panelu określa, jakie obiekty są wyświetlane w drugim panelu. To rozwiązanie jest bardzo skuteczne do wyświetlania i przeglądania informacji. Posiadanie dwóch paneli pozwala na agregowanie informacji w obszarach, a pasek lub "rozdzielacz" ułatwia użytkownikom zmianę rozmiaru paneli.  
  
 Więcej niż jeden formant <xref:System.Windows.Forms.SplitContainer> może być również zagnieżdżony, a druga kontrolka <xref:System.Windows.Forms.SplitContainer> w poziomie, aby utworzyć panele górne i dolne.  
  
 Należy pamiętać, że formant <xref:System.Windows.Forms.SplitContainer> jest domyślnie dostępny dla klawiatury; Użytkownicy mogą nacisnąć klawisze strzałek, aby przenieść rozdzielacz, jeśli właściwość <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> jest ustawiona na `false`.  
  
 Właściwość <xref:System.Windows.Forms.SplitContainer.Orientation%2A> kontrolki <xref:System.Windows.Forms.SplitContainer> określa kierunek rozdzielacza, a nie sam formant. W związku z tym, gdy ta właściwość jest ustawiona na <xref:System.Windows.Forms.Orientation.Vertical>, rozdzielacz jest uruchamiany z góry do dołu, tworząc lewe i prawe panele.  
  
 Ponadto należy pamiętać, że wartość właściwości <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> różni się w zależności od wartości właściwości <xref:System.Windows.Forms.SplitContainer.Orientation%2A>. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> właściwość.  
  
 Możesz również ograniczyć rozmiar i przenoszenie kontrolki <xref:System.Windows.Forms.SplitContainer>. Właściwość <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> określa, który panel pozostanie o takim samym rozmiarze po zmianie rozmiaru kontrolki <xref:System.Windows.Forms.SplitContainer>, a właściwość <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> określa, czy rozdzielacz jest Movable przez klawiaturę, czy mysz.  
  
> [!NOTE]
> Nawet jeśli właściwość <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> jest ustawiona na `true`, rozdzielacz może być nadal przenoszony programowo; na przykład za pomocą właściwości <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>.  
  
 Na koniec każdy panel kontrolki <xref:System.Windows.Forms.SplitContainer> ma właściwości, aby określić jego rozmiar indywidualny.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Najczęściej używane właściwości, metody i zdarzenia  
  
|Nazwa|Opis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> Właściwość|Określa, który panel będzie mieć ten sam rozmiar po zmianie rozmiaru kontrolki <xref:System.Windows.Forms.SplitContainer>.|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> Właściwość|Określa, czy rozdzielacz można przenieść za pomocą klawiatury lub myszy.|  
|<xref:System.Windows.Forms.SplitContainer.Orientation%2A> Właściwość|Określa, czy rozdzielacz jest ułożony pionowo czy poziomo.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> Właściwość|Określa odległość (w pikselach) od lewej lub górnej krawędzi do ruchomego paska rozdzielacza.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> Właściwość|Określa minimalną odległość (w pikselach), którą można przenieść rozdzielacza przez użytkownika.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A> Właściwość|Określa grubość (w pikselach) rozdzielacza.|  
|zdarzenie <xref:System.Windows.Forms.SplitContainer.SplitterMoving>|Występuje po przeniesieniu rozdzielacza.|  
|zdarzenie <xref:System.Windows.Forms.SplitContainer.SplitterMoved>|Występuje po przeniesieniu rozdzielacza.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer, kontrolka](splitcontainer-control-windows-forms.md)
- [Przykład kontrolki SplitContainer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/0ffz7d1b(v=vs.90))
