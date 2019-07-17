---
title: Automatyzacja interfejsu użytkownika a skalowanie ekranu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scaling, screens
- screens, scaling
- UI (user interface), automation
- UI Automation
ms.assetid: 4380cad7-e509-448f-b9a5-6de042605fd4
ms.openlocfilehash: 4e101fffbd7e53cadce0b621d73ade2d1459ba00
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68237444"
---
# <a name="ui-automation-and-screen-scaling"></a>Automatyzacja interfejsu użytkownika a skalowanie ekranu
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] Umożliwia użytkownikom zmianę [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)] ustawienie dlatego najlepiej odpowiadającej [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementów na ekranie są większe. Mimo że tę funkcję długo udostępniono w [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)], w poprzednich wersjach skalowanie musiały być implementowana przez aplikacje. W [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)], Menedżer okien pulpitu wykonuje domyślne skalowanie dla wszystkich aplikacji, które nie obsługują własne skalowania. Aplikacje klienckie automatyzacji interfejsu użytkownika musi uwzględniać tej funkcji.  
  
<a name="Scaling_in_Windows_Vista"></a>   
## <a name="scaling-in-windows-vista"></a>Skalowanie w Windows Vista  
 Wartość domyślna [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ustawienie jest 96, co oznacza, że 96 pikseli zajmować szerokość lub wysokość jednego cala referencyjną. Dokładna miara "inch" zależy od tego, rozmiar i fizyczne rozdzielczości monitora. Na przykład w monitorze 12 cala, wysokość, w poziomie rozdzielczości 1280 pikseli linii poziomej 96 pikseli rozszerza o 9: 10 cala.  
  
 Zmiana [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ustawienie nie jest taka sama jak zmiana rozdzielczości ekranu. Za pomocą [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] skalowania, w pikselach fizycznych na ekranie pozostaje bez zmian. Jednak skalowanie jest stosowany do rozmiar i położenie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów. To skalowanie, które mogą być wykonywane automatycznie przez okno Menedżera pulpitu (DWM) dla pulpitu i aplikacje, które nie jawnie chcą nie można skalować.  
  
 W efekcie po użytkownik ustawia współczynnik skali do 120 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], poziomy lub pionowy CAL na ekranie staje się większe o 25 procent. Wszystkie wymiary są skalowane odpowiednio. Przesunięcie okna aplikacji z górnej i lewej krawędzi ekranu, zwiększa się o 25 procent. Jeśli włączono skalowanie aplikacji i aplikacja nie jest [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-pamiętać zwiększa rozmiar okna proporcję, wraz z przesunięcia i rozmiary wszystkich [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy, które zawiera.  
  
> [!NOTE]
>  Domyślnie Menedżera okien pulpitu nie przeprowadza skalowanie dla non -[!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-aplikacjom obsługującym, gdy użytkownik ustawi [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] do 120, ale to wykonać po [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] jest ustawiona na wartość niestandardową 144 lub wyższej. Użytkownik może jednak zmienić to zachowanie domyślne.  
  
 Skalowanie ekranu tworzy nowe wyzwania dla aplikacji, które są zainteresowane w jakikolwiek sposób za pomocą współrzędnych ekranu. Ekran zawiera teraz dwoma układami współrzędnych: fizycznymi i logicznymi. Fizyczne współrzędnych punktu są rzeczywiste przesunięcie w pikseli od górnej left pochodzenia. Logiczne współrzędne są przesunięcia, tak jak powinny, jeśli zostały skalowany pikseli, samodzielnie.  
  
 Załóżmy, że projekt okno dialogowe z przyciskiem na współrzędnych (100, 48). Gdy to okno dialogowe zostanie wyświetlona w domyślnej 96 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], przycisk znajduje się w fizycznych współrzędne (100, 48). Na 120 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], znajduje się on w fizycznych współrzędne (125, 60). Ale współrzędne logiczne są takie same, w dowolnym [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ustawienia: (100, 48).  
  
 Współrzędne logiczne są istotne, ponieważ ich zachowania systemu operacyjnego i aplikacji spójne bez względu na to [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ustawienie. Na przykład <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> zwykle zwraca wartość logiczną współrzędnych. Jeśli przesuniesz kursor nad elementem w oknie dialogowym takich samych współrzędnych są zwracane niezależnie od wartości [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ustawienie. Jeśli podczas rysowania kontrolki u (100, 100), są wizualizowane w tych współrzędnych w logiczne i zajmie się do tej samej pozycji względnej w dowolnym [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ustawienie.  
  
<a name="Scaling_in_UI_Automation_Clients"></a>   
## <a name="scaling-in-ui-automation-clients"></a>Skalowanie w klientach automatyzacji interfejsu użytkownika  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Interfejsu API nie korzysta z logicznego współrzędnych. Poniżej przedstawiono metody i właściwości zwracają współrzędne fizycznego lub wykonać je jako parametry.  
  
- <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 Domyślnie automatyzacji interfejsu użytkownika aplikacji klienckiej, uruchomiony w non-96 - [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] środowisko nie będzie można uzyskać poprawne wyniki z tych metod i właściwości. Na przykład, ponieważ pozycja kursora jest logiczną współrzędne, klient nie można po prostu przekazać tych współrzędnych w celu <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> uzyskać element, który jest pod kursorem. Ponadto aplikacja nie będzie można poprawnie umieścić windows spoza obszaru klienckiego.  
  
 Rozwiązanie jest w dwóch częściach.  
  
1. Po pierwsze należy aplikacja kliencka [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-aware. Aby to zrobić, należy wywołać [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] funkcja `SetProcessDPIAware` przy uruchamianiu. W kodzie zarządzanym następującą deklarację udostępnia tę funkcję.  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     Ta funkcja sprawia, że cały proces obsługującą ustawienia DPI, co oznacza, że wszystkie systemy windows, które należą do procesu nieskalowanego. W [przykładowe wyróżnienia](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter), na przykład czterech systemu windows, które tworzą prostokąt wyróżnienia znajdują się w fizycznych współrzędne uzyskany z automatyzacji interfejsu użytkownika, współrzędne logiczne. Jeśli plik nie były obsługującą ustawienia DPI, Podświetlenie będzie rysowany w współrzędne logiczne na komputerze stacjonarnym, co mogłoby spowodować nieprawidłowe położenie w środowisku bez rozdzielczości 96.  
  
2. Aby uzyskać współrzędne kursora, należy wywołać [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] funkcja `GetPhysicalCursorPos`. Poniższy przykład pokazuje sposób deklarowania i użyć tej funkcji.  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
>  Nie używaj <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>. Zachowanie tej właściwości poza klient — windows w skalowanym środowisku jest niezdefiniowane.  
  
 Jeśli Twoja aplikacja działa bezpośredniej komunikacji między procesami z non - [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-aplikacjom obsługującym może mieć konwertowania między logiczne i fizyczne współrzędnych przy użyciu [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] funkcje `PhysicalToLogicalPoint` i `LogicalToPhysicalPoint`.  
  
## <a name="see-also"></a>Zobacz także

- [Przykładowe wyróżnienia](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
