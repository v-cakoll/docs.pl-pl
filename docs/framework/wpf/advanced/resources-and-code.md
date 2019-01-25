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
ms.openlocfilehash: ff259dae06ef7347dd9fa3afbab68ae67e9146a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725534"
---
# <a name="resources-and-code"></a>Zasoby i kod
W tym omówieniu koncentruje się na temat [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zasobów można uzyskać dostępu do lub utworzone przy użyciu kodu zamiast [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] składni. Aby uzyskać więcej informacji na temat użycia zasobów ogólnych i zasobów z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] perspektywy składni, zobacz [zasoby XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
  
  
<a name="accessing"></a>   
## <a name="accessing-resources-from-code"></a>Uzyskiwanie dostępu do zasobów z poziomu kodu  
 Klucze, określających zasoby, jeśli są one definiowane za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] są również używane do pobierania określonych zasobów, jeśli żądanie zasobów w kodzie. Najprostszym sposobem pobrania zasobu z kodu jest wywołanie, albo <xref:System.Windows.FrameworkElement.FindResource%2A> lub <xref:System.Windows.FrameworkElement.TryFindResource%2A> metody z obiektów o poziomie struktury w aplikacji. Zachowania różnica między te metody polega na tym, co się stanie, jeśli nie odnaleziono żądanego klucza. <xref:System.Windows.FrameworkElement.FindResource%2A> zgłasza wyjątek; <xref:System.Windows.FrameworkElement.TryFindResource%2A> nie zgłosi wyjątek, ale zwraca `null`. Każda metoda pobiera klucz zasobu jako parametr wejściowy i zwraca obiekt, co słabo typizowana. Zazwyczaj klucz zasobu jest ciągiem, ale występują sporadyczne typu użycia; zobacz [przy użyciu obiektów jako klucze](#objectaskey) sekcji, aby uzyskać szczegółowe informacje. Zwykle będzie rzutować zwracany obiekt na typ wymagany przez właściwość, dla którego ustawiany podczas żądania zasobu. Logika wyszukiwania do rozpoznawania zasobu kod jest taki sam jak odwołanie do zasobu dynamiczne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przypadek. Wyszukaj zasoby rozpoczyna się od elementu wywołującego, a następnie w dalszym ciągu kolejnych nadrzędne elementy w drzewie logicznym. Wyszukiwanie jest kontynuowane i nowszych wersjach do zasobów aplikacji, kompozycje i zasobów systemowych, jeśli to konieczne. Żądanie kodu dla zasobu poprawnie będzie uwzględniać zmiany środowiska uruchomieniowego w słownikach zasobów, które może być wprowadzone po tego słownika zasobów ładowana z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], a także do zmiany zasobu systemu czasu rzeczywistego.  
  
 Poniżej przedstawiono przykładowy kod krótki wyszukuje zasób według klucza, która używa zwracanej wartości do ustawienia właściwości zaimplementowane jako <xref:System.Windows.Controls.Primitives.ButtonBase.Click> programu obsługi zdarzeń.  
  
 [!code-csharp[PropertiesOvwSupport#ResourceProceduralGet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#resourceproceduralget)]
 [!code-vb[PropertiesOvwSupport#ResourceProceduralGet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#resourceproceduralget)]  
  
 Alternatywną metodą w przypadku przypisywania odwołanie do zasobu jest <xref:System.Windows.FrameworkElement.SetResourceReference%2A>. Ta metoda przyjmuje dwa parametry: klucz zasobu oraz identyfikator dla właściwości określonej zależności, który jest dostępny w wystąpieniu elementu, do której można przypisać wartość zasobu. Funkcjonalnie ta metoda jest taki sam i ma tę zaletę nie wymaga żadnych Rzutowanie wartości zwracanych.  
  
 Inny sposób programowo uzyskać dostęp do zasobów jest uzyskać dostęp do zawartości <xref:System.Windows.FrameworkElement.Resources%2A> właściwości w formie słownika. Uzyskiwanie dostępu do słownika zawarte w tej właściwości jest również, jak dodać nowe zasoby do istniejących kolekcji, wyboru, aby sprawdzić, czy dana nazwa klucza jest już zajęta w kolekcji i inne operacje słownik/kolekcji. Jeśli piszesz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikację całkowicie w kodzie, należy można również utworzyć całą kolekcję w kodzie, przypisać klucze do niej, a następnie przypisz kolekcja gotowych do <xref:System.Windows.FrameworkElement.Resources%2A> właściwość ustanowionych elementu. Spowoduje to być opisane w następnej sekcji.  
  
 Umożliwia indeksowanie w dowolnej podanej <xref:System.Windows.FrameworkElement.Resources%2A> kolekcji, przy użyciu określonego klucza jako indeks, ale należy pamiętać, że dostęp do zasobu w ten sposób nie jest zgodna z reguły normalne środowiska uruchomieniowego rozdzielczości zasobów. Tylko uzyskujesz dostęp do tej określonej kolekcji. Wyszukiwania zasobów będzie nie być przechodzenie przez zakres głównego lub aplikacji Jeśli nie prawidłowego obiektu została odnaleziona na żądany klucz. Jednak takie podejście może być korzyści związanych z wydajnością w niektórych przypadkach precyzyjnie, ponieważ zakres wyszukiwania dla klucza jest bardziej ograniczone. Zobacz <xref:System.Windows.ResourceDictionary> klasy, aby uzyskać więcej informacji na temat sposobu pracy z słownik zasobów bezpośrednio.  
  
<a name="creating"></a>   
## <a name="creating-resources-with-code"></a>Tworzenie zasobów przy użyciu kodu  
 Jeśli chcesz tworzyć cały [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji w kodzie, można także utworzyć wszystkie zasoby w tej aplikacji w kodzie. Aby to osiągnąć, Utwórz nowy <xref:System.Windows.ResourceDictionary> wystąpienia, a następnie dodaj wszystkie zasoby do słownika przy użyciu kolejne wywołania <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>. Następnie należy użyć <xref:System.Windows.ResourceDictionary> utworzony w ten sposób, aby ustawić <xref:System.Windows.FrameworkElement.Resources%2A> właściwość element, który znajduje się w zakresie strony lub <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>. Można również utrzymania <xref:System.Windows.ResourceDictionary> jako obiektu autonomicznego bez dodawania go do elementu. Jednak jeśli to zrobisz, możesz musi uzyskać dostęp do zasobów w niej według klucza elementu, tak jakby generyczny słownik. A <xref:System.Windows.ResourceDictionary> nie jest dołączony do elementu `Resources` właściwości czy istnieje jako część drzewa elementów i ma nie zakres, w kolejności wyszukiwania, który może być używany przez <xref:System.Windows.FrameworkElement.FindResource%2A> i powiązanych metod.  
  
<a name="objectaskey"></a>   
## <a name="using-objects-as-keys"></a>Użycie obiektów jako klucze  
 Większość użycia zasobów ustawi klucz zasobu jest ciąg. Jednak różne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcji celowo nie należy używać typu string do określania kluczy należy zamiast tego parametru jest obiektem. Możliwość wystąpienia zasobu, można wprowadzić za pomocą obiektu jest używany przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] styl i motyw pomocy technicznej. Style motywów, które stają się domyślnego stylu dla formantu inaczej niż stylem są każdego kluczach <xref:System.Type> kontrolki, do którego mają dotyczyć. Trwa kluczach typu zapewnia mechanizm niezawodne wyszukiwania, który działa na wystąpień każdego typu formantu, a typ można wykrywane przez odbicie i umożliwiający style klasy pochodne, nawet jeśli typ pochodny, w przeciwnym razie ma nie domyślnego stylu. Można określić <xref:System.Type> klucza dla zasobu zdefiniowanego w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przy użyciu [x: Type Markup Extension](../../../../docs/framework/xaml-services/x-type-markup-extension.md). Podobne rozszerzenia istnieje inne użycia klucza typu, które obsługują [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcje, takie jak [componentresourcekey — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md).  
  
## <a name="see-also"></a>Zobacz także
- [Zasoby XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)
- [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)
