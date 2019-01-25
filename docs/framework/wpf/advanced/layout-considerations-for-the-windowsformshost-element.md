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
ms.openlocfilehash: a399cc9742ff9b19aabd6dcee558f94147c88356
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625630"
---
# <a name="layout-considerations-for-the-windowsformshost-element"></a>Opcje układu dla elementu WindowsFormsHost
W tym temacie opisano sposób, w jaki <xref:System.Windows.Forms.Integration.WindowsFormsHost> element wchodzi w interakcję z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] system układu.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Obsługa logiki różnych, ale podobne, rozmiar i położenie elementów na formularzu lub na stronie. Po utworzeniu hybrydowego interfejsu użytkownika (UI) obsługujący [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Forms.Integration.WindowsFormsHost> element integruje schematy dwóch układu.  
  
## <a name="differences-in-layout-between-wpf-and-windows-forms"></a>Różnice w układzie WPF i Windows Forms  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa układ niezależne od rozdzielczości. Wszystkie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wymiary układu są określane za pomocą *pikselach niezależnych od urządzenia*. Piksele niezależne od urządzenia jest jednej szóstej 90 cala rozmiaru i niezależne od rozdzielczości, więc otrzymujesz podobne wyniki, niezależnie od tego, czy są renderowania do 72 dpi monitora lub drukarki 19 200 dpi.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] również opiera się na *układ dynamiczny*. Oznacza to, że element interfejsu użytkownika rozmieszcza się na formularzu lub na stronie zgodnie z jego zawartości, jej nadrzędny kontener układu i rozmiaru ekranu dostępne. Układ dynamiczny ułatwia lokalizacji przez automatyczne dopasowanie rozmiaru i położenia elementów interfejsu użytkownika po ciągów, które zawierają zmiany długości.  
  
 Układ w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jest zależny od urządzenia i większe szanse na statyczny. Zazwyczaj [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty są pozycjonowane absolutnie w formularzu, przy użyciu wymiarów w pikselach sprzętu. Jednak [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] obsługuje niektóre funkcje układ dynamiczny, zgodnie z opisem w poniższej tabeli.  
  
|Funkcja układ|Opis|  
|--------------------|-----------------|  
|Automatyczne określanie rozmiaru|Niektóre [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] zmiany rozmiaru kontrolek się do prawidłowego wyświetlenia ich zawartość. Aby uzyskać więcej informacji, zobacz [AutoSize właściwość — omówienie](../../../../docs/framework/winforms/controls/autosize-property-overview.md).|  
|Zakotwiczanie i dokowanie|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Formanty obsługują pozycjonowanie i zmianę rozmiaru, oparte na kontenerze nadrzędnym. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType> i <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>.|  
|Skalowanie automatyczne|Kontrole kontenerów rozmiar nimi i ich elementy podrzędne na podstawie rozdzielczości urządzenia wyjściowego lub rozmiar w pikselach domyślna czcionka kontenera. Aby uzyskać więcej informacji, zobacz [automatyczne skalowanie w formularzach Windows Forms](../../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md).|  
|Kontenery układów|<xref:System.Windows.Forms.FlowLayoutPanel> i <xref:System.Windows.Forms.TableLayoutPanel> formanty rozmiaru się zgodnie z ich zawartość i rozmieszczanie ich formantów podrzędnych.|  
  
## <a name="layout-limitations"></a>Ograniczenia układu  
 Ogólnie rzecz biorąc [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki nie mogą być skalowane i przekształcone w miarę możliwości w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Na poniższej liście opisano znane ograniczenia podczas <xref:System.Windows.Forms.Integration.WindowsFormsHost> element próbuje integrowanie swojej hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sterowania do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] system układu.  
  
-   W niektórych przypadkach [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty nie można zmienić rozmiaru lub rozmiar można zmieniać tylko dla określonych wymiarów. Na przykład [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> kontrolka obsługuje tylko jedną wysokość, która jest zdefiniowana przez rozmiar czcionki formantu. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układ dynamiczny, gdzie elementy można rozciągnąć pionowo, hostowany <xref:System.Windows.Forms.ComboBox> nie można rozproszyć kontrolki, zgodnie z oczekiwaniami.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki nie można obracać lub nierówne. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Wywołuje element <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> zdarzeń, jeśli zastosujesz przekształcenia przesunięcia czasowego lub obrotu. Jeśli nie obsługują <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> zdarzenia <xref:System.InvalidOperationException> jest wywoływane.  
  
-   W większości przypadków [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów nie obsługują skalowanie proporcjonalne. Mimo że będzie się skalować wymiary formantu formanty podrzędne i elementy składowe formantu może nie zmienić rozmiar zgodnie z oczekiwaniami. To ograniczenie zależy od stopnia każdy [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolka obsługuje skalowanie. Ponadto, nie będzie można skalować [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolek w dół, aby rozmiar 0 pikseli.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Formanty obsługują skalowanie automatyczne, w którym formularza będzie automatycznie zmieniać rozmiar wraz z jego formantów, w oparciu o rozmiar czcionki. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsu użytkownika, zmienianie rozmiaru czcionki nie zmienia rozmiaru całej układ, mimo że poszczególne elementy mogą dynamicznie rozmiar.  
  
### <a name="z-order"></a>Z-order  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsu użytkownika można zmienić porządek elementów do formantu nakładających się zachowanie. Hostowany [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] rysowania kontrolki w oddzielnych HWND, dzięki czemu jest zawsze wstawiany w górnej części [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementów.  
  
 Hostowany [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] również rysowania kontrolki na podstawie dowolnej <xref:System.Windows.Documents.Adorner> elementów.  
  
## <a name="layout-behavior"></a>Zachowanie układu  
 W poniższych sekcjach opisano specyficzne aspekty zachowania układu, w przypadku hostowania [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="scaling-unit-conversion-and-device-independence"></a>Skalowanie, konwersję jednostek i niezależność urządzenia  
 Zawsze, gdy <xref:System.Windows.Forms.Integration.WindowsFormsHost> element wykonuje operacje obejmujące [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] wymiarów, dwoma układami współrzędnych są zaangażowane: pikselach niezależnych od urządzenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i pikseli sprzętu dla [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. W związku z tym należy najpierw zastosować odpowiednie jednostki i skalowanie konwersje w celu osiągnięcia spójnego układu.  
  
 Konwersja między systemów współrzędnych zależy od bieżącego rozdzielczość urządzenia i wszelkie układu transformacje renderowania do lub <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu lub jego elementy nadrzędne.  
  
 Jeśli urządzenie danych wyjściowych jest rozdzielczości 96 dpi i bez skalowania została zastosowana do <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, jeden piksel niezależnych od urządzenia jest równa jeden piksel sprzętu.  
  
 System współrzędnych skalowanie wymagane wszystkich innych przypadkach. Hostowana nie zmieni się rozmiar kontrolki. Zamiast tego <xref:System.Windows.Forms.Integration.WindowsFormsHost> element próbuje skalowanie obsługiwanego formantu i wszystkich jego formantów podrzędnych. Ponieważ [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nie obsługuje w pełni skalowania, <xref:System.Windows.Forms.Integration.WindowsFormsHost> element skaluje stopień obsługiwanych przez określonej kontrolki.  
  
 Zastąp <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A> metody w celu zapewnienia niestandardowe zachowanie skalowania dla hostowanej kontrolki Windows Forms.  
  
 Oprócz skalowania, <xref:System.Windows.Forms.Integration.WindowsFormsHost> element obsługuje zaokrąglania i przepełnienie przypadkach, zgodnie z opisem w poniższej tabeli.  
  
|Konwersja problem|Opis|  
|----------------------|-----------------|  
|Zaokrąglenie|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozmiar w pikselach niezależnych od urządzenia są określane jako `double`, i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sprzętu wymiary są określane jako `int`. W przypadkach, gdzie `double`— na podstawie wymiary są konwertowane na `int`— na podstawie wymiarów, <xref:System.Windows.Forms.Integration.WindowsFormsHost> element używa standardowych zaokrąglania tak, aby wartościami ułamkowymi, mniejsze niż 0,5 są zaokrąglane w dół do 0.|  
|przepełnienia|Gdy <xref:System.Windows.Forms.Integration.WindowsFormsHost> konwertuje element `double` wartości `int` wartości, jest możliwe przepełnienie. Wartości, które są większe niż <xref:System.Int32.MaxValue> są ustawione na <xref:System.Int32.MaxValue>.|  
  
### <a name="layout-related-properties"></a>Właściwości związane z układem  
 Właściwości, które kontrolują zachowanie układu w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolek i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy są zmapowane odpowiednio przez <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. Aby uzyskać więcej informacji, zobacz [Windows Forms i WPF właściwość mapowanie](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
### <a name="layout-changes-in-the-hosted-control"></a>Zmian układu w formancie hostowanej  
 Zmian układu w hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrola jest przekazywana do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wyzwolić aktualizacje układu. <xref:System.Windows.UIElement.InvalidateMeasure%2A> Metody <xref:System.Windows.Forms.Integration.WindowsFormsHost> zapewnia, że zmiany układu w formancie hostowanej spowodują [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aparatu układu do uruchomienia.  
  
### <a name="continuously-sized-windows-forms-controls"></a>Stale rozmiar kontrolek formularzy Windows Forms  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty, które obsługują ciągłą skalowania w pełni korzystać z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] system układu. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element używa <xref:System.Windows.FrameworkElement.MeasureOverride%2A> i <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody zwykły rozmiar i Rozmieść hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli.  
  
### <a name="sizing-algorithm"></a>Algorytm zmiany rozmiaru  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element używa następującej procedury, aby rozmiar kontrolki hostowanej:  
  
1.  <xref:System.Windows.Forms.Integration.WindowsFormsHost> Zastępuje element <xref:System.Windows.FrameworkElement.MeasureOverride%2A> i <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody.  
  
2.  Określanie rozmiaru obsługiwanego formantu <xref:System.Windows.FrameworkElement.MeasureOverride%2A> metoda wywołuje obsługiwanego formantu <xref:System.Windows.Forms.Control.GetPreferredSize%2A> metody z ograniczeniem translacji z ograniczenia przekazany do <xref:System.Windows.FrameworkElement.MeasureOverride%2A> metody.  
  
3.  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> Metoda próbuje ustawić hostowanej kontroli do powiązanych dany rozmiar.  
  
4.  Jeśli kontrolka hostowanej <xref:System.Windows.Forms.Control.Size%2A> właściwość odpowiada określonym ograniczeniem, obsługiwanego formantu ma rozmiar do ograniczenia.  
  
 Jeśli <xref:System.Windows.Forms.Control.Size%2A> właściwości jest niezgodny z określonym ograniczeniem, obsługiwanego formantu nie obsługuje ciągłego zmiany rozmiaru. Na przykład <xref:System.Windows.Forms.MonthCalendar> kontrolka zezwala na tylko dyskretnych rozmiarów. Dozwolone rozmiary dla tego formantu składają się z liczb całkowitych (reprezentująca liczbę miesięcy) na szerokość i wysokość. W przypadkach, takich jak ta <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu zachowuje się w następujący sposób:  
  
-   Jeśli <xref:System.Windows.Forms.Control.Size%2A> właściwość zwraca większy rozmiar niż określona ograniczenie <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu klipów obsługiwanego formantu. Wysokość i szerokość są obsługiwane osobno, dzięki czemu mogą zostać obcięte kontroli hostowanych w dowolnym kierunku.  
  
-   Jeśli <xref:System.Windows.Forms.Control.Size%2A> właściwość zwraca rozmiar mniejszy niż określony ograniczenie <xref:System.Windows.Forms.Integration.WindowsFormsHost> akceptuje tej wartości rozmiaru i zwraca wartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] system układu.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Przewodnik: Kontrolek rozmieszczanie Windows Forms w WPF](../../../../docs/framework/wpf/advanced/walkthrough-arranging-windows-forms-controls-in-wpf.md)
- [Windows rozmieszczanie formantów formularzy w przykładzie WPF](https://go.microsoft.com/fwlink/?LinkID=159971)
- [Mapowanie właściwości Windows Forms i WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)
- [Migracja i współdziałanie](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
