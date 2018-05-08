---
title: Działanie myszy w formularzach systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, mouse input
- mouse [Windows Forms], input
ms.assetid: 48fc5240-75a6-44bf-9fce-6aa21b49705a
ms.openlocfilehash: 265693eef3008362994ad04d9faaf8e20554d13e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-mouse-input-works-in-windows-forms"></a>Działanie myszy w formularzach systemu Windows
Otrzymywanie i obsługę myszą jest ważnym elementem każda aplikacja systemu Windows. Obsługa zdarzeń myszy do wykonywania akcji w aplikacji lub za pomocą myszy informacji o lokalizacji do testowania trafień lub innych działań. Ponadto można zmienić sposób myszą obsługi formantów w aplikacji. W tym temacie opisano te zdarzenia myszy w szczegółów i sposobu uzyskiwania i zmieniać ustawień systemowych myszy. Aby uzyskać więcej informacji na temat danych dostarczonych przy użyciu myszy pojawienia się zdarzenia i kolejność, w którym zdarzenia kliknięcia myszą, zobacz [zdarzenia myszy w formularzach systemu Windows](../../../docs/framework/winforms/mouse-events-in-windows-forms.md).  
  
## <a name="mouse-location-and-hit-testing"></a>Położenie myszy i testowania trafień  
 Gdy użytkownik przesuwa wskaźnik myszy, system operacyjny wskaźnika myszy. Wskaźnik myszy zawiera piksela wywołuje punkt aktywny, który system operacyjny śledzi i jest rozpoznawany jako położenia wskaźnika. Gdy użytkownik przesuwa wskaźnik myszy lub naciśnie przycisk myszy <xref:System.Windows.Forms.Control> zawierający <xref:System.Windows.Forms.Cursor.HotSpot%2A> zgłasza myszy odpowiednie zdarzenie. Możesz uzyskać bieżącej pozycji myszy <xref:System.Windows.Forms.MouseEventArgs.Location%2A> właściwość <xref:System.Windows.Forms.MouseEventArgs> podczas obsługi zdarzenia myszy lub za pomocą <xref:System.Windows.Forms.Cursor.Position%2A> właściwość <xref:System.Windows.Forms.Cursor> klasy. Można następnie użyć do testowania trafień informacji o lokalizacji myszy, a następnie wykonaj akcję na podstawie lokalizacji kursora myszy. Możliwość testowania trafień jest wbudowana w kilku formantów w formularzach systemu Windows takich jak <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.MonthCalendar> i <xref:System.Windows.Forms.DataGridView> kontrolki. Używane z zdarzeń myszy odpowiednie <xref:System.Windows.Forms.Control.MouseHover> na przykład testowania trafień jest przydatne do określenia, kiedy aplikacja powinna wykonywać konkretną akcję.  
  
## <a name="mouse-events"></a>Zdarzenia myszy  
 Odpowiadanie na wejście myszy podstawową metodą jest do obsługi zdarzeń myszy. Poniższa tabela przedstawia zdarzenia myszy oraz opisano, kiedy są wywoływane.  
  
