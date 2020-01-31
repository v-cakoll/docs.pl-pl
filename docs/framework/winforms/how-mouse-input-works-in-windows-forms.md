---
title: Jak działa wprowadzanie za myszą
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, mouse input
- mouse [Windows Forms], input
ms.assetid: 48fc5240-75a6-44bf-9fce-6aa21b49705a
ms.openlocfilehash: 1164974e65ca1e96c0650569626ad4140baf004e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739637"
---
# <a name="how-mouse-input-works-in-windows-forms"></a>Działanie myszy w formularzach systemu Windows
Pobieranie i obsługa danych wejściowych myszy jest ważną częścią każdej aplikacji systemu Windows. Możesz obsłużyć zdarzenia myszy w celu wykonania akcji w aplikacji lub użyć informacji o lokalizacji myszy w celu przeprowadzenia testów trafień lub innych akcji. Ponadto możesz zmienić sposób, w jaki kontrolki w aplikacji obsługują dane wejściowe myszy. W tym temacie opisano szczegółowo te zdarzenia myszy oraz sposób uzyskiwania i zmieniania ustawień systemowych dla myszy. Aby uzyskać więcej informacji na temat danych dostarczonych ze zdarzeniami myszy i kolejnością, w której są wywoływane zdarzenia kliknięcia myszą, zobacz [zdarzenia myszy w Windows Forms](mouse-events-in-windows-forms.md).  
  
## <a name="mouse-location-and-hit-testing"></a>Lokalizacja myszy i testowanie trafień  
 Gdy użytkownik przesuwa mysz, system operacyjny przesuwa wskaźnik myszy. Wskaźnik myszy zawiera pojedynczy piksel, zwany gorącą plamą, którą system operacyjny śledzi i rozpoznaje jako położenie wskaźnika. Gdy użytkownik przesuwa mysz lub naciśnie przycisk myszy, <xref:System.Windows.Forms.Control>, który zawiera <xref:System.Windows.Forms.Cursor.HotSpot%2A> wywołuje odpowiednie zdarzenie myszy. Bieżącą pozycję myszy można uzyskać przy użyciu właściwości <xref:System.Windows.Forms.MouseEventArgs.Location%2A> <xref:System.Windows.Forms.MouseEventArgs> podczas obsługi zdarzenia myszy lub przy użyciu właściwości <xref:System.Windows.Forms.Cursor.Position%2A> klasy <xref:System.Windows.Forms.Cursor>. Następnie można użyć informacji o lokalizacji myszy w celu przeprowadzenia testowania trafień, a następnie wykonać akcję na podstawie lokalizacji myszy. Możliwość testowania trafień jest wbudowana w kilka kontrolek w Windows Forms, takich jak <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.MonthCalendar> i <xref:System.Windows.Forms.DataGridView> formantów. Używany z odpowiednim zdarzeniem myszy, <xref:System.Windows.Forms.Control.MouseHover> na przykład testowanie trafień jest bardzo przydatne do określania, kiedy aplikacja powinna wykonać konkretną akcję.  
  
## <a name="mouse-events"></a>Zdarzenia myszy  
 Podstawowym sposobem odpowiadania na dane wejściowe myszy jest obsługa zdarzeń myszy. W poniższej tabeli przedstawiono zdarzenia myszy i opisano, kiedy zostały zgłoszone.  
  
