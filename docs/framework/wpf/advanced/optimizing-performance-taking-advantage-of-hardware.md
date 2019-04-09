---
title: 'Optymalizacja wydajności: Wykorzystanie możliwości sprzętu'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], performance
- hardware rendering pipeline [WPF]
- rendering tiers [WPF]
- graphics rendering tiers [WPF]
- graphics [WPF], rendering tiers
- software rendering pipeline [WPF]
ms.assetid: bfb89bae-7aab-4cac-a26c-a956eda8fce2
ms.openlocfilehash: 683804acf43065543fa5d4ffb1a5ecf7e5b4c49a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163179"
---
# <a name="optimizing-performance-taking-advantage-of-hardware"></a>Optymalizacja wydajności: Wykorzystanie możliwości sprzętu
Wewnętrznej architekturze programu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ma renderowania dwa potoki, sprzętu i oprogramowania. Ten temat zawiera informacje o tych potoków renderowania ułatwiające podejmowanie decyzji dotyczących optymalizacji wydajności aplikacji.  
  
## <a name="hardware-rendering-pipeline"></a>Sprzętowy potok renderowania  
 Jedną z najważniejszych czynników przy określaniu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wydajności jest powiązana renderowania — więcej pikseli, masz do renderowania i większą wydajność kosztów. Jednak im więcej renderowania, który może być przenoszona do [!INCLUDE[TLA#tla_gpu](../../../../includes/tlasharptla-gpu-md.md)], uzyskać więcej korzyści w zakresie wydajności. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Aplikacji sprzętowy potok renderowania wykorzystuje pełną [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] funkcji na sprzęcie, który obsługuje co najmniej [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] w wersji 7.0. Dodatkowe optymalizacje mogą zostać uzyskane przez sprzęt obsługujący [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] w wersji 7.0 i funkcje PixelShader 2.0 +.  
  
## <a name="software-rendering-pipeline"></a>Programowy potok renderowania  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Programowy potok renderowania całkowicie CPU jest powiązany. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wykorzystuje instrukcji SSE i SSE2 ustawia w procesorze CPU do zaimplementowania rasteryzatora zoptymalizowane, w pełni funkcjonalne oprogramowanie. Powrót do oprogramowania działa bezproblemowo, każdym razem, gdy funkcjonalność aplikacji nie może być renderowany przy użyciu sprzętowy potok renderowania.  
  
 Największy problem z wydajnością można napotkać podczas renderowania w trybie oprogramowania jest powiązany do wypełnienia szybkości, która jest zdefiniowana jako liczbę pikseli, które są renderowania. Jeśli dane dotyczące wydajności w tryb renderowania oprogramowania próbuje zminimalizować liczbę przypadków, gdy jest odświeżana, piksel. Na przykład jeśli masz aplikację z niebieskim tłem, która następnie renderuje nieco przezroczysty obraz nad nim, będą renderowane wszystkie piksele w aplikacji, dwa razy. W rezultacie potrwa dwa razy tak długo, aby renderować aplikacji przy użyciu tego obrazu, niż gdyby miał tylko niebieskie tło.  
  
### <a name="graphics-rendering-tiers"></a>Poziomy zmiany grafiki  
 Może być bardzo trudne do przewidzenia konfiguracji sprzętowej, która aplikacja zostanie uruchomiona w. Jednak warto wziąć pod uwagę projekt, który umożliwia aplikacji bezproblemowo przełączyć funkcji podczas uruchamiania na różnym sprzęcie, tak aby go mogą w pełni korzystać z każdej innej konfiguracji sprzętu.  
  
 Aby to osiągnąć, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferuje funkcje, aby określić możliwości grafiki systemu w czasie wykonywania. Możliwości grafiki jest określana przez skategoryzowanie karty wideo, jako jeden z trzech warstw możliwości renderowania. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] umożliwiająca aplikacji do wykonywania zapytań w warstwie możliwości renderowania. Aplikacja może następnie podjąć różne ścieżki w czasie wykonywania, w zależności od warstwy renderowania obsługiwana przez sprzęt.  
  
 Dostępne są następujące funkcje, możliwości sprzętu graficznego i że mają największy wpływ na poziom warstwy renderowania:  
  
-   **Pamięć RAM wideo** określa ilość pamięci wideo na sprzęt graficzny, rozmiar i liczba buforów, które mogą służyć do składania grafiki.  
  
-   **Program do cieniowania pikseli** program do cieniowania pikseli jest funkcja, która oblicza wpływ na podstawie każdego piksela GPU. W zależności od rozwiązania wyświetlanych grafiki może być kilka milionów piksele, które muszą być przetworzone w każdej klatce wyświetlania.  
  
-   **Program do cieniowania wierzchołków** program do cieniowania wierzchołków jest funkcja, która wykonuje operacje matematyczne na danych wierzchołka obiektu GPU.  
  
-   **Obsługa multitekstur** multitekstur pomocy technicznej, który odwołuje się do możliwość stosowania co najmniej dwóch odrębnych tekstury podczas mieszania operacji na obiekcie grafiki 3D. Stopień multitexture pomocy technicznej jest określana przez liczbę jednostek multitexture na sprzęt graficzny.  
  
 Program do cieniowania pikseli, program do cieniowania wierzchołków i multitexture funkcje, które są używane do definiowania określonego [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] poziomy wersji, które z kolei są używane do definiowania warstwy renderowania różnią w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Funkcje, możliwości sprzętu graficznego i określić możliwości renderowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] System definiuje trzy poziomy renderowania:  
  
-   **Renderowanie warstwy 0** nie przyspieszania sprzętowego grafiki. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Poziom wersji jest niższy niż w wersji 7.0.  
  
-   **Renderowanie warstwy 1** przyspieszanie sprzętowe częściowe grafiki. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Poziomie wersji jest większa lub równa wersji 7.0, i **mniejszym** niż wersja 9.0.  
  
-   **Renderowanie warstwy 2** większość funkcji grafiki używał przyspieszania sprzętowego grafiki. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Poziomie wersji jest większa lub równa wersji 9.0.  
  
 Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] renderowanie warstw, zobacz [warstwy renderowania grafiki](graphics-rendering-tiers.md).  
  
## <a name="see-also"></a>Zobacz także

- [Optymalizacja wydajności aplikacji WPF](optimizing-wpf-application-performance.md)
- [Planowanie wydajności aplikacji](planning-for-application-performance.md)
- [Układ i projekt](optimizing-performance-layout-and-design.md)
- [Grafika 2D i obrazowanie](optimizing-performance-2d-graphics-and-imaging.md)
- [Zachowanie obiektu](optimizing-performance-object-behavior.md)
- [Zasoby aplikacji](optimizing-performance-application-resources.md)
- [Tekst](optimizing-performance-text.md)
- [Powiązanie danych](optimizing-performance-data-binding.md)
- [Inne zalecenia dotyczące wydajności](optimizing-performance-other-recommendations.md)
