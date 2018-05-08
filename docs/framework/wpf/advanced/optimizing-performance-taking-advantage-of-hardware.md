---
title: 'Optymalizacja wydajności: wykorzystanie sprzętu'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], performance
- hardware rendering pipeline [WPF]
- rendering tiers [WPF]
- graphics rendering tiers [WPF]
- graphics [WPF], rendering tiers
- software rendering pipeline [WPF]
ms.assetid: bfb89bae-7aab-4cac-a26c-a956eda8fce2
ms.openlocfilehash: eb790da63b4636e3dd6c25ea118075304702acc0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="optimizing-performance-taking-advantage-of-hardware"></a>Optymalizacja wydajności: wykorzystanie sprzętu
Architektura wewnętrzny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ma dwa renderowania potoki, sprzętu i oprogramowania. Ten temat zawiera informacje o tych potoki renderowania podejmowanie decyzji o optymalizacji wydajności aplikacji.  
  
## <a name="hardware-rendering-pipeline"></a>Potoku renderowania sprzętu  
 Jedną z najbardziej ważne czynniki wpływające [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wydajności jest powiązany renderowania — więcej pikseli, należy renderować większą wydajność kosztów. Jednak im więcej renderowania, które można odciążać do [!INCLUDE[TLA#tla_gpu](../../../../includes/tlasharptla-gpu-md.md)], uzyskać więcej korzyści w zakresie wydajności. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Potoku renderowania sprzętu aplikacja wykorzystuje pełną [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] funkcje na sprzęcie, który obsługuje co najmniej [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] w wersji 7.0. Dodatkowe optymalizacje można uzyskać przez sprzęt obsługujący [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] w wersji 7.0 i właściwość PixelShader 2.0 + funkcji.  
  
## <a name="software-rendering-pipeline"></a>Potoku renderowania oprogramowania  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Potoku renderowania oprogramowania całkowicie CPU jest powiązany. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wykorzystuje instrukcji SSE i SSE2 ustawia w Procesora do zaimplementowania rasteryzator oprogramowania zoptymalizowane, w pełni funkcjonalne. Powrót do oprogramowania jest bezproblemowe funkcjonalność aplikacji nie może być renderowany przy użyciu sprzętu potoku renderowania za każdym razem.  
  
 Problem z wydajnością największych wystąpią podczas renderowania w trybie oprogramowania jest powiązany z wypełnienia szybkości, która jest zdefiniowana jako liczbę pikseli, które są renderowania. Jeśli dane dotyczące wydajności w tryb renderowania oprogramowania, należy dążyć do minimalizacji ile razy piksel jest rysowane. Na przykład jeśli masz aplikację niebieskim tle nad nim następnie renderuje nieco przezroczystego obrazu, będą zawierały wszystkie piksele w aplikacji dwa razy. W związku z tym potrwa dwa razy tak długo, renderowanie aplikacji z obrazem niż niebieskiego tła.  
  
### <a name="graphics-rendering-tiers"></a>Poziomy zmiany grafiki  
 Może być bardzo trudne do przewidzenia, aplikacja zostanie uruchomiona w konfiguracji sprzętu. Warto jednak wziąć pod uwagę projekt, który umożliwia aplikacjom bezproblemowo przełączyć funkcji uruchomionej na inny sprzęt, tak aby może potrwać zalet każdej innej konfiguracji sprzętu.  
  
 Aby to osiągnąć, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia funkcje, aby określić możliwości grafiki systemu w czasie wykonywania. Możliwość grafiki zależy od klasyfikacji karty wideo jako jedną z trzech renderowania możliwości warstwy. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przedstawia [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] umożliwiająca aplikacji do badania warstwy możliwość renderowania. Aplikację można następnie automatycznie podjąć różne ścieżki w czasie wykonywania w zależności od warstwy renderowania obsługiwana przez sprzęt.  
  
 Funkcje sprzętu grafiki, że większość wpływ poziomy warstwy renderowania to:  
  
-   **Ilość pamięci RAM wideo** określa ilość pamięci wideo na sprzęcie grafiki, rozmiaru i liczby buforów, które mogą służyć do składania grafiki.  
  
-   **Program do cieniowania pikseli** programu do cieniowania pikseli jest grafiki, funkcji, który oblicza wyniki na podstawie każdego piksela przetwarzania. W zależności od rozdzielczości grafiki wyświetlane może istnieć kilka milionów pikseli, które muszą być przetworzone dla każdej ramce wyświetlania.  
  
-   **Program do cieniowania wierzchołków** grafiki, funkcji, który wykonuje operacji matematycznych na dane wierzchołków obiektu przetwarzania jest cieniowania wierzchołków.  
  
-   **Obsługa multitekstur** Obsługa multitekstur odwołuje się do możliwość zastosowania co najmniej dwa różne tekstury podczas mieszania operacji na obiekcie grafiki 3D. Stopień multitexture pomocy technicznej jest określana przez liczbę jednostek multitexture na sprzęcie grafiki.  
  
 Program do cieniowania pikseli, program do cieniowania wierzchołków i multitexture funkcje, które są używane do definiowania określonych [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] poziomy wersji, które z kolei są używane do definiowania warstw różnych renderowania w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Funkcje sprzętowe grafiki stwierdzenie, renderowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Systemu definiuje trzy warstwy renderowania:  
  
-   **Renderowanie warstwy 0** nie przyspieszanie sprzętowe grafiki. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Poziom wersja jest starsza niż wersja 7.0.  
  
-   **Renderowanie warstwy 1** przyspieszanie sprzętowe grafiki częściowej. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Poziom wersji jest większa niż lub równa w wersji 7.0, i **mniejszym** niż wersja 9.0.  
  
-   **Renderowanie warstwy 2** przyspieszanie sprzętowe grafiki używać większości jej funkcji grafiki. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Poziom wersji jest większa niż lub równa wersji 9.0.  
  
 Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] renderowania warstw, zobacz [warstw renderowania grafiki](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Optymalizacja wydajności aplikacji WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Planowanie wydajności aplikacji](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Układ i projekt](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Grafika 2D i obrazowanie](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Zachowanie obiektu](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Zasoby aplikacji](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Tekst](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Powiązanie danych](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Inne zalecenia dotyczące wydajności](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