|Zdarzenie myszy|Opis|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.Click>|To zdarzenie występuje, gdy przycisk myszy zostanie wydzierżawiony, zazwyczaj przed zdarzeniem <xref:System.Windows.Forms.Control.MouseUp>. Procedura obsługi dla tego zdarzenia otrzymuje argument typu <xref:System.EventArgs>. Obsługuj to zdarzenie, gdy wystarczy określić, kiedy wystąpi.|  
|<xref:System.Windows.Forms.Control.MouseClick>|To zdarzenie występuje, gdy użytkownik kliknie kontrolkę za pomocą myszy. Procedura obsługi dla tego zdarzenia otrzymuje argument typu <xref:System.Windows.Forms.MouseEventArgs>. Obsłuż to zdarzenie, gdy będzie konieczne uzyskanie informacji o myszy po kliknięciu.|  
|<xref:System.Windows.Forms.Control.DoubleClick>|To zdarzenie występuje po dwukrotnym kliknięciu formantu. Procedura obsługi dla tego zdarzenia otrzymuje argument typu <xref:System.EventArgs>. Obsłuż to zdarzenie, gdy wystarczy określić, kiedy występuje dwukrotne kliknięcie.|  
|<xref:System.Windows.Forms.Control.MouseDoubleClick>|To zdarzenie występuje, gdy użytkownik kliknie dwukrotnie formant z myszą. Procedura obsługi dla tego zdarzenia otrzymuje argument typu <xref:System.Windows.Forms.MouseEventArgs>. Obsłuż to zdarzenie, gdy będzie konieczne uzyskanie informacji o myszy po dwukrotnym kliknięciu.|  
|<xref:System.Windows.Forms.Control.MouseDown>|To zdarzenie występuje, gdy wskaźnik myszy znajduje się nad kontrolką, a użytkownik naciśnie przycisk myszy. Procedura obsługi dla tego zdarzenia otrzymuje argument typu <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseEnter>|To zdarzenie występuje, gdy wskaźnik myszy zostanie przesunięty w obszar obramowania lub klienta kontrolki, w zależności od typu formantu. Procedura obsługi dla tego zdarzenia otrzymuje argument typu <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseHover>|To zdarzenie występuje, gdy wskaźnik myszy zostanie zatrzymany i zatrzyma się nad formantem. Procedura obsługi dla tego zdarzenia otrzymuje argument typu <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseLeave>|To zdarzenie występuje, gdy wskaźnik myszy opuszcza obszar obramowania lub klienta kontrolki, w zależności od typu formantu. Procedura obsługi dla tego zdarzenia otrzymuje argument typu <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseMove>|To zdarzenie występuje, gdy wskaźnik myszy zostanie przesunięty nad formantem. Procedura obsługi dla tego zdarzenia otrzymuje argument typu <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseUp>|To zdarzenie występuje, gdy wskaźnik myszy znajduje się nad kontrolką, a użytkownik zwolni przycisk myszy. Procedura obsługi dla tego zdarzenia otrzymuje argument typu <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseWheel>|To zdarzenie występuje, gdy użytkownik obraca kółko myszy, gdy kontrolka ma fokus. Procedura obsługi dla tego zdarzenia otrzymuje argument typu <xref:System.Windows.Forms.MouseEventArgs>. Możesz użyć właściwości <xref:System.Windows.Forms.MouseEventArgs.Delta%2A> <xref:System.Windows.Forms.MouseEventArgs>, aby określić, jak daleko przesuwa się wskaźnik myszy.|  
  
## <a name="changing-mouse-input-and-detecting-system-settings"></a>Zmiana danych wejściowych i wykrywanie ustawień systemowych myszy  
 Możesz wykryć i zmienić sposób, w jaki formant obsługuje wprowadzanie za pomocą myszy, pobierając z kontrolki i korzystając z metod <xref:System.Windows.Forms.Control.GetStyle%2A> i <xref:System.Windows.Forms.Control.SetStyle%2A>. Metoda <xref:System.Windows.Forms.Control.SetStyle%2A> przyjmuje bitową kombinację <xref:System.Windows.Forms.ControlStyles> wartości, aby określić, czy kontrolka będzie miała standardowe kliknięcie, czy dwukrotne kliknięcie, czy kontrolka będzie obsługiwać własne przetwarzanie myszy. Ponadto Klasa <xref:System.Windows.Forms.SystemInformation> zawiera właściwości opisujące możliwości myszy i określają, jak mysz współdziała z systemem operacyjnym. Poniższa tabela zawiera podsumowanie tych właściwości.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>|Pobiera Wymiary (w pikselach) obszaru, w którym użytkownik musi dwukrotnie kliknąć dwukrotnie, aby wziąć pod uwagę dwa kliknięcia.|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A>|Pobiera maksymalną liczbę milisekund, jaką może upłynąć między pierwszym kliknięciem a drugim kliknięciem dla systemu operacyjnego, aby rozważyć akcję myszy kliknij dwukrotnie.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtons%2A>|Pobiera liczbę przycisków na myszy.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtonsSwapped%2A>|Pobiera wartość wskazującą, czy funkcje lewego i prawego przycisku myszy zostały zamienione.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverSize%2A>|Pobiera Wymiary (w pikselach) prostokąta, w którym wskaźnik myszy ma pozostać na czas, gdy zostanie wygenerowany komunikat o umieszczeniu wskaźnika myszy.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverTime%2A>|Pobiera czas (w milisekundach), przez jaki wskaźnik myszy ma pozostać w prostokącie aktywowania przed wygenerowaniem komunikatu o umieszczeniu wskaźnika myszy.|  
|<xref:System.Windows.Forms.SystemInformation.MousePresent%2A>|Pobiera wartość wskazującą, czy mysz jest zainstalowana.|  
|<xref:System.Windows.Forms.SystemInformation.MouseSpeed%2A>|Pobiera wartość wskazującą bieżącą szybkość myszy z przedziału od 1 do 20.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelPresent%2A>|Pobiera wartość wskazującą, czy mysz z kółkiem myszy jest zainstalowana.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollDelta%2A>|Pobiera wartość różnicy przyrostu pojedynczego obrotu kółka myszy.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollLines%2A>|Pobiera liczbę wierszy do przewinięcia po obróceniu kółka myszy.|  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzanie za pomocą myszy w aplikacjach Windows Forms](mouse-input-in-a-windows-forms-application.md)
- [Przechwytywanie myszy w formularzach Windows Forms](mouse-capture-in-windows-forms.md)
- [Wskaźniki myszy w formularzach Windows Forms](mouse-pointers-in-windows-forms.md)
