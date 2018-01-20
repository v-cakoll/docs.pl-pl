---
title: "Automatyzacja interfejsu użytkownika a skalowanie ekranu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scaling, screens
- screens, scaling
- UI (user interface), automation
- UI Automation
ms.assetid: 4380cad7-e509-448f-b9a5-6de042605fd4
caps.latest.revision: "16"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: bb33d3175cf9e43797125b47c811042771e45782
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ui-automation-and-screen-scaling"></a>Automatyzacja interfejsu użytkownika a skalowanie ekranu
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)]Umożliwia użytkownikom zmianę [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)] ustawienie dlatego najlepiej odpowiadającej [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementy na ekranie są większe. Mimo że ta funkcja długo był dostępny w [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)], w poprzednich wersjach skalowanie musiały być implementowana przez aplikacje. W [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)], domyślne skalowania dla wszystkich aplikacji, które nie obsługują skalowanie własnej wykonuje Menedżera okien pulpitu. Automatyzacja interfejsu użytkownika aplikacji klienckich musi uwzględniać tej funkcji.  
  
<a name="Scaling_in_Windows_Vista"></a>   
## <a name="scaling-in-windows-vista"></a>Skalowanie w systemie Windows Vista  
 Wartość domyślna [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ustawienie jest 96, co oznacza, że 96 pikseli zajmują szerokości lub wysokości jednego zakładaną cala. Dokładna miara "inch" zależy od rozmiaru i fizycznej rozdzielczości monitora. Na przykład na monitorze 12 cala, wysokość, na rozdzielczość pozioma 1280 pikseli, linia pozioma 96 pikseli rozszerza około 9/10 cala.  
  
 Zmiana [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ustawienie nie jest taka sama jak zmiana rozdzielczości ekranu. Z [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] skalowania, liczba fizycznych pikseli na ekranie jest taka sama. Jednak skalowania jest stosowana do rozmiar i położenie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów. Skalowanie tego mogą być wykonywane automatycznie przez Menedżera okien pulpitu (DWM) dla komputera stacjonarnego i dla aplikacji, które jawnie nie pytaj o skalowania.  
  
 W efekcie Jeśli użytkownik ustawia współczynnik skali do 120 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], wzrost pionowych lub poziomych CAL na ekranie o 25 procent. Wszystkie wymiary są skalowane odpowiednio. Przesunięcie okna aplikacji z górnej i lewej krawędzi ekranu zwiększa się o 25 procent. Jeśli aplikacji odbierającej jest włączone, a aplikacja nie jest [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-pamiętać zwiększa rozmiar okna proporcję, wraz z przesunięcia i rozmiary wszystkich [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] zawiera elementy.  
  
> [!NOTE]
>  Domyślnie DWM nie przeprowadza skalowanie inną niż[!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-aplikacjom obsługującym, gdy użytkownik [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] do 120, ale tego dokonać podczas [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ma ustawioną wartość niestandardową 144 lub wyższy. Użytkownik może jednak zmienić zachowanie domyślne.  
  
 Skalowanie ekranu tworzy nowe problemy dotyczące aplikacji, które są w żadnym z współrzędne ekranu. Ekran zawiera teraz dwa systemy współrzędnych: fizycznych i logicznych. Rzeczywiste przesunięcie w pikselach od góry są fizycznych współrzędne punktu początkowego w lewo. Współrzędne logiczne są przesunięcia, jakie byłyby, jeśli zostały skalowane pikseli, same.  
  
 Załóżmy, że projekt okno dialogowe z przyciskiem współrzędne (100, 48). Gdy to okno dialogowe jest wyświetlane domyślną 96 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], przycisk znajduje się w fizycznych współrzędne (100, 48). Na 120 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], znajduje się on w fizycznych współrzędne (125, 60). Ale współrzędne logiczne są takie same, w dowolnym [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ustawienie: (100, 48).  
  
 Współrzędne logiczne są ważne, ponieważ ich dostosowania zachowania systemu operacyjnego i aplikacji niezależnie od tego [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ustawienie. Na przykład <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> zwykle zwraca wartość logiczną współrzędne. Jeśli przenosisz kursor nad elementem w oknie dialogowym, niezależnie od tego są zwracane takich samych współrzędnych [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ustawienie. Po narysowaniu formantu w (100, 100), jest rysowane tych współrzędnych logicznych i będą używać tej samej pozycji względnej w dowolnym [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ustawienie.  
  
<a name="Scaling_in_UI_Automation_Clients"></a>   
## <a name="scaling-in-ui-automation-clients"></a>Skalowanie w klientach automatyzacji interfejsu użytkownika  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA#tla_api](../../../includes/tlasharptla-api-md.md)] Nie korzysta z logicznego współrzędnych. Następujące metody i właściwości zwracać współrzędne fizycznego lub ich przyjmować jako parametry.  
  
-   <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
-   <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 Domyślnie aplikacja kliencka automatyzacji interfejsu użytkownika uruchomiony w innej niż-96 - [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] środowisko nie będzie mógł uzyskać poprawnych wyników z tych metod i właściwości. Na przykład ponieważ pozycji kursora jest logiczną współrzędne, klient nie może po prostu przekazuje tych współrzędnych w celu <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> uzyskanie element, który jest pod kursorem. Ponadto aplikacja nie będzie poprawnie umieścić poza obszaru klienckiego systemu windows.  
  
 Rozwiązanie jest w dwóch częściach.  
  
1.  Po pierwsze należy aplikacja kliencka [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-aware. Aby to zrobić, należy wywołać [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] funkcja `SetProcessDPIAware` podczas uruchamiania. W kodzie zarządzanym następujące oświadczenie udostępnia tę funkcję.  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     Funkcja ta sprawia, że cały proces [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-aware, co oznacza, że wszystkie okna, które należą do procesu są nieskalowanego. W [próbki wyróżnienia](http://msdn.microsoft.com/library/19ba4577-753e-4efd-92cc-c02ee67c1b69), na przykład znajdują się w fizycznych współrzędne uzyskane z czterech systemu windows wchodzące w skład prostokąta [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], współrzędne logiczne. Jeśli próbka nie były [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-pamiętać wyróżnienie może być rysowany w logiczne współrzędne na pulpicie, co spowoduje nieprawidłowe położenie w innych niż-96 - [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] środowiska.  
  
2.  Aby uzyskać współrzędne kursora, należy wywołać [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] funkcja `GetPhysicalCursorPos`. Poniższy przykład pokazuje, jak deklarowanie i użycie tej funkcji.  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
>  Nie używaj <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>. Zachowanie tej właściwości poza oknami klienta w skalowanym środowisku jest niezdefiniowany.  
  
 Jeśli aplikacja przeprowadza bezpośrednia komunikacja między procesami z inną niż [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-aplikacjami, może mieć konwersji między współrzędne logicznej i fizycznej za pomocą [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] funkcje `PhysicalToLogicalPoint` i `LogicalToPhysicalPoint`.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe wyróżnienia](http://msdn.microsoft.com/library/19ba4577-753e-4efd-92cc-c02ee67c1b69)
