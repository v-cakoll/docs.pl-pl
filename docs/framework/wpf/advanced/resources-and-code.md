---
title: Zasoby i kod
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys [WPF], using objects as
- resources [WPF], accessing from procedural code
- procedural code [WPF], creating resources with
- procedural code [WPF], accessing resources from
- resources [WPF], creating with procedural code
ms.assetid: c1cfcddb-e39c-41c8-a7f3-60984914dfae
ms.openlocfilehash: 3d504467c137c1e3f494e120217957661f4e75a3
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458759"
---
# <a name="resources-and-code"></a>Zasoby i kod
Ten przegląd koncentruje się na sposobie uzyskiwania dostępu do zasobów [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] lub tworzenia ich przy użyciu kodu, a nie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] składni. Aby uzyskać więcej informacji na temat ogólnego użycia zasobów i zasobów z perspektywy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ej składni, zobacz [zasoby XAML](xaml-resources.md).  

<a name="accessing"></a>   
## <a name="accessing-resources-from-code"></a>Uzyskiwanie dostępu do zasobów z kodu  
 Klucze identyfikujące zasoby, jeśli są zdefiniowane za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] są również używane do pobierania określonych zasobów, Jeśli zażądasz zasobu w kodzie. Najprostszym sposobem na pobranie zasobu z kodu jest wywołanie <xref:System.Windows.FrameworkElement.FindResource%2A> lub metody <xref:System.Windows.FrameworkElement.TryFindResource%2A> z obiektów poziomu platformy w aplikacji. Różnica między tymi metodami zależy od tego, co się stanie, jeśli nie zostanie znaleziony żądany klucz. <xref:System.Windows.FrameworkElement.FindResource%2A> zgłasza wyjątek; <xref:System.Windows.FrameworkElement.TryFindResource%2A> nie zgłosi wyjątku, ale zwraca `null`. Każda metoda przyjmuje klucz zasobu jako parametr wejściowy i zwraca obiekt z swobodnym typem. Zazwyczaj klucz zasobu jest ciągiem, ale istnieją sporadyczne nieciągi użycia; Aby uzyskać szczegółowe informacje, zobacz sekcję [Używanie obiektów jako kluczy](#objectaskey) . Zazwyczaj można rzutować zwracany obiekt na typ wymagany przez właściwość, która jest ustawiana podczas żądania zasobu. Logika wyszukiwania dla rozpoznawania zasobów kodu jest taka sama jak w przypadku odwołania do zasobu dynamicznego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przypadku. Wyszukiwanie zasobów zaczyna się od wywołującego elementu, a następnie kontynuuje kolejne elementy nadrzędne w drzewie logicznym. Wyszukiwanie jest kontynuowane w zasobach aplikacji, motywach i zasobach systemowych w razie potrzeby. Żądanie Code dla zasobu będzie poprawnie uwzględniać zmiany w środowisku uruchomieniowym w słownikach zasobów, które mogły zostać wprowadzone po załadowaniu tego słownika zasobów z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], a także w przypadku zmian zasobów systemu w czasie rzeczywistym.  
  
 Poniżej znajduje się krótki kod przykładowy, który wyszukuje zasób według klucza i używa wartości zwracanej do ustawiania właściwości wdrożonej jako <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obsługi zdarzeń.  
  
 [!code-csharp[PropertiesOvwSupport#ResourceProceduralGet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#resourceproceduralget)]
 [!code-vb[PropertiesOvwSupport#ResourceProceduralGet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#resourceproceduralget)]  
  
 Alternatywną metodą przypisywania odwołania do zasobu jest <xref:System.Windows.FrameworkElement.SetResourceReference%2A>. Ta metoda przyjmuje dwa parametry: klucz zasobu i identyfikator określonej właściwości zależności, która jest obecna w wystąpieniu elementu, do którego ma zostać przypisana wartość zasobu. Funkcjonalnie ta metoda jest taka sama i ma zalety niewymagające rzutowania wartości zwracanych.  
  
 Nadal inny sposób uzyskiwania dostępu do zasobów programowo polega na uzyskiwaniu dostępu do zawartości właściwości <xref:System.Windows.FrameworkElement.Resources%2A> jako słownika. Dostęp do słownika zawartego w tej właściwości polega na tym, jak dodać nowe zasoby do istniejących kolekcji, sprawdzić, czy dana nazwa klucza została już wprowadzona w kolekcji, oraz innych operacji słownika/kolekcji. Jeśli piszesz aplikację [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w całości w kodzie, możesz również utworzyć całą kolekcję w kodzie, przypisać do niej klucze, a następnie przypisać ukończoną kolekcję do właściwości <xref:System.Windows.FrameworkElement.Resources%2A> określonego elementu. Zostanie to opisane w następnej sekcji.  
  
 Można indeksować w ramach danej kolekcji <xref:System.Windows.FrameworkElement.Resources%2A> przy użyciu określonego klucza jako indeksu, ale należy pamiętać, że uzyskanie dostępu do zasobu w ten sposób nie jest zgodne z normalnymi regułami środowiska uruchomieniowego w ramach rozwiązywania zasobów. Uzyskujesz dostęp do tej konkretnej kolekcji. Wyszukiwanie zasobów nie przejdzie do zakresu głównego lub aplikacji, jeśli w żądanym kluczu nie znaleziono prawidłowego obiektu. Jednak takie podejście może mieć precyzyjne zalety wydajności w niektórych przypadkach, ponieważ zakres wyszukiwania klucza jest bardziej ograniczony. Zapoznaj się z klasą <xref:System.Windows.ResourceDictionary>, aby uzyskać szczegółowe informacje na temat sposobu pracy bezpośrednio z słownikiem zasobów.  
  
<a name="creating"></a>   
## <a name="creating-resources-with-code"></a>Tworzenie zasobów przy użyciu kodu  
 Jeśli chcesz utworzyć całą aplikację [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w kodzie, możesz również utworzyć wszystkie zasoby w tej aplikacji w kodzie. Aby to osiągnąć, Utwórz nowe wystąpienie <xref:System.Windows.ResourceDictionary> a następnie Dodaj wszystkie zasoby do słownika przy użyciu kolejnych wywołań do <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>. Następnie użyj <xref:System.Windows.ResourceDictionary> utworzonego w ten sposób, aby ustawić właściwość <xref:System.Windows.FrameworkElement.Resources%2A> dla elementu, który znajduje się w zakresie strony, lub <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>. Można również zachować <xref:System.Windows.ResourceDictionary> jako obiekt autonomiczny bez dodawania go do elementu. Jeśli jednak to zrobisz, musisz uzyskać dostęp do zasobów w ramach klucza elementu, tak jakby były słownikiem ogólnym. <xref:System.Windows.ResourceDictionary>, który nie jest dołączony do właściwości elementu `Resources` nie istnieje jako część drzewa elementów i nie ma zakresu w sekwencji wyszukiwania, który może być używany przez <xref:System.Windows.FrameworkElement.FindResource%2A> i powiązane metody.  
  
<a name="objectaskey"></a>   
## <a name="using-objects-as-keys"></a>Używanie obiektów jako kluczy  
 Większość użycia zasobów ustawi klucz zasobu jako ciąg. Jednak różne funkcje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] celowo nie używają typu ciągu do określenia kluczy, zamiast tego ten parametr jest obiektem. Możliwość umieszczania zasobu przez obiekt jest używana przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stylu i obsługi motywów. Style w motywach, które stają się stylem domyślnym dla kontrolki nieposiadające stylu, są podżądane przez <xref:System.Type> kontrolki, do których mają zastosowanie. Ustalanie przez typ zapewnia niezawodny mechanizm wyszukiwania, który działa na wystąpieniach domyślnych każdego typu formantu, a typ może być wykrywany przez odbicie i używane do ustawiania stylów klas pochodnych, mimo że typ pochodny nie ma stylu domyślnego. Możesz określić klucz <xref:System.Type> dla zasobu zdefiniowanego w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przy użyciu [rozszerzenia znacznika x:Type —](../../xaml-services/x-type-markup-extension.md). Podobne rozszerzenia istnieją dla innych nieciąguowych użycia kluczy, które obsługują funkcje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], takie jak [rozszerzenie znacznika ComponentResourceKey](componentresourcekey-markup-extension.md).  
  
## <a name="see-also"></a>Zobacz także

- [Zasoby XAML](xaml-resources.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
