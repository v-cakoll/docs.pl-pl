---
title: ClearType — Przegląd
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], ClearType technology
- ClearType [WPF], technology
ms.assetid: 7e2392e0-75dc-463d-a716-908772782431
ms.openlocfilehash: 0127ee4112c4b42a7a55b9233217ea1e02604042
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051350"
---
# <a name="cleartype-overview"></a>ClearType — Przegląd
Ten temat zawiera omówienie [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] technologii znaleziony w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  

<a name="overview"></a>   
## <a name="technology-overview"></a>Omówienie technologii  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] jest to technologia oprogramowanie opracowane przez [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] który poprawia czytelność tekstu na istniejące LCD (należy zmienić.), takie jak ekranów komputerów przenośnych, ekrany Pocket PC i monitory płaskie.  [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] działa, uzyskując dostęp do poszczególnych kolor pionowych elementy usługi stripe w każdy piksel ekran LCD. Przed [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], najmniejszy poziom szczegółowości, który można wyświetlić komputera został piksela, ale z [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] uruchamiania monitora LCD, można jest teraz wyświetlany funkcji tekst tak małej, jako ułamek pikseli szerokości. Dodatkowe rozwiązanie zwiększa ostrość niewielki Szczegóły sposobu wyświetlania tekstu, znacznie ułatwiając przeczytaniu długim czasie trwania.  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] Dostępne w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] to najnowsza generacja [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] mającym kilka ulepszeń wprowadzonych w wersji [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)].  
  
<a name="sub-pixel_positioning"></a>   
## <a name="sub-pixel-positioning"></a>Pozycjonowanie podrzędnych pikseli  
 Wprowadzono znaczące ulepszenia przez poprzednią wersję [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] polega na użyciu pozycjonowanie podrzędnych pikseli. W odróżnieniu od [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] implementacji znaleziony w [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)], [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] umożliwia symbole, które można uruchomić w ramach piksela i nie tylko granic początku piksela. Ze względu na to dodatkowe rozwiązanie pozycjonowania symbole odstępy i proporcje glify jest bardziej precyzyjna i spójne.  
  
 Dwa poniższe przykłady pokazują, jak zacząć symbole na krawędzi podrzędnych pikseli stosowania pozycjonowanie podrzędnych pikseli. Przykład po lewej stronie jest renderowany przy użyciu wcześniejszej wersji [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] modułu renderowania, która nie zastosowana pozycjonowanie podrzędnych pikseli. Przykład po prawej stronie jest renderowany przy użyciu nowej wersji [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] modułu renderowania, za pomocą rozmieszczania podrzędnych pikseli. Należy zauważyć, jak każdy **e** i **l** obrazie po prawej stronie jest renderowany nieco inaczej, ponieważ każdy uruchamia się na różnych pikseli podrzędnych. Podczas wyświetlania tekstu normalnego rozmiaru na ekranie, różnica ta jest niezauważalne ze względu na wysoki kontrast obrazu symbolu. Jest to możliwe tylko ze względu na kolor zaawansowane filtrowanie zawartym w [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)].  
  
 ![Tekst wyświetlany w dwóch wersjach ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-01.png "wcpsdk_mmgraphics_text_cleartype_overview_01")  
Tekst wyświetlany w starszych i nowszych wersjach ClearType  
  
 Dwa poniższe przykłady porównać dane wyjściowe z wcześniej [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] renderowania przy użyciu nowej wersji [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] modułu renderowania. Pozycjonowanie subpixel wyświetlane po prawej stronie, znacznie zwiększa odstępy typu na ekranie, zwłaszcza w małych rozmiarów, gdzie różnica między podrzędnych pikseli i całego pikseli reprezentuje znaczna część szerokość symbolu. Należy pamiętać, że odstępów między literami więcej nawet w przypadku drugi obraz. Zbiorcza zaletą podrzędnych pikseli pozycjonowanie na ogólny wygląd ekranu tekstu znacznie zwiększa się i reprezentuje znaczne zmiany w [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] technologii.  
  
 ![Tekst wyświetlany za pomocą wcześniejszej wersji ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-02.png "wcpsdk_mmgraphics_text_cleartype_overview_02")  
Tekst w starszych i nowszych wersjach ClearType  
  
<a name="y-direction_antialiasing"></a>   
## <a name="y-direction-antialiasing"></a>Antyaliasing kierunku Y  
 Ulepszanie innego [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jest wygładzanie kierunku y. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] w [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] bez kierunku y wygładzanie zapewnia lepsze rozwiązania na osi x, ale nie osi y. Wierzchołki i dołu krzywych płytkie nierówne krawędzie zmniejszyć jego czytelność.  
  
 Poniższy przykład pokazuje wpływ o bez antialiasingu kierunku y. W tym przypadku nieregularnej krawędzie u góry i u dołu litery są widoczne.  
  
 ![Tekst z nierówne krawędzie na płytka krzywych](./media/wcpsdk-mmgraphics-text-cleartype-overview-03.png "wcpsdk_mmgraphics_text_cleartype_overview_03")  
Tekst z nierówne krawędzie na płytka krzywych  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia antialiasingu na poziomie kierunku y do wygładzania nagłych żadnych nieregularne krawędzi. Jest to szczególnie ważne, zwiększających czytelność języki wschodnioazjatyckie, gdzie ideogramy ma prawie taką samą ilość poziome i pionowe krzywych skrócona.  
  
 Poniższy przykład pokazuje wpływ antialiasingu kierunku y. W tym przypadku to krzywa Pokaż górnej i dolnej części literę.  
  
 ![Tekst z ClearType y&#45;kierunek ochrony przed złośliwym&#45;aliasów](./media/wcpsdk-mmgraphics-text-cleartype-overview-04.png "wcpsdk_mmgraphics_text_cleartype_overview_04")  
Tekst z antialiasingu kierunku y ClearType  
  
<a name="hardware_acceleration"></a>   
## <a name="hardware-acceleration"></a>Przyspieszanie sprzętowe  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] korzystać z zalet przyspieszanie sprzętowe, aby uzyskać lepszą wydajność i zmniejszyć wymagania pamięci systemu i obciążenia procesora CPU. Przy użyciu programów do cieniowania pikseli i pamięci wideo karty graficznej [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] zapewnia szybsze renderowanie tekstu, szczególnie w przypadku, gdy jest używana animacji.  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nie powoduje modyfikacji całego systemu [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] ustawienia. Wyłączanie [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] w [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] ustawia [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] antialiasingu tryb skali szarości. Ponadto [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nie modyfikuje ustawienia [ClearType Tuner PowerToy](https://www.microsoft.com/typography/ClearTypePowerToy.mspx).  
  
 Jedną z [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] decyzji w zakresie projektowania architektury jest korzystać z funkcji rozpoznawania niezależnie od układu lepszą obsługę wyższej rozdzielczości DPI monitory, które stają się coraz bardziej powszechne. Ma to konsekwencją [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nie obsługuje aliasem renderowanie tekstu lub mapy bitowej w przypadku niektórych czcionek wschodnioazjatyckich ponieważ są one zarówno zależna od rozdzielczości.  
  
<a name="further_information"></a>   
## <a name="further-information"></a>Dalsze informacje  
 [Informacje o ClearType](https://www.microsoft.com/typography/ClearTypeInfo.mspx)  
  
 [PowerToy ClearType Tuner](https://www.microsoft.com/typography/ClearTypePowerToy.mspx)  
  
## <a name="see-also"></a>Zobacz także

- [Ustawienia rejestru ClearType](cleartype-registry-settings.md)
