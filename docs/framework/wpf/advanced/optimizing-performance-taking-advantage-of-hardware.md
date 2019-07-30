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
ms.openlocfilehash: 7acf5a3f48ac4987037873c63111d988ec3a4979
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629647"
---
# <a name="optimizing-performance-taking-advantage-of-hardware"></a>Optymalizacja wydajności: Wykorzystanie możliwości sprzętu
Wewnętrzna architektura programu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ma dwa potoki renderowania, sprzęt i oprogramowanie. Ten temat zawiera informacje o tych potokach renderowania, które ułatwiają podejmowanie decyzji dotyczących optymalizacji wydajności aplikacji.  
  
## <a name="hardware-rendering-pipeline"></a>Potok renderowania sprzętowego  
 Jednym z najważniejszych czynników decydujących [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o wydajności jest to, że jest ona powiązana — im więcej pikseli ma być renderowanych, tym większym kosztem wydajności. Jednak lepsze renderowanie [!INCLUDE[TLA#tla_gpu](../../../../includes/tlasharptla-gpu-md.md)], które może zostać przeciążać do, osiąga korzyści, które można uzyskać. Potok renderowania sprzętowego aplikacji korzysta z funkcji Microsoft DirectX na sprzęcie, który obsługuje co najmniej program Microsoft DirectX w wersji 7,0. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Dalsze optymalizacje mogą być uzyskane przez sprzęt obsługujący funkcje Microsoft DirectX w wersji 7,0 i Właściwość PixelShader 2.0.  
  
## <a name="software-rendering-pipeline"></a>Potok renderowania oprogramowania  
 Potok [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] renderowania oprogramowania jest całkowicie powiązany z procesorem. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]wykorzystuje zestawy instrukcji SSE i SSE2 w PROCESORze, aby zaimplementować zoptymalizowany, w pełni funkcjonalny Rasteryzuj oprogramowania. Powrót do oprogramowania jest bezproblemowe, gdy funkcje aplikacji nie mogą być renderowane przy użyciu potoku renderowania sprzętowego.  
  
 Największym problemem z wydajnością podczas renderowania w trybie oprogramowania jest powiązana ze stawką wypełnienia, która jest definiowana jako liczba pikseli, które są używane. Jeśli obawiasz się o wydajność w trybie renderowania oprogramowania, spróbuj zminimalizować liczbę razy, przez które piksel zostanie odrysowany. Jeśli na przykład aplikacja ma niebieskie tło, a następnie renderuje nieco przezroczystego obrazu nad nim, wszystkie piksele w aplikacji zostaną wyrenderowane dwa razy. W związku z tym potrwa dwa razy, gdy aplikacja będzie renderowana w obrazie, niż gdyby miało tylko niebieskie tło.  
  
### <a name="graphics-rendering-tiers"></a>Poziomy zmiany grafiki  
 Przewidywanie konfiguracji sprzętowej, na której będzie działać aplikacja, może być bardzo trudne. Warto jednak wziąć pod uwagę projekt, który umożliwia aplikacji bezproblemowe przełączanie funkcji w przypadku uruchamiania na różnych urządzeniach, dzięki czemu może ona w pełni korzystać z każdej innej konfiguracji sprzętowej.  
  
 W tym celu program [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia funkcje umożliwiające określenie możliwości grafiki systemu w czasie wykonywania. Możliwość grafiki jest określana przez kategoryzację karty wideo jako jedną z trzech warstw możliwości renderowania. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]udostępnia interfejs API, który umożliwia aplikacji Wysyłanie zapytań do warstwy możliwości renderowania. Aplikacja może następnie zastosować różne ścieżki kodu w czasie wykonywania w zależności od warstwy renderowania obsługiwanej przez sprzęt.  
  
 Funkcje sprzętu grafiki, które mają największy wpływ na poziomy warstwy renderowania są następujące:  
  
- **Pamięć RAM wideo** Ilość pamięci wideo na sprzęcie graficznym określa rozmiar i liczbę buforów, które mogą być używane do składania grafiki.  
  
- Program do **cieniowania pikseli** Program do cieniowania pikseli jest funkcją przetwarzania grafiki, która oblicza wpływ na piksele. W zależności od rozdzielczości wyświetlanej grafiki może istnieć kilka milionów pikseli, które muszą zostać przetworzone dla każdej ramki wyświetlanej.  
  
- Program do cieniowania wierzchołków Program do cieniowania wierzchołków jest funkcją przetwarzania grafiki, która wykonuje operacje matematyczne na danych wierzchołka obiektu.  
  
- **Obsługa** wieloteksturowa Obsługa wieloteksturowego odnosi się do możliwości zastosowania dwóch lub większej liczby odrębnych tekstur podczas operacji mieszania na obiekcie graficznym 3W. Stopień wsparcia wieloteksturowego zależy od liczby jednostek wieloteksturowych na sprzęcie graficznym.  
  
 Program do cieniowania pikseli, cieniowania wierzchołków i funkcji wieloteksturowych jest używany do definiowania określonych poziomów wersji programu DirectX, które z kolei są używane do definiowania różnych warstw renderowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]w programie.  
  
 Funkcje sprzętu graficznego określają możliwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] renderowania aplikacji. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] System definiuje trzy warstwy renderowania:  
  
- **Warstwa renderowania 0** Brak przyspieszania sprzętowego. Poziom wersji programu DirectX jest mniejszy niż wersja 7,0.  
  
- **Warstwa renderowania 1** Częściowe przyspieszenie sprzętowe grafiki. Poziom wersji programu DirectX jest większy lub równy wersji 7,0 i jest **mniejszy** niż wersja 9,0.  
  
- **Renderowanie warstwy 2** Większość funkcji graficznych wykorzystuje przyspieszenie sprzętowe grafiki. Poziom wersji programu DirectX jest większy lub równy wersji 9,0.  
  
 Aby uzyskać więcej informacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na temat warstw renderowania, zobacz [warstwy renderowania grafiki](graphics-rendering-tiers.md).  
  
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
