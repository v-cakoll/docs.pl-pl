---
title: Działanie myszy w formularzach systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, mouse input
- mouse [Windows Forms], input
ms.assetid: 48fc5240-75a6-44bf-9fce-6aa21b49705a
ms.openlocfilehash: 7817b6a414f313cd2891fe0e124e230643b06e07
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725331"
---
# <a name="how-mouse-input-works-in-windows-forms"></a>Działanie myszy w formularzach systemu Windows
Otrzymywanie i obsługę wejście myszy jest ważnym elementem każdej aplikacji Windows. Obsługa zdarzeń myszy do wykonania akcji w aplikacji lub za pomocą informacji o lokalizacji myszy do testowania trafień lub innych działań. Ponadto można zmienić sposób kontrolki w aplikacji obsługi myszy w danych wejściowych. W tym temacie opisano te zdarzenia myszy w szczegółów i jak uzyskać i zmieniać ustawień systemowych myszy. Aby uzyskać więcej informacji na temat danych dostarczanych za pomocą myszy wywoływania zdarzeń i kolejności, w którym zdarzenia kliknięcia myszą, zobacz [zdarzeń myszy w formularzach Windows Forms](mouse-events-in-windows-forms.md).  
  
## <a name="mouse-location-and-hit-testing"></a>Położenie myszy i testowania trafień  
 Gdy użytkownik przesuwa mysz, system operacyjny wskaźnika myszy. Wskaźnik myszy zawiera piksela o nazwie aktywny, którego system operacyjny śledzi i jest rozpoznawany jako położenia wskaźnika. Gdy użytkownik przesuwa wskaźnik myszy lub naciśnie przycisk myszy <xref:System.Windows.Forms.Control> zawierający <xref:System.Windows.Forms.Cursor.HotSpot%2A> wywołuje zdarzenie myszy odpowiednie. Można uzyskać bieżącego położenia kursora myszy przy użyciu <xref:System.Windows.Forms.MouseEventArgs.Location%2A> właściwość <xref:System.Windows.Forms.MouseEventArgs> podczas obsługi zdarzenia myszy lub za pomocą <xref:System.Windows.Forms.Cursor.Position%2A> właściwość <xref:System.Windows.Forms.Cursor> klasy. Można później użyć informacji o lokalizacji myszy do testowania trafień, a następnie wykonać akcję na podstawie lokalizacji kursora myszy. Możliwość testowania trafień jest wbudowana w kilku formantów w formularzach Windows Forms takich jak <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.MonthCalendar> i <xref:System.Windows.Forms.DataGridView> kontrolki. Używane ze zdarzeniem myszy odpowiednie <xref:System.Windows.Forms.Control.MouseHover> na przykład testowania trafień jest bardzo przydatne do określenia, kiedy aplikacja powinna przeprowadzić określonej akcji.  
  
## <a name="mouse-events"></a>Zdarzenia myszy  
 Podstawowym sposobem, aby odpowiedzieć na wejście myszy jest do obsługi zdarzeń myszy. Poniższa tabela przedstawia zdarzenia myszy i opisuje, kiedy są wywoływane.  
  
|Zdarzenia myszy|Opis|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.Click>|To zdarzenie występuje po zwolnieniu przycisku myszy, zwykle przed <xref:System.Windows.Forms.Control.MouseUp> zdarzeń. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.EventArgs>. Obsługa tego zdarzenia, kiedy należy ustalić, kiedy wystąpi kliknięcie.|  
|<xref:System.Windows.Forms.Control.MouseClick>|To zdarzenie występuje, gdy użytkownik kliknie kontrolkę, za pomocą myszy. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.Windows.Forms.MouseEventArgs>. Obsługiwać to zdarzenie, gdy trzeba uzyskać informacje na temat myszy, gdy wystąpi kliknięcie.|  
|<xref:System.Windows.Forms.Control.DoubleClick>|To zdarzenie występuje po dwukrotnym kliknięciu formantu. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.EventArgs>. Obsługa tego zdarzenia, kiedy należy ustalić, kiedy wystąpi dwukrotne kliknięcie.|  
|<xref:System.Windows.Forms.Control.MouseDoubleClick>|To zdarzenie występuje, gdy użytkownik kliknie dwukrotnie sterowania za pomocą myszy. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.Windows.Forms.MouseEventArgs>. Obsługa tego zdarzenia, kiedy koniecznych do uzyskania informacji na temat myszy, gdy wystąpi dwukrotne kliknięcie.|  
|<xref:System.Windows.Forms.Control.MouseDown>|To zdarzenie występuje, gdy wskaźnik myszy znajduje się nad formantem i naciśnięciu przycisku myszy. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseEnter>|To zdarzenie występuje, gdy wskaźnik myszy zostanie obszaru klienta lub obramowania kontrolki, w zależności od typu formantu. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseHover>|To zdarzenie występuje, gdy wskaźnik myszy zatrzyma i opiera się nad formantem. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseLeave>|To zdarzenie występuje, gdy wskaźnik myszy opuszcza obszar klienta lub obramowania kontrolki, w zależności od typu kontrolki. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseMove>|To zdarzenie występuje, gdy wskaźnik myszy jest przemieszczany nad formantu. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseUp>|To zdarzenie występuje, gdy wskaźnik myszy znajduje się nad formantem i użytkownik zwolni przycisk myszy. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseWheel>|To zdarzenie występuje, gdy użytkownik obraca kółko myszy, gdy kontrolka jest ustawiony fokus. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.Windows.Forms.MouseEventArgs>. Możesz użyć <xref:System.Windows.Forms.MouseEventArgs.Delta%2A> właściwość <xref:System.Windows.Forms.MouseEventArgs> ustalenie, jak daleko jest przewijane myszy.|  
  
