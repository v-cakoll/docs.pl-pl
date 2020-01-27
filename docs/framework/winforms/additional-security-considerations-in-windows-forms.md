---
title: Dodatkowe zagadnienia dotyczące zabezpieczeń
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, secure calls to Windows API
- security [Windows Forms]
- security [Windows Forms], calling APIs
- Clipboard [Windows Forms], securing access
ms.assetid: 15abda8b-0527-47c7-aedb-77ab595f2bf1
ms.openlocfilehash: c8d51a57194f1dc536bc4b5d0376987dbfd3b2cf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739811"
---
# <a name="additional-security-considerations-in-windows-forms"></a>Dodatkowe zagadnienia dotyczące zabezpieczeń dotyczące formularzy systemu Windows
.NET Framework ustawienia zabezpieczeń mogą spowodować, że aplikacja będzie działać inaczej w środowisku częściowego zaufania niż na komputerze lokalnym. .NET Framework ogranicza dostęp do takich krytycznych zasobów lokalnych, jak system plików, Sieć i niezarządzane interfejsy API, między innymi. Ustawienia zabezpieczeń mają wpływ na możliwość wywołania interfejsu API systemu Microsoft Windows lub innych interfejsów API, które nie mogą być zweryfikowane przez system zabezpieczeń. Zabezpieczenia mają również wpływ na inne aspekty aplikacji, w tym dostęp do plików i danych oraz drukowanie. Aby uzyskać więcej informacji na temat dostępu do plików i danych w środowisku częściowej relacji zaufania, zobacz [bardziej bezpieczny dostęp do plików i danych w Windows Forms](more-secure-file-and-data-access-in-windows-forms.md). Aby uzyskać więcej informacji na temat drukowania w środowisku częściowej relacji zaufania, zobacz [bezpieczniejsze drukowanie w Windows Forms](more-secure-printing-in-windows-forms.md).  
  
 W poniższych sekcjach omówiono, jak pracować ze schowkiem, przeprowadzać manipulowanie oknami i wywoływać interfejs API systemu Windows z aplikacji, które działają w środowisku częściowej relacji zaufania.  
  
## <a name="clipboard-access"></a>Dostęp do schowka  
 Klasa <xref:System.Security.Permissions.UIPermission> kontroluje dostęp do schowka, a skojarzona wartość wyliczenia <xref:System.Security.Permissions.UIPermissionClipboard> wskazuje poziom dostępu. W poniższej tabeli przedstawiono możliwe poziomy uprawnień.  
  
|UIPermissionClipboard wartość|Opis|  
|---------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard>|Schowka można używać bez ograniczeń.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard>|Schowek może być używany z pewnymi ograniczeniami. Możliwość umieszczania danych w schowku (operacje kopiowania lub wycinania) jest nieograniczona. Formanty wewnętrzne akceptujące Wklej, takie jak pole tekstowe, mogą akceptować dane ze schowka, ale formanty użytkownika nie mogą programistycznie odczytywać ze schowka.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.NoClipboard>|Nie można użyć Schowka.|  
  
 Domyślnie strefa Lokalny intranet otrzymuje <xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard> dostęp, a strefa Internet odbiera <xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard> dostęp. Oznacza to, że aplikacja może kopiować dane do schowka, ale aplikacja nie może programistycznie wkleić ani odczytać ze schowka. Te ograniczenia uniemożliwiają programom bez pełnego zaufania odczytywanie zawartości skopiowanej do schowka przez inną aplikację. Jeśli aplikacja wymaga pełnego dostępu do schowka, ale nie masz uprawnień, musisz podwyższyć poziom uprawnień aplikacji. Aby uzyskać więcej informacji na temat podnoszenia uprawnień, zobacz [Ogólne administrowanie zasadami zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100)).  
  
## <a name="window-manipulation"></a>Manipulowanie oknem  
 Klasa <xref:System.Security.Permissions.UIPermission> kontroluje również uprawnienia do wykonywania manipulowania oknem i innych akcji związanych z interfejsem użytkownika, a skojarzona wartość wyliczenia <xref:System.Security.Permissions.UIPermissionWindow> wskazuje poziom dostępu. W poniższej tabeli przedstawiono możliwe poziomy uprawnień.  
  
 Domyślnie strefa Lokalny intranet otrzymuje <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> dostęp, a strefa Internet odbiera <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> dostęp. Oznacza to, że w strefie Internet aplikacja może wykonywać większość działań okna i interfejsów użytkownika, ale wygląd okna zostanie zmodyfikowany. Zmodyfikowane okno wyświetla powiadomienie w dymku, gdy pierwsze uruchomienie, zawiera zmodyfikowany tekst paska tytułu i wymaga przycisku Zamknij na pasku tytułu. Powiadomienie w dymku i pasek tytułu identyfikują użytkownika aplikacji, która jest uruchomiona przez aplikację w ramach częściowej relacji zaufania.  
  
