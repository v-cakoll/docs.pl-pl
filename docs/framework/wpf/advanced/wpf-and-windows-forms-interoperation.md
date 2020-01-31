---
title: WPF i Windows Forms międzyoperacyjności
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- nester interoperation [WPF]
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid control [WPF interoperability]
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
ms.openlocfilehash: 5141b84ecd002d920f0d4130bdc2529c0fce4994
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794054"
---
# <a name="wpf-and-windows-forms-interoperation"></a>Współdziałanie WPF i Windows Forms
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i Windows Forms są obecne dwie różne architektury do tworzenia interfejsów aplikacji. Przestrzeń nazw <xref:System.Windows.Forms.Integration?displayProperty=nameWithType> zawiera klasy, które umożliwiają wspólne scenariusze międzyoperacyjności. Dwie klasy kluczy, które implementują możliwości międzyoperacyjności, są <xref:System.Windows.Forms.Integration.WindowsFormsHost> i <xref:System.Windows.Forms.Integration.ElementHost>. W tym temacie opisano, które scenariusze międzyoperacyjności są obsługiwane i które scenariusze nie są obsługiwane.  
  
> [!NOTE]
> Szczególny nacisk jest przyznany do scenariusza *kontroli hybrydowej* . Kontrolka hybrydowa ma kontrolkę z jednej technologii, która jest zagnieżdżona w kontrolce innej technologii. Jest to również nazywane *zagnieżdżoną operacją międzyoperacyjną*. *Wielopoziomowa kontrolka hybrydowa* ma więcej niż jeden poziom zagnieżdżenia kontroli hybrydowej. Przykładem wielopoziomowej zagnieżdżonej międzyoperacji jest formant Windows Forms, który zawiera kontrolkę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], która zawiera inną kontrolkę Windows Forms. Wielopoziomowe kontrolki hybrydowe nie są obsługiwane.  

<a name="Windows_Presentation_Foundation_Application_Hosting"></a>   
## <a name="hosting-windows-forms-controls-in-wpf"></a>Hostowanie formantów Windows Forms w WPF  
 Następujące scenariusze międzyoperacji są obsługiwane, gdy kontrolka [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje kontrolkę Windows Forms:  
  
- Kontrolka [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] może hostować co najmniej jedną kontrolkę Windows Forms przy użyciu języka XAML.  
  
- Może on hostować co najmniej jedną Windows Formsą kontrolę przy użyciu kodu.  
  
- Może hostować Windows Forms formantów kontenera, które zawierają inne kontrolki Windows Forms.  
  
- Może on obsługiwać formularz główny/szczegółowy z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wzorzec i Windows Forms szczegóły.  
  
- Może on obsługiwać formularz główny/szczegółowy z Windows Forms wzorzec i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] szczegóły.  
  
- Może hostować co najmniej jedną kontrolkę ActiveX.  
  
- Może obsługiwać jeden lub więcej kontrolek złożonych.  
  
