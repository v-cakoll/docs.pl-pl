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
ms.openlocfilehash: 2e3390c3e387e75168958f946472a5a24a4bd440
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129275"
---
# <a name="wpf-and-windows-forms-interoperation"></a>Współdziałanie WPF i Windows Forms
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] przedstawić dwie różne architektury służące do tworzenia interfejsów aplikacji. <xref:System.Windows.Forms.Integration?displayProperty=nameWithType> Przestrzeń nazw zawiera klasy, które umożliwiają typowych scenariuszy współdziałanie. Są dwa klucza klasy, które implementują funkcje współdziałanie <xref:System.Windows.Forms.Integration.WindowsFormsHost> i <xref:System.Windows.Forms.Integration.ElementHost>. W tym temacie opisano, jakie współdziałanie scenariusze są obsługiwane i scenariuszy, do których nie są obsługiwane.  
  
> [!NOTE]
>  Jest szczególną uwagę na *formant hybrydowy* scenariusza. Formant hybrydowy zawiera formant z jednej technologii zagnieżdżona w kontrolki z poziomu innej technologii. Jest to również nazywane *zagnieżdżone współdziałanie*. A *formant hybrydowy wielopoziomowej* ma więcej niż jeden poziom hybrydowego kontrolować zagnieżdżania. Na przykład wielopoziomowej, zagnieżdżonej współdziałanie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolkę zawierającą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formant, który zawiera inny [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli. Formanty wielopoziomowej hybrydowe nie są obsługiwane.  

<a name="Windows_Presentation_Foundation_Application_Hosting"></a>   
## <a name="hosting-windows-forms-controls-in-wpf"></a>Kontrolek hostingu Windows Forms w WPF  
 Obsługiwane są następujące scenariusze współdziałanie podczas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formant obsługuje formant programu Windows Forms:  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Kontrolki mogą być hostowane w co najmniej jeden [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki przy użyciu XAML.  
  
-   Mogą być hostowane, co najmniej jeden [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki przy użyciu kodu.  
  
-   Może być obsługiwanych [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrole kontenerów, które zawierają inne [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki.  
  
-   Może być obsługiwanych formularza wzorzec/szczegół za pomocą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] głównego i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] szczegółowe informacje.  
  
-   Może być obsługiwanych formularza wzorzec/szczegół za pomocą [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] głównego i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] szczegółowe informacje.  
  
-   Mogą być hostowane, co najmniej jeden [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] kontrolki.  
  
-   Może on hostowanie jedną lub więcej kontrolek złożonych.  
  
-   Może być obsługiwanych kontrolek hybrydowych przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
-   Może on hosta kontrolek hybrydowych przy użyciu kodu.  
  
### <a name="layout-support"></a>Obsługa układów  
 Na poniższej liście opisano znane ograniczenia podczas <xref:System.Windows.Forms.Integration.WindowsFormsHost> element próbuje integrowanie swojej hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sterowania do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] system układu.  
  
-   W niektórych przypadkach [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty nie można zmienić rozmiaru lub rozmiar można zmieniać tylko dla określonych wymiarów. Na przykład [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> kontrolka obsługuje tylko jedną wysokość, która jest zdefiniowana przez rozmiar czcionki formantu. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dynamicznego układu, w którym przyjęto założenie, że elementy rozciągnąć pionowo, hostowany <xref:System.Windows.Forms.ComboBox> nie można rozproszyć kontrolki, zgodnie z oczekiwaniami.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki nie można obracać lub nierówne. Na przykład, gdy interfejs użytkownika jest obrót o 90 stopni, hostowane [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] będą one zachowywały ich pozycji pionowo.  
  
-   W większości przypadków [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów nie obsługują skalowanie proporcjonalne. Mimo że będzie się skalować wymiary formantu formanty podrzędne i elementy składowe formantu może nie zmienić rozmiar zgodnie z oczekiwaniami. To ograniczenie zależy od stopnia każdy [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolka obsługuje skalowanie.  
  
-   W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsu użytkownika można zmienić porządek elementów do formantu nakładających się zachowanie. Hostowany [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] rysowania kontrolki w oddzielnych HWND, dzięki czemu jest zawsze wstawiany w górnej części [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementów.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Formanty obsługują skalowanie automatyczne w oparciu o rozmiar czcionki. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsu użytkownika, zmienianie rozmiaru czcionki nie zmienia rozmiaru całej układ, mimo że poszczególne elementy mogą dynamicznie rozmiar.  
  
### <a name="ambient-properties"></a>Właściwości otoczenia  
 Niektóre właściwości otoczenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formanty mają [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] odpowiedniki. Te właściwości otoczenia są propagowane do obsługiwanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroluje i udostępniane jako właściwości publiczne na <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Kontroli tłumaczy każdego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zmieniono właściwość do jego [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] równoważne.  
  
 Aby uzyskać więcej informacji, zobacz [Windows Forms i WPF właściwość mapowanie](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Zachowanie  
 W poniższej tabeli opisano współdziałanie zachowanie.  
  
|Zachowanie|Obsługiwane|Nieobsługiwane|  
|--------------|---------------|-------------------|  
|Przezroczystość|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Renderowanie formantu obsługuje przezroczystość. Tło elementu nadrzędnego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontroli może stać się tła hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki.|Niektóre [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów nie obsługują przezroczystość. Na przykład <xref:System.Windows.Forms.TextBox> i <xref:System.Windows.Forms.ComboBox> kontrolki nie będzie w przezroczysty, w przypadku hostowania za [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|  
|TAB|Kolejność tabulacji dla hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki jest taka sama jak gdy te kontrolki znajdują się w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-aplikacji opartej na.<br /><br /> Tabulacja w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolę [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolką naciśnij klawisz TAB lub klawisze SHIFT + TAB działa w zwykły sposób.<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty, które mają <xref:System.Windows.Forms.Control.TabStop%2A> wartość właściwości `false` nie przenieść fokus, gdy użytkownik karty za pomocą kontrolki.<br /><br /> -Każdy <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontrolkę <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> wartość, która określa, kiedy, <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli otrzyma fokus.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty, które są zawarte wewnątrz <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontenera, postępuj zgodnie z kolejnością określoną przez <xref:System.Windows.Forms.Control.TabIndex%2A> właściwości. Tabulacja od ostatniego kolejność tabulacji umieszcza skoncentrować się na następnej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolować, jeśli taka istnieje. Jeśli nie inne focusable [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] istnieje kontroli tabulacji powrót do pierwszego [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli w kolejności tabulacji.<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> wartości kontrolek w <xref:System.Windows.Forms.Integration.WindowsFormsHost> są względne wobec element równorzędny [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów, które są zawarte w <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli.<br />-Tabulacji honoruje specyficznej dla kontroli zachowania. Na przykład naciśnięcie klawisza TAB w <xref:System.Windows.Forms.TextBox> formantu, który ma <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> wartość właściwości `true` wprowadza karty w polu tekstowym, zamiast przenoszenia fokusu.|Nie dotyczy.|  
|Nawigacja z użyciem klawisze strzałek|— Nawigacja z użyciem strzałkę klucze w <xref:System.Windows.Forms.Integration.WindowsFormsHost> formant jest taki sam jak zwykłej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formant kontenera: Strzałka w górę i Strzałka w lewo zaznacz poprzednią kontrolkę i klawiszy Strzałka w dół i Strzałka w prawo zaznacz następną kontrolkę.<br />SIĘ strzałka w lewo i strzałki kluczy z pierwszy formant, który jest zawarty w <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli wykonania tego samego działania jako skrót klawiaturowy SHIFT + TAB. W przypadku focusable [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontroli fokusu poza <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli. To zachowanie różni się od standardowej <xref:System.Windows.Forms.ContainerControl> w tym nie zawijania ostatniej kontroli zachowanie. Jeśli nie inne focusable [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formant istnieje, powrót do ostatnio [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli w kolejności tabulacji.<br />WCIŚNIĘTYCH klawiszy i Strzałka w prawo z ostatniego formantu, który znajduje się w <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli wykonaj tę samą akcję jako klawisz TAB. W przypadku focusable [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontroli fokusu poza <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli. To zachowanie różni się od standardowej <xref:System.Windows.Forms.ContainerControl> w tym bez zawijania pierwszy formant zachowanie. Jeśli nie inne focusable [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formant istnieje, sterowanie przechodzi pierwszy [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli w kolejności tabulacji.|Nie dotyczy.|  
|Akceleratory|Akceleratory działają w zwykły sposób, z wyjątkiem sytuacji, gdy wskazane w kolumnie "Nie jest obsługiwany".|Nie działają duplikowania akceleratorów różnych technologii takich jak zwykłe duplikowania akceleratorów. Po akceleratorze występuje na wielu technologii z co najmniej jednym na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli, a drugi na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontroli [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantu zawsze będzie otrzymywał akceleratora. Fokus nie Przełącz między formantami po naciśnięciu zduplikowanych klawiszy skrótów.|  
|Klawisze skrótów|Klawisze skrótów działają w zwykły sposób, z wyjątkiem sytuacji, gdy wskazane w kolumnie "Nie jest obsługiwany".|-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] klawisze skrótów, które są obsługiwane w fazie przetwarzania wstępnego, zawsze mają pierwszeństwo względem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klawiszy skrótów. Na przykład, jeśli masz <xref:System.Windows.Forms.ToolStrip> kontrolką zdefiniowane klawisze skrótu CTRL + S, a istnieje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] polecenia powiązany z CTRL + S, <xref:System.Windows.Forms.ToolStrip> program obsługi sterowania zawsze jest wywoływany po pierwsze, niezależnie od tego, fokus.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] klawisze skrótów, które są obsługiwane przez <xref:System.Windows.Forms.Control.KeyDown> zdarzeń są przetwarzane jako ostatnie w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. To zachowanie można zapobiec przez zastąpienie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki <xref:System.Windows.Forms.Control.IsInputKey%2A> metoda lub obchodzenia <xref:System.Windows.Forms.Control.PreviewKeyDown> zdarzeń. Zwróć `true` z <xref:System.Windows.Forms.Control.IsInputKey%2A> metody, lub ustaw wartość <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType> właściwości `true` w swojej <xref:System.Windows.Forms.Control.PreviewKeyDown> programu obsługi zdarzeń.|  
|AcceptsReturn AcceptsTab zostanie zmieniona i innych zachowań specyficznej dla kontroli|Właściwości, zmienić domyślne zachowanie klawiatury, które działają w zwykły sposób, przy założeniu, że [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolować zastąpienia <xref:System.Windows.Forms.Control.IsInputKey%2A> metodę, aby zwrócić `true`.|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty, które zmienić ustawienie domyślne za pomocą klawiatury zachowanie obsługi <xref:System.Windows.Forms.Control.KeyDown> zdarzeń są przetwarzane jako ostatnie na hoście [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontroli. Ponieważ te kontrolki są przetwarzane jako ostatnie, może powodować nieoczekiwane zachowanie.|  
|Wprowadź i pozostawić zdarzenia|Gdy fokus nie zostanie zawierający <xref:System.Windows.Forms.Integration.ElementHost> kontroli, Enter i pozostaw zdarzenia są wywoływane w zwykły sposób, gdy zmiana fokusu w jednym <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli.|Wprowadź i pozostaw zdarzenia nie są wywoływane, gdy wystąpią następujące zmiany fokus:<br /><br /> -Od wewnątrz-poza <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli.<br />-Z zewnątrz do wewnątrz <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli.<br />-Poza <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli.<br />-From [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sterowania hostowaną w <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontrolę <xref:System.Windows.Forms.Integration.ElementHost> kontrolka jest hostowana w taki sam <xref:System.Windows.Forms.Integration.WindowsFormsHost>.|  
|Wielowątkowość|Wszystkie odmiany wielowątkowość są obsługiwane.|Zarówno [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] technologii przyjęto założenie, model jednowątkowe współbieżności. Podczas debugowania, wywołań framework obiektów z innych wątków zgłosi wyjątek, aby wymusić to wymaganie.|  
|Zabezpieczenia|Wszystkie scenariusze współdziałanie wymaga pełnego zaufania.|Scenariusze współdziałanie, nie są dozwolone w częściowej relacji zaufania.|  
|Ułatwienia dostępu|Wszystkie scenariusze ułatwień dostępu są obsługiwane. Produkty technologii pomocniczej działać prawidłowo, jeśli są one używane w przypadku aplikacji hybrydowych, które zawierają zarówno [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.|Nie dotyczy.|  
|Schowek|Wszystkie operacje na schowku pracować w zwykły sposób. Obejmuje to wycinanie i wklejanie między [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.|Nie dotyczy.|  
|Funkcja przeciągania i upuszczania|Wszystkie operacje przeciągania i upuszczania pracować w zwykły sposób. Dotyczy to również operacji między [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.|Nie dotyczy.|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>   
## <a name="hosting-wpf-controls-in-windows-forms"></a>Hosting kontrolek WPF w formularzach Windows Forms  
 Gdy hosty formantu Windows Forms, obsługiwane są następujące scenariusze współdziałanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sterowania:  
  
-   Hostuje co najmniej jedną [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki przy użyciu kodu.  
  
-   Kojarzenie właściwości arkusza za pomocą jednego lub więcej hostowanej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.  
  
-   Hostuje co najmniej jedną [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stron w formularzu.  
  
-   Uruchamianie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] okna.  
  
-   Hosting formularza wzorzec/szczegół za pomocą [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] głównego i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] szczegółowe informacje.  
  
-   Hosting formularza wzorzec/szczegół za pomocą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] głównego i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] szczegółowe informacje.  
  
-   Hostowanie niestandardowego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.  
  
-   Hosting kontrolek hybrydowych.  
  
### <a name="ambient-properties"></a>Właściwości otoczenia  
 Niektóre właściwości otoczenia [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty mają [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odpowiedniki. Te właściwości otoczenia są propagowane do obsługiwanej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontroluje i udostępniane jako właściwości publiczne na <xref:System.Windows.Forms.Integration.ElementHost> kontroli. <xref:System.Windows.Forms.Integration.ElementHost> Kontroli tłumaczy każdego [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] właściwości otoczenia jego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] równoważne.  
  
 Aby uzyskać więcej informacji, zobacz [Windows Forms i WPF właściwość mapowanie](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Zachowanie  
 W poniższej tabeli opisano współdziałanie zachowanie.  
  
|Zachowanie|Obsługiwane|Nieobsługiwane|  
|--------------|---------------|-------------------|  
|Przezroczystość|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Renderowanie formantu obsługuje przezroczystość. Tło elementu nadrzędnego [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli może stać się tła hostowanej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.|Nie dotyczy.|  
|Wielowątkowość|Wszystkie odmiany wielowątkowość są obsługiwane.|Zarówno [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] technologii przyjęto założenie, model jednowątkowe współbieżności. Podczas debugowania, wywołań framework obiektów z innych wątków zgłosi wyjątek, aby wymusić to wymaganie.|  
|Zabezpieczenia|Wszystkie scenariusze współdziałanie wymaga pełnego zaufania.|Scenariusze współdziałanie, nie są dozwolone w częściowej relacji zaufania.|  
|Ułatwienia dostępu|Wszystkie scenariusze ułatwień dostępu są obsługiwane. Produkty technologii pomocniczej działać prawidłowo, jeśli są one używane w przypadku aplikacji hybrydowych, które zawierają zarówno [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.|Nie dotyczy.|  
|Schowek|Wszystkie operacje na schowku pracować w zwykły sposób. Obejmuje to wycinanie i wklejanie między [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.|Nie dotyczy.|  
|Funkcja przeciągania i upuszczania|Wszystkie operacje przeciągania i upuszczania pracować w zwykły sposób. Dotyczy to również operacji między [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.|Nie dotyczy.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Przewodnik: Hosting kontrolki Windows Forms w WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Przewodnik: Hostowanie kontrolki złożonej Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Przewodnik: Hosting złożonego formantu WPF w formularzach Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Mapowanie właściwości Windows Forms i WPF](windows-forms-and-wpf-property-mapping.md)
