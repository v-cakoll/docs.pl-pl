---
title: ClearType — Przegląd
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], ClearType technology
- ClearType [WPF], technology
ms.assetid: 7e2392e0-75dc-463d-a716-908772782431
ms.openlocfilehash: b76c0cb04e5de498374cbf28c8813fe5c95d41ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186164"
---
# <a name="cleartype-overview"></a>ClearType — Przegląd
Ten temat zawiera omówienie technologii Microsoft ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]znalezionej w pliku .  

<a name="overview"></a>
## <a name="technology-overview"></a>Przegląd technologii  
 ClearType to technologia oprogramowania opracowana przez firmę Microsoft, która poprawia czytelność tekstu na istniejących monitorach LCD (Wyświetlacze Ciekłokrystaliczne), takich jak ekrany laptopów, ekrany Pocket PC i monitory płaskoekranowe.  Funkcja ClearType działa poprzez dostęp do poszczególnych pionowych kolorowych elementów paska w każdym pikselu ekranu LCD. Przed ClearType, najmniejszy poziom szczegółowości, że komputer może wyświetlać był pojedynczy piksel, ale z ClearType działa na monitorze LCD, możemy teraz wyświetlić funkcje tekstu tak małe, jak ułamek piksela szerokości. Dodatkowa rozdzielczość zwiększa ostrość drobnych szczegółów na ekranie tekstu, dzięki czemu znacznie łatwiej jest czytać przez długi czas.  
  
 ClearType dostępne [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] w jest najnowszej generacji ClearType, który ma kilka ulepszeń w stosunku do wersji znalezionej w microsoft windows graphics device interface (GDI).  
  
<a name="sub-pixel_positioning"></a>
## <a name="sub-pixel-positioning"></a>Pozycjonowanie subpiksele  
 Znaczną poprawą w stosunku do poprzedniej wersji ClearType jest użycie pozycjonowania subpikselowego. W przeciwieństwie do ClearType implementacji znalezionej w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] GDI, ClearType znaleźć w umożliwia glifów, aby rozpocząć w pikselu, a nie tylko granicy początkowej piksela. Ze względu na tę dodatkową rozdzielczość w glifach pozycjonowania odstępy i proporcje glifów są bardziej precyzyjne i spójne.  
  
 Poniższe dwa przykłady pokazują, jak glify mogą rozpoczynać się na dowolnej granicy subpikseli, gdy używane jest pozycjonowanie subpikseli. Przykład po lewej stronie jest renderowany przy użyciu wcześniejszej wersji modułu renderowania ClearType, który nie używał pozycjonowania subpikselowego. Przykład po prawej stronie jest renderowany przy użyciu nowej wersji modułu renderowania ClearType przy użyciu pozycjonowania subpikseli. Zwróć uwagę, jak każdy **obraz e** i **l** w obrazie po prawej stronie jest renderowany nieco inaczej, ponieważ każdy rozpoczyna się od innego subpiksela. Podczas wyświetlania tekstu w normalnym rozmiarze na ekranie różnica ta nie jest zauważalna ze względu na wysoki kontrast obrazu glifów. Jest to możliwe tylko ze względu na zaawansowane filtrowanie kolorów, który jest włączony w ClearType.  
  
 ![Tekst wyświetlany w dwóch wersjach cleartype](./media/wcpsdk-mmgraphics-text-cleartype-overview-01.png "wcpsdk_mmgraphics_text_cleartype_overview_01")  
Tekst wyświetlany we wcześniejszych i nowszych wersjach cleartype  
  
 Poniższe dwa przykłady porównać dane wyjściowe z wcześniejszego modułu renderowania ClearType z nową wersją modułu renderowania ClearType. Pozycjonowanie subpikselowe, pokazane po prawej stronie, znacznie poprawia odstępy między typem na ekranie, szczególnie przy małych rozmiarach, gdzie różnica między subpikselem a całym pikselem stanowi znaczną część szerokości glifów. Należy zauważyć, że odstępy między literami są bardziej równomierne na drugim obrazie. Skumulowana korzyść pozycjonowania subpikseli do ogólnego wyglądu ekranu tekstu jest znacznie zwiększona i stanowi znaczną ewolucję w technologii ClearType.  
  
 ![Tekst wyświetlany z wcześniejszą wersją ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-02.png "wcpsdk_mmgraphics_text_cleartype_overview_02")  
