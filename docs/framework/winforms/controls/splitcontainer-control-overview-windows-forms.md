---
title: "SplitContainer — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SplitContainer
helpviewer_keywords: SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d2e538241cca8288158628df777895fae9aa756
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="splitcontainer-control-overview-windows-forms"></a>SplitContainer — Informacje o formancie [Formularze systemu Windows]
Formularze systemu Windows <xref:System.Windows.Forms.SplitContainer> formantu można traktować jako projekt wstępny; jest dwa panele oddzielone ruchomy paska. Gdy wskaźnik myszy znajduje się nad paskiem, kursor zmienia kształt pokazują, że pasek jest ruchomy.  
  
> [!IMPORTANT]
>  W **przybornika**, <xref:System.Windows.Forms.SplitContainer> kontrolować zastępuje <xref:System.Windows.Forms.Splitter> formant, który był w poprzedniej wersji [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]. <xref:System.Windows.Forms.SplitContainer> Formant jest znacznie preferowany nad <xref:System.Windows.Forms.Splitter> formantu. <xref:System.Windows.Forms.Splitter> Klasy jest dostępny w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dla zgodności z istniejącymi aplikacjami, ale zdecydowanie zalecamy używania <xref:System.Windows.Forms.SplitContainer> kontroli dla nowych projektów.  
  
 Z <xref:System.Windows.Forms.SplitContainer> formantu, mogą tworzyć interfejsy użytkownika złożonych; często zaznaczenia w jednym panelu Określa, jakie obiekty są wyświetlane w panelu. To rozmieszczenie jest bardzo efektywnym sposobem wyświetlania oraz informacji o przeglądaniu. Pozwala na dwa panele o agregacji informacji w obszarach i paska lub "podziału," ułatwia użytkownikom zmienianie rozmiaru paneli.  
  
 Więcej niż jeden <xref:System.Windows.Forms.SplitContainer> kontroli mogą być zagnieżdżone, drugi <xref:System.Windows.Forms.SplitContainer> kontroli orientacji poziomej, aby utworzyć górny i dolny paneli.  
  
 Należy pamiętać, że <xref:System.Windows.Forms.SplitContainer> kontroli jest klawiatury dostępny domyślnie; użytkowników można nacisnąć klawisze strzałek, aby przenieść rozdzielacza, jeśli <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> właściwość jest ustawiona na `false`.  
  
 <xref:System.Windows.Forms.SplitContainer.Orientation%2A> Właściwość <xref:System.Windows.Forms.SplitContainer> kontroli określa kierunek rozdzielacza, a nie samego formantu. W związku z tym, jeśli ta właściwość jest równa <xref:System.Windows.Forms.Orientation.Vertical>, rozdzielacz jest uruchamiany od góry do dołu, tworzenie lewy i prawy paneli.  
  
 Ponadto należy pamiętać, że wartość <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> właściwość może być różna w zależności od wartości <xref:System.Windows.Forms.SplitContainer.Orientation%2A> właściwości. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> właściwości.  
  
 Można również ograniczyć rozmiar i przepływu <xref:System.Windows.Forms.SplitContainer> formantu. <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> Właściwość określa, który panel pozostaje taki sam rozmiar po <xref:System.Windows.Forms.SplitContainer> zostanie zmieniony rozmiar formantu i <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> właściwość określa, czy rozdzielacz jest ruchomy klawiatury lub myszy.  
  
> [!NOTE]
>  Nawet jeśli <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> właściwość jest ustawiona na `true`, rozdzielacza nadal może przenieść programowo, na przykład za pomocą <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> właściwości.  
  
 Na koniec każdego panelu <xref:System.Windows.Forms.SplitContainer> formant ma właściwości, aby określić rozmiar poszczególnych.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Typowe właściwości, metod i zdarzeń  
  
|Nazwa|Opis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.FixedPanel%2A>Właściwość|Określa, który panel pozostaje taki sam rozmiar po <xref:System.Windows.Forms.SplitContainer> zostanie zmieniony rozmiar formantu.|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>Właściwość|Określa, czy rozdzielacz można przenosić z klawiatury lub myszy.|  
|<xref:System.Windows.Forms.SplitContainer.Orientation%2A>Właściwość|Określa, czy rozdzielacz jest rozmieszczona pionie lub poziomie.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>Właściwość|Określa odległość w pikselach pasek podziału ruchomy od lewej lub górnej krawędzi.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>Właściwość|Określa minimalny odstęp w pikselach, że rozdzielacza mogą być przenoszone przez użytkownika.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A>Właściwość|Określa szerokość, w pikselach rozdzielacza.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoving>zdarzenia|Występuje, gdy rozdzielacz jest przenoszenie.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoved>zdarzenia|Występuje, gdy rozdzielacz został przeniesiony.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.SplitContainer>  
 [SplitContainer, kontrolka](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)  
 [Przykładowe SplitContainer — formant](http://msdn.microsoft.com/library/9015fad0-7108-4d85-a83a-a72d038c4f65)
