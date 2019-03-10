---
title: Dodatkowe zagadnienia dotyczące zabezpieczeń dotyczące formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, secure calls to Windows API
- security [Windows Forms]
- security [Windows Forms], calling APIs
- Clipboard [Windows Forms], securing access
ms.assetid: 15abda8b-0527-47c7-aedb-77ab595f2bf1
ms.openlocfilehash: 276def9db2ff610a22b42a88ad658727793b53de
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718912"
---
# <a name="additional-security-considerations-in-windows-forms"></a>Dodatkowe zagadnienia dotyczące zabezpieczeń dotyczące formularzy systemu Windows
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ustawienia zabezpieczeń może spowodować aplikację do uruchamiania inaczej w środowisku częściowej relacji zaufania, niż na komputerze lokalnym. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Ogranicza dostęp do takich krytycznych zasobów lokalnych, jak system plików, sieci i niezarządzanych interfejsów API, między innymi. Ustawienia zabezpieczeń wpływają na możliwość wywołania interfejsu API Win32 firmy Microsoft lub innych interfejsów API, którego nie można zweryfikować przez system zabezpieczeń. Zabezpieczenia wpływa również na innych aspektach związanych z aplikacji, w tym pliku i dostęp do danych i drukowania. Aby uzyskać więcej informacji na temat plików i dostęp do danych w środowisku częściowej relacji zaufania, zobacz [więcej bezpieczny plik i dostęp do danych w formularzach Windows Forms](more-secure-file-and-data-access-in-windows-forms.md). Aby uzyskać więcej informacji na temat Drukowanie w środowisku częściowej relacji zaufania, zobacz [więcej Secure drukowanie w formularzach Windows Forms](more-secure-printing-in-windows-forms.md).  
  
 W poniższych sekcjach omówiono sposób pracy ze Schowka, wykonywać operacje na okno i wywoływanie interfejsu API systemu Win32 z aplikacji, które są uruchomione w środowisku częściowej relacji zaufania.  
  
## <a name="clipboard-access"></a>Dostęp do Schowka  
 <xref:System.Security.Permissions.UIPermission> Klasy kontrolowanie dostępu do Schowka i skojarzonej <xref:System.Security.Permissions.UIPermissionClipboard> wartość wyliczenia wskazuje poziom dostępu. W poniższej tabeli przedstawiono poziomy uprawnień możliwe.  
  
|Wartość UIPermissionClipboard|Opis|  
|---------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard>|Schowka mogą być używane bez ograniczeń.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard>|Schowek może służyć z pewnymi ograniczeniami. Możliwość umieszczenia danych w Schowku (operacje polecenia Kopiuj lub Wytnij) jest nieograniczony. Wewnętrzne formantów, które akceptują wklejania, takie jak pole tekstowe, może akceptować danych ze Schowka, ale formanty użytkownika programowo nie można odczytać ze Schowka.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.NoClipboard>|Nie można użyć Schowka.|  
  
 Domyślnie, otrzymuje lokalnej strefy intranetowej <xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard> dostępu i strefy Internet odbiera <xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard> dostępu. Oznacza to, że aplikacja może kopiować dane do Schowka, ale aplikacja nie programowo Wklej, aby ani odczytu ze Schowka. Te ograniczenia uniemożliwiają programów bez pełnego zaufania odczytu zawartości, które zostały skopiowane do Schowka przez inną aplikację. Jeśli aplikacja wymaga pełnego dostępu do Schowka, ale nie masz uprawnień, konieczne będzie podniesienie poziomu uprawnień dla aplikacji. Aby uzyskać więcej informacji o uprawnieniach wzrasta, zobacz [ogólne administrowanie zasadami zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100)).  
  
## <a name="window-manipulation"></a>Manipulowanie okna  
 <xref:System.Security.Permissions.UIPermission> Klasy kontroluje również uprawnienia do wykonania manipulacji okna i innych działań związanych z interfejsem użytkownika oraz skojarzonych z nimi <xref:System.Security.Permissions.UIPermissionWindow> wartość wyliczenia wskazuje poziom dostępu. W poniższej tabeli przedstawiono poziomy uprawnień możliwe.  
  
 Domyślnie, otrzymuje lokalnej strefy intranetowej <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> dostępu i strefy Internet odbiera <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> dostępu. Oznacza to, że w strefie Internet aplikacja może wykonywać większości obsługi okien i działania interfejsu użytkownika, ale będzie można zmodyfikować wygląd. Zmodyfikowanego okna wyświetla dymek powiadomienie po pierwszym uruchomieniu, zawiera tekst paska tytułu zmodyfikowane i wymaga przycisk Zamknij na pasku tytułu. Powiadomienie dymek i na pasku tytułu zidentyfikować użytkownika aplikacji, która aplikacja jest uruchomiona w częściowej relacji zaufania.  
  
