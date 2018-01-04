---
title: "ClearType — Przegląd"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- typography [WPF], ClearType technology
- ClearType [WPF], technology
ms.assetid: 7e2392e0-75dc-463d-a716-908772782431
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eaeeeee921ac5cda3a4ce09dd3ebaeeb11aea3f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cleartype-overview"></a>ClearType — Przegląd
Ten temat zawiera omówienie [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] technologii znalezione w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
  
<a name="overview"></a>   
## <a name="technology-overview"></a>Omówienie technologii  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]jest to technologia oprogramowania opracowane przez [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] która poprawia czytelność tekstu w istniejących LCDs (należy zmienić.), takie jak ekranów komputerów przenośnych, Pocket PC ekrany i prosty monitory.  [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]Uzyskiwanie dostępu do elementów usługi stripe poszczególnych pionowy kolorów w każdym pikselu ciekłokrystalicznym utworów. Przed [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], najmniejszą poziom szczegółowości, który komputer można wyświetlić został pojedynczego piksela, ale [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] uruchomione na monitorze LCD, można teraz wyświetlany funkcje jak część piksel tekstu szerokości. Dodatkowe rozpoznawania zwiększa ostrość szczegóły niewielki rozmiar wyświetlania tekstu, co znacznie ułatwia odczytanie przez długi czas trwania.  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] Dostępne w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] najnowszej generacji [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] która zawiera kilka ulepszeń w wersji [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)].  
  
<a name="sub-pixel_positioning"></a>   
## <a name="sub-pixel-positioning"></a>Pozycjonowanie podrzędne pikseli  
 Znaczne ulepszenia w poprzedniej wersji [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] jest użycie pozycjonowanie podrzędne pikseli. W odróżnieniu od [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] implementacji znalezione w [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)], [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] umożliwia symboli można uruchomić w ramach piksela i nie tylko granic początku piksela. Ze względu na to dodatkowe rozwiązanie pozycjonowania symboli odstępy i proporcje symboli jest bardziej dokładne i spójne.  
  
 W poniższych przykładach dwóch pokazano, jak symboli może niekorzystnie na krawędzi podrzędne piksela podczas rozmieszczania podrzędne pikseli jest używany. Przykład po lewej stronie jest renderowany przy użyciu wcześniejszej wersji [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] renderowanie, nie zastosowana pozycjonowanie podrzędne pikseli. Przykład po prawej stronie jest renderowany przy użyciu nowej wersji [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] renderowania przy użyciu pozycjonowanie podrzędne pikseli. Należy zauważyć, jak każdy **e** i **l** w obrazie po prawej stronie jest renderowany nieco inaczej ponieważ każdy rozpoczyna się na różnych pikseli podrzędnych. Podczas wyświetlania tekstu w normalnym rozmiarze na ekranie, ta różnica nie jest widoczne z powodu dużego kontrastu obrazu symbolu. Jest to możliwe tylko ze względu na kolor zaawansowane filtrowanie zawartym w [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)].  
  
 ![Tekst wyświetlany w dwóch wersjach ClearType](../../../../docs/framework/wpf/advanced/media/wcpsdk-mmgraphics-text-cleartype-overview-01.png "wcpsdk_mmgraphics_text_cleartype_overview_01")  
Tekst wyświetlany z wcześniejszych i jego nowsze wersje ClearType  
  
 Dane wyjściowe z wcześniej porównać dwa poniższe przykłady [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] renderowania z nową wersją [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] renderowania. Pozycjonowanie subpixel wyświetlany po prawej stronie, znacznie skraca odstępy typu na ekranie, zwłaszcza w małych rozmiarów, gdzie różnica między podrzędne pikseli i całego pikseli reprezentuje znaczna część szerokość symbolu. Należy pamiętać, że odstępów między literami więcej nawet w przypadku drugiego obrazu. Zbiorcza zaletą podrzędne pikseli pozycjonowanie na ogólny wygląd ekranu tekstu znacznie zwiększa się i reprezentuje znaczne zmiany w [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] technologii.  
  
 ![Tekst wyświetlany z wcześniejszej wersji ClearType](../../../../docs/framework/wpf/advanced/media/wcpsdk-mmgraphics-text-cleartype-overview-02.png "wcpsdk_mmgraphics_text_cleartype_overview_02")  