- Można hostować kontrolki hybrydowe za pomocą [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
- Mogą hostować formanty hybrydowe za pomocą kodu.  
  
### <a name="layout-support"></a>Obsługa układu  
 Poniższa lista zawiera opis znanych ograniczeń, gdy element <xref:System.Windows.Forms.Integration.WindowsFormsHost> próbuje zintegrować swoją obsługiwaną kontrolę Windows Forms z systemem układów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- W niektórych przypadkach nie można zmienić rozmiaru formantów Windows Forms lub można je zmieniać tylko do określonych wymiarów. Na przykład kontrolka <xref:System.Windows.Forms.ComboBox> Windows Forms obsługuje tylko jedną wysokość, która jest definiowana przez rozmiar czcionki kontrolki. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dynamicznym, który zakłada, że elementy można rozciągnąć w pionie, hostowana kontrolka <xref:System.Windows.Forms.ComboBox> nie rozciąga się zgodnie z oczekiwaniami.  
  
- Kontrolki Windows Forms nie mogą być obrócone lub skośne. Na przykład po obróceniu interfejsu użytkownika o 90 stopni, hostowane kontrolki Windows Forms będą zachować ich położenie w pozycji pionowej.  
  
- W większości przypadków formanty Windows Forms nie obsługują skalowania proporcjonalnie. Chociaż ogólne wymiary kontrolki będą skalowane, formanty podrzędne i elementy składnika formantu mogą nie zmieniać rozmiaru zgodnie z oczekiwaniami. To ograniczenie zależy od tego, jak dobrze każda kontrolka Windows Forms obsługuje skalowanie.  
  
- W interfejsie użytkownika [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] można zmienić porządek osi z elementów w celu kontrolowania nakładających się zachowań. Kontrolka hostowana Windows Forms jest rysowana w oddzielnym elemencie HWND, więc jest zawsze rysowana na elementach [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Formanty Windows Forms obsługują Skalowanie automatyczne na podstawie rozmiaru czcionki. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsie użytkownika zmiana rozmiaru czcionki nie powoduje zmiany rozmiaru całego układu, chociaż poszczególne elementy mogą dynamicznie zmieniać rozmiar.  
  
### <a name="ambient-properties"></a>Właściwości otoczenia  
 Niektóre właściwości otoczenia formantów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mają Windows Forms odpowiedniki. Te właściwości otoczenia są propagowane do hostowanych formantów Windows Forms i udostępniane jako właściwości publiczne na kontrolce <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Formant <xref:System.Windows.Forms.Integration.WindowsFormsHost> przekształca każdą właściwość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] otoczenia w Windows Forms odpowiedniki.  
  
 Aby uzyskać więcej informacji, zobacz [Windows Forms i mapowanie właściwości WPF](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Zachowanie  
 W poniższej tabeli opisano zachowanie międzyoperacyjności.  
  
|Zachowanie|Obsługiwana|Nieobsługiwane|  
|--------------|---------------|-------------------|  
|Przezroczystość|Renderowanie formantów Windows Forms obsługuje przezroczystość. Tło formantu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nadrzędnego może stać się tłem formantów hostowanych Windows Forms.|Niektóre formanty Windows Forms nie obsługują przezroczystości. Na przykład kontrolki <xref:System.Windows.Forms.TextBox> i <xref:System.Windows.Forms.ComboBox> nie będą przezroczyste, gdy są hostowane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|  
|TAB|Kolejność tabulacji dla obsługiwanych formantów Windows Forms jest taka sama jak w przypadku, gdy te kontrolki są hostowane w aplikacji opartej na Windows Forms.<br /><br /> Tabulacja z kontrolki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do kontrolki Windows Forms z klawiszem TAB i klawiszy SHIFT + TAB działa jak zwykle.<br /><br /> Windows Forms kontrolki, które mają <xref:System.Windows.Forms.Control.TabStop%2A> wartość właściwości `false` nie są odbierane po przejściu na karty użytkownika przez kontrolki.<br /><br /> -Każda kontrolka <xref:System.Windows.Forms.Integration.WindowsFormsHost> ma wartość <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>, która określa, kiedy formant <xref:System.Windows.Forms.Integration.WindowsFormsHost> będzie miał fokus.<br />-Windows Forms kontrolki, które znajdują się wewnątrz kontenera <xref:System.Windows.Forms.Integration.WindowsFormsHost>, są zgodne z kolejnością określoną przez właściwość <xref:System.Windows.Forms.Control.TabIndex%2A>. Tabulacja od ostatniego indeksu karty przenosi fokus na następną kontrolkę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], jeśli taka istnieje. Jeśli nie istnieje inna kontrolka [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], karta wraca do pierwszej kontrolki Windows Forms w kolejności tabulacji.<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> wartości formantów w <xref:System.Windows.Forms.Integration.WindowsFormsHost> są względne w stosunku do elementów równorzędnych Windows Forms, które znajdują się w kontrolce <xref:System.Windows.Forms.Integration.WindowsFormsHost>.<br />-Tabulacja honoruje zachowanie specyficzne dla kontroli. Na przykład naciśnięcie klawisza TAB w kontrolce <xref:System.Windows.Forms.TextBox>, która ma <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> wartość właściwości `true` wprowadza kartę w polu tekstowym zamiast przesuwania fokusu.|Nie dotyczy.|  
|Nawigacja przy użyciu klawiszy strzałek|-Nawigacja przy użyciu klawiszy strzałek w kontrolce <xref:System.Windows.Forms.Integration.WindowsFormsHost> jest taka sama jak w przypadku zwykłej kontrolki kontenera Windows Forms: Strzałka w górę i Strzałka w lewo wybierają poprzednią kontrolkę, a klawisz Strzałka w dół i Strzałka w prawo wybierają następną kontrolkę.<br />-Klawisze STRZAŁKA w górę i Strzałka w lewo z pierwszej kontrolki, która jest zawarta w kontrolce <xref:System.Windows.Forms.Integration.WindowsFormsHost>, wykonują tę samą akcję co skrót klawiaturowy SHIFT + TAB. Jeśli istnieje formant [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], fokus jest przesuwany poza formantem <xref:System.Windows.Forms.Integration.WindowsFormsHost>. To zachowanie różni się od standardowego zachowania <xref:System.Windows.Forms.ContainerControl> w tym, że nie występuje zawijanie do ostatniego formantu. Jeśli nie istnieje inna kontrolka [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] z fokusem, fokus powraca do ostatniej kontrolki Windows Forms w kolejności tabulacji.<br />-Klawisze STRZAŁKA w dół i Strzałka w prawo z ostatniej kontrolki, która jest zawarta w kontrolce <xref:System.Windows.Forms.Integration.WindowsFormsHost>, wykonują tę samą akcję co klucz TABULACJi. Jeśli istnieje formant [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], fokus jest przesuwany poza formantem <xref:System.Windows.Forms.Integration.WindowsFormsHost>. To zachowanie różni się od standardowego zachowania <xref:System.Windows.Forms.ContainerControl> w tym, że nie występuje zawijanie do pierwszej kontrolki. Jeśli nie istnieje inna kontrolka [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] z fokusem, fokus powraca do pierwszej kontrolki Windows Forms w kolejności tabulacji.|Nie dotyczy.|  
|Akceleratorów|Akceleratory działają w zwykły sposób, chyba że zaznaczono w kolumnie "nieobsługiwane".|Zduplikowane akceleratory między technologiami nie działają podobnie jak zwykłe zduplikowane akceleratory. Gdy akcelerator jest duplikowany między technologiami, z co najmniej jednym na kontrolce Windows Forms i drugim na kontrolce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], formant Windows Forms zawsze otrzymuje akcelerator. Fokus nie jest przełączany między kontrolkami, gdy zostanie naciśnięty zduplikowany akcelerator.|  
|Klawisze skrótów|Klawisze skrótu działają w zwykły sposób, chyba że zaznaczono w kolumnie "nieobsługiwane".|-Windows Forms klawiszy skrótów, które są obsługiwane w procesie przetwarzania wstępnego, zawsze mają pierwszeństwo przed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] skrótów. Na przykład jeśli masz kontrolkę <xref:System.Windows.Forms.ToolStrip> ze zdefiniowanymi klawiszami skrótu CTRL + S i istnieje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] polecenie powiązane z CTRL + S, procedura obsługi kontrolki <xref:System.Windows.Forms.ToolStrip> jest zawsze wywoływana jako pierwsza, niezależnie od fokusu.<br />-Windows Forms klawiszy skrótów, które są obsługiwane przez zdarzenie <xref:System.Windows.Forms.Control.KeyDown>, są przetwarzane ostatnio w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Można uniknąć tego zachowania, zastępując metodę <xref:System.Windows.Forms.Control.IsInputKey%2A> formantu Windows Forms lub obsłużyć zdarzenie <xref:System.Windows.Forms.Control.PreviewKeyDown>. Zwróć `true` z metody <xref:System.Windows.Forms.Control.IsInputKey%2A> lub ustaw wartość właściwości <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType> na `true` w obsłudze zdarzeń <xref:System.Windows.Forms.Control.PreviewKeyDown>.|  
|AcceptsReturn, AcceptsTab i inne zachowanie dotyczące kontroli|Właściwości, które zmieniają domyślne zachowanie klawiatury, przy założeniu, że formant Windows Forms przesłania metodę <xref:System.Windows.Forms.Control.IsInputKey%2A> w celu zwrócenia `true`.|Windows Forms kontrolki, które zmieniają domyślne zachowanie klawiatury przez obsługę zdarzenia <xref:System.Windows.Forms.Control.KeyDown>, są przetwarzane jako ostatnie w kontrolce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hosta. Ponieważ te kontrolki są przetwarzane jako ostatnie, mogą powodować nieoczekiwane zachowanie.|  
|Wprowadź i opuszczaj zdarzenia|Gdy fokus nie przechodzi do zawartej kontrolki <xref:System.Windows.Forms.Integration.ElementHost>, zdarzenia wejścia i opuszczenia są zgłaszane w zwykły sposób, gdy fokus zmieni się w jednym formancie <xref:System.Windows.Forms.Integration.WindowsFormsHost>.|Zdarzenia Enter i opuszcza nie są zgłaszane w przypadku wystąpienia następujących zmian fokusu:<br /><br /> — Od wewnątrz do poza kontrolką <xref:System.Windows.Forms.Integration.WindowsFormsHost>.<br />— Od zewnątrz do wewnątrz kontrolki <xref:System.Windows.Forms.Integration.WindowsFormsHost>.<br />— Poza kontrolką <xref:System.Windows.Forms.Integration.WindowsFormsHost>.<br />— Z formantu Windows Forms hostowanego w kontrolce <xref:System.Windows.Forms.Integration.WindowsFormsHost> do kontrolki <xref:System.Windows.Forms.Integration.ElementHost> hostowanej w tym samym <xref:System.Windows.Forms.Integration.WindowsFormsHost>.|  
|Wielowątkowość|Wszystkie odmiany wielowątkowości są obsługiwane.|Technologie Windows Forms i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zakładają jednowątkowy model współbieżności. Podczas debugowania wywołania obiektów Framework z innych wątków spowodują wyjątek, aby wymusić to wymaganie.|  
|Zabezpieczenia|Wszystkie scenariusze międzyoperacyjności wymagają pełnego zaufania.|W częściowej relacji zaufania nie są dozwolone żadne scenariusze międzyoperacyjności.|  
|Ułatwienia dostępu|Obsługiwane są wszystkie scenariusze ułatwień dostępu. Produkty technologii pomocniczych działają prawidłowo, gdy są używane w aplikacjach hybrydowych, które zawierają zarówno Windows Forms, jak i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Nie dotyczy.|  
|Schowek|Wszystkie operacje na schowku działają w zwykły sposób. Obejmuje to wycinanie i wklejanie między kontrolkami Windows Forms i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Nie dotyczy.|  
|Funkcja przeciągania i upuszczania|Wszystkie operacje przeciągania i upuszczania działają w zwykły sposób. Obejmuje to operacje między Windows Forms i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolkami.|Nie dotyczy.|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>   
## <a name="hosting-wpf-controls-in-windows-forms"></a>Hostowanie formantów WPF w Windows Forms  
 Następujące scenariusze międzyoperacji są obsługiwane, gdy kontrolka Windows Forms obsługuje kontrolkę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
