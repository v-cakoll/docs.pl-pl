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
ms.openlocfilehash: 2a68a74fa6aadcaba21f142d394a1f8a3d8af371
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179965"
---
# <a name="ui-automation-and-screen-scaling"></a>Automatyzacja interfejsu użytkownika a skalowanie ekranu
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
Począwszy od systemu Windows Vista, system Windows umożliwia użytkownikom zmianę ustawienia punktów na cal (dpi), tak aby większość elementów interfejsu użytkownika na ekranie była większa. Chociaż ta funkcja jest od dawna dostępna w systemie Windows, w poprzednich wersjach skalowanie musiało zostać zaimplementowane przez aplikacje. Począwszy od systemu Windows Vista, Menedżer okien pulpitu wykonuje domyślne skalowanie dla wszystkich aplikacji, które nie obsługują własnego skalowania. Aplikacje klienckie automatyzacji interfejsu użytkownika muszą uwzględniać tę funkcję.  
  
<a name="Scaling_in_Windows_Vista"></a>
## <a name="scaling-in-windows-vista"></a>Skalowanie w systemie Windows Vista  
 Domyślne ustawienie dpi to 96, co oznacza, że 96 pikseli zajmuje szerokość lub wysokość jednego hipotetycznego cala. Dokładna miara "cala" zależy od wielkości i fizycznej rozdzielczości monitora. Na przykład na monitorze o szerokości 12 cali, przy rozdzielczości poziomej 1280 pikseli, pozioma linia 96 pikseli rozciąga się na około 9/10 cala.  
  
 Zmiana ustawienia dpi to nie to samo, co zmiana rozdzielczości ekranu. W skali dpi liczba fizycznych pikseli na ekranie pozostaje taka sama. Jednak skalowanie jest stosowane do rozmiaru [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] i lokalizacji elementów. To skalowanie może być wykonywane automatycznie przez Menedżera okien pulpitu (DWM) dla pulpitu i dla aplikacji, które nie proszą jawnie, aby nie być skalowane.  
  
 W efekcie, gdy użytkownik ustawi współczynnik skali na 120 dpi, pionowy lub poziomy cal na ekranie staje się większy o 25 procent. Wszystkie wymiary są odpowiednio skalowane. Przesunięcie okna aplikacji od górnej i lewej krawędzi ekranu zwiększa się o 25 procent. Jeśli skalowanie aplikacji jest włączone, a aplikacja nie jest obsługujących dpi, rozmiar okna zwiększa się w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] tej samej proporcji, wraz z przesunięcia i rozmiary wszystkich elementów, które zawiera.  
  
> [!NOTE]
> Domyślnie DWM nie wykonuje skalowania dla aplikacji innych niż dpi,gdy użytkownik ustawia dpi na 120, ale wykonuje go, gdy dpi jest ustawiona na wartość niestandardową 144 lub wyższą. Jednak użytkownik może zastąpić domyślne zachowanie.  
  
 Skalowanie ekranu stwarza nowe wyzwania dla aplikacji, które są w jakikolwiek sposób związane ze współrzędnymi ekranu. Ekran zawiera teraz dwa układy współrzędnych: fizyczne i logiczne. Współrzędne fizyczne punktu są rzeczywistym przesunięciem w pikselach od lewej górnej części początku układu współrzędnych. Współrzędne logiczne są przesunięcia, jak byłoby, gdyby same piksele zostały przeskalowane.  
  
 Załóżmy, że projektujesz okno dialogowe z przyciskiem we współrzędnych (100, 48). Gdy to okno dialogowe jest wyświetlane w domyślnej rozdzielczości 96 dpi, przycisk znajduje się we współrzędnych fizycznych (100, 48). Przy 120 dpi znajduje się we współrzędnych fizycznych (125, 60). Ale współrzędne logiczne są takie same w każdym ustawieniu dpi: (100, 48).  
  
 Współrzędne logiczne są ważne, ponieważ sprawiają, że zachowanie systemu operacyjnego i aplikacji jest spójne niezależnie od ustawienia dpi. Na przykład <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> zwykle zwraca współrzędne logiczne. Jeśli kursor zostanie przesunięty na element w oknie dialogowym, te same współrzędne są zwracane niezależnie od ustawienia dpi. Jeśli rysujesz formant w (100, 100), jest on rysowany do tych współrzędnych logicznych i zajmie tę samą pozycję względną w dowolnym ustawieniu dpi.  
  
<a name="Scaling_in_UI_Automation_Clients"></a>
## <a name="scaling-in-ui-automation-clients"></a>Skalowanie w klientach automatyzacji interfejsu użytkownika  
 Interfejs [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] API nie używa współrzędnych logicznych. Następujące metody i właściwości zwracają współrzędne fizyczne lub przyjmują je jako parametry.  
  
- <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 Domyślnie aplikacja kliencka automatyzacji interfejsu użytkownika działająca w środowisku o rozdzielczości 96 dpi nie będzie w stanie uzyskać prawidłowych wyników z tych metod i właściwości. Na przykład, ponieważ położenie kursora znajduje się we współrzędnych <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> logicznych, klient nie może po prostu przekazać tych współrzędnych, aby uzyskać element, który znajduje się pod kursorem. Ponadto aplikacja nie będzie w stanie poprawnie umieścić okna poza swoim obszarem klienta.  
  
 Rozwiązanie składa się z dwóch części.  
  
1. Najpierw upewnij się, że aplikacja kliencka dpi-aware. Aby to zrobić, wywołaj `SetProcessDPIAware` funkcję Win32 podczas uruchamiania. W kodzie zarządzanym następująca deklaracja udostępnia tę funkcję.  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     Ta funkcja sprawia, że cały proces dpi-aware, co oznacza, że wszystkie okna, które należą do procesu są nieskalowe. Na przykład w [przykładzie zakreślenia](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)cztery okna, które tworzą prostokąt podświetlenia, znajdują się na fizycznych współrzędnych uzyskanych z automatyzacji interfejsu użytkownika, a nie współrzędnych logicznych. Jeśli próbka nie była obsługująca dpi, podświetlenie zostanie narysowane na współrzędnych logicznych na pulpicie, co spowodowałoby nieprawidłowe umieszczenie w środowisku o rozdzielczości 96 dpi.  
  
2. Aby uzyskać współrzędne kursora, `GetPhysicalCursorPos`należy wywołać funkcję Win32 . W poniższym przykładzie pokazano, jak zadeklarować i używać tej funkcji.  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
> Nie używaj <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>. Zachowanie tej właściwości poza oknami klienta w środowisku skalowanym jest niezdefiniowane.  
  
 Jeśli aplikacja wykonuje bezpośrednią komunikację między procesami z aplikacjami nieoświeżnymi dpi, być może `PhysicalToLogicalPoint` `LogicalToPhysicalPoint`można przekonwertować współrzędne logiczne i fizyczne przy użyciu funkcji Win32 i .  
  
## <a name="see-also"></a>Zobacz też

- [Przykład zakreślenia](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
