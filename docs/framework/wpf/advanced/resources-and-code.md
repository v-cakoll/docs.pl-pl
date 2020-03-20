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
ms.openlocfilehash: 2917c9d15a6195c2d67781d6b2cfb0a5f1c136d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187172"
---
# <a name="resources-and-code"></a>Zasoby i kod
W tym przeglądzie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] koncentruje się na jak zasoby [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] mogą być dostępne lub tworzone przy użyciu kodu, a nie składni. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ogólnego wykorzystania zasobów i zasobów z perspektywy składni, zobacz [Zasoby XAML](xaml-resources.md).  

<a name="accessing"></a>
## <a name="accessing-resources-from-code"></a>Uzyskiwanie dostępu do zasobów z kodu  
 Klucze, które identyfikują zasoby, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jeśli są one zdefiniowane za pośrednictwem są również używane do pobierania określonych zasobów, jeśli zażądasz zasobu w kodzie. Najprostszym sposobem pobrania zasobu z kodu jest wywołanie <xref:System.Windows.FrameworkElement.FindResource%2A> <xref:System.Windows.FrameworkElement.TryFindResource%2A> lub metody z obiektów na poziomie struktury w aplikacji. Różnica w zachowaniu między tymi metodami jest, co się dzieje, jeśli żądany klucz nie zostanie znaleziony. <xref:System.Windows.FrameworkElement.FindResource%2A>podnosi wyjątek; <xref:System.Windows.FrameworkElement.TryFindResource%2A> nie spowoduje wyjątku, `null`ale zwraca . Każda metoda przyjmuje klucz zasobu jako parametr wejściowy i zwraca luźno wpisany obiekt. Zazwyczaj klucz zasobu jest ciągiem, ale istnieją okazjonalne użycie nieciągłe; szczegółowe informacje można znaleźć w sekcji [Używanie obiektów jako klawiszy.](#objectaskey) Zazwyczaj można rzutować zwrócony obiekt do typu wymaganego przez właściwość, która jest ustawiana podczas żądania zasobu. Logika wyszukiwania dla rozpoznawania zasobów kodu jest taka [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sama jak przypadek odwołania do zasobu dynamicznego. Wyszukiwanie zasobów rozpoczyna się od elementu wywołującego, a następnie kontynuuje kolejne elementy nadrzędne w drzewie logicznym. Wyszukiwanie kontynuuje w dalszym ciągu do zasobów aplikacji, motywów i zasobów systemowych, jeśli to konieczne. Żądanie kodu dla zasobu będzie poprawnie uwzględniać zmiany środowiska uruchomieniowego w słownikach zasobów, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]które mogły zostać wprowadzone po załadowaniu tego słownika zasobów z , a także dla zmian zasobów systemowych w czasie rzeczywistym.  
  
 Poniżej przedstawiono przykład krótkiego kodu, który znajduje zasób według klucza i <xref:System.Windows.Controls.Primitives.ButtonBase.Click> używa zwracaną wartość do ustawienia właściwości, zaimplementowane jako program obsługi zdarzeń.  
  
 [!code-csharp[PropertiesOvwSupport#ResourceProceduralGet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#resourceproceduralget)]
 [!code-vb[PropertiesOvwSupport#ResourceProceduralGet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#resourceproceduralget)]  
  
 Alternatywną metodą przypisywania odwołania <xref:System.Windows.FrameworkElement.SetResourceReference%2A>do zasobu jest . Ta metoda przyjmuje dwa parametry: klucz zasobu i identyfikator dla określonej właściwości zależności, która jest obecna w wystąpieniu elementu, do którego należy przypisać wartość zasobu. Funkcjonalnie ta metoda jest taka sama i ma tę zaletę, że nie wymaga żadnych rzutowania wartości zwracanych.  
  
 Jeszcze innym sposobem uzyskania dostępu do zasobów programowo <xref:System.Windows.FrameworkElement.Resources%2A> jest dostęp do zawartości właściwości jako słownika. Dostęp do słownika zawartego przez tę właściwość jest również jak można dodać nowe zasoby do istniejących kolekcji, sprawdź, czy dana nazwa klucza jest już podjęta w kolekcji i innych operacji słownika/kolekcji. Jeśli piszesz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikację w całości w kodzie, można również utworzyć całą kolekcję w kodzie, <xref:System.Windows.FrameworkElement.Resources%2A> przypisać klucze do niej, a następnie przypisać gotową kolekcję do właściwości ustalonego elementu. Zostanie to opisane w następnej sekcji.  
  
 Można indeksować w <xref:System.Windows.FrameworkElement.Resources%2A> obrębie dowolnej kolekcji, przy użyciu określonego klucza jako indeksu, ale należy pamiętać, że uzyskiwanie dostępu do zasobu w ten sposób nie jest zgodne z regułami normalnego środowiska wykonawczego rozpoznawania zasobów. Uzyskujesz tylko dostęp do tej konkretnej kolekcji. Wyszukiwanie zasobów nie będzie przechodzić przez zakres do katalogu głównego lub aplikacji, jeśli nie znaleziono prawidłowego obiektu na żądanym kluczu. Jednak to podejście może mieć korzyści wydajności w niektórych przypadkach właśnie dlatego, że zakres wyszukiwania klucza jest bardziej ograniczona. Zobacz <xref:System.Windows.ResourceDictionary> klasy, aby uzyskać więcej informacji na temat pracy ze słownikiem zasobów bezpośrednio.  
  
<a name="creating"></a>
## <a name="creating-resources-with-code"></a>Tworzenie zasobów za pomocą kodu  
 Jeśli chcesz utworzyć całą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikację w kodzie, można również utworzyć wszelkie zasoby w tej aplikacji w kodzie. Aby to osiągnąć, <xref:System.Windows.ResourceDictionary> utwórz nowe wystąpienie, a następnie dodaj wszystkie <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>zasoby do słownika przy użyciu kolejnych wywołań programu . Następnie należy <xref:System.Windows.ResourceDictionary> użyć utworzonego <xref:System.Windows.FrameworkElement.Resources%2A> w ten sposób elementu na elemencie, który jest obecny w zakresie strony lub <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>. Można również zachować <xref:System.Windows.ResourceDictionary> jako obiekt autonomiczny bez dodawania go do elementu. Jednak jeśli to zrobisz, należy uzyskać dostęp do zasobów w nim według klucza elementu, tak jakby był słownik ogólny. A, <xref:System.Windows.ResourceDictionary> który nie jest `Resources` dołączony do właściwości elementu nie istnieje jako część drzewa elementów i nie <xref:System.Windows.FrameworkElement.FindResource%2A> ma zakresu w sekwencji odnośnych, które mogą być używane przez i powiązanych metod.  
  
<a name="objectaskey"></a>
## <a name="using-objects-as-keys"></a>Używanie obiektów jako klawiszy  
 Większość użycia zasobów ustawi klucz zasobu jako ciąg. Jednak różne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcje celowo nie używają typu ciągu do określania kluczy, zamiast tego ten parametr jest obiektem. Możliwość posiadania zasobu być kluczem przez obiekt jest [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używany przez styl i obsługi motywów. Style w motywach, które stają się domyślnym stylem formantu <xref:System.Type> w przeciwnym razie niestągnął są kluczem do formantu, który powinien zastosować do. Jest kluczem według typu zapewnia niezawodny mechanizm wyszukiwania, który działa na domyślne wystąpienia każdego typu formantu i typ może być wykryty przez odbicie i używane do stylizacji klas pochodnych, nawet jeśli typ pochodny w przeciwnym razie nie ma stylu domyślnego. Klucz zasobu <xref:System.Type> zdefiniowanego w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku [x:Type Markup Extension](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)można określić za pomocą rozszerzenia znaczników typu . Podobne rozszerzenia istnieją dla innych użycia klucza [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nieciągłego, które obsługują funkcje, takie jak [ComponentResourceKey Markup Extension](componentresourcekey-markup-extension.md).  
  
## <a name="see-also"></a>Zobacz też

- [Zasoby XAML](xaml-resources.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