Tekst z wcześniejszą i nowszą wersją cleartype  
  
<a name="y-direction_antialiasing"></a>
## <a name="y-direction-antialiasing"></a>Y-Kierunek Antialiasing  
 Inną ulepszeniem ClearType w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jest y-kierunek wygładzenie. ClearType w GDI bez wygładzania kierunkowego y zapewnia lepszą rozdzielczość na osi x, ale nie na osi y. Na szczytach i dnach płytkich krzywych postrzępione krawędzie umniejszają jego czytelność.  
  
 Poniższy przykład pokazuje efekt braku antyaliasingu w kierunku y. W tym przypadku widoczne są postrzępione krawędzie na górze i na dole litery.  
  
 ![Tekst z postrzępionymi krawędziami na płytkich krzywych](./media/wcpsdk-mmgraphics-text-cleartype-overview-03.png "wcpsdk_mmgraphics_text_cleartype_overview_03")  
Tekst z postrzępionymi krawędziami na płytkich krzywych  
  
 ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] in zapewnia antyaliasing na poziomie kierunku y, aby wygładzić wszelkie postrzępione krawędzie. Jest to szczególnie ważne dla poprawy czytelności języków wschodnioazjatyckich, gdzie ideografy mają prawie taką samą ilość poziomych i pionowych płytkich krzywych.  
  
 Poniższy przykład pokazuje efekt antialiasing kierunku y. W tym przypadku górna i dolna część litery pokazuje gładką krzywą.  
  
 ![Tekst z&#45;kierunkiem&#45;&#45;aliasem](./media/wcpsdk-mmgraphics-text-cleartype-overview-04.png "wcpsdk_mmgraphics_text_cleartype_overview_04")  
Tekst z antialiasing cleartype y-kierunek  
  
<a name="hardware_acceleration"></a>
## <a name="hardware-acceleration"></a>Przyspieszanie sprzętowe  
 ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] in może korzystać z przyspieszenia sprzętowego dla lepszej wydajności i zmniejszyć obciążenie procesora i wymagania dotyczące pamięci systemowej. Korzystając z modułów cieniujących pikseli i pamięci wideo karty graficznej, funkcja ClearType zapewnia szybsze renderowanie tekstu, szczególnie w przypadku użycia animacji.  
  
 Opcja ClearType in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nie modyfikuje ustawień ClearType dla całego systemu. Wyłączenie ClearType w systemie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Windows ustawia antialiasing do trybu skali szarości. Ponadto program ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] in nie modyfikuje ustawień [programu ClearType Tuner PowerToy](https://www.microsoft.com/typography/ClearTypePowerToy.mspx).  
  
 Jedną z [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] decyzji dotyczących projektowania architektonicznego jest uzyskanie niezależnego układu rozdzielczości lepiej obsługują monitory DPI o wyższej rozdzielczości, które stają się coraz bardziej rozpowszechnione. Ma to konsekwencję [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] niewspierania renderowania tekstu aliasów lub map bitowych w niektórych czcionkach wschodnioazjatyckich, ponieważ są one zależne od obu rozdzielczości.  
  
<a name="further_information"></a>
## <a name="further-information"></a>Dalsze informacje  
 [Informacje o typie cleartype](https://www.microsoft.com/typography/ClearTypeInfo.mspx)  
  
 [Technologia ClearType Tunener PowerToy](https://www.microsoft.com/typography/ClearTypePowerToy.mspx)  
  
## <a name="see-also"></a>Zobacz też

- [Ustawienia rejestru ClearType](cleartype-registry-settings.md)
