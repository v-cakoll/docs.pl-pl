---
title: Opcje układu dla elementu WindowsFormsHost
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element layout considerations [WPF]
- dynamic layout [WPF interoperability]
- device-independent pixels
ms.assetid: 3c574597-bbde-440f-95cc-01371f1a5d9d
ms.openlocfilehash: 786e3adae6c5b8167fbba00aa140d4d728308dc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="layout-considerations-for-the-windowsformshost-element"></a>Opcje układu dla elementu WindowsFormsHost
W tym temacie opisano sposób <xref:System.Windows.Forms.Integration.WindowsFormsHost> element współdziała z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układu systemu.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] obsługę logiki różne, ale podobne, zmiany rozmiaru i rozmieszczenia elementów w formularzu lub strony. Po utworzeniu hybrydowego interfejsu użytkownika (UI) obsługującego [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Forms.Integration.WindowsFormsHost> element integruje schematy dwóch układu.  
  
## <a name="differences-in-layout-between-wpf-and-windows-forms"></a>Różnice w układzie WPF i formularze systemu Windows  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa układu niezależne od rozdzielczości. Wszystkie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wymiarów układu są określane za pomocą *pikselach niezależnych od urządzenia*. Piksel niezależnych od urządzenia jest jeden szóstego dziewięćdziesięciu cala rozmiary i niezależne od rozdzielczości, dzięki czemu możesz uzyskać podobne wyniki niezależnie od tego, czy są renderowania monitor 72 dpi lub drukarki 19 200 dpi.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] również jest oparta na *układ dynamiczny*. Oznacza to, że element interfejsu użytkownika rozmieszcza się w formularzu lub na stronie zgodnie z zawartością, jego kontener układu i rozmiar obrazu. Układ dynamiczny ułatwia lokalizacja automatycznie dostosowując rozmiar i położenie elementów interfejsu użytkownika z ciągów, które zawierają zmiany długości.  
  
 Układ w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jest zależny od urządzenia, które bardziej mogą być statyczne. Zazwyczaj [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty są pozycjonowane absolutnie na formularzu przy użyciu wymiarów w pikselach sprzętu. Jednak [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] obsługuje niektóre funkcje układ dynamiczny, zgodnie z opisem w poniższej tabeli.  
  
|Funkcja układu|Opis|  
|--------------------|-----------------|  
|Automatyczna zmiana rozmiaru|Niektóre [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] zmiana rozmiaru formantów się do prawidłowego wyświetlenia ich zawartość. Aby uzyskać więcej informacji, zobacz [AutoSize — Przegląd właściwości](../../../../docs/framework/winforms/controls/autosize-property-overview.md).|  
|Zakotwiczanie i dokowanie|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Formanty obsługuje pozycjonowanie i zmianę rozmiaru w oparciu kontenera nadrzędnego. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType> i <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>.|  
|Skalowanie automatyczne|Kontrole kontenerów resize nimi i ich elementy podrzędne na podstawie rozdzielczości urządzenia wyjściowego lub rozmiar w pikselach czcionki kontenera domyślnego. Aby uzyskać więcej informacji, zobacz [automatyczne skalowanie w formularzach systemu Windows](../../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md).|  
|Kontenery układów|<xref:System.Windows.Forms.FlowLayoutPanel> i <xref:System.Windows.Forms.TableLayoutPanel> formanty Rozmieść ich formantów podrzędnych i rozmiar się zgodnie z ich zawartość.|  
  
## <a name="layout-limitations"></a>Ograniczenia układu  
 Ogólnie rzecz biorąc [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów nie mogą być skalowane i przekształcony w miarę możliwości w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Poniżej opisano znane ograniczenia podczas <xref:System.Windows.Forms.Integration.WindowsFormsHost> element próbuje integracji jego hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sterowania do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układu systemu.  
  
-   W niektórych przypadkach [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów nie można zmienić rozmiaru lub mogą być określane tylko do określonych wymiarów. Na przykład [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> sterowanie obsługuje tylko pojedynczy wysokości, który jest zdefiniowany przez rozmiar czcionki formantu. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układ dynamiczny, której elementy można stretch pionie hostowany <xref:System.Windows.Forms.ComboBox> formantu nie rozciąga zgodnie z oczekiwaniami.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty nie można obracać lub niesymetryczna. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Wywołuje element <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> zdarzeń w przypadku zastosowania transformację zegara lub obrotu. Jeśli nie obsługują <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> zdarzenia <xref:System.InvalidOperationException> jest wywoływane.  
  
-   W większości przypadków [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty nie obsługują proporcjonalne skalowania. Chociaż Ogólne wymiary formant są skalowane, formantów podrzędnych oraz elementów składowych formant może nie zmienić rozmiar zgodnie z oczekiwaniami. To ograniczenie zależy od jak każdy [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sterowanie obsługuje skalowania. Ponadto nie można skalować [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty w dół o rozmiarze 0 pikseli.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Formanty obsługuje funkcję skalowania automatycznego, w którym formularzu będzie automatycznie zmieniać rozmiar się i jego kontroli oparte na rozmiar czcionki. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsu użytkownika, zmienianie rozmiaru czcionki nie zmienia rozmiaru całego układu, mimo że poszczególne elementy mogą zostać dynamicznego dopasowania rozmiaru.  
  
### <a name="z-order"></a>Porządek osi z  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsu użytkownika można zmienić porządek osi z elementów do formantu nakładających się zachowanie. Hostowany [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli jest rysowana w oddzielnych HWND, więc jest zawsze wstawiany nad [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementów.  
  
 Hostowany [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli również jest rysowana na dowolne <xref:System.Windows.Documents.Adorner> elementów.  
  
## <a name="layout-behavior"></a>Zachowanie układu  
 W poniższych sekcjach opisano określone aspekty zachowania układu odnośnie do hostowania [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="scaling-unit-conversion-and-device-independence"></a>Skalowanie, konwersja jednostek i niezależność urządzenia  
 Zawsze, gdy <xref:System.Windows.Forms.Integration.WindowsFormsHost> element wykonuje operacje dotyczące [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] są związane z wymiarów, dwóch systemów współrzędnych: pikselach niezależnych od urządzenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i pikseli sprzętu dla [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. W związku z tym należy zastosować odpowiednie jednostki i skalowanie konwersje do osiągnięcia spójnego układu.  
  
 Konwersja między system współrzędnych zależy od bieżącego rozdzielczość urządzenia i wszelkie układ lub transformacje renderowania dotyczą <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu lub jego elementy nadrzędne.  
  
 Jeśli urządzenie wyjściowe jest 96 dpi i nie skalowanie spowodowany niedawnym <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu jeden piksel niezależnych od urządzenia jest równa jeden piksel sprzętu.  
  
 Wszystkich innych przypadkach wymagane skalowanie współrzędnych. Hostowanej nie zmieni się rozmiar kontrolki. Zamiast tego <xref:System.Windows.Forms.Integration.WindowsFormsHost> element próbuje skalowania obsługiwanego formantu i wszystkich jego formantów podrzędnych. Ponieważ [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nie obsługuje w pełni skalowania, <xref:System.Windows.Forms.Integration.WindowsFormsHost> element skaluje w stopniu, w szczególności formantów.  
  
 Zastąpienie <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A> metodę w celu zapewnienia zachowania niestandardowego skalowania dla obsługiwanego formantu formularzy systemu Windows.  
  
 Oprócz skalowania, <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu obsługuje zaokrąglania i przepełnienie przypadkach zgodnie z opisem w poniższej tabeli.  
  
|Konwersja problem|Opis|  
|----------------------|-----------------|  
|Zaokrąglanie|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wymiary w pikselach niezależnych od urządzenia są określone jako `double`, i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sprzętu wymiary są określone jako `int`. W przypadkach, gdy `double`— oparte na wymiary są konwertowane na `int`— na podstawie wymiarów, <xref:System.Windows.Forms.Integration.WindowsFormsHost> element używa standardowych zaokrąglania tak, aby ułamkowych wartości mniejszej niż 0,5 jest zaokrąglana do 0.|  
|Przepełnienie|Gdy <xref:System.Windows.Forms.Integration.WindowsFormsHost> konwertuje element `double` wartości do `int` wartości, możliwe jest przepełnienie. Wartości, które są większe niż <xref:System.Int32.MaxValue> są ustawione na <xref:System.Int32.MaxValue>.|  
  
### <a name="layout-related-properties"></a>Właściwości związane z układem  
 Właściwości, które kontrolują zachowanie układu w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy są mapowane odpowiednio przez <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. Aby uzyskać więcej informacji, zobacz [formularzy systemu Windows i mapowania właściwości WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
### <a name="layout-changes-in-the-hosted-control"></a>Zmian układu w formancie hostowanej  
 Zmian układu w hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrola jest przekazywana do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aby wyzwolić aktualizacje układu. <xref:System.Windows.UIElement.InvalidateMeasure%2A> Metoda <xref:System.Windows.Forms.Integration.WindowsFormsHost> zapewnia, że zmiany układu w formancie hostowanej spowodują [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aparatu układu do uruchomienia.  
  
### <a name="continuously-sized-windows-forms-controls"></a>Stale rozmiaru formantów formularzy systemu Windows  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty, które obsługuje ciągłego skalowania w pełni interakcyjnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układu systemu. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element używa <xref:System.Windows.FrameworkElement.MeasureOverride%2A> i <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metod w zwykły sposób, aby rozmiar i rozmieszczania hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantu.  
  
### <a name="sizing-algorithm"></a>Algorytm zmiany rozmiaru  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element używa następującej procedury, aby rozmiar formantu hostowanej:  
  
1.  <xref:System.Windows.Forms.Integration.WindowsFormsHost> Zastępuje element <xref:System.Windows.FrameworkElement.MeasureOverride%2A> i <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody.  
  
2.  Do określenia rozmiaru obsługiwanego formantu <xref:System.Windows.FrameworkElement.MeasureOverride%2A> metoda wywołuje obsługiwanego formantu <xref:System.Windows.Forms.Control.GetPreferredSize%2A> metody z ograniczeniem translacji z ograniczenia przekazany do <xref:System.Windows.FrameworkElement.MeasureOverride%2A> metody.  
  
3.  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> Metoda próbuje ustawić obsługiwanego formantu ograniczenia dany rozmiar.  
  
4.  Jeśli obsługiwanego formantu <xref:System.Windows.Forms.Control.Size%2A> właściwość odpowiada określonym ograniczeniem, obsługiwanego formantu jest dopasowywany do ograniczenia.  
  
 Jeśli <xref:System.Windows.Forms.Control.Size%2A> właściwość nie jest zgodna z określonym ograniczeniem, obsługiwanego formantu nie obsługuje ciągłego zmiany rozmiaru. Na przykład <xref:System.Windows.Forms.MonthCalendar> kontroli umożliwia tylko odrębny rozmiary. Dozwolone rozmiary dla tego formantu składają się z liczbami całkowitymi (reprezentujący liczbę miesięcy) na szerokość i wysokość. W przypadkach, takich jak ta <xref:System.Windows.Forms.Integration.WindowsFormsHost> element działa w następujący sposób:  
  
-   Jeśli <xref:System.Windows.Forms.Control.Size%2A> właściwość zwraca większy rozmiar niż określony ograniczenie <xref:System.Windows.Forms.Integration.WindowsFormsHost> element klipy obsługiwanego formantu. Wysokość i szerokość są obsługiwane oddzielnie, więc obsługiwanego formantu może zostać obcięty w żadnym kierunku.  
  
-   Jeśli <xref:System.Windows.Forms.Control.Size%2A> właściwość zwraca mniejszy rozmiar niż określony ograniczenie, <xref:System.Windows.Forms.Integration.WindowsFormsHost> akceptuje tej wartości rozmiaru i zwraca wartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układu systemu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Przewodnik: rozmieszczanie kontrolek formularzy Windows Forms w WPF](../../../../docs/framework/wpf/advanced/walkthrough-arranging-windows-forms-controls-in-wpf.md)  
 [Rozmieszczanie okien formantów formularzy w przykładowym WPF](http://go.microsoft.com/fwlink/?LinkID=159971)  
 [Mapowanie właściwości Windows Forms i WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [Migracja i współdziałanie](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