|UIPermissionWindow wartość|Opis|  
|------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>|Użytkownicy mogą używać wszystkich zdarzeń systemu Windows i danych wejściowych użytkownika bez ograniczeń.|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>|Użytkownicy mogą używać tylko bezpieczniejszego systemu Windows najwyższego poziomu i bezpieczniejszego systemu Windows na potrzeby rysowania i mogą używać tylko zdarzeń wejściowych użytkownika dla interfejsu użytkownika w tych oknach najwyższego poziomu i w podsystemach Windows. Te bezpieczniejsze okna są jasno oznaczone i mają minimalne i maksymalne ograniczenia rozmiaru. Ograniczenia uniemożliwiają potencjalnie szkodliwe ataki, takie jak imitacje ekranów logowania systemu lub pulpit systemowy, a także ograniczają dostęp programistyczny do okien nadrzędnych, interfejsów API związanych z ostrością i używania kontrolki <xref:System.Windows.Forms.ToolTip>,|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows>|Użytkownicy mogą używać tylko bezpieczniejszego systemu Windows do rysowania i mogą korzystać tylko z zdarzeń wejściowych użytkownika dla interfejsu użytkownika w tym podsystemie. Kontrolka wyświetlana w przeglądarce to przykład bezpieczniejszego podokna.|  
|<xref:System.Security.Permissions.UIPermissionWindow.NoWindows>|Użytkownicy nie mogą używać żadnych zdarzeń interfejsu systemu Windows ani użytkownika. Nie można użyć interfejsu użytkownika.|  
  
 Każdy poziom uprawnień identyfikowany przez Wyliczenie <xref:System.Security.Permissions.UIPermissionWindow> umożliwia mniejszą liczbę akcji niż wyższy poziom. Poniższe tabele wskazują akcje ograniczone przez wartości <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> i <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows>. Aby uzyskać dokładne uprawnienia, które są wymagane dla każdego elementu członkowskiego, zobacz odwołanie do tego elementu członkowskiego w dokumentacji biblioteki klas .NET Framework.  
  
 uprawnienie <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> ogranicza akcje wymienione w poniższej tabeli.  
  
|Składnik|Akcje z ograniczeniami|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.Application>|-Ustawianie właściwości <xref:System.Windows.Forms.Application.SafeTopLevelCaptionFormat%2A>.|  
|<xref:System.Windows.Forms.Control>|— Pobieranie właściwości <xref:System.Windows.Forms.Control.Parent%2A>.<br />-Ustawianie właściwości `Region`.<br />-Wywoływanie metody <xref:System.Windows.Forms.Control.FindForm%2A>, <xref:System.Windows.Forms.Control.Focus%2A>, <xref:System.Windows.Forms.Control.FromChildHandle%2A> i <xref:System.Windows.Forms.Control.FromHandle%2A>, <xref:System.Windows.Forms.Control.PreProcessMessage%2A>, <xref:System.Windows.Forms.Control.ReflectMessage%2A>lub <xref:System.Windows.Forms.Control.SetTopLevel%2A>.<br />-Wywoływanie metody <xref:System.Windows.Forms.Control.GetChildAtPoint%2A>, jeśli zwrócona kontrolka nie jest elementem podrzędnym kontrolki wywołującej.<br />-Modyfikuj fokus kontroli wewnątrz kontrolki kontenera.|  
|<xref:System.Windows.Forms.Cursor>|-Ustawianie właściwości <xref:System.Windows.Forms.Cursor.Clip%2A>.<br />-Wywoływanie metody <xref:System.Windows.Forms.Control.Hide%2A>.|  
|<xref:System.Windows.Forms.DataGrid>|-Wywoływanie metody <xref:System.Windows.Forms.ContainerControl.ProcessTabKey%2A>.|  
|<xref:System.Windows.Forms.Form>|-Pobieranie właściwości <xref:System.Windows.Forms.Form.ActiveForm%2A> lub <xref:System.Windows.Forms.Form.MdiParent%2A>.<br />-Ustawianie właściwości <xref:System.Windows.Forms.Form.ControlBox%2A>, <xref:System.Windows.Forms.Form.ShowInTaskbar%2A>lub <xref:System.Windows.Forms.Form.TopMost%2A>.<br />-Ustawianie właściwości <xref:System.Windows.Forms.Form.Opacity%2A> poniżej 50%.<br />-Ustawianie właściwości <xref:System.Windows.Forms.Form.WindowState%2A> na <xref:System.Windows.Forms.FormWindowState.Minimized> programowo.<br />-Wywoływanie metody <xref:System.Windows.Forms.Form.Activate%2A>.<br />— Przy użyciu wartości <xref:System.Windows.Forms.FormBorderStyle.None>, <xref:System.Windows.Forms.FormBorderStyle.FixedToolWindow>i <xref:System.Windows.Forms.FormBorderStyle.SizableToolWindow><xref:System.Windows.Forms.FormBorderStyle>.|  
|<xref:System.Windows.Forms.NotifyIcon>|— Używanie składnika <xref:System.Windows.Forms.NotifyIcon> jest całkowicie ograniczone.|  
  
 Wartość <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows> ogranicza akcje wymienione w poniższej tabeli, a także ograniczenia wprowadzone przez wartość <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>.  
  