Tekst z wcześniejszych i jego nowsze wersje ClearType  
  
<a name="y-direction_antialiasing"></a>   
## <a name="y-direction-antialiasing"></a>Antialiasingu kierunku Y  
 Poprawa innego [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jest wygładzanie kierunku y. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] w [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] bez kierunku y wygładzanie zapewnia wyższą rozdzielczość na osi x, ale nie osi y. Wierzchołki i dołu skrócona krzywych nierówne krawędzie one wpływu z jego czytelności.  
  
 W poniższym przykładzie przedstawiono efekt o bez antialiasingu kierunku y. W takim przypadku nieregularne krawędzie na górny i dolny litery są widoczne.  
  
 ![Tekst na krawędzi nieregularne na krzywe skrócona](../../../../docs/framework/wpf/advanced/media/wcpsdk-mmgraphics-text-cleartype-overview-03.png "wcpsdk_mmgraphics_text_cleartype_overview_03")  
Tekst na krawędzi nieregularne na skrócona krzywych  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia antialiasingu na poziomie kierunku y wygładzania się żadnych nieregularne krawędzi. Jest to szczególnie ważne w przypadku Poprawa czytelności języków wschodnioazjatyckich, gdzie ideogramami mają w przybliżeniu równe ilość poziome i pionowe krzywych skrócona.  
  
 W poniższym przykładzie przedstawiono wpływ antialiasingu kierunku y. W takim przypadku to krzywa Pokaż górny i dolny litery.  
  
 ![Tekst z & ClearType y 45; kierunek anty &#45; aliasów](../../../../docs/framework/wpf/advanced/media/wcpsdk-mmgraphics-text-cleartype-overview-04.png "wcpsdk_mmgraphics_text_cleartype_overview_04")  
Tekst z ClearType antialiasingu kierunku y  
  
<a name="hardware_acceleration"></a>   
## <a name="hardware-acceleration"></a>Przyspieszanie sprzętowe  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] można wykorzystać przyspieszanie sprzętowe w celu poprawy wydajności i zmniejszenia wymagania pamięci systemu i obciążenia Procesora. Przy użyciu programów do cieniowania pikseli i pamięci wideo karty grafiki, [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] zapewnia szybsze renderowanie tekstu, szczególnie w przypadku, gdy jest używana animacja.  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nie modyfikuje całego systemu [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] ustawienia. Wyłączanie [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] w [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] ustawia [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] antialiasingu tryb skali szarości. Ponadto [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nie modyfikuje ustawienia [ClearType Tuner PowerToy](http://www.microsoft.com/typography/ClearTypePowerToy.mspx).  
  
 Jeden z [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] decyzji dotyczących projektowania architektonicznego ma mieć niezależne układu lepszej obsługi wyższej rozdzielczości DPI monitory, które stają się coraz bardziej rozpowszechnione rozpoznawania. To ustawienie konsekwencją [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nie obsługuje aliasem renderowanie tekstu i mapy bitowej w niektórych czcionki wschodnioazjatyckie ponieważ są one zarówno zależna od rozdzielczości.  
  
<a name="further_information"></a>   
## <a name="further-information"></a>Dalsze informacje  
 [Informacje o ClearType](http://www.microsoft.com/typography/ClearTypeInfo.mspx)  
  
 [PowerToy ClearType Tuner](http://www.microsoft.com/typography/ClearTypePowerToy.mspx)  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia rejestru ClearType](../../../../docs/framework/wpf/advanced/cleartype-registry-settings.md)
