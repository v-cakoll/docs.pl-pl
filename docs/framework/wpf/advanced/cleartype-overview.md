---
title: ClearType — Przegląd
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], ClearType technology
- ClearType [WPF], technology
ms.assetid: 7e2392e0-75dc-463d-a716-908772782431
ms.openlocfilehash: c9d86cadd5f2115d0214d9a1b1dce7e6682341e0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629727"
---
# <a name="cleartype-overview"></a>ClearType — Przegląd
Ten temat zawiera omówienie technologii Microsoft ClearType, która znajduje się w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  

<a name="overview"></a>   
## <a name="technology-overview"></a>Omówienie technologii  
 Technologia ClearType jest technologią oprogramowania opracowaną przez [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] program, która zwiększa czytelność tekstu w istniejących LCDS (w przypadku wyświetlaczy Liquid Crystal), takich jak ekrany laptopów, urządzenia Pocket PC i monitory płaskoekranowe.  Technologia ClearType działa przez uzyskanie dostępu do poszczególnych elementów pasków kolorów w pionie w każdym piksel ekranu LCD. Przed użyciem technologii ClearType najmniejszy poziom szczegółowości wyświetlany przez komputer był pojedynczy piksel, ale dzięki technologii ClearType działającej na monitorze LCD można teraz wyświetlać funkcje tekstu jako małe jako ułamek o szerokości pikseli. Dodatkowe rozwiązanie zwiększa ostrość niewielkich szczegółów w wyświetlaniu tekstu, ułatwiając odczytywanie ich w dłuższym czasie.  
  
 Technologia ClearType dostępna w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programie to najnowsza generacja technologii ClearType, która ma kilka ulepszeń w porównaniu z [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)]wersją zainstalowaną w programie.  
  
<a name="sub-pixel_positioning"></a>   
## <a name="sub-pixel-positioning"></a>Pozycjonowanie w pikselach podrzędnych  
 Znaczną poprawę w porównaniu z poprzednią wersją technologii ClearType jest użycie pozycjonowania w pikselach podrzędnych. W przeciwieństwie do implementacji technologii ClearType [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]w programie technologia ClearType znaleziona w programie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] umożliwia uruchamianie symboli w pikselach, a nie tylko na początku piksela. Ze względu na to, że dodatkowe rozwiązanie w symbolach pozycjonowania, odstępy i proporcje symboli są bardziej precyzyjne i spójne.  
  
 W poniższych dwóch przykładach pokazano, jak symbole mogą rozpoczynać się w dowolnej granicy podrzędnej pikseli, gdy jest używane pozycjonowanie w pikselach podrzędnych. Przykład po lewej stronie jest renderowany przy użyciu wcześniejszej wersji modułu renderowania ClearType, która nie wykorzystuje pozycjonowania w pikselach podrzędnych. Przykład po prawej stronie jest renderowany przy użyciu nowej wersji renderowania ClearType przy użyciu pozycjonowania w pikselach podrzędnych. Zwróć uwagę, jak każda **e** i **l** w obrazie po prawej stronie jest renderowany nieco inaczej, ponieważ każdy z nich zaczyna się na innym pikselu. W przypadku wyświetlania tekstu na normalnym rozmiarze na ekranie różnica nie jest zauważalna ze względu na duży kontrast obrazu glifu. Jest to możliwe tylko ze względu na zaawansowane filtrowanie kolorów, które jest włączone w technologii ClearType.  
  
 ![Tekst wyświetlany z dwiema wersjami technologii ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-01.png "wcpsdk_mmgraphics_text_cleartype_overview_01")  