|Składnik|Akcje z ograniczeniami|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.CommonDialog>|— Wyświetlanie okna dialogowego pochodnego od klasy <xref:System.Windows.Forms.CommonDialog>.|  
|<xref:System.Windows.Forms.Control>|-Wywoływanie metody <xref:System.Windows.Forms.Control.CreateGraphics%2A>.<br />-Ustawianie właściwości <xref:System.Windows.Forms.Control.Cursor%2A>.|  
|<xref:System.Windows.Forms.Control.Cursor%2A>|-Ustawianie właściwości <xref:System.Windows.Forms.Cursor.Current%2A>.|  
|<xref:System.Windows.Forms.MessageBox>|-Wywoływanie metody <xref:System.Windows.Forms.Form.Show%2A>.|  
  
### <a name="hosting-third-party-controls"></a>Hosting kontrolek innych firm  
 Inne rodzaje manipulowania oknem mogą wystąpić, jeśli formularze obsługują kontrolki innych firm. Kontrolka innej firmy to wszelkie niestandardowe <xref:System.Windows.Forms.UserControl>, które nie zostały opracowane i skompilowane samodzielnie. Chociaż scenariusz hostingu jest trudno wykorzystać, teoretycznie jest możliwe, aby formant innej firmy mógł rozwijać powierzchnię renderowania w celu pokrycia całego obszaru formularza. Ta kontrolka może następnie naśladować krytyczne okno dialogowe i żądać informacji, takich jak kombinacje nazwy użytkownika/hasła lub numery kont bankowych od użytkowników.  
  
 Aby ograniczyć to potencjalne ryzyko, należy użyć kontrolek innych firm tylko od dostawców, którym można zaufać. Jeśli używasz kontrolek innych firm pobranych z niemożliwego do zweryfikowania źródła, zalecamy zapoznanie się z kodem źródłowym w celu uzyskania potencjalnych luk w zabezpieczeniach. Po sprawdzeniu, że źródło nie jest złośliwe, należy skompilować zestaw samodzielnie, aby upewnić się, że źródło jest zgodne z zestawem.  
  
## <a name="windows-api-calls"></a>Wywołania interfejsu API systemu Windows  
 Jeśli projekt aplikacji wymaga wywołania funkcji z interfejsu API systemu Windows, uzyskujesz dostęp do kodu niezarządzanego. W takim przypadku nie można ustalić akcji kodu do okna lub systemu operacyjnego podczas pracy z wywołaniami lub wartościami interfejsu API systemu Windows. Klasy <xref:System.Security.Permissions.SecurityPermission> i <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> wartość wyliczenia <xref:System.Security.Permissions.SecurityPermissionFlag> kontrolują dostęp do niezarządzanego kodu. Aplikacja może uzyskać dostęp do kodu niezarządzanego tylko wtedy, gdy udzielono mu uprawnienia <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>. Domyślnie tylko aplikacje działające lokalnie mogą wywoływać kod niezarządzany.  
  
 Niektórzy członkowie Windows Forms zapewniają niezarządzany dostęp, który wymaga uprawnień <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>. Poniższa tabela zawiera listę elementów członkowskich w przestrzeni nazw <xref:System.Windows.Forms>, które wymagają uprawnienia. Aby uzyskać więcej informacji o uprawnieniach, które są wymagane dla elementu członkowskiego, zapoznaj się z dokumentacją biblioteki klas .NET Framework.  
  
