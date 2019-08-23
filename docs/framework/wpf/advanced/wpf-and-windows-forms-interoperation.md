---
title: Współdziałanie WPF i Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- nester interoperation [WPF]
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid control [WPF interoperability]
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
ms.openlocfilehash: 0326f283cb271d1578e94b648e423c6f88c579f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917404"
---
# <a name="wpf-and-windows-forms-interoperation"></a>Współdziałanie WPF i Windows Forms
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] są obecne dwie różne architektury służące do tworzenia interfejsów aplikacji. <xref:System.Windows.Forms.Integration?displayProperty=nameWithType> Przestrzeń nazw zawiera klasy, które umożliwiają wspólne scenariusze międzyoperacyjności. Dwie klasy kluczy, które implementują możliwości międzyoperacyjności <xref:System.Windows.Forms.Integration.ElementHost>, to <xref:System.Windows.Forms.Integration.WindowsFormsHost> i. W tym temacie opisano, które scenariusze międzyoperacyjności są obsługiwane i które scenariusze nie są obsługiwane.  
  
> [!NOTE]
> Szczególny nacisk jest przyznany do scenariusza *kontroli hybrydowej* . Kontrolka hybrydowa ma kontrolkę z jednej technologii, która jest zagnieżdżona w kontrolce innej technologii. Jest to również nazywane *zagnieżdżoną operacją*międzyoperacyjną. Wielopoziomowa *kontrolka hybrydowa* ma więcej niż jeden poziom zagnieżdżenia kontroli hybrydowej. Przykładem wielopoziomowej zagnieżdżonej międzyoperacji jest [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formant, który [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera kontrolkę, która zawiera [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] inną kontrolkę. Wielopoziomowe kontrolki hybrydowe nie są obsługiwane.  

<a name="Windows_Presentation_Foundation_Application_Hosting"></a>   
## <a name="hosting-windows-forms-controls-in-wpf"></a>Hostowanie formantów Windows Forms w WPF  
 Następujące scenariusze międzyoperacji są obsługiwane, gdy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolka obsługuje formant Windows Forms:  
  
- Kontrolka może hostować co najmniej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jedną kontrolkę przy użyciu języka XAML. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
- Może hostować co najmniej jedną [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolkę przy użyciu kodu.  
  
- Może hostować [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty kontenera, które zawierają [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] inne kontrolki.  
  
- Może on obsługiwać formularz główny/szczegółowy z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wzorcem i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] szczegółami.  
  
- Może on obsługiwać formularz główny/szczegółowy z [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] wzorcem i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] szczegółami.  
  
- Może hostować co najmniej jedną kontrolkę ActiveX.  
  
- Może obsługiwać jeden lub więcej kontrolek złożonych.  
  
- Mogą hostować formanty hybrydowe [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]za pomocą.  
  
- Mogą hostować formanty hybrydowe za pomocą kodu.  
  
### <a name="layout-support"></a>Obsługa układu  
 Poniższa lista zawiera opis znanych ograniczeń, gdy <xref:System.Windows.Forms.Integration.WindowsFormsHost> element próbuje zintegrować swoją [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] obsługiwaną kontrolę z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systemem układu.  
  
- W niektórych przypadkach [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nie można zmienić rozmiaru formantów lub można je zmieniać tylko do określonych wymiarów. Na przykład [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> kontrolka obsługuje tylko jedną wysokość, która jest definiowana przez rozmiar czcionki kontrolki. W układzie <xref:System.Windows.Forms.ComboBox> dynamicznym, który zakłada, że elementy można rozciągnąć w pionie, hostowana kontrolka nie rozciąga się w oczekiwany sposób. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]kontrolki nie mogą być obrócone lub skośne. Na przykład podczas obracania interfejsu użytkownika o 90 stopni, formanty hostowane [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] zachowają położenie w pozycji pionowej.  
  
- W większości przypadków [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty nie obsługują skalowania proporcjonalnie. Chociaż ogólne wymiary kontrolki będą skalowane, formanty podrzędne i elementy składnika formantu mogą nie zmieniać rozmiaru zgodnie z oczekiwaniami. To ograniczenie zależy od tego, jak dobrze [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] każda kontrolka obsługuje skalowanie.  
  
- W interfejsie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] użytkownika można zmienić porządek osi z elementów w celu kontrolowania nakładających się zachowań. Formant hostowany [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jest rysowany w osobnym elemencie HWND, więc jest on zawsze rysowany na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementach.  
  
- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]formanty obsługują Skalowanie automatyczne na podstawie rozmiaru czcionki. W interfejsie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] użytkownika zmiana rozmiaru czcionki nie powoduje zmiany rozmiaru całego układu, chociaż poszczególne elementy mogą dynamicznie zmieniać rozmiar.  
  
### <a name="ambient-properties"></a>Właściwości otoczenia  
 Niektóre właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] otoczenia formantów mają [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] równoważne. Te właściwości otoczenia są propagowane do formantów hostowanych [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i udostępniane jako właściwości publiczne <xref:System.Windows.Forms.Integration.WindowsFormsHost> na formancie. Kontrolka tłumaczy każdą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Właściwość otoczenia na jej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] odpowiednik. <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
  
 Aby uzyskać więcej informacji, zobacz [Windows Forms i mapowanie właściwości WPF](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Zachowanie  
 W poniższej tabeli opisano zachowanie międzyoperacyjności.  
  
|Zachowanie|Obsługiwane|Nieobsługiwane|  
|--------------|---------------|-------------------|  
|Przezroczystość|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]renderowanie formantów obsługuje przezroczystość. Tło kontrolki nadrzędnej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] może stać się tłem formantów hostowanych [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] .|Niektóre [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki nie obsługują przezroczystości. Na przykład <xref:System.Windows.Forms.TextBox> formanty i <xref:System.Windows.Forms.ComboBox> nie będą przezroczyste, gdy są hostowane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]przez.|  
|TAB|Kolejność tabulacji dla [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów hostowanych jest taka sama jak [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]w przypadku, gdy te kontrolki są hostowane w aplikacji opartej na bazie.<br /><br /> Tabulacja z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] za pomocą klawisza Tab i klawiszy Shift + Tab działa jak zwykle.<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]kontrolki, które <xref:System.Windows.Forms.Control.TabStop%2A> mają `false` wartość właściwości nie są odbierane, gdy użytkownik przeprowadzi karty przez kontrolki.<br /><br /> -Każda <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontrolka <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> ma wartość, która określa, kiedy <xref:System.Windows.Forms.Integration.WindowsFormsHost> ten formant będzie miał fokus.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]kontrolki, które znajdują <xref:System.Windows.Forms.Integration.WindowsFormsHost> się wewnątrz kontenera, są zgodne z <xref:System.Windows.Forms.Control.TabIndex%2A> kolejnością określoną przez właściwość. Tabulacja od ostatniego indeksu karty umieszcza fokus na następnym [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formancie (jeśli taki istnieje). Jeśli nie istnieje inna [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolka z fokusem, tabulacja powraca do pierwszej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki w kolejności tabulacji.<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>wartości formantów wewnątrz <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementów są względne w stosunku [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] do elementów równorzędnych <xref:System.Windows.Forms.Integration.WindowsFormsHost> , które są zawarte w formancie.<br />-Tabulacja honoruje zachowanie specyficzne dla kontroli. Na przykład naciśnięcie klawisza Tab w <xref:System.Windows.Forms.TextBox> kontrolce, która <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> ma wartość właściwości, `true` wprowadza kartę w polu tekstowym zamiast przesuwania fokusu.|Nie dotyczy.|  
|Nawigacja przy użyciu klawiszy strzałek|-Nawigacja przy użyciu klawiszy strzałek w <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontrolce jest taka sama jak w przypadku [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] zwykłej kontroli kontenera: Klawisz Strzałka w górę i Strzałka w lewo wybierają poprzednią kontrolkę, a klawisz Strzałka w dół i Strzałka w prawo wybierają następną kontrolkę.<br />-Klawisze STRZAŁKA w górę i Strzałka w lewo z pierwszej kontrolki, która jest zawarta w <xref:System.Windows.Forms.Integration.WindowsFormsHost> formancie, wykonują tę samą akcję co skrót klawiaturowy SHIFT + TAB. Jeśli istnieje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formant z fokusem, fokus jest przenoszony <xref:System.Windows.Forms.Integration.WindowsFormsHost> poza formant. To zachowanie różni się od zachowania <xref:System.Windows.Forms.ContainerControl> standardowego w tym, że nie występuje zawijanie do ostatniego formantu. Jeśli nie istnieje inna [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolka z fokusem, fokus powraca do ostatniej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki w kolejności tabulacji.<br />-Klawisze STRZAŁKA w dół i Strzałka w prawo z ostatniej kontrolki, która jest zawarta w <xref:System.Windows.Forms.Integration.WindowsFormsHost> formancie, wykonują tę samą akcję co klawisz Tab. Jeśli istnieje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formant z fokusem, fokus jest przenoszony <xref:System.Windows.Forms.Integration.WindowsFormsHost> poza formant. To zachowanie różni się od zachowania <xref:System.Windows.Forms.ContainerControl> standardowego w tym, że nie występuje zawijanie do pierwszej kontrolki. Jeśli nie istnieje inna [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolka z fokusem, fokus powraca do pierwszej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki w kolejności tabulacji.|Nie dotyczy.|  
|Akceleratorów|Akceleratory działają w zwykły sposób, chyba że zaznaczono w kolumnie "nieobsługiwane".|Zduplikowane akceleratory między technologiami nie działają podobnie jak zwykłe zduplikowane akceleratory. Gdy akcelerator jest duplikowany między technologiami, z co najmniej jednym na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolce i drugim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na kontrolce, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formant zawsze otrzymuje akcelerator. Fokus nie jest przełączany między kontrolkami, gdy zostanie naciśnięty zduplikowany akcelerator.|  
|Klawisze skrótów|Klawisze skrótu działają w zwykły sposób, chyba że zaznaczono w kolumnie "nieobsługiwane".|-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]skróty klawiaturowe, które są obsługiwane w fazie przetwarzania wstępnego, zawsze mają [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pierwszeństwo przed klawiszami skrótów. Na przykład jeśli masz <xref:System.Windows.Forms.ToolStrip> kontrolkę z zdefiniowanymi skrótami Ctrl + s i istnieje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] polecenie powiązane z <xref:System.Windows.Forms.ToolStrip> Ctrl + s, procedura obsługi kontroli jest zawsze wywoływana jako pierwsza, niezależnie od fokusu.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]skróty klawiaturowe, które są obsługiwane <xref:System.Windows.Forms.Control.KeyDown> przez zdarzenie, są przetwarzane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]jako ostatnie w. Można uniknąć tego zachowania, zastępując [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.IsInputKey%2A> metodę kontrolki lub obsługując <xref:System.Windows.Forms.Control.PreviewKeyDown> zdarzenie. Wróć `true` `true` z metody lub <xref:System.Windows.Forms.Control.PreviewKeyDown> ustaw wartość właściwości na w programie obsługi zdarzeń. <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.Control.IsInputKey%2A>|  
|AcceptsReturn, AcceptsTab i inne zachowanie dotyczące kontroli|Właściwości, które zmieniają domyślne zachowanie klawiatury, przy założeniu, że [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formant <xref:System.Windows.Forms.Control.IsInputKey%2A> zastępuje metodę zwracaną `true`.|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]kontrolki, które zmieniają domyślne zachowanie klawiatury przez <xref:System.Windows.Forms.Control.KeyDown> obsługę zdarzenia, są przetwarzane ostatnio w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formancie hosta. Ponieważ te kontrolki są przetwarzane jako ostatnie, mogą powodować nieoczekiwane zachowanie.|  
|Wprowadź i opuszczaj zdarzenia|Gdy fokus nie przechodzi do kontrolki zawierającej <xref:System.Windows.Forms.Integration.ElementHost> , zdarzenia Enter i opuszcza są wywoływane w zwykły sposób, gdy fokus zmienia się w jednym <xref:System.Windows.Forms.Integration.WindowsFormsHost> formancie.|Zdarzenia Enter i opuszcza nie są zgłaszane w przypadku wystąpienia następujących zmian fokusu:<br /><br /> — Od wewnątrz do <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontrolki.<br />— Od zewnątrz do wewnątrz <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontrolki.<br />— Poza <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontrolką.<br />— Z [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki hostowanej <xref:System.Windows.Forms.Integration.WindowsFormsHost> w kontrolce do <xref:System.Windows.Forms.Integration.ElementHost> kontrolki hostowanej w <xref:System.Windows.Forms.Integration.WindowsFormsHost>tym samym elemencie.|  
|Wielowątkowość|Wszystkie odmiany wielowątkowości są obsługiwane.|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Technologie i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zakładają jednowątkowy model współbieżności. Podczas debugowania wywołania obiektów Framework z innych wątków spowodują wyjątek, aby wymusić to wymaganie.|  
|Zabezpieczenia|Wszystkie scenariusze międzyoperacyjności wymagają pełnego zaufania.|W częściowej relacji zaufania nie są dozwolone żadne scenariusze międzyoperacyjności.|  
|Ułatwienia dostępu|Obsługiwane są wszystkie scenariusze ułatwień dostępu. Produkty technologii pomocniczej działają prawidłowo, gdy są używane w aplikacjach hybrydowych, które [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] zawierają [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zarówno formanty, jak i.|Nie dotyczy.|  
|Schowek|Wszystkie operacje na schowku działają w zwykły sposób. Obejmuje to wycinanie i wklejanie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] między [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolkami i.|Nie dotyczy.|  
|Funkcja przeciągania i upuszczania|Wszystkie operacje przeciągania i upuszczania działają w zwykły sposób. Obejmuje to operacje między [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolkami.|Nie dotyczy.|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>   
## <a name="hosting-wpf-controls-in-windows-forms"></a>Hostowanie formantów WPF w Windows Forms  
 Następujące scenariusze międzyoperacji są obsługiwane, gdy kontrolka Windows Forms obsługuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolkę:  
  
- Hostowanie co najmniej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jednej kontrolki przy użyciu kodu.  
  
- Kojarzenie arkusza właściwości z co najmniej jedną obsługiwaną [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolką.  
  
- Hostowanie co najmniej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jednej strony w formularzu.  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Uruchamianie okna.  
  
- Hostowanie formularza głównego/szczegółów z [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] wzorcem i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] szczegółami.  
  
- Hostowanie formularza głównego/szczegółów z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wzorcem i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] szczegółami.  
  
- Hostowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] niestandardowych kontrolek.  
  
- Hostowanie kontrolek hybrydowych.  
  
### <a name="ambient-properties"></a>Właściwości otoczenia  
 Niektóre właściwości [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] otoczenia formantów mają [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] równoważne. Te właściwości otoczenia są propagowane do formantów hostowanych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i udostępniane jako właściwości publiczne <xref:System.Windows.Forms.Integration.ElementHost> na formancie. Kontrolka tłumaczy każdą [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Właściwość otoczenia na jej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odpowiednik. <xref:System.Windows.Forms.Integration.ElementHost>  
  
 Aby uzyskać więcej informacji, zobacz [Windows Forms i mapowanie właściwości WPF](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Zachowanie  
 W poniższej tabeli opisano zachowanie międzyoperacyjności.  
  
|Zachowanie|Obsługiwane|Nieobsługiwane|  
|--------------|---------------|-------------------|  
|Przezroczystość|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]renderowanie formantów obsługuje przezroczystość. Tło kontrolki nadrzędnej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] może stać się tłem formantów hostowanych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .|Nie dotyczy.|  
|Wielowątkowość|Wszystkie odmiany wielowątkowości są obsługiwane.|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Technologie i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zakładają jednowątkowy model współbieżności. Podczas debugowania wywołania obiektów Framework z innych wątków spowodują wyjątek, aby wymusić to wymaganie.|  
|Zabezpieczenia|Wszystkie scenariusze międzyoperacyjności wymagają pełnego zaufania.|W częściowej relacji zaufania nie są dozwolone żadne scenariusze międzyoperacyjności.|  
|Ułatwienia dostępu|Obsługiwane są wszystkie scenariusze ułatwień dostępu. Produkty technologii pomocniczej działają prawidłowo, gdy są używane w aplikacjach hybrydowych, które [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] zawierają [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zarówno formanty, jak i.|Nie dotyczy.|  
|Schowek|Wszystkie operacje na schowku działają w zwykły sposób. Obejmuje to wycinanie i wklejanie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] między [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolkami i.|Nie dotyczy.|  
|Funkcja przeciągania i upuszczania|Wszystkie operacje przeciągania i upuszczania działają w zwykły sposób. Obejmuje to operacje między [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolkami.|Nie dotyczy.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Przewodnik: Hostowanie formantu Windows Forms w WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Przewodnik: Hostowanie złożonego formantu Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Przewodnik: Hostowanie złożonego formantu WPF w Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Mapowanie właściwości Windows Forms i WPF](windows-forms-and-wpf-property-mapping.md)