|Wartość UIPermissionWindow|Opis|  
|------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>|Użytkownicy mogą używać wszystkich okien i zdarzenia wejściowe użytkownika bez ograniczeń.|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>|Użytkownicy mogą używać tylko bezpieczniejsze okien najwyższego poziomu i bezpieczniejsze okien podrzędnych do rysowania i można użyć tylko zdarzenia wejściowe użytkownika dla interfejsu użytkownika w ramach tych okien najwyższego poziomu i okien podrzędnych. Te bezpieczniejszego systemu windows są wyraźnie oznaczone etykietami i obowiązują ograniczenia wielkości minimalne i maksymalne. Ograniczenia zapobiegają atakom metodą fałszowania potencjalnie szkodliwe, takie jak imitating ekrany logowania systemu lub pulpit systemu oraz ogranicza dostęp programowy do elementu nadrzędnego systemu windows, związane z fokusem interfejsów API i korzystanie z <xref:System.Windows.Forms.ToolTip> kontroli|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows>|Użytkownicy, można użyć tylko bezpieczniejsze okien podrzędnych do rysowania i służy tylko zdarzenia wejściowe użytkownika do interfejsu użytkownika, w tym subwindow. Kontrolki wyświetlane w przeglądarce jest przykładem subwindow bezpieczniejsze.|  
|<xref:System.Security.Permissions.UIPermissionWindow.NoWindows>|Użytkownicy nie mogą używać systemu windows ani zdarzenia interfejsu użytkownika. Można bez interfejsu użytkownika.|  
  
 Każdy poziom uprawnień identyfikowane przez <xref:System.Security.Permissions.UIPermissionWindow> wyliczenie zezwala na akcje mniej niż poziomami wyższymi. Następujące tabele wskazują akcje, które są ograniczone przez <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> i <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows> wartości. Aby uzyskać uprawnienia, które są wymagane dla każdego elementu członkowskiego Zobacz odwołania dla tego elementu członkowskiego w dokumentacji biblioteki klas .NET Framework.  
  
 <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> uprawnienie ogranicza akcji wymienionych w poniższej tabeli.  
  
|Składnik|Ograniczone operacje|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.Application>|-Ustawianie <xref:System.Windows.Forms.Application.SafeTopLevelCaptionFormat%2A> właściwości.|  
|<xref:System.Windows.Forms.Control>|— Wprowadzenie <xref:System.Windows.Forms.Control.Parent%2A> właściwości.<br />-Ustawianie `Region` właściwości.<br />-Wywołanie <xref:System.Windows.Forms.Control.FindForm%2A> , <xref:System.Windows.Forms.Control.Focus%2A>, <xref:System.Windows.Forms.Control.FromChildHandle%2A> i <xref:System.Windows.Forms.Control.FromHandle%2A>, <xref:System.Windows.Forms.Control.PreProcessMessage%2A>, <xref:System.Windows.Forms.Control.ReflectMessage%2A>, lub <xref:System.Windows.Forms.Control.SetTopLevel%2A> metody.<br />-Wywołanie <xref:System.Windows.Forms.Control.GetChildAtPoint%2A> metodę, jeśli zwrócony kontrolki nie jest elementem podrzędnym, wywołujący formantu.<br />-Modyfikowanie fokus kontrolki wewnątrz kontrolki kontenera.|  
|<xref:System.Windows.Forms.Cursor>|-Ustawianie <xref:System.Windows.Forms.Cursor.Clip%2A> właściwości.<br />-Wywołanie <xref:System.Windows.Forms.Control.Hide%2A> metody.|  
|<xref:System.Windows.Forms.DataGrid>|-Wywołanie <xref:System.Windows.Forms.ContainerControl.ProcessTabKey%2A> metody.|  
|<xref:System.Windows.Forms.Form>|— Wprowadzenie <xref:System.Windows.Forms.Form.ActiveForm%2A> lub <xref:System.Windows.Forms.Form.MdiParent%2A> właściwości.<br />-Ustawianie <xref:System.Windows.Forms.Form.ControlBox%2A>, <xref:System.Windows.Forms.Form.ShowInTaskbar%2A>, lub <xref:System.Windows.Forms.Form.TopMost%2A> właściwości.<br />-Ustawianie <xref:System.Windows.Forms.Form.Opacity%2A> właściwość spadnie poniżej 50%.<br />-Ustawianie <xref:System.Windows.Forms.Form.WindowState%2A> właściwość <xref:System.Windows.Forms.FormWindowState.Minimized> programowo.<br />-Wywołanie <xref:System.Windows.Forms.Form.Activate%2A> metody.<br />— Za pomocą <xref:System.Windows.Forms.FormBorderStyle.None>, <xref:System.Windows.Forms.FormBorderStyle.FixedToolWindow>, i <xref:System.Windows.Forms.FormBorderStyle.SizableToolWindow> <xref:System.Windows.Forms.FormBorderStyle> wartości wyliczenia.|  
|<xref:System.Windows.Forms.NotifyIcon>|— Za pomocą <xref:System.Windows.Forms.NotifyIcon> składnik jest całkowicie ograniczony.|  
  
 <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows> Wartość ogranicza akcji wymienionych w poniższej tabeli, dodatkowo do ograniczeń nałożonych przez <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> wartość.  
  
