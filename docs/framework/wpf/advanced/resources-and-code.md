---
title: Zasoby i kod
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1177f7eeb2b6184ea6ae0a021730658913a4794b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="resources-and-code"></a>Zasoby i kod
To omówienie koncentruje się na temat [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zasobów można uzyskać dostępu do lub utworzone za pomocą kodu zamiast [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] składni. Aby uzyskać więcej informacji na temat użycia zasobów ogólne i zasoby z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] perspektywy składni, zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
  
  
<a name="accessing"></a>   
## <a name="accessing-resources-from-code"></a>Uzyskiwanie dostępu do zasobów z kodu  
 Zidentyfikuj zasoby, jeśli są one zdefiniowane za pomocą kluczy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] są również używane do pobierania określonych zasobów, jeśli żądanie zasobu w kodzie. Najprostszym sposobem, aby pobrać zasobu z kodu jest wywołać albo <xref:System.Windows.FrameworkElement.FindResource%2A> lub <xref:System.Windows.FrameworkElement.TryFindResource%2A> metody z obiektów o poziomie struktury w aplikacji. Behawioralnej różnią te metody się, co się stanie, jeśli nie odnaleziono żądanego klucza. <xref:System.Windows.FrameworkElement.FindResource%2A>zgłasza wyjątek; <xref:System.Windows.FrameworkElement.TryFindResource%2A> nie generuje wyjątku lecz zwraca `null`. Każda metoda przyjmuje jako parametr wejściowy klucz zasobu i zwraca obiekt słabo typizowana. Zazwyczaj klucz zasobu jest ciągiem, ale ma typu okazjonalne użycia; zobacz [przy użyciu obiektów jako klucze](#objectaskey) sekcji, aby uzyskać szczegółowe informacje. Zwykle będzie rzutować zwróconego obiektu na typ wymagany przez właściwość ustawieniu podczas żądania do zasobu. Logika wyszukiwania do rozpoznania zasobu kodu jest taka sama jak odwołanie do zasobu dynamicznego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] case. Wyszukaj zasoby rozpoczyna się od elementu wywołującego, a następnie w dalszym ciągu elementy nadrzędne kolejnych w drzewie logicznym. Wyszukiwanie i jego nowszych wersjach nadal do zasobów aplikacji, kompozycje i zasobów systemowych, jeśli to konieczne. Żądanie kodu dla zasobu zostaną prawidłowo konto do zmiany środowiska uruchomieniowego w słownikach zasobów, które może zostały wprowadzone po tym słownik zasobów ładowana z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], a także do zmiany zasobów systemu w czasie rzeczywistym.  
  
 Przykład kodu krótki, wyszukuje zasób według klucza, który używa zwrócona wartość można ustawić właściwości, zaimplementowane jako <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obsługi zdarzeń.  
  
 [!code-csharp[PropertiesOvwSupport#ResourceProceduralGet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#resourceproceduralget)]
 [!code-vb[PropertiesOvwSupport#ResourceProceduralGet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#resourceproceduralget)]  
  
 Alternatywną metodą przypisywania odwołania zasobu jest <xref:System.Windows.FrameworkElement.SetResourceReference%2A>. Ta metoda przyjmuje dwa parametry: klucz zasobu oraz identyfikatora właściwości zależności w szczególności w wystąpieniu elementu, do której można przypisać wartości zasobów. Funkcjonalnym ta metoda jest taka sama i daje możliwość nie wymaga żadnych Rzutowanie wartości zwracanych.  
  
 Inny sposób programowy dostęp do zasobów ma dostępu do zawartości <xref:System.Windows.FrameworkElement.Resources%2A> właściwości w formie słownika. Uzyskiwanie dostępu do słownika zawarty w tej właściwości jest również, jak dodać nowych zasobów do istniejącej kolekcji, sprawdź, czy podana nazwa klucza jest już zajęty w kolekcji i innych operacji słownika/kolekcji. Jeśli piszesz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji całkowicie w kodzie, możesz można również utworzyć całą kolekcję w kodzie, przypisać kluczy, a następnie przypisz kolekcję gotowych do <xref:System.Windows.FrameworkElement.Resources%2A> właściwość elementu ustalonych. Będzie to opisana w następnej sekcji.  
  
 Może indeksować w żadnej podanej <xref:System.Windows.FrameworkElement.Resources%2A> kolekcji, przy użyciu określonego klucza jako indeks, ale należy zwrócić uwagę, że dostęp do zasobu w ten sposób nie zgodne z regułami normalne środowiska uruchomieniowego rozpoznawania zasobów. Tylko uzyskujesz dostęp do tej określonej kolekcji. Wyszukiwania zasobów zostanie nie można przechodzących przez zakres do katalogu głównego lub aplikacji Jeśli znaleziono nie prawidłowego obiektu żądanego klucza. Takie podejście może jednak zawierać zalety wydajności w niektórych przypadkach mówiąc, ponieważ zakres wyszukiwania dla klucza jest bardziej ograniczone. Zobacz <xref:System.Windows.ResourceDictionary> klasy, aby uzyskać więcej informacji na temat pracy z słownika zasobów bezpośrednio.  
  
<a name="creating"></a>   
## <a name="creating-resources-with-code"></a>Tworzenie zasobów z kodem  
 Jeśli chcesz utworzyć cały [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji w kodzie, można także utworzyć wszystkie zasoby w tej aplikacji w kodzie. Aby to osiągnąć, Utwórz nową <xref:System.Windows.ResourceDictionary> wystąpienia, a następnie dodaj wszystkie zasoby do słownika przy użyciu kolejnych wywołań <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>. Następnie należy użyć <xref:System.Windows.ResourceDictionary> utworzony w ten sposób, aby ustawić <xref:System.Windows.FrameworkElement.Resources%2A> właściwości w elemencie, który znajduje się w zakresie strony lub <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>. Można również obsługa <xref:System.Windows.ResourceDictionary> jako obiektu autonomicznego bez dodawania go do elementu. Jednak jeśli to zrobisz, można musi uzyskać dostęp do zasobów w niej według klucza elementu, tak jakby był on słownika ogólnego. A <xref:System.Windows.ResourceDictionary> nie jest dołączony do elementu `Resources` właściwość czy istnieje jako część elementu drzewa i ma żaden zakres w sekwencji wyszukiwania, które mogą być używane przez <xref:System.Windows.FrameworkElement.FindResource%2A> i związanych z metod.  
  
<a name="objectaskey"></a>   
## <a name="using-objects-as-keys"></a>Jako klucze przy użyciu obiektów  
 Większość użycia zasobów ustawi klucz zasób powinien być ciągiem. Jednak różnych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcje celowo nie należy używać typu ciąg do określenia klucze, zamiast tego parametru jest obiektem. Możliwość wystąpienia zasobu trzeba wprowadzić przez obiekt jest używany przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Obsługa stylów i motywów. Style w kompozycje, które stają się domyślny styl formantu w przeciwnym razie nie stylem każdego określonemu przez <xref:System.Type> którego ma być stosowana do formantu. Trwa wyznaczaną przez typ zapewnia mechanizm niezawodnej wyszukiwania, który działa na wystąpień poszczególnych typów kontroli i typu może być wykrywane przez odbicie i używane do zdefiniowania stylów klas pochodnych, nawet jeśli typ pochodny, w przeciwnym razie ma żaden styl domyślny. Można określić <xref:System.Type> klucza zdefiniowane w zasobu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] za pomocą [x: Type — rozszerzenie znaczników](../../../../docs/framework/xaml-services/x-type-markup-extension.md). Podobne rozszerzenia istnieją inne użycia klucza typu, które obsługują [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcje, takie jak [ComponentResourceKey — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zasoby dla języka XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Style i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md)