## <a name="changing-mouse-input-and-detecting-system-settings"></a>Zmiana wejście myszy oraz wykrywania ustawień systemowych  
 Można wykryć i zmienić sposób, w jaki formant obsługuje wprowadzanie za pomocą myszy pochodząca z formantu i używając <xref:System.Windows.Forms.Control.GetStyle%2A> i <xref:System.Windows.Forms.Control.SetStyle%2A> metody. <xref:System.Windows.Forms.Control.SetStyle%2A> Metoda przyjmuje bitowa kombinacja <xref:System.Windows.Forms.ControlStyles> wartości do określenia, czy kontrolka będzie miała standard, kliknij lub kliknij dwukrotnie działanie, lub jeśli formant będzie obsługiwać własne przetwarzanie myszy. Ponadto <xref:System.Windows.Forms.SystemInformation> klasa zawiera właściwości, które opisują możliwości myszy, a następnie określ, jak myszy wchodzi w interakcję z systemem operacyjnym. Poniższa tabela zawiera podsumowanie tych właściwości.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>|Pobiera wymiarów, w pikselach, obszaru, w którym użytkownik musi kliknąć dwukrotnie dla systemu operacyjnego należy wziąć pod uwagę dwa kliknięcia dwukrotne kliknięcie.|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A>|Pobiera maksymalną liczbę milisekund, które mogą upłynąć między pierwsze kliknięcie, a drugie kliknięcie systemu operacyjnego, należy wziąć pod uwagę Akcja myszy dwukrotne kliknięcie.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtons%2A>|Pobiera liczbę przycisków myszy.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtonsSwapped%2A>|Pobiera wartość wskazującą, czy funkcje przycisków myszy lewy i prawy zostały zamienione.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverSize%2A>|Pobiera wymiarów, w pikselach, prostokąt, w którym wskaźnik myszy ma pozostać raz po wskazaniu wskaźnikiem myszy przed wygenerowaniem komunikat po wskazaniu wskaźnikiem myszy.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverTime%2A>|Pobiera czas w milisekundach, do których wskaźnik myszy ma pozostać w prostokącie po wskazaniu wskaźnikiem, przed wygenerowaniem komunikat po wskazaniu wskaźnikiem myszy.|  
|<xref:System.Windows.Forms.SystemInformation.MousePresent%2A>|Pobiera wartość wskazującą, czy zainstalowano myszy.|  
|<xref:System.Windows.Forms.SystemInformation.MouseSpeed%2A>|Pobiera wartość wskazującą, bieżąca prędkość myszy z zakresu od 1 do 20.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelPresent%2A>|Pobiera wartość wskazującą, czy zainstalowano myszą z kółkiem myszy.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollDelta%2A>|Pobiera ilość różnicy przyrostu obrót kółka myszy pojedynczy.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollLines%2A>|Pobiera liczbę wierszy do przewijania podczas obracania kółka myszy.|  
  
## <a name="see-also"></a>Zobacz także
- [Wprowadzanie za pomocą myszy w aplikacjach Windows Forms](mouse-input-in-a-windows-forms-application.md)
- [Przechwytywanie myszy w formularzach Windows Forms](mouse-capture-in-windows-forms.md)
- [Wskaźniki myszy w formularzach Windows Forms](mouse-pointers-in-windows-forms.md)