|Składnik|Ograniczone operacje|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.CommonDialog>|-Wyświetlono okno dialogowe pochodną <xref:System.Windows.Forms.CommonDialog> klasy.|  
|<xref:System.Windows.Forms.Control>|-Wywołanie <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody.<br />-Ustawianie <xref:System.Windows.Forms.Control.Cursor%2A> właściwości.|  
|<xref:System.Windows.Forms.Control.Cursor%2A>|-Ustawianie <xref:System.Windows.Forms.Cursor.Current%2A> właściwości.|  
|<xref:System.Windows.Forms.MessageBox>|-Wywołanie <xref:System.Windows.Forms.Form.Show%2A> metody.|  
  
### <a name="hosting-third-party-controls"></a>Hosting kontrolek innych firm  
 Inny rodzaj manipulacji okna może wystąpić, jeśli formularze hosta formanty innych firm. Kontrolka innej firmy jest niestandardowe <xref:System.Windows.Forms.UserControl> nie opracowane i kompilowane samodzielnie. Mimo że scenariusza hostingu jest trudny do wykorzystania, teoretycznie możliwe jest kontrolki innych firm rozwinąć jego powierzchnię renderowania dla pokrycia całego obszaru formularza. Ten formant może następnie naśladować okno dialogowe krytycznych i żądania informacje takie jak kombinacji nazwy użytkownika/hasła lub konta bankowego liczby użytkowników.  
  
 Aby ograniczyć to potencjalne zagrożenie, formanty innych firm tylko od dostawców, w której można zaufać. Jeśli używasz formanty innych firm, które zostały pobrane ze źródła niemożliwy, firma Microsoft zaleca zapoznanie się kod źródłowy potencjalne luki w zabezpieczeniach. Po zweryfikowaniu, czy źródło jest niezłośliwych, należy skompilować zestawu sobie, aby zapewnić zgodność źródło zestawu.  
  
## <a name="win32-api-calls"></a>Wywołania interfejsu API Win32  
 Jeśli projekt wymaga, wywołanie funkcji z interfejsu API Win32, uzyskujesz dostęp do kodu niezarządzanego. W tym przypadku nie można określić akcje kodu do okna lub systemu operacyjnego, podczas pracy z wywołania interfejsu API systemu Win32 lub wartości. <xref:System.Security.Permissions.SecurityPermission> Klasy i <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> wartość <xref:System.Security.Permissions.SecurityPermissionFlag> wyliczenie kontrola dostępu do kodu niezarządzanego. Aplikacja ma dostęp do kodu niezarządzanego, tylko w przypadku, gdy udzielany jest <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> uprawnień. Domyślnie tylko aplikacje, które działają lokalnie może wywoływać kod niezarządzany.  
  
 Niektóre elementy członkowskie Windows Forms dostęp niezarządzanych wymagającego <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> uprawnień. Poniższa tabela zawiera listę elementów członkowskich w <xref:System.Windows.Forms> przestrzeni nazw, które wymagają uprawnień. Aby uzyskać więcej informacji na temat uprawnień, które są wymagane dla elementu członkowskiego zobacz dokumentację biblioteki klas .NET Framework.  
  