Tekst wyświetlany w starszych i nowszych wersjach technologii ClearType  
  
 Poniższe dwa przykłady porównują dane wyjściowe z wcześniejszego modułu renderowania ClearType przy użyciu nowej wersji modułu renderowania ClearType. Pozycjonowanie w pikselach, pokazane po prawej stronie, znacznie poprawia odstępy typu na ekranie, szczególnie w małych rozmiarach, w których różnica między pikselami podrzędnymi a całością pikseli reprezentuje znaczną część szerokości glifów. Należy zauważyć, że odstępy między literami są bardziej nawet w drugim obrazie. Skumulowana korzyść w stosunku do rozmieszczenia w pikselach na ogólny wygląd ekranu tekstu jest znacznie większa i reprezentuje znaczną ewolucję technologii ClearType.  
  
 ![Tekst wyświetlany w starszej wersji technologii ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-02.png "wcpsdk_mmgraphics_text_cleartype_overview_02")  
Tekst z wcześniejszymi i nowszymi wersjami technologii ClearType  
  
<a name="y-direction_antialiasing"></a>   
## <a name="y-direction-antialiasing"></a>Wygładzanie kierunku Y  
 Innym ulepszeniem technologii ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] w programie jest Antyaliasowanie kierunku y. Technologia ClearType w [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] programie bez kierunku y ma lepszą rozdzielczość na osi x, ale nie oś y. Na wierzchołkach i u dołu płytki są postrzępione krawędzie, które są niezależne od ich czytelności.  
  
 W poniższym przykładzie przedstawiono efekt braku wygładzania kierunku osi y. W takim przypadku widoczne są nieregularne krawędzie na górze i u dołu litery.  
  
 ![Tekst z nieregularnymi krawędziami na skróconych krzywych](./media/wcpsdk-mmgraphics-text-cleartype-overview-03.png "wcpsdk_mmgraphics_text_cleartype_overview_03")  
Tekst z nieregularnymi krawędziami na skróconych krzywych  
  
 Technologia ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] w systemie zapewnia wygładzanie na poziomie kierunku y, aby wygładzić wszystkie nieregularne krawędzie. Jest to szczególnie ważne, aby poprawić czytelność języków wschodnioazjatyckich, gdzie ideogramy mają prawie równą liczbę pikseli w poziomie i w pionie.  
  
 W poniższym przykładzie pokazano efekt wygładzania kierunku osi y. W takim przypadku Góra i dół litery pokazują gładką krzywą.  
  
 ![Tekst z wygładzaniem&#45;&#45;kierunku x ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-04.png "wcpsdk_mmgraphics_text_cleartype_overview_04")  
Tekst z wygładzaniem kierunku y w technologii ClearType  
  
<a name="hardware_acceleration"></a>   
## <a name="hardware-acceleration"></a>Przyspieszenie sprzętowe  
 Technologia ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] w systemie może wykorzystać przyspieszenie sprzętowe, aby zapewnić lepszą wydajność i zmniejszyć wymagania dotyczące obciążenia procesora i pamięci systemowej. Za pomocą programów do cieniowania pikseli i wideo karty graficznej technologia ClearType zapewnia szybsze renderowanie tekstu, szczególnie w przypadku używania animacji.  
  
 Technologia ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] w programie nie modyfikuje ustawień technologii ClearType dla całego systemu. Wyłączenie technologii ClearType [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programie ustawia funkcję antyaliasowania na tryb Skala szarości. Ponadto technologia ClearType w programie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nie modyfikuje ustawień [tunera ClearType PowerToy](https://www.microsoft.com/typography/ClearTypePowerToy.mspx).  
  
 Jedną z [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] decyzji projektowych dotyczących architektury jest to, że rozwiązanie niezależne pozwala lepiej obsługiwać monitory dpi o wyższej rozdzielczości, które stają się bardziej rozpowszechnione. Jest to wynikiem [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nieobsługiwanego renderowania tekstu aliasów lub map bitowych w niektórych czcionkach wschodnioazjatyckich, ponieważ są one zależne od rozdzielczości.  
  
<a name="further_information"></a>   
## <a name="further-information"></a>Dodatkowe informacje  
 [Informacje o technologii ClearType](https://www.microsoft.com/typography/ClearTypeInfo.mspx)  
  
 [PowerToy tunera ClearType](https://www.microsoft.com/typography/ClearTypePowerToy.mspx)  
  
## <a name="see-also"></a>Zobacz także

- [Ustawienia rejestru ClearType](cleartype-registry-settings.md)