|Składnik|Element członkowski|  
|---------------|------------|  
|<xref:System.Windows.Forms.Application>|-   <xref:System.Windows.Forms.Application.AddMessageFilter%2A> Metoda<br />Właściwość <xref:System.Windows.Forms.Application.CurrentInputLanguage%2A> -   <br />-   `Exit` Metoda<br />-   <xref:System.Windows.Forms.Application.ExitThread%2A> Metoda<br />zdarzenie <xref:System.Windows.Forms.Application.ThreadException> -   |  
|<xref:System.Windows.Forms.CommonDialog>|-   <xref:System.Windows.Forms.CommonDialog.HookProc%2A> Metoda<br />-   <xref:System.Windows.Forms.CommonDialog.OwnerWndProc%2A>\ Metoda<br />-   <xref:System.Windows.Forms.CommonDialog.Reset%2A> Metoda<br />-   <xref:System.Windows.Forms.CommonDialog.RunDialog%2A> Metoda|  
|<xref:System.Windows.Forms.Control>|-   <xref:System.Windows.Forms.Control.CreateParams%2A> Metoda<br />-   <xref:System.Windows.Forms.Control.DefWndProc%2A> Metoda<br />-   <xref:System.Windows.Forms.Control.DestroyHandle%2A> Metoda<br />-   <xref:System.Windows.Forms.Control.WndProc%2A> Metoda|  
|<xref:System.Windows.Forms.Help>|Metody <xref:System.Windows.Forms.Help.ShowHelp%2A> -   <br />-   <xref:System.Windows.Forms.Help.ShowHelpIndex%2A> Metoda|  
|<xref:System.Windows.Forms.NativeWindow>|Klasa <xref:System.Windows.Forms.NativeWindow> -   |  
|<xref:System.Windows.Forms.Screen>|-   <xref:System.Windows.Forms.Screen.FromHandle%2A> Metoda|  
|<xref:System.Windows.Forms.SendKeys>|-   <xref:System.Windows.Forms.SendKeys.Send%2A> Metoda<br />-   <xref:System.Windows.Forms.SendKeys.SendWait%2A> Metoda|  
  
 Jeśli aplikacja nie ma uprawnień do wywoływania kodu niezarządzanego, aplikacja musi zażądać uprawnień <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> lub należy rozważyć alternatywne sposoby wdrażania funkcji; w wielu przypadkach Windows Forms zapewnia zarządzaną alternatywę funkcji interfejsu API systemu Windows. Jeśli żaden alternatywny nie istnieje i aplikacja musi uzyskać dostęp do niezarządzanego kodu, konieczne będzie podniesienie poziomu uprawnień aplikacji.  
  
 Uprawnienie do wywoływania kodu niezarządzanego umożliwia aplikacji wykonywanie większości elementów. W związku z tym uprawnienia do wywoływania kodu niezarządzanego powinny być przyznawane tylko dla aplikacji, które pochodzą z zaufanego źródła. Alternatywnie, w zależności od aplikacji, element funkcjonalności aplikacji, który sprawia, że wywołanie do kodu niezarządzanego może być opcjonalny lub włączony tylko w środowisku pełnego zaufania. Aby uzyskać więcej informacji o uprawnieniach niebezpiecznych, zobacz temat [niebezpieczne uprawnienia i administrowanie zasadami](../misc/dangerous-permissions-and-policy-administration.md). Aby uzyskać więcej informacji na temat podnoszenia uprawnień, zobacz [Ogólne administrowanie zasadami zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz także

- [Bezpieczniejszy dostęp do plików i danych w formularzach Windows Forms](more-secure-file-and-data-access-in-windows-forms.md)
- [Bezpieczniejsze drukowanie w formularzach Windows Forms](more-secure-printing-in-windows-forms.md)
- [Przegląd zabezpieczeń w formularzach Windows Forms](security-in-windows-forms-overview.md)
- [Zabezpieczenia formularzy Windows Forms](windows-forms-security.md)
- [Zabezpieczanie aplikacji ClickOnce](/visualstudio/deployment/securing-clickonce-applications)