|Składnik|Element członkowski|  
|---------------|------------|  
|<xref:System.Windows.Forms.Application>|-   <xref:System.Windows.Forms.Application.AddMessageFilter%2A> — Metoda<br />-   <xref:System.Windows.Forms.Application.CurrentInputLanguage%2A> Właściwość<br />-   `Exit` — Metoda<br />-   <xref:System.Windows.Forms.Application.ExitThread%2A> — Metoda<br />-   <xref:System.Windows.Forms.Application.ThreadException> Zdarzenia|  
|<xref:System.Windows.Forms.CommonDialog>|-   <xref:System.Windows.Forms.CommonDialog.HookProc%2A> — Metoda<br />-   <xref:System.Windows.Forms.CommonDialog.OwnerWndProc%2A>\ — metoda<br />-   <xref:System.Windows.Forms.CommonDialog.Reset%2A> — Metoda<br />-   <xref:System.Windows.Forms.CommonDialog.RunDialog%2A> — Metoda|  
|<xref:System.Windows.Forms.Control>|-   <xref:System.Windows.Forms.Control.CreateParams%2A> — Metoda<br />-   <xref:System.Windows.Forms.Control.DefWndProc%2A> — Metoda<br />-   <xref:System.Windows.Forms.Control.DestroyHandle%2A> — Metoda<br />-   <xref:System.Windows.Forms.Control.WndProc%2A> — Metoda|  
|<xref:System.Windows.Forms.Help>|-   <xref:System.Windows.Forms.Help.ShowHelp%2A> Metody<br />-   <xref:System.Windows.Forms.Help.ShowHelpIndex%2A> — Metoda|  
|<xref:System.Windows.Forms.NativeWindow>|-   <xref:System.Windows.Forms.NativeWindow> Klasa|  
|<xref:System.Windows.Forms.Screen>|-   <xref:System.Windows.Forms.Screen.FromHandle%2A> — Metoda|  
|<xref:System.Windows.Forms.SendKeys>|-   <xref:System.Windows.Forms.SendKeys.Send%2A> — Metoda<br />-   <xref:System.Windows.Forms.SendKeys.SendWait%2A> — Metoda|  
  
 Jeśli aplikacja nie ma uprawnień do wywoływania niezarządzanego kodu, aplikacja musi żądać <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> uprawnień lub należy wziąć pod uwagę alternatywnych sposobów implementowania funkcji, w wielu przypadkach, Windows Forms zapewnia alternatywnego kodu zarządzanego interfejsu API Win32 funkcje. Jeśli nie ma innego oznacza, że istnieje i aplikacja muszą uzyskiwać dostęp do kodu niezarządzanego, trzeba będzie podnoszenia uprawnień dla aplikacji.  
  
 Uprawnień do wywoływania niezarządzanego kodu umożliwia aplikacji przeprowadzenie najbardziej niczego. W związku z tym, aby wywoływać kod niezarządzany należy tylko udzielić zezwolenia dla aplikacji, które pochodzą z zaufanego źródła. Alternatywnie w zależności od aplikacji, część funkcjonalności aplikacji, która wywołuje tę funkcję do kodu niezarządzanego może być opcjonalne lub włączonych w środowisku pełnego zaufania tylko. Aby uzyskać więcej informacji na temat niebezpieczne uprawnienia Zobacz [niebezpieczne uprawnienia i administrowanie zasadami](../misc/dangerous-permissions-and-policy-administration.md). Aby uzyskać więcej informacji o uprawnieniach wzrasta, zobacz [ogólne administrowanie zasadami zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz także
- [Bezpieczniejszy dostęp do plików i danych w formularzach Windows Forms](more-secure-file-and-data-access-in-windows-forms.md)
- [Bezpieczniejsze drukowanie w formularzach Windows Forms](more-secure-printing-in-windows-forms.md)
- [Przegląd zabezpieczeń w formularzach Windows Forms](security-in-windows-forms-overview.md)
- [Zabezpieczenia formularzy Windows Forms](windows-forms-security.md)
- [Zabezpieczanie aplikacji ClickOnce](/visualstudio/deployment/securing-clickonce-applications)
