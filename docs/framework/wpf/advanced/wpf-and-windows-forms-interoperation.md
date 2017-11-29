---
title: "Współdziałanie WPF i Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- nester interoperation [WPF]
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid control [WPF interoperability]
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d713a03469edc5d4c950c75c8094386372657486
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="wpf-and-windows-forms-interoperation"></a>Współdziałanie WPF i Windows Forms
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] przedstawia dwie różne architektury do tworzenia interfejsów aplikacji. <xref:System.Windows.Forms.Integration?displayProperty=nameWithType> Przestrzeń nazw zawiera klasy, które umożliwiają typowych scenariuszy współdziałanie. Są dwa klucza klasy, które implementują współdziałanie możliwości <xref:System.Windows.Forms.Integration.WindowsFormsHost> i <xref:System.Windows.Forms.Integration.ElementHost>. W tym temacie opisano, jakie współdziałanie scenariusze są obsługiwane i jakie scenariusze nie są obsługiwane.  
  
> [!NOTE]
>  Specjalny do *kontroli hybrydowego* scenariusza. Formant hybrydowego ma formantu z jednego technologii zagnieżdżone w formancie z innych technologii. Jest to również *zagnieżdżonych współdziałanie*. A *kontroli wielopoziomowej hybrydowego* ma więcej niż jeden poziom elementów hybrydowego kontrolować zagnieżdżenia. Na przykład wielopoziomowej współdziałanie zagnieżdżonych [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formant, który zawiera [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formantu, który zawiera inny [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantu. Formanty wielopoziomowej hybrydowe nie są obsługiwane.  
  
  
<a name="Windows_Presentation_Foundation_Application_Hosting"></a>   
## <a name="hosting-windows-forms-controls-in-wpf"></a>Hosting Windows formantów formularzy na platformie WPF  
 Są obsługiwane następujące scenariusze współdziałanie podczas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolowanie hostów [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] sterowania:  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Formant może obsługiwać jeden lub więcej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] steruje przy użyciu kodu XAML.  
  
-   Mogą być hostowane, co najmniej jeden [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] steruje przy użyciu kodu.  
  
-   Może być obsługiwanych [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrole kontenerów, które zawierają inne [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki.  
  
-   Mogą być hostowane formularza wzorzec/szczegół z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wzorca i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] szczegóły.  
  
-   Mogą być hostowane formularza wzorzec/szczegół z [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] wzorca i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] szczegóły.  
  
-   Mogą być hostowane, co najmniej jeden [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] kontrolki.  
  
-   Go może obsługiwać jeden lub kilka formantów złożonych.  
  
-   Mogą być hostowane kontrolki hybrydowych przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
-   Może on hosta formanty hybrydowych przy użyciu kodu.  
  
### <a name="layout-support"></a>Obsługa układu  
 Poniżej opisano znane ograniczenia podczas <xref:System.Windows.Forms.Integration.WindowsFormsHost> element próbuje integracji jego hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sterowania do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układu systemu.  
  
-   W niektórych przypadkach [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów nie można zmienić rozmiaru lub mogą być określane tylko do określonych wymiarów. Na przykład [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> sterowanie obsługuje tylko pojedynczy wysokości, który jest zdefiniowany przez rozmiar czcionki formantu. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układ dynamiczny, zakłada się, że elementy można stretch pionie hostowany <xref:System.Windows.Forms.ComboBox> formantu nie rozciąga zgodnie z oczekiwaniami.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]formanty nie można obracać lub niesymetryczna. Na przykład podczas obracania interfejsu użytkownika o 90 stopni, hostowana [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty będzie zachowują swoją pozycję pionowo.  
  
-   W większości przypadków [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty nie obsługują proporcjonalne skalowania. Chociaż Ogólne wymiary formant są skalowane, formantów podrzędnych oraz elementów składowych formant może nie zmienić rozmiar zgodnie z oczekiwaniami. To ograniczenie zależy od jak każdy [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sterowanie obsługuje skalowania.  
  
-   W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsu użytkownika można zmienić porządek osi z elementów do formantu nakładających się zachowanie. Hostowany [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli jest rysowana w oddzielnych HWND, więc jest zawsze wstawiany nad [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementów.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]Formanty obsługuje funkcję skalowania automatycznego na podstawie rozmiaru czcionki. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsu użytkownika, zmienianie rozmiaru czcionki nie zmienia rozmiaru całego układu, mimo że poszczególne elementy mogą zostać dynamicznego dopasowania rozmiaru.  
  
### <a name="ambient-properties"></a>Właściwości otaczających  
 Niektóre właściwości otoczenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formanty mają [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] odpowiedniki. Te właściwości otaczających są propagowane do hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty i udostępniany jako właściwości publiczne na <xref:System.Windows.Forms.Integration.WindowsFormsHost> formantu. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Kontroli tłumaczy każdego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] — właściwość otoczenia do jego [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] równoważne.  
  
 Aby uzyskać więcej informacji, zobacz [formularzy systemu Windows i mapowania właściwości WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Zachowanie  
 W poniższej tabeli opisano współdziałanie zachowanie.  
  
|Zachowanie|Obsługiwane|Nieobsługiwane|  
|--------------|---------------|-------------------|  
|Przezroczystość|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]Renderowanie formantu obsługuje przezroczystość. Tło elementu nadrzędnego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formant może stać się tła hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki.|Niektóre [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty nie obsługują przezroczystość. Na przykład <xref:System.Windows.Forms.TextBox> i <xref:System.Windows.Forms.ComboBox> formanty nie ma być przezroczysty, gdy obsługiwanych przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|  
|Klawisza TAB|Kolejność tabulacji dla obsługiwanych [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów jest taka sama jak po nich znajdują się w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-aplikacji.<br /><br /> Klawisza TAB z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formant [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sterować za pomocą klawisz TAB lub klawisze SHIFT + TAB działa normalnie.<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]formanty, które mają <xref:System.Windows.Forms.Control.TabStop%2A> wartość właściwości `false` nie mają fokus, gdy użytkownik karty za pomocą formantów.<br /><br /> -Każdy <xref:System.Windows.Forms.Integration.WindowsFormsHost> formant ma <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> wartość, która określa, kiedy który <xref:System.Windows.Forms.Integration.WindowsFormsHost> formantu zostanie fokusu.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]formanty, które znajdują się wewnątrz <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontenera postępuj zgodnie z kolejnością określoną przez <xref:System.Windows.Forms.Control.TabIndex%2A> właściwości. Klawisza TAB z ostatnich indeks umieszcza fokus na następne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolować, jeśli taka istnieje. Jeśli nie inne focusable [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] istnieje formantu klawisza TAB zwraca jako pierwszy [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantu w kolejności tabulacji.<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>wartości dla formantów wewnątrz <xref:System.Windows.Forms.Integration.WindowsFormsHost> są względem tego samego poziomu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów, które są zawarte w <xref:System.Windows.Forms.Integration.WindowsFormsHost> formantu.<br />-Klawisza TAB honoruje zachowanie specyficzne dla formantu. Na przykład naciśnięcie klawisza TAB w <xref:System.Windows.Forms.TextBox> formantu, który ma <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> wartość właściwości `true` wprowadza karty w polu tekstowym zamiast przeniesienie fokusu.|Nie dotyczy.|  
|Nawigacja z użyciem klawiszy strzałek|-Klawisze nawigacji ze strzałką w <xref:System.Windows.Forms.Integration.WindowsFormsHost> formant jest taki sam jak zwykły [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantu kontenera: klawiszy Strzałka w górę i Strzałka w lewo wybierz poprzednią kontrolkę, a klawiszy Strzałka w dół i Strzałka w prawo wybierz następnego formantu.<br />-SIĘ klawiszy Strzałka i Strzałka w lewo z pierwszą kontrolkę, który jest zawarty w <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli wykonania ta sama akcja co skrót klawiaturowy SHIFT + TAB. Jeśli focusable [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontroli, fokusu poza <xref:System.Windows.Forms.Integration.WindowsFormsHost> formantu. To zachowanie różni się od standardowego <xref:System.Windows.Forms.ContainerControl> w tym nie zawijania ostatni formant zachowanie. Jeśli nie inne focusable [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formant istnieje, nastąpi powrót do ostatniego [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantu w kolejności tabulacji.<br />-DÓŁ kluczy i Strzałka w prawo z ostatni formant, który jest zawarty w <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli wykonania ta sama akcja co klawisz TAB. Jeśli focusable [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontroli, fokusu poza <xref:System.Windows.Forms.Integration.WindowsFormsHost> formantu. To zachowanie różni się od standardowego <xref:System.Windows.Forms.ContainerControl> w tym bez zawijania pierwszy formant zachowanie. Jeśli nie inne focusable [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formant istnieje, nastąpi powrót do pierwszego [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantu w kolejności tabulacji.|Nie dotyczy.|  
|Akceleratorów|Akceleratorów działać jak zwykle, inaczej w przypadku gdy w kolumnie "Nie jest obsługiwany".|Duplikowania akceleratorów między technologie nie działają podobnie jak zwykłe duplikowania akceleratorów. Gdy akceleratora jest zduplikowany w technologii z co najmniej jednym na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli, a drugi na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontroli, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formant zawsze otrzymuje akceleratora. Fokus nie przełączanie między formantami po naciśnięciu zduplikowanych klawiszy skrótów.|  
|Klawisze skrótu|Klawisze skrótów w zwykły sposób, działają inaczej w przypadku gdy w kolumnie "Nie jest obsługiwany".|-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]klawisze skrótów, które są zawsze obsługiwane na etapie przetwarzania wstępnego pierwszeństwo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klawiszy skrótów. Na przykład, jeśli masz <xref:System.Windows.Forms.ToolStrip> sterować za pomocą klawiszy skrótu CTRL + S zdefiniowany i jest [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] polecenia powiązany CTRL + S <xref:System.Windows.Forms.ToolStrip> obsługi sterowania zawsze jest wywoływana po pierwsze, niezależnie od fokus.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]klawisze skrótów, które są obsługiwane przez <xref:System.Windows.Forms.Control.KeyDown> zdarzenia są przetwarzane jako ostatnie w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Można zapobiec przez zastąpienie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantu <xref:System.Windows.Forms.Control.IsInputKey%2A> metody lub obsługa <xref:System.Windows.Forms.Control.PreviewKeyDown> zdarzeń. Zwraca `true` z <xref:System.Windows.Forms.Control.IsInputKey%2A> metody, lub ustaw wartość <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType> właściwości `true` w Twojej <xref:System.Windows.Forms.Control.PreviewKeyDown> obsługi zdarzeń.|  
|AcceptsReturn, AcceptsTab zostanie zmieniona, a inne zachowanie specyficzne dla formantu|Właściwości, które spowodują zmianę domyślnego zachowania klawiatury pracować w zwykły sposób, przy założeniu, że [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolować zastąpienia <xref:System.Windows.Forms.Control.IsInputKey%2A> metodę, aby zwrócić `true`.|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]formanty, które zmienić ustawienie domyślne klawiatury zachowanie obsługa <xref:System.Windows.Forms.Control.KeyDown> zdarzenia są przetwarzane jako ostatnie na hoście [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formantu. Ponieważ te formanty są przetwarzane jako ostatnie, może powodować nieoczekiwane zachowanie.|  
|Wprowadź i pozostawić zdarzenia|Gdy fokus nie będzie zawierający <xref:System.Windows.Forms.Integration.ElementHost> kontroli, wprowadź i pozostaw zdarzenia są zgłaszane w zwykły sposób, gdy fokus się zmieni się w jednej <xref:System.Windows.Forms.Integration.WindowsFormsHost> formantu.|Wprowadź i pozostaw zdarzenia nie są wywoływane, gdy występują następujące zmiany fokusu:<br /><br /> -Z wnętrza poza <xref:System.Windows.Forms.Integration.WindowsFormsHost> formantu.<br />-Z zewnątrz do wewnątrz <xref:System.Windows.Forms.Integration.WindowsFormsHost> formantu.<br />-Poza <xref:System.Windows.Forms.Integration.WindowsFormsHost> formantu.<br />-From [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli hostowanych w <xref:System.Windows.Forms.Integration.WindowsFormsHost> formant <xref:System.Windows.Forms.Integration.ElementHost> kontrolka jest hostowana w taki sam <xref:System.Windows.Forms.Integration.WindowsFormsHost>.|  
|Wielowątkowość|Wszystkie odmiany wielowątkowość są obsługiwane.|Zarówno [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] technologii założono modelu jednowątkowe współbieżności. Podczas debugowania, wywołań obiekty struktury z innych wątków zgłosi wyjątek, aby wymusić to wymaganie.|  
|Zabezpieczenia|Wszystkie scenariusze współdziałanie wymagają pełnego zaufania.|Nie współdziałanie scenariusze są dozwolone w częściowej relacji zaufania.|  
|Ułatwienia dostępu|Obsługiwane są wszystkie scenariusze ułatwień dostępu. Produkty technologii pomocniczej działać prawidłowo, jeśli są one używane dla hybrydowych aplikacji, które zawierają zarówno [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.|Nie dotyczy.|  
|Schowek|Wszystkie operacje schowka działać jak zwykle. Obejmuje to wycinanie i wklejanie między [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.|Nie dotyczy.|  
|Funkcja przeciągania i upuszczania|Wszystkie operacje przeciągania i upuszczania działać jak zwykle. Obejmuje to operacje między [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.|Nie dotyczy.|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>   
## <a name="hosting-wpf-controls-in-windows-forms"></a>Hosting formantów WPF w formularzach systemu Windows  
 Są obsługiwane następujące scenariusze współdziałanie podczas [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] kontrolowanie hostów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sterowania:  
  
-   Hosting co najmniej jeden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] steruje przy użyciu kodu.  
  
-   Kojarzenie właściwości arkusza z jedną lub więcej hostowanej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.  
  
-   Hosting co najmniej jeden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stron w formularzu.  
  
-   Uruchamianie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] okna.  
  
-   Hosting formularza wzorzec/szczegół z [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] wzorca i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] szczegóły.  
  
-   Hosting formularza wzorzec/szczegół z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wzorca i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] szczegóły.  
  
-   Hosting niestandardowe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.  
  
-   Hosting formantów hybrydowego.  
  
### <a name="ambient-properties"></a>Właściwości otaczających  
 Niektóre właściwości otoczenia [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty mają [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odpowiedniki. Te właściwości otaczających są propagowane do hostowanej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formanty i udostępniany jako właściwości publiczne na <xref:System.Windows.Forms.Integration.ElementHost> formantu. <xref:System.Windows.Forms.Integration.ElementHost> Kontroli tłumaczy każdego [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] — właściwość otoczenia do jego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] równoważne.  
  
 Aby uzyskać więcej informacji, zobacz [formularzy systemu Windows i mapowania właściwości WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Zachowanie  
 W poniższej tabeli opisano współdziałanie zachowanie.  
  
|Zachowanie|Obsługiwane|Nieobsługiwane|  
|--------------|---------------|-------------------|  
|Przezroczystość|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Renderowanie formantu obsługuje przezroczystość. Tło elementu nadrzędnego [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formant może stać się tła hostowanej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.|Nie dotyczy.|  
|Wielowątkowość|Wszystkie odmiany wielowątkowość są obsługiwane.|Zarówno [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] technologii założono modelu jednowątkowe współbieżności. Podczas debugowania, wywołań obiekty struktury z innych wątków zgłosi wyjątek, aby wymusić to wymaganie.|  
|Zabezpieczenia|Wszystkie scenariusze współdziałanie wymagają pełnego zaufania.|Nie współdziałanie scenariusze są dozwolone w częściowej relacji zaufania.|  
|Ułatwienia dostępu|Obsługiwane są wszystkie scenariusze ułatwień dostępu. Produkty technologii pomocniczej działać prawidłowo, jeśli są one używane dla hybrydowych aplikacji, które zawierają zarówno [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.|Nie dotyczy.|  
|Schowek|Wszystkie operacje schowka działać jak zwykle. Obejmuje to wycinanie i wklejanie między [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.|Nie dotyczy.|  
|Funkcja przeciągania i upuszczania|Wszystkie operacje przeciągania i upuszczania działać jak zwykle. Obejmuje to operacje między [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.|Nie dotyczy.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Wskazówki: Hostowanie kontrolki formularza systemu Windows na platformie WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [Wskazówki: Obsługa formantu złożonego formularzy systemu Windows na platformie WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Wskazówki: Hostowanie formantu złożonego WPF w formularzach systemu Windows](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [Mapowanie właściwości WPF i formularze systemu Windows](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)
