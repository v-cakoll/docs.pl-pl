---
title: Formularze WPF i Windows
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- nester interoperation [WPF]
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid control [WPF interoperability]
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
ms.openlocfilehash: 76d1e97c92946267aa1217f52c93594fb63d20de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187147"
---
# <a name="wpf-and-windows-forms-interoperation"></a>Współdziałanie WPF i Windows Forms
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]i Windows Forms prezentują dwie różne architektury do tworzenia interfejsów aplikacji. Obszar <xref:System.Windows.Forms.Integration?displayProperty=nameWithType> nazw zawiera klasy, które umożliwiają typowe scenariusze współpracy. Dwie kluczowe klasy, które implementują <xref:System.Windows.Forms.Integration.WindowsFormsHost> możliwości <xref:System.Windows.Forms.Integration.ElementHost>współpracy są i . W tym temacie opisano, które scenariusze współpracy są obsługiwane, a które scenariusze nie są obsługiwane.  
  
> [!NOTE]
> Szczególną uwagę zwraca się na scenariusz *kontroli hybrydowej.* Sterowanie hybrydowe ma kontrolę z jednej technologii zagnieżdżonej w formancie z drugiej technologii. Jest to również *nazywane zagnieżdżoną interoperacyjności*. *Wielopoziomowy formant hybrydowy* ma więcej niż jeden poziom zagnieżdżania kontroli hybrydowej. Przykładem wielopoziomowej zagnieżdżonej współpracy jest [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formant Windows Forms, który zawiera formant, który zawiera inny formant Windows Forms. Wielopoziomowe hybrydowe formanty nie są obsługiwane.  

<a name="Windows_Presentation_Foundation_Application_Hosting"></a>
## <a name="hosting-windows-forms-controls-in-wpf"></a>Hostowanie formantów formularzy systemu Windows w programie WPF  
 Następujące scenariusze współpracy są obsługiwane, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gdy formant obsługuje formant Windows Forms:  
  
- Formant [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] może obsługiwać jeden lub więcej formantów Windows Forms przy użyciu języka XAML.  
  
- Może obsługiwać jeden lub więcej formantów Windows Forms przy użyciu kodu.  
  
- Może obsługiwać formanty kontenera Windows Forms, które zawierają inne formanty formularzy systemu Windows.  
  
- Może być hostowanie formularza głównego/szczegółowego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ze szczegółami wzorca i formularzy systemu Windows.  
  
- Może być gospodarzem formularza wzorca/szczegółu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] z wzorcem formularzy systemu Windows i szczegółami.  
  
- Może obsługiwać jeden lub więcej formantów ActiveX.  
  
- Może obsługiwać jeden lub więcej formantów złożonych.  
  
- Może obsługiwać kontrolki hybrydowe przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
- Może obsługiwać kontrolki hybrydowe przy użyciu kodu.  
  
### <a name="layout-support"></a>Obsługa układu  
 Na poniższej liście opisano <xref:System.Windows.Forms.Integration.WindowsFormsHost> znane ograniczenia, gdy element próbuje zintegrować swój hostowany formant Windows Forms z systemem układowym. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
- W niektórych przypadkach formantów Windows Forms nie można zwymiarować ani rozmiarować tylko do określonych wymiarów. Na przykład formant <xref:System.Windows.Forms.ComboBox> Windows Forms obsługuje tylko jedną wysokość, która jest zdefiniowana przez rozmiar czcionki formantu. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układzie dynamicznym, który zakłada, że elementy <xref:System.Windows.Forms.ComboBox> można rozciągnąć pionowo, hostowane formant nie będzie rozciągać zgodnie z oczekiwaniami.  
  
- Formantów Formularzy systemu Windows nie można obracać ani pochylać. Na przykład po obróceniu interfejsu użytkownika o 90 stopni, hostowane formanty windows forms zachowają ich pozycję pionową.  
  
- W większości przypadków formanty windows forms nie obsługują skalowania proporcjonalnego. Chociaż ogólne wymiary formantu będzie skalować, formanty podrzędne i elementy składowe formantu nie może zmienić rozmiar zgodnie z oczekiwaniami. To ograniczenie zależy od tego, jak dobrze każdy formant formularzy systemu Windows obsługuje skalowanie.  
  