- Hostowanie co najmniej jednej kontrolki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przy użyciu kodu.  
  
- Kojarzenie arkusza właściwości z co najmniej jednym hostowaną kontrolką [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Hostowanie co najmniej jednej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stron w formularzu.  
  
- Uruchamianie okna [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Hostowanie formularza wzorzec/szczegół z Windows Forms Master i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] szczegóły.  
  
- Hostowanie formularza wzorzec/szczegół z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Master i Windows Forms szczegóły.  
  
- Hostowanie niestandardowych kontrolek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Hostowanie kontrolek hybrydowych.  
  
### <a name="ambient-properties"></a>Właściwości otoczenia  
 Niektóre właściwości otoczenia formantów Windows Forms mają [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odpowiedniki. Te właściwości otoczenia są propagowane do hostowanych formantów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i udostępniane jako właściwości publiczne na kontrolce <xref:System.Windows.Forms.Integration.ElementHost>. Formant <xref:System.Windows.Forms.Integration.ElementHost> tłumaczy każdą właściwość Windows Forms otoczenia na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odpowiedniki.  
  
 Aby uzyskać więcej informacji, zobacz [Windows Forms i mapowanie właściwości WPF](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Zachowanie  
 W poniższej tabeli opisano zachowanie międzyoperacyjności.  
  
|Zachowanie|Obsługiwana|Nieobsługiwane|  
|--------------|---------------|-------------------|  
|Przezroczystość|renderowanie formantów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje przezroczystość. Tło formantu Windows Forms nadrzędnego może stać się tłem formantów hostowanych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Nie dotyczy.|  
|Wielowątkowość|Wszystkie odmiany wielowątkowości są obsługiwane.|Technologie Windows Forms i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zakładają jednowątkowy model współbieżności. Podczas debugowania wywołania obiektów Framework z innych wątków spowodują wyjątek, aby wymusić to wymaganie.|  
|Zabezpieczenia|Wszystkie scenariusze międzyoperacyjności wymagają pełnego zaufania.|W częściowej relacji zaufania nie są dozwolone żadne scenariusze międzyoperacyjności.|  
|Ułatwienia dostępu|Obsługiwane są wszystkie scenariusze ułatwień dostępu. Produkty technologii pomocniczych działają prawidłowo, gdy są używane w aplikacjach hybrydowych, które zawierają zarówno Windows Forms, jak i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Nie dotyczy.|  
|Schowek|Wszystkie operacje na schowku działają w zwykły sposób. Obejmuje to wycinanie i wklejanie między kontrolkami Windows Forms i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Nie dotyczy.|  
|Funkcja przeciągania i upuszczania|Wszystkie operacje przeciągania i upuszczania działają w zwykły sposób. Obejmuje to operacje między Windows Forms i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolkami.|Nie dotyczy.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Przewodnik: hosting kontrolki Windows Forms w WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Przewodnik: hosting złożonej kontrolki Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Przewodnik: hosting złożonej kontrolki WPF w Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Mapowanie właściwości Windows Forms i WPF](windows-forms-and-wpf-property-mapping.md)
