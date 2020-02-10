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
ms.openlocfilehash: 89ed57a787b93a1326b4accd3bb1bc5ff9a825fd
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095154"
---
# <a name="layout-considerations-for-the-windowsformshost-element"></a>Opcje układu dla elementu WindowsFormsHost
W tym temacie opisano sposób współdziałania elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> z układem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układu.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i Windows Forms obsługują różne, ale podobne, logiki do ustalania rozmiarów i pozycjonowania elementów na formularzu lub stronie. Podczas tworzenia hybrydowego interfejsu użytkownika, który hostuje Windows Forms formantów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], element <xref:System.Windows.Forms.Integration.WindowsFormsHost> integruje dwa schematy układu.  
  
## <a name="differences-in-layout-between-wpf-and-windows-forms"></a>Różnice w układzie między WPF i Windows Forms  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa układu niezależnego od rozpoznawania. Wszystkie wymiary układu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są określane przy użyciu *pikseli niezależnych od urządzenia*. Piksel niezależny od urządzenia to jeden z 90 szóstych wielkości i niezależny od rozdzielczości, dzięki czemu można uzyskać podobne wyniki bez względu na to, czy renderuje się do monitora 72 dpi czy drukarki 19 200 dpi.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest również oparty na *układzie dynamicznym*. Oznacza to, że element interfejsu użytkownika jest układany na formularzu lub na stronie zgodnie z jego zawartością, kontenerem układu nadrzędnego i dostępnym rozmiarem ekranu. Układ dynamiczny ułatwia lokalizowanie przez automatyczne dopasowanie rozmiaru i położenia elementów interfejsu użytkownika, gdy ciągi zawierają długość zmian.  
  
 Układ w Windows Forms jest zależny od urządzenia i najprawdopodobniej będzie statyczny. Zazwyczaj kontrolki Windows Forms są pozycjonowane absolutnie na formularzu przy użyciu wymiarów określonych w pikselach sprzętowych. Jednak Windows Forms obsługuje niektóre funkcje układu dynamicznego, zgodnie z podsumowaniem w poniższej tabeli.  
  
|Funkcja układu|Opis|  
|--------------------|-----------------|  
|Automatyczne określanie rozmiaru|Niektóre Windows Forms kontroluje zmianę samego rozmiaru w celu poprawnego wyświetlania ich zawartości. Aby uzyskać więcej informacji, zobacz [Omówienie właściwości AutoSize](../../winforms/controls/autosize-property-overview.md).|  
|Zakotwiczanie i dokowanie|Kontrolki Windows Forms obsługują pozycjonowanie i ustalanie rozmiarów na podstawie kontenera nadrzędnego. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType> i <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>.|  
|Skalowanie automatyczne|Kontrolki kontenerów zmieniają rozmiar i ich elementy podrzędne na podstawie rozdzielczości urządzenia wyjściowego lub rozmiaru (w pikselach) domyślnej czcionki kontenera. Aby uzyskać więcej informacji, zobacz [Automatyczne skalowanie w Windows Forms](../../winforms/automatic-scaling-in-windows-forms.md).|  
|Kontenery układów|Kontrolki <xref:System.Windows.Forms.FlowLayoutPanel> i <xref:System.Windows.Forms.TableLayoutPanel> układają swoje kontrolki podrzędne i same same rozmiary według ich zawartości.|  
  
## <a name="layout-limitations"></a>Ograniczenia układu  
 Ogólnie rzecz biorąc, Windows Forms kontrolki nie mogą być skalowane i przekształcone w miarę możliwości w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Poniższa lista zawiera opis znanych ograniczeń, gdy element <xref:System.Windows.Forms.Integration.WindowsFormsHost> próbuje zintegrować swoją obsługiwaną kontrolę Windows Forms z systemem układów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- W niektórych przypadkach nie można zmienić rozmiaru formantów Windows Forms lub można je zmieniać tylko do określonych wymiarów. Na przykład kontrolka <xref:System.Windows.Forms.ComboBox> Windows Forms obsługuje tylko jedną wysokość, która jest definiowana przez rozmiar czcionki kontrolki. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dynamicznym układu, w którym elementy można rozciągnąć w pionie, hostowana kontrolka <xref:System.Windows.Forms.ComboBox> nie rozciąga się w oczekiwany sposób.  
  
