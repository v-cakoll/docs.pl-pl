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
ms.openlocfilehash: a59223bfbe9506aa0028933d55b74e24d5595c32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629551"
---
# <a name="ui-automation-and-screen-scaling"></a>Automatyzacja interfejsu użytkownika a skalowanie ekranu
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)]umożliwia użytkownikom zmianę ustawienia punktów na cal (dpi), tak aby większość [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementów na ekranie była większa. Chociaż ta funkcja była dostępna w programie [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)], we wcześniejszych wersjach skalowanie musiało zostać zaimplementowane przez aplikacje. W [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)]programie Menedżer okien pulpitu wykonuje domyślne skalowanie dla wszystkich aplikacji, które nie obsługują własnego skalowania. Aplikacje klienckie automatyzacji interfejsu użytkownika muszą korzystać z tej funkcji w ramach konta.  
  
<a name="Scaling_in_Windows_Vista"></a>   
## <a name="scaling-in-windows-vista"></a>Skalowanie w systemie Windows Vista  
 Domyślnym ustawieniem DPI jest 96, co oznacza, że 96 pikseli zajmują szerokość lub wysokość jednego zakładanego cala. Dokładna miara "CAL" zależy od rozmiaru i fizycznej rozdzielczości monitora. Na przykład w przypadku monitora o szerokości 12 cali, w rozdzielczości poziomej 1280 pikseli, pozioma linia 96 pikseli rozciąga się na około 9/10 cala.  
  
 Zmiana ustawienia DPI nie jest taka sama jak zmiana rozdzielczości ekranu. W przypadku skalowania dpi liczba pikseli fizycznych na ekranie pozostaje taka sama. Jednak skalowanie jest stosowane do rozmiaru i lokalizacji [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów. Skalowanie może być wykonywane automatycznie przez Menedżer okien pulpitu (DWM) dla komputerów stacjonarnych i dla aplikacji, które nie proszą jawnie o skalowanie.  
  
 W efekcie, gdy użytkownik ustawia współczynnik skalowania na 120 DPI, poziom pionowy lub poziomy na ekranie będzie większy o 25%. Wszystkie wymiary są odpowiednio skalowane. Przesunięcie okna aplikacji od górnej i lewej krawędzi ekranu zwiększa się o 25%. Jeśli skalowanie aplikacji jest włączone i aplikacja nie obsługuje rozdzielczości DPI, rozmiar okna zwiększa się w tej samej proporcji wraz z przesunięciami i rozmiarem wszystkich [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów, które zawiera.  
  
> [!NOTE]
>  Domyślnie Menedżer DWM nie wykonuje skalowania dla aplikacji nieobsługujących rozdzielczości DPI, gdy użytkownik ustawia wartość DPI na 120, ale wykonuje ją, gdy dla dpi zostanie ustawiona niestandardowa wartości 144 lub wyższej. Jednak użytkownik może zastąpić zachowanie domyślne.  
  
 Skalowanie ekranu tworzy nowe wyzwania dla aplikacji, które są zainteresowane w dowolny sposób z współrzędnymi ekranu. Na ekranie znajdują się teraz dwa systemy współrzędnych: fizyczne i logiczne. Współrzędne fizyczne punktu to rzeczywiste przesunięcie (w pikselach) od lewego górnego rogu pochodzenia. Współrzędne logiczne są przesunięciami, tak jak gdyby same piksele były skalowane.  
  
 Załóżmy, że zaprojektowano okno dialogowe z przyciskiem we współrzędnych (100, 48). Gdy to okno dialogowe jest wyświetlane domyślnie 96 dpi, przycisk znajduje się w fizycznych współrzędnych (100, 48). O 120 DPI, znajduje się on w fizycznych współrzędnych (125, 60). Jednak współrzędne logiczne są takie same w dowolnym ustawieniu dpi: (100, 48).  
  
 Współrzędne logiczne są ważne, ponieważ sprawiają, że zachowanie systemu operacyjnego i aplikacji jest spójne niezależnie od ustawienia DPI. Na przykład <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> zwykle zwraca współrzędne logiczne. Jeśli przesuniesz kursor nad element w oknie dialogowym, te same współrzędne są zwracane niezależnie od ustawienia DPI. Jeśli narysujesz formant w (100, 100), jest on rysowany jako współrzędne logiczne i zastąpi to samo względne położenie przy użyciu dowolnego ustawienia DPI.  
  
<a name="Scaling_in_UI_Automation_Clients"></a>   
## <a name="scaling-in-ui-automation-clients"></a>Skalowanie w klientach automatyzacji interfejsu użytkownika  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Interfejs API nie używa współrzędnych logicznych. Następujące metody i właściwości zwracają współrzędne fizyczne lub przyjmują je jako parametry.  
  
- <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 Domyślnie aplikacja klienta automatyzacji interfejsu użytkownika działająca w środowisku innym niż 96 dpi nie będzie mogła uzyskać prawidłowych wyników z tych metod i właściwości. Na przykład ze względu na to, że położenie kursora jest zgodne ze współrzędnymi logicznymi, <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> klient nie może po prostu przekazać tych współrzędnych w celu uzyskania elementu znajdującego się pod kursorem. Ponadto aplikacja nie będzie w stanie poprawnie umieścić okien poza jego obszarem klienckim.  
  
 Rozwiązanie znajduje się w dwóch częściach.  
  
1. Najpierw należy pamiętać o rozdzielczości DPI aplikacji klienta. W tym celu wywołaj [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] funkcję `SetProcessDPIAware` przy uruchamianiu. W kodzie zarządzanym następująca deklaracja udostępnia tę funkcję.  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     Ta funkcja wykonuje cały proces z uwzględnieniem rozdzielczości DPI, co oznacza, że wszystkie okna, które należą do procesu, nie są skalowane. W [przykładzie](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)wyróżnienia, na przykład cztery okna, które tworzą prostokąt wyróżnienia, znajdują się na współrzędnych fizycznych uzyskanych z automatyzacji interfejsu użytkownika, a nie na współrzędnych logicznych. Jeśli próbka nie była uwzględniana przy użyciu rozdzielczości DPI, wyróżnienie zostanie narysowane na współrzędne logiczne na pulpicie, co spowoduje nieprawidłowe umieszczenie w środowisku innym niż 96 dpi.  
  
2. Aby uzyskać współrzędne kursora, wywołaj [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] funkcję `GetPhysicalCursorPos`. Poniższy przykład pokazuje, jak zadeklarować tę funkcję i korzystać z niej.  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
>  Nie należy używać <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>. Zachowanie tej właściwości poza oknami klienckimi w środowisku skalowanym jest niezdefiniowane.  
  
 Jeśli aplikacja wykonuje bezpośrednią komunikację międzyprocesową z aplikacjami obsługującymi [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] funkcję bez użycia rozdzielczości DPI, można skonwertować współrzędne logiczne i fizyczne przy użyciu funkcji `PhysicalToLogicalPoint` i `LogicalToPhysicalPoint`.  
  
## <a name="see-also"></a>Zobacz także

- [Wyróżnij przykład](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