- W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsie użytkownika można zmienić kolejność z elementów, aby kontrolować nakładające się zachowanie. Hostowany formant formularzy systemu Windows jest rysowany w oddzielnym [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND, więc jest zawsze rysowany na wierzchu elementów.  
  
- Formularze systemu Windows steruje obsługą skalowania automatycznego na podstawie rozmiaru czcionki. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsie użytkownika zmiana rozmiaru czcionki nie zmienia rozmiaru całego układu, chociaż poszczególne elementy mogą dynamicznie zmieniać rozmiar.  
  
### <a name="ambient-properties"></a>Właściwości otoczenia  
 Niektóre właściwości otoczenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formantów mają odpowiedniki formularzy systemu Windows. Te właściwości otoczenia są propagowane do hostowanych formantów windows <xref:System.Windows.Forms.Integration.WindowsFormsHost> forms i udostępniane jako właściwości publiczne w formancie. Formant <xref:System.Windows.Forms.Integration.WindowsFormsHost> tłumaczy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] każdą właściwość otoczenia na jego odpowiednik windows forms.  
  
 Aby uzyskać więcej informacji, zobacz [Formularze systemu Windows i mapowanie właściwości WPF](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Zachowanie  
 W poniższej tabeli opisano zachowanie operacji współdziałania.  
  
|Zachowanie|Obsługiwane|Nieobsługiwane|  
|--------------|---------------|-------------------|  
|Przezroczystość|Renderowanie formantu Formularze systemu Windows obsługuje przezroczystość. Tło formantu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nadrzędnego może stać się tłem hostowanych formantów formularzy systemu Windows.|Niektóre formanty formularzy systemu Windows nie obsługują przezroczystości. Na przykład <xref:System.Windows.Forms.TextBox> i <xref:System.Windows.Forms.ComboBox> formanty nie będą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]przezroczyste, gdy hostowane przez program .|  
|Tabulatorem|Kolejność tabulatorów dla hostowanych formantów formularzy systemu Windows jest taka sama, jak wtedy, gdy te formanty są hostowane w aplikacji opartej na formularzach systemu Windows.<br /><br /> Tabulatorowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] z formantu do formantu Windows Forms za pomocą klawisza TAB i klawiszy SHIFT+TAB działa jak zwykle.<br /><br /> Formantów formularzy <xref:System.Windows.Forms.Control.TabStop%2A> systemu `false` Windows, które mają wartość właściwości nie otrzymują fokus, gdy użytkownik karty za pomocą formantów.<br /><br /> - <xref:System.Windows.Forms.Integration.WindowsFormsHost> Każdy formant ma <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> wartość, <xref:System.Windows.Forms.Integration.WindowsFormsHost> która określa, kiedy ta formant otrzyma fokus.<br />- Formantów windows forms, <xref:System.Windows.Forms.Integration.WindowsFormsHost> które znajdują się <xref:System.Windows.Forms.Control.TabIndex%2A> wewnątrz kontenera postępuj zgodnie z kolejnością określoną przez właściwość. Tabulowanie z indeksu ostatniej karty [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kładzie fokus na następny formant, jeśli istnieje. Jeśli nie istnieje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] żadna inna formant focusable, tabulator powraca do pierwszego formantu Windows Forms w kolejności tabulacji.<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>wartości formanty <xref:System.Windows.Forms.Integration.WindowsFormsHost> wewnątrz są względem równorzędnych <xref:System.Windows.Forms.Integration.WindowsFormsHost> formantów Windows Forms, które są zawarte w formancie.<br />- Tabulator honoruje zachowanie specyficzne dla kontroli. Na przykład naciśnięcie klawisza <xref:System.Windows.Forms.TextBox> TAB w <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> formancie, który ma wartość `true` właściwości, wprowadza kartę w polu tekstowym zamiast przenoszenia fokusu.|Nie dotyczy.|  
|Nawigacja za pomocą klawiszy strzałek|- Nawigacja z <xref:System.Windows.Forms.Integration.WindowsFormsHost> klawiszami strzałek w formancie jest taka sama jak w zwykłym formancie kontenera Windows Forms: klawisze STRZAŁKA W GÓRĘ i STRZAŁKA W LEWO wybierają poprzedni kontrolkę, a klawisze STRZAŁKA W DÓŁ i STRZAŁKA W PRAWO wybierają następny formant.<br />- Klawisze STRZAŁKA W GÓRĘ i STRZAŁKA W <xref:System.Windows.Forms.Integration.WindowsFormsHost> LEWO z pierwszego formantu, który znajduje się w formancie, wykonują tę samą akcję, co skrót klawiaturowy SHIFT+TAB. Jeśli istnieje kontrolka focusable, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Forms.Integration.WindowsFormsHost> fokus przenosi poza formant. To zachowanie różni się <xref:System.Windows.Forms.ContainerControl> od standardowego zachowania, ponieważ nie występuje zawijanie do ostatniego formantu. Jeśli nie istnieje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] żadna inna formant focusable, fokus powraca do ostatniego formantu Windows Forms w kolejności tabulacji.<br />- Klawisze STRZAŁKA W DÓŁ i STRZAŁKA W <xref:System.Windows.Forms.Integration.WindowsFormsHost> PRAWO z ostatniego formantu, który znajduje się w formancie, wykonują tę samą akcję co klawisz TAB. Jeśli istnieje kontrolka focusable, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Forms.Integration.WindowsFormsHost> fokus przenosi poza formant. To zachowanie różni się <xref:System.Windows.Forms.ContainerControl> od standardowego zachowania, ponieważ nie występuje zawijanie do pierwszego formantu. Jeśli nie istnieje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] żadna inna formant focusable, fokus powraca do pierwszego formantu Windows Forms w kolejności tabulacji.|Nie dotyczy.|  
|Akceleratory|Akceleratory działają jak zwykle, z wyjątkiem przypadków wymienionych w kolumnie "Nie obsługiwane".|Zduplikowane akceleratory w różnych technologiach nie działają jak zwykłe zduplikowane akceleratory. Gdy akcelerator jest duplikowany między technologiami, z co [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] najmniej jednym w formancie Windows Forms, a drugi na formancie, formant Windows Forms zawsze odbiera akcelerator. Fokus nie przełącza się między formantami po naciśnięciu zduplikowanego akceleratora.|  
|Klawisze skrótów|Klawisze skrótów działają jak zwykle, z wyjątkiem sytuacji, gdy zaznaczono w kolumnie "Nie obsługiwane".|- Klawisze skrótów formularzy systemu Windows, które są obsługiwane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na etapie przetwarzania wstępnego, zawsze mają pierwszeństwo przed klawiszami skrótów. Na przykład jeśli masz <xref:System.Windows.Forms.ToolStrip> formant z ctrl + S klawisze skrótów zdefiniowane i istnieje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] polecenie powiązane z CTRL + S, program obsługi <xref:System.Windows.Forms.ToolStrip> jest zawsze wywoływane najpierw, niezależnie od fokusu.<br />- Klawisze skrótów formularzy <xref:System.Windows.Forms.Control.KeyDown> systemu Windows obsługiwane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]przez zdarzenie są przetwarzane jako ostatnie w programie . Można zapobiec takie zachowanie, zastępując <xref:System.Windows.Forms.Control.IsInputKey%2A> metodę formantu Windows <xref:System.Windows.Forms.Control.PreviewKeyDown> Forms lub obsługi zdarzenia. Powrót `true` z <xref:System.Windows.Forms.Control.IsInputKey%2A> metody lub ustawić wartość <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType> właściwości `true` w <xref:System.Windows.Forms.Control.PreviewKeyDown> programie obsługi zdarzeń.|  
|AkceptujeReturn, AcceptsTab i inne zachowanie specyficzne dla formantu|Właściwości, które zmieniają domyślne zachowanie klawiatury działają jak zwykle, <xref:System.Windows.Forms.Control.IsInputKey%2A> przy założeniu, że formant Windows Forms zastępuje metodę zwracania `true`.|Formantów windows forms, które <xref:System.Windows.Forms.Control.KeyDown> zmieniają domyślne zachowanie klawiatury przez obsługę zdarzenia są przetwarzane ostatnio w formancie hosta. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ponieważ te formanty są przetwarzane jako ostatnie, mogą powodować nieoczekiwane zachowanie.|  
|Wprowadzanie i opuszczanie zdarzeń|Gdy fokus nie przechodzi <xref:System.Windows.Forms.Integration.ElementHost> do formantu zawierającego, Enter i Leave <xref:System.Windows.Forms.Integration.WindowsFormsHost> zdarzenia są wywoływane jak zwykle, gdy zmienia fokus w jednym formancie.|Zdarzenia Enter i Leave nie są wywoływane po wystąpieniu następujących zmian fokusu:<br /><br /> - Od wewnątrz <xref:System.Windows.Forms.Integration.WindowsFormsHost> do zewnątrz kontroli.<br />- Z zewnątrz <xref:System.Windows.Forms.Integration.WindowsFormsHost> do wewnątrz kontroli.<br />- Poza <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontrolą.<br />- Z formantu Windows <xref:System.Windows.Forms.Integration.WindowsFormsHost> Forms hostowanego w formancie do <xref:System.Windows.Forms.Integration.ElementHost> formantu hostowanego wewnątrz tego samego <xref:System.Windows.Forms.Integration.WindowsFormsHost>.|  
|Wielowątkowość|Obsługiwane są wszystkie odmiany wielowątkowe.|Zarówno formularze [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systemu Windows, jak i technologie zakładają model współbieżności jednowątkowej. Podczas debugowania wywołania obiektów struktury z innych wątków spowoduje wyjątek wymuszania tego wymogu.|  
|Zabezpieczenia|Wszystkie scenariusze współpracy wymagają pełnego zaufania.|Żadne scenariusze współpracy nie są dozwolone w częściowym zaufaniu.|  
|Ułatwienia dostępu|Obsługiwane są wszystkie scenariusze ułatwień dostępu. Produkty technologii ułatwiwczej działają poprawnie, gdy są używane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dla aplikacji hybrydowych, które zawierają zarówno formularze systemu Windows, jak i formanty.|Nie dotyczy.|  
|Schowek|Wszystkie operacje schowka działają jak zwykle. Obejmuje to wycinanie i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wklejanie między formularzami systemu Windows i formantami.|Nie dotyczy.|  
|Funkcja przeciągania i upuszczania|Wszystkie operacje przeciągania i upuszczania działają jak zwykle. Obejmuje to operacje między [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formularzami systemu Windows i formantami.|Nie dotyczy.|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>
## <a name="hosting-wpf-controls-in-windows-forms"></a>Hostowanie formantów WPF w formularzach systemu Windows  
 Następujące scenariusze współpracy są obsługiwane, gdy formant [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Windows Forms obsługuje formant:  
  
- Hostowanie jednego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lub więcej formantów przy użyciu kodu.  
  
- Kojarzenie arkusza właściwości z co [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] najmniej jednym hostowanym formantem.  
  
- Hostowanie jednej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lub więcej stron w formularzu.  
  
- Uruchamianie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] okna.  
  
- Hostowanie formularza wzorca/szczegółów z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wzorcem formularzy systemu Windows i szczegółami.  
  
- Hostowanie formularza wzorca/szczegółów ze [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] szczegółami wzorca i formularzy systemu Windows.  
  
- Hostowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] niestandardowych formantów.  
  
- Hosting elementów sterujących hybrydowych.  
  
### <a name="ambient-properties"></a>Właściwości otoczenia  
 Niektóre właściwości otoczenia formantów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] windows forms mają odpowiedniki. Te właściwości otoczenia są propagowane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do hostowanych formantów <xref:System.Windows.Forms.Integration.ElementHost> i udostępniane jako właściwości publiczne w formancie. Formant <xref:System.Windows.Forms.Integration.ElementHost> tłumaczy każdą właściwość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] otoczenia windows forms na jej odpowiednik.  
  
 Aby uzyskać więcej informacji, zobacz [Formularze systemu Windows i mapowanie właściwości WPF](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Zachowanie  
 W poniższej tabeli opisano zachowanie operacji współdziałania.  
  
|Zachowanie|Obsługiwane|Nieobsługiwane|  
|--------------|---------------|-------------------|  
|Przezroczystość|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]renderowanie sterowania obsługuje przezroczystość. Tło nadrzędnego formantu Windows Forms może [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stać się tłem hostowanych formantów.|Nie dotyczy.|  
|Wielowątkowość|Obsługiwane są wszystkie odmiany wielowątkowe.|Zarówno formularze [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systemu Windows, jak i technologie zakładają model współbieżności jednowątkowej. Podczas debugowania wywołania obiektów struktury z innych wątków spowoduje wyjątek wymuszania tego wymogu.|  
|Zabezpieczenia|Wszystkie scenariusze współpracy wymagają pełnego zaufania.|Żadne scenariusze współpracy nie są dozwolone w częściowym zaufaniu.|  
|Ułatwienia dostępu|Obsługiwane są wszystkie scenariusze ułatwień dostępu. Produkty technologii ułatwiwczej działają poprawnie, gdy są używane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dla aplikacji hybrydowych, które zawierają zarówno formularze systemu Windows, jak i formanty.|Nie dotyczy.|  
|Schowek|Wszystkie operacje schowka działają jak zwykle. Obejmuje to wycinanie i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wklejanie między formularzami systemu Windows i formantami.|Nie dotyczy.|  
|Funkcja przeciągania i upuszczania|Wszystkie operacje przeciągania i upuszczania działają jak zwykle. Obejmuje to operacje między [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formularzami systemu Windows i formantami.|Nie dotyczy.|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Wskazówki: hosting formantu Windows Forms w WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Przewodnik: hosting złożonej kontrolki Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Przewodnik: hosting złożonej kontrolki WPF w Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Mapowanie właściwości Windows Forms i WPF](windows-forms-and-wpf-property-mapping.md)