- Kontrolki Windows Forms nie mogą być obrócone lub skośne. Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> wywołuje zdarzenie <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> w przypadku zastosowania transformacji skośnej lub rotacji. Jeśli nie obsłużysz zdarzenia <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>, zostanie zgłoszony <xref:System.InvalidOperationException>.  
  
- W większości przypadków formanty Windows Forms nie obsługują skalowania proporcjonalnie. Chociaż ogólne wymiary kontrolki będą skalowane, formanty podrzędne i elementy składnika formantu mogą nie zmieniać rozmiaru zgodnie z oczekiwaniami. To ograniczenie zależy od tego, jak dobrze każda kontrolka Windows Forms obsługuje skalowanie. Ponadto nie można skalować formantów Windows Forms w dół do rozmiaru 0 pikseli.  
  
- Kontrolki Windows Forms obsługują Skalowanie automatyczne, w którym formularz będzie automatycznie zmieniać rozmiar i jego kontrolki w oparciu o rozmiar czcionki. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsie użytkownika zmiana rozmiaru czcionki nie powoduje zmiany rozmiaru całego układu, chociaż poszczególne elementy mogą dynamicznie zmieniać rozmiar.  
  
### <a name="z-order"></a>Porządek osi Z  
 W interfejsie użytkownika [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] można zmienić porządek osi z elementów w celu kontrolowania nakładających się zachowań. Kontrolka hostowana Windows Forms jest rysowana w oddzielnym elemencie HWND, więc jest zawsze rysowana na elementach [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Kontrolka hostowana Windows Forms jest również rysowana na wszystkich elementach <xref:System.Windows.Documents.Adorner>.  
  
## <a name="layout-behavior"></a>Zachowanie układu  
 W poniższych sekcjach opisano określone aspekty zachowania układu podczas hostowania Windows Forms formantów w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="scaling-unit-conversion-and-device-independence"></a>Skalowanie, Konwersja jednostek i niezależność urządzenia  
 Za każdym razem, gdy <xref:System.Windows.Forms.Integration.WindowsFormsHost> element wykonuje operacje obejmujące [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i Windows Forms wymiary, są zaangażowane dwa systemy współrzędnych: piksele niezależne od urządzenia dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i pikseli sprzętu dla Windows Forms. W związku z tym należy zastosować poprawne konwersje jednostek i skalowania, aby osiągnąć spójny układ.  
  
 Konwersja między systemami współrzędnych zależy od bieżącej rozdzielczości urządzenia i wszelkich przekształceń układu lub renderowania zastosowanych do elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> lub do jego obiektów nadrzędnych.  
  
 Jeśli urządzenie wyjściowe ma 96 dpi i nie zastosowano skalowania do elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>, jeden piksel niezależny od urządzenia jest równy jednemu pikselowi sprzętowemu.  
  
 Wszystkie inne przypadki wymagają skalowania systemu współrzędnych. Rozmiar hostowanej kontroli nie jest zmieniany. Zamiast tego element <xref:System.Windows.Forms.Integration.WindowsFormsHost> próbuje skalować formant hostowany i wszystkie jego formanty podrzędne. Ponieważ Windows Forms nie obsługuje w pełni skalowania, element <xref:System.Windows.Forms.Integration.WindowsFormsHost> jest skalowany do stopnia obsługiwanego przez poszczególne kontrolki.  
  
 Zastąp metodę <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A>, aby zapewnić niestandardowe zachowanie skalowania hostowanej Windows Forms.  
  
 Oprócz skalowania element <xref:System.Windows.Forms.Integration.WindowsFormsHost> obsługuje zaokrąglanie i przypadki przepełnienia, zgodnie z opisem w poniższej tabeli.  
  
|Problem z konwersją|Opis|  
|----------------------|-----------------|  
|Zaokrąglania|Wymiary w pikselach niezależnych od urządzenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są określone jako `double`, a Windows Forms wymiary sprzętowe w pikselach są określane jako `int`. W przypadkach, gdy wymiary `double`są konwertowane na wymiary oparte na `int`, element <xref:System.Windows.Forms.Integration.WindowsFormsHost> używa zaokrąglania standardowego, więc wartości ułamkowe mniejsze niż 0,5 są zaokrąglane w dół do wartości 0.|  
|Przepływ|Gdy <xref:System.Windows.Forms.Integration.WindowsFormsHost> element konwertuje wartości `double` na wartości `int`, możliwe jest przepełnienie. Wartości, które są większe niż <xref:System.Int32.MaxValue> są ustawione na <xref:System.Int32.MaxValue>.|  
  
### <a name="layout-related-properties"></a>Właściwości związane z układem  
 Właściwości sterujące zachowaniem układu w formantach Windows Forms i elementy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są mapowane odpowiednio przez element <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Aby uzyskać więcej informacji, zobacz [Windows Forms i mapowanie właściwości WPF](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="layout-changes-in-the-hosted-control"></a>Zmiany układu w hostowanej kontroli  
 Zmiany układu w hostowanej formancie Windows Forms są propagowane do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], aby wyzwolić aktualizacje układu. Metoda <xref:System.Windows.UIElement.InvalidateMeasure%2A> na <xref:System.Windows.Forms.Integration.WindowsFormsHost> zapewnia, że zmiany układu w hostowanej formancie powodują uruchomienie aparatu układu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="continuously-sized-windows-forms-controls"></a>Windows Forms kontrolki o stałym rozmiarze  
 Windows Forms kontrolki obsługujące ciągłe skalowanie w pełni współpracujące z systemem układów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> używa metod <xref:System.Windows.FrameworkElement.MeasureOverride%2A> i <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> w sposób typowy, aby rozmiar i rozmieścić hostowaną kontrolkę Windows Forms.  
  
### <a name="sizing-algorithm"></a>Algorytm ustalania wielkości  
 Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> używa następującej procedury, aby zmienić rozmiar hostowanej kontroli:  
  
1. Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> zastępuje metody <xref:System.Windows.FrameworkElement.MeasureOverride%2A> i <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>.  
  
2. Aby określić rozmiar hostowanej kontrolki, Metoda <xref:System.Windows.FrameworkElement.MeasureOverride%2A> wywołuje metodę <xref:System.Windows.Forms.Control.GetPreferredSize%2A> kontroli hostowanej z ograniczeniem przetłumaczonym przez ograniczenie przesłane do metody <xref:System.Windows.FrameworkElement.MeasureOverride%2A>.  
  
3. Metoda <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> podejmuje próbę ustawienia kontrolki hostowanej na podanym ograniczeniu rozmiaru.  
  
4. Jeśli właściwość <xref:System.Windows.Forms.Control.Size%2A> kontrolki hostowanej pasuje do określonego ograniczenia, hostowana kontrolka ma rozmiar do ograniczenia.  
  
 Jeśli właściwość <xref:System.Windows.Forms.Control.Size%2A> nie jest zgodna z określonym ograniczeniem, formant hostowany nie obsługuje ciągłego ustalania rozmiarów. Na przykład kontrolka <xref:System.Windows.Forms.MonthCalendar> zezwala tylko na rozmiary dyskretne. Dozwolone rozmiary tego formantu składają się z liczb całkowitych (reprezentujących liczbę miesięcy) dla wysokości i szerokości. W takich przypadkach <xref:System.Windows.Forms.Integration.WindowsFormsHost> element zachowuje się w następujący sposób:  
  
- Jeśli właściwość <xref:System.Windows.Forms.Control.Size%2A> zwraca większy rozmiar niż określone ograniczenie, element <xref:System.Windows.Forms.Integration.WindowsFormsHost> przycina formant hostowany. Wysokość i szerokość są obsługiwane oddzielnie, dlatego hostowana kontrolka może być przycinana w dowolnym kierunku.  
  
- Jeśli właściwość <xref:System.Windows.Forms.Control.Size%2A> zwraca mniejszy rozmiar niż określone ograniczenie, <xref:System.Windows.Forms.Integration.WindowsFormsHost> akceptuje tę wartość rozmiaru i zwraca wartość do systemu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układu.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Przewodnik: rozmieszczanie kontrolek formularzy Windows Forms w WPF](walkthrough-arranging-windows-forms-controls-in-wpf.md)
- [Rozmieszczanie formantów Windows Forms w przykładzie WPF](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WpfLayoutHostingWfWithXaml)
- [Mapowanie właściwości Windows Forms i WPF](windows-forms-and-wpf-property-mapping.md)
- [Migracja i współdziałanie](migration-and-interoperability.md)