|Zdarzenia myszy|Opis|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.Click>|To zdarzenie występuje, gdy przycisk myszy jest zwolniony, zwykle przed <xref:System.Windows.Forms.Control.MouseUp> zdarzeń. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.EventArgs>. Obsługa tego zdarzenia, kiedy należy ustalić, kiedy występuje, kliknij przycisk.|  
|<xref:System.Windows.Forms.Control.MouseClick>|To zdarzenie występuje po kliknięciu formantu przy użyciu myszy. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.Windows.Forms.MouseEventArgs>. Obsługa tego zdarzenia, kiedy należy uzyskać informacje na temat myszy po wystąpieniu przez kliknięcie.|  
|<xref:System.Windows.Forms.Control.DoubleClick>|To zdarzenie występuje, gdy formant zostanie dwukrotnie kliknięty. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.EventArgs>. Obsługa tego zdarzenia, kiedy należy ustalić, kiedy występuje, kliknij dwukrotnie.|  
|<xref:System.Windows.Forms.Control.MouseDoubleClick>|To zdarzenie występuje, gdy użytkownik kliknie dwukrotnie formantu przy użyciu myszy. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.Windows.Forms.MouseEventArgs>. Obsługa tego zdarzenia, kiedy należy uzyskać informacje na temat myszy, gdy wystąpi dwukrotne.|  
|<xref:System.Windows.Forms.Control.MouseDown>|To zdarzenie występuje, gdy wskaźnik myszy znajduje się nad formantem i użytkownik naciśnie przycisk myszy. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseEnter>|To zdarzenie występuje, gdy wskaźnik myszy zostanie umieszczony obszar klienta lub obramowania formantu, w zależności od typu formantu. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseHover>|To zdarzenie występuje, gdy wskaźnik myszy zatrzyma i opiera się nad formantem. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseLeave>|To zdarzenie występuje, gdy wskaźnik myszy opuści obszaru klienta lub obramowania formantu, w zależności od typu formantu. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseMove>|To zdarzenie występuje, gdy wskaźnik myszy jest przemieszczany nad formantem. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseUp>|To zdarzenie występuje, gdy wskaźnik myszy znajduje się nad formantem, a użytkownik zwolni przycisk myszy. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseWheel>|To zdarzenie występuje, gdy użytkownik obraca kółko myszy, gdy formant ma fokus. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.Windows.Forms.MouseEventArgs>. Można użyć <xref:System.Windows.Forms.MouseEventArgs.Delta%2A> właściwość <xref:System.Windows.Forms.MouseEventArgs> ustalenie, jak daleko przewijane ma myszy.|  
  
## <a name="changing-mouse-input-and-detecting-system-settings"></a>Zmiana myszą i wykrywania ustawień systemowych  
 Mogą wykrywać i zmienić sposób formantu obsługuje wejście myszy wynikających z formantu i używając <xref:System.Windows.Forms.Control.GetStyle%2A> i <xref:System.Windows.Forms.Control.SetStyle%2A> metody. <xref:System.Windows.Forms.Control.SetStyle%2A> Metoda przyjmuje bitowe połączenie <xref:System.Windows.Forms.ControlStyles> wartości, aby ustalić, czy kontrolka będzie miała standard kliknij lub kliknij dwukrotnie działanie, lub jeśli formant będzie obsługiwać przetwarzania myszy. Ponadto <xref:System.Windows.Forms.SystemInformation> klasy zawiera właściwości, które opisują możliwości myszy i określ sposób interakcji myszy w systemie operacyjnym. W poniższej tabeli przedstawiono te właściwości.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>|Pobiera wymiarów w pikselach, obszaru, w którym użytkownik musi kliknąć dwukrotnie dla systemu operacyjnego, które należy uwzględnić dwa kliknie dwukrotne.|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A>|Pobiera maksymalną liczbę milisekund, jaką może upłynąć między pierwszym kliknięciem drugie kliknięcie na należy wziąć pod uwagę Akcja myszy dwukrotne systemu operacyjnego.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtons%2A>|Pobiera liczbę przycisków myszy.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtonsSwapped%2A>|Pobiera wartość wskazującą, czy funkcje dla przycisku myszy w lewy i prawy zostały zamienione.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverSize%2A>|Pobiera wymiarów w pikselach, prostokąt, w którym wskaźnik myszy ma pozostanie podczas przesuwania myszy powoduje wygenerowanie komunikatu przesuwania myszy.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverTime%2A>|Pobiera czas (w milisekundach), które ma wskaźnik myszy pozostanie w prostokącie hover wygenerowanie komunikatu przesuwania myszy.|  
|<xref:System.Windows.Forms.SystemInformation.MousePresent%2A>|Pobiera wartość wskazującą, czy zainstalowano myszy.|  
|<xref:System.Windows.Forms.SystemInformation.MouseSpeed%2A>|Pobiera wartość wskazującą bieżącej szybkości myszy od 1 do 20.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelPresent%2A>|Pobiera wartość wskazującą, czy zainstalowano myszy kółko myszy.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollDelta%2A>|Pobiera ilość wartość różnicy przyrostu obrotu kółka myszy jednego.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollLines%2A>|Pobiera liczbę wierszy do przewijania podczas obracania kółka myszy.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzanie za pomocą myszy w aplikacjach Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)  
 [Przechwytywanie myszy w formularzach Windows Forms](../../../docs/framework/winforms/mouse-capture-in-windows-forms.md)  
 [Wskaźniki myszy w formularzach Windows Forms](../../../docs/framework/winforms/mouse-pointers-in-windows-forms.md)
