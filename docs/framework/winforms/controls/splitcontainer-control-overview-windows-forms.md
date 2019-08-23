---
title: SplitContainer — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- SplitContainer
helpviewer_keywords:
- SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
ms.openlocfilehash: 76299d9bbd2b3eac4e765dfacf579c9979721fff
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963213"
---
# <a name="splitcontainer-control-overview-windows-forms"></a>SplitContainer — Informacje o formancie [Formularze systemu Windows]
Formant Windows Forms <xref:System.Windows.Forms.SplitContainer> może być uważany za złożony; dwa panele oddzielone przez ruchomy pasek. Gdy wskaźnik myszy znajduje się nad paskiem, wskaźnik zmieni kształt, aby pokazać, że pasek jest przenośny.  
  
> [!IMPORTANT]
> W **przyborniku**, <xref:System.Windows.Forms.SplitContainer> formant zastępuje <xref:System.Windows.Forms.Splitter> formant, który znajdował się w poprzedniej wersji programu Visual Studio. Formant jest dużo preferowany <xref:System.Windows.Forms.Splitter> nad formantem. <xref:System.Windows.Forms.SplitContainer> Klasa jest nadal uwzględniona w .NET Framework w celu zapewnienia zgodności z istniejącymi aplikacjami, ale zdecydowanie zachęcamy do <xref:System.Windows.Forms.SplitContainer> używania kontrolki dla nowych projektów. <xref:System.Windows.Forms.Splitter>  
  
 Za pomocą <xref:System.Windows.Forms.SplitContainer> kontrolki można tworzyć złożone interfejsy użytkownika. często wybór w jednym panelu określa, jakie obiekty są wyświetlane w drugim panelu. To rozwiązanie jest bardzo skuteczne do wyświetlania i przeglądania informacji. Posiadanie dwóch paneli pozwala na agregowanie informacji w obszarach, a pasek lub "rozdzielacz" ułatwia użytkownikom zmianę rozmiaru paneli.  
  
 Więcej niż jeden <xref:System.Windows.Forms.SplitContainer> formant może być również zagnieżdżony z drugim <xref:System.Windows.Forms.SplitContainer> formantem zorientowanym w poziomie, aby utworzyć panele z góry i u dołu.  
  
 Należy pamiętać, że <xref:System.Windows.Forms.SplitContainer> kontrolka jest domyślnie dostępna dla klawiatury; użytkownicy mogą nacisnąć klawisze strzałek, aby przenieść rozdzielacz, <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> Jeśli właściwość jest ustawiona na `false`.  
  
 <xref:System.Windows.Forms.SplitContainer.Orientation%2A> Właściwość<xref:System.Windows.Forms.SplitContainer> kontrolki określa kierunek rozdzielacza, a nie sam formant. W związku z tym, gdy ta właściwość <xref:System.Windows.Forms.Orientation.Vertical>jest ustawiona na, rozdzielacz jest uruchamiany z góry do dołu, tworząc lewe i prawe panele.  
  
 Ponadto należy pamiętać, że wartość <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> właściwości jest różna w zależności od wartości <xref:System.Windows.Forms.SplitContainer.Orientation%2A> właściwości. Aby uzyskać więcej informacji, <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> Zobacz właściwość.  
  
 Można również ograniczyć rozmiar i przenoszenie <xref:System.Windows.Forms.SplitContainer> formantu. Właściwość określa, który panel pozostanie o takim samym rozmiarze <xref:System.Windows.Forms.SplitContainer> po <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> zmianie rozmiaru kontrolki, i Właściwość określa, czy rozdzielacz jest Movable przez klawiaturę lub mysz. <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A>  
  
> [!NOTE]
> Nawet jeśli <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> właściwość jest ustawiona na `true`, rozdzielacz może nadal zostać przesunięty programowo; na <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> przykład przy użyciu właściwości.  
  
 Na koniec każdy panel <xref:System.Windows.Forms.SplitContainer> kontrolki ma właściwości, aby określić jego rozmiar indywidualny.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Najczęściej używane właściwości, metody i zdarzenia  
  
|Nazwa|Opis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.FixedPanel%2A>wartość|Określa, który panel będzie mieć ten sam rozmiar po <xref:System.Windows.Forms.SplitContainer> zmianie rozmiaru formantu.|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>wartość|Określa, czy rozdzielacz można przenieść za pomocą klawiatury lub myszy.|  
|<xref:System.Windows.Forms.SplitContainer.Orientation%2A>wartość|Określa, czy rozdzielacz jest ułożony pionowo czy poziomo.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>wartość|Określa odległość (w pikselach) od lewej lub górnej krawędzi do ruchomego paska rozdzielacza.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>wartość|Określa minimalną odległość (w pikselach), którą można przenieść rozdzielacza przez użytkownika.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A>wartość|Określa grubość (w pikselach) rozdzielacza.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoving>wydarzen|Występuje po przeniesieniu rozdzielacza.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoved>wydarzen|Występuje po przeniesieniu rozdzielacza.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer, kontrolka](splitcontainer-control-windows-forms.md)
- [Przykład kontrolki SplitContainer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/0ffz7d1b(v=vs.90))
