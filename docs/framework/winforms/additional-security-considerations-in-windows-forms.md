---
title: Dodatkowe zagadnienia dotyczące zabezpieczeń dotyczące formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, secure calls to Windows API
- security [Windows Forms]
- security [Windows Forms], calling APIs
- Clipboard [Windows Forms], securing access
ms.assetid: 15abda8b-0527-47c7-aedb-77ab595f2bf1
ms.openlocfilehash: a1d8606eb972a6e3bea52f6230cb893a4bbb5aac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="additional-security-considerations-in-windows-forms"></a>Dodatkowe zagadnienia dotyczące zabezpieczeń dotyczące formularzy systemu Windows
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ustawienia zabezpieczeń może spowodować aplikację do uruchamiania inaczej w środowisku częściowej relacji zaufania niż na komputerze lokalnym. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Ogranicza dostęp do takich krytyczne zasoby lokalne jako system plików, sieci i niezarządzane interfejsy API, między innymi. Ustawienia zabezpieczeń wpływają na możliwość wywołania interfejsu API Win32 firmy Microsoft lub innych interfejsów API, którego nie można zweryfikować przez system zabezpieczeń. Zabezpieczeń dotyczy również inne aspekty aplikacji, łącznie z dostępem do plików i danych i drukowania. Aby uzyskać więcej informacji na temat dostępu do plików i danych w środowisku częściowej relacji zaufania, zobacz [więcej Zabezpieczanie plików i dostępu do danych w formularzach systemu Windows](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md). Aby uzyskać więcej informacji na temat drukowania w środowisku częściowej relacji zaufania, zobacz [więcej Secure drukowania w formularzach systemu Windows](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md).  
  
 W poniższych sekcjach omówiono, jak pracować z Schowka, wykonywanie manipulowania okna i wywołania interfejsu API Win32 z aplikacji, które są uruchomione w środowisku częściowej relacji zaufania.  
  
## <a name="clipboard-access"></a>Dostęp do Schowka  
 <xref:System.Security.Permissions.UIPermission> Klasy kontroluje dostęp do Schowka oraz skojarzonych z nimi <xref:System.Security.Permissions.UIPermissionClipboard> wartość wyliczenia wskazuje poziom dostępu. W poniższej tabeli przedstawiono poziomy uprawnień możliwe.  
  
|Wartość UIPermissionClipboard|Opis|  
|---------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard>|Schowka można używać bez ograniczeń.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard>|Schowka można używać z pewnymi ograniczeniami. Umieszczanie danych w Schowku (operacje polecenia kopiowania lub wycinania) jest nieograniczony. Formantów wewnętrznych, które akceptują wklejania, takich jak pole tekstowe, może akceptować danych ze Schowka, ale kontrolek użytkownika programowo nie można odczytać ze Schowka.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.NoClipboard>|Nie można użyć Schowka.|  
  
 Domyślnie odbiera lokalnej strefy intranetowej <xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard> dostępu i strefy internetowej odbiera <xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard> dostępu. Oznacza to, że aplikację można skopiować dane do Schowka, ale aplikacji programowo nie można wkleić do lub ze Schowka do odczytu. Te ograniczenia zapobieganie programów bez pełnego zaufania odczytu zawartości, które zostały skopiowane do Schowka przez inną aplikację. Jeśli aplikacja wymaga pełnego dostępu do Schowka, ale nie masz uprawnień, należy podnieść uprawnienia dla aplikacji. Aby uzyskać więcej informacji na temat wzrasta uprawnień, zobacz [ogólne administrowanie zasadami zabezpieczeń](http://msdn.microsoft.com/library/5121fe35-f0e3-402c-94ab-4f35b0a87b4b).  
  
## <a name="window-manipulation"></a>Manipulowanie okna  
 <xref:System.Security.Permissions.UIPermission> Klasy kontroluje również uprawnienia do wykonywania manipulowania okna i innych działań związanych z interfejsu użytkownika oraz skojarzonych z nimi <xref:System.Security.Permissions.UIPermissionWindow> wartość wyliczenia wskazuje poziom dostępu. W poniższej tabeli przedstawiono poziomy uprawnień możliwe.  
  
 Domyślnie odbiera lokalnej strefy intranetowej <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> dostępu i strefy internetowej odbiera <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> dostępu. Oznacza to, że w strefie Internet aplikacji można wykonać większość okien i działania interfejsu użytkownika, ale wygląd zostaną zmodyfikowane. Zmodyfikowanego okna wyświetli powiadomienie dymek po pierwszym uruchomieniu zawiera tekst paska tytułu zmodyfikowane i wymaga przycisk Zamknij na pasku tytułu. Powiadomienie dymek i na pasku tytułu identyfikacji użytkownika aplikacji, która aplikacja działa w częściowej relacji zaufania.  
  
|Wartość UIPermissionWindow|Opis|  
|------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>|Użytkownicy mogą używać wszystkie okna i zdarzenia wejściowe użytkownika bez ograniczeń.|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>|Użytkownicy można używać tylko bezpieczniejsze okien najwyższego poziomu i bezpieczniejsze subwindows do rysowania i można użyć tylko zdarzenia wejściowe użytkownika dla interfejsu użytkownika w tych okien najwyższego poziomu i subwindows. Te bezpieczniejsze windows wyraźnie oznaczone i ograniczenia minimalnego i maksymalnego rozmiaru. Ograniczenia zapobiegają atakom metodą fałszowania potencjalnie szkodliwe, takie jak imitating ekrany logowania systemu lub pulpit systemu i ogranicza dostęp programistyczny do nadrzędnego systemu windows, związanych z fokusem interfejsów API i korzystanie z <xref:System.Windows.Forms.ToolTip> formantu|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows>|Użytkownicy można użyć tylko bezpieczniejsze subwindows do rysowania i można użyć tylko zdarzenia wejściowe użytkownika dla interfejsu użytkownika, w tym subwindow. Formant wyświetlanym w przeglądarce jest przykładem subwindow bezpieczniejsze.|  
|<xref:System.Security.Permissions.UIPermissionWindow.NoWindows>|Użytkownicy nie mogą korzystać z systemu windows lub zdarzenia interfejsu użytkownika. Można bez interfejsu użytkownika.|  
  
 Każdy poziom uprawnień identyfikowane przez <xref:System.Security.Permissions.UIPermissionWindow> wyliczenie umożliwia akcje mniej niż poziom wyżej. Następujące tabele wskazują akcje, które są ograniczone przez <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> i <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows> wartości. Dokładne uprawnienia, które są wymagane dla każdego elementu członkowskiego zobacz dokumentację dla tego elementu członkowskiego w dokumentacji biblioteki klas programu .NET Framework.  
  
 <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> uprawnienie ogranicza akcji wymienionych w poniższej tabeli.  
  
|Składnik|Akcje z ograniczeniami|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.Application>|-Ustawienie <xref:System.Windows.Forms.Application.SafeTopLevelCaptionFormat%2A> właściwości.|  
|<xref:System.Windows.Forms.Control>|— Pobranie <xref:System.Windows.Forms.Control.Parent%2A> właściwości.<br />-Ustawienie `Region` właściwości.<br />-Wywoływania <xref:System.Windows.Forms.Control.FindForm%2A> , <xref:System.Windows.Forms.Control.Focus%2A>, <xref:System.Windows.Forms.Control.FromChildHandle%2A> i <xref:System.Windows.Forms.Control.FromHandle%2A>, <xref:System.Windows.Forms.Control.PreProcessMessage%2A>, <xref:System.Windows.Forms.Control.ReflectMessage%2A>, lub <xref:System.Windows.Forms.Control.SetTopLevel%2A> metody.<br />-Wywoływania <xref:System.Windows.Forms.Control.GetChildAtPoint%2A> metodę, jeśli formant zwrócony nie jest elementem podrzędnym wywołujący formantu.<br />-Modyfikowanie formantowi fokus wewnątrz formantu kontenera.|  
|<xref:System.Windows.Forms.Cursor>|-Ustawienie <xref:System.Windows.Forms.Cursor.Clip%2A> właściwości.<br />-Wywoływania <xref:System.Windows.Forms.Control.Hide%2A> metody.|  
|<xref:System.Windows.Forms.DataGrid>|-Wywoływania <xref:System.Windows.Forms.ContainerControl.ProcessTabKey%2A> metody.|  
|<xref:System.Windows.Forms.Form>|— Pobranie <xref:System.Windows.Forms.Form.ActiveForm%2A> lub <xref:System.Windows.Forms.Form.MdiParent%2A> właściwości.<br />-Ustawienie <xref:System.Windows.Forms.Form.ControlBox%2A>, <xref:System.Windows.Forms.Form.ShowInTaskbar%2A>, lub <xref:System.Windows.Forms.Form.TopMost%2A> właściwości.<br />-Ustawienie <xref:System.Windows.Forms.Form.Opacity%2A> właściwości poniżej 50%.<br />-Ustawienie <xref:System.Windows.Forms.Form.WindowState%2A> właściwości <xref:System.Windows.Forms.FormWindowState.Minimized> programowo.<br />-Wywoływania <xref:System.Windows.Forms.Form.Activate%2A> metody.<br />— Za pomocą <xref:System.Windows.Forms.FormBorderStyle.None>, <xref:System.Windows.Forms.FormBorderStyle.FixedToolWindow>, i <xref:System.Windows.Forms.FormBorderStyle.SizableToolWindow> <xref:System.Windows.Forms.FormBorderStyle> wartości wyliczenia.|  
|<xref:System.Windows.Forms.NotifyIcon>|— Za pomocą <xref:System.Windows.Forms.NotifyIcon> składnika jest całkowicie ograniczone.|  
  
 <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows> Wartość ogranicza akcji wymienionych w poniższej tabeli, oprócz ograniczenia wprowadzane przez <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> wartość.  
  
|Składnik|Akcje z ograniczeniami|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.CommonDialog>|-Przedstawiający okno dialogowe pochodną <xref:System.Windows.Forms.CommonDialog> klasy.|  
|<xref:System.Windows.Forms.Control>|-Wywoływania <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody.<br />-Ustawienie <xref:System.Windows.Forms.Control.Cursor%2A> właściwości.|  
|<xref:System.Windows.Forms.Control.Cursor%2A>|-Ustawienie <xref:System.Windows.Forms.Cursor.Current%2A> właściwości.|  
|<xref:System.Windows.Forms.MessageBox>|-Wywoływania <xref:System.Windows.Forms.Form.Show%2A> metody.|  
  
### <a name="hosting-third-party-controls"></a>Hosting formantów innych firm  
 Inny rodzaj manipulowania okna może wystąpić, jeśli formularze hosta formanty innych firm. Formant innej firmy jest niestandardowe <xref:System.Windows.Forms.UserControl> nie opracowany i kompilowane samodzielnie. Mimo że scenariuszu obsługi jest trudny do wykorzystania, teoretycznie możliwe jest dla formantu innych firm rozwinąć jego powierzchnię renderowania do pokrycia obszaru całego formularza. Ten formant może następnie naśladować krytyczne okno dialogowe i poproś informacje, takie jak kombinacji nazwy użytkownika i hasła lub konta bankowego liczby użytkowników.  
  
 Aby ograniczyć to ryzyko, należy użyć formantów innych firm tylko od dostawców, które można ufać. Jeśli używasz kontrolki innych firm, które zostały pobrane ze źródła, którego nie można zweryfikować, firma Microsoft zaleca przejrzenie kod źródłowy potencjalne luki w zabezpieczeniach. Po upewnieniu się, czy źródło jest system inny niż złośliwe, należy skompilować zestawu samodzielnie, aby zapewnić zgodność źródło zestawu.  
  
## <a name="win32-api-calls"></a>Wywołania API Win32  
 Jeśli projekt wymaga wywoływania funkcji z interfejsu API Win32, uzyskują dostęp do kodu niezarządzanego. W takim przypadku akcje kodu do okna lub systemu operacyjnego nie można określić podczas pracy z interfejsu API Win32 lub wartości. <xref:System.Security.Permissions.SecurityPermission> Klasy i <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> wartość <xref:System.Security.Permissions.SecurityPermissionFlag> wyliczenie kontroli dostępu do kodu niezarządzanego. Aplikacja ma dostęp do kodu niezarządzanego, tylko wtedy, gdy uzyskuje on <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> uprawnienia. Domyślnie tylko aplikacje, uruchomionych lokalnie mogą wywoływać kodu niezarządzanego.  
  
 Niektóre elementy formularzy systemu Windows Podaj niezarządzane dostępu, który wymaga <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> uprawnienia. Poniższa tabela zawiera listę elementów członkowskich w <xref:System.Windows.Forms> przestrzeni nazw, które wymagają uprawnień. Aby uzyskać więcej informacji dotyczących uprawnień, które są wymagane dla elementu członkowskiego zobacz dokumentację biblioteki klasy .NET Framework.  
  
|Składnik|Element członkowski|  
|---------------|------------|  
|<xref:System.Windows.Forms.Application>|-   <xref:System.Windows.Forms.Application.AddMessageFilter%2A> — Metoda<br />-   <xref:System.Windows.Forms.Application.CurrentInputLanguage%2A> Właściwość<br />-   `Exit` — Metoda<br />-   <xref:System.Windows.Forms.Application.ExitThread%2A> — Metoda<br />-   <xref:System.Windows.Forms.Application.ThreadException> Zdarzenia|  
|<xref:System.Windows.Forms.CommonDialog>|-   <xref:System.Windows.Forms.CommonDialog.HookProc%2A> — Metoda<br />-   <xref:System.Windows.Forms.CommonDialog.OwnerWndProc%2A>\ — metoda<br />-   <xref:System.Windows.Forms.CommonDialog.Reset%2A> — Metoda<br />-   <xref:System.Windows.Forms.CommonDialog.RunDialog%2A> — Metoda|  
|<xref:System.Windows.Forms.Control>|-   <xref:System.Windows.Forms.Control.CreateParams%2A> — Metoda<br />-   <xref:System.Windows.Forms.Control.DefWndProc%2A> — Metoda<br />-   <xref:System.Windows.Forms.Control.DestroyHandle%2A> — Metoda<br />-   <xref:System.Windows.Forms.Control.WndProc%2A> — Metoda|  
|<xref:System.Windows.Forms.Help>|-   <xref:System.Windows.Forms.Help.ShowHelp%2A> Metody<br />-   <xref:System.Windows.Forms.Help.ShowHelpIndex%2A> — Metoda|  
|<xref:System.Windows.Forms.NativeWindow>|-   <xref:System.Windows.Forms.NativeWindow> Klasy|  
|<xref:System.Windows.Forms.Screen>|-   <xref:System.Windows.Forms.Screen.FromHandle%2A> — Metoda|  
|<xref:System.Windows.Forms.SendKeys>|-   <xref:System.Windows.Forms.SendKeys.Send%2A> — Metoda<br />-   <xref:System.Windows.Forms.SendKeys.SendWait%2A> — Metoda|  
  
 Jeśli aplikacja nie ma uprawnienia do wywoływania kodu niezarządzanego, aplikacja musi żądać <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> uprawnień lub należy wziąć pod uwagę alternatywny sposób wdrażania funkcji; w wielu przypadkach formularzy systemu Windows zapewnia zarządzanych alternatywę do interfejsu API Win32 funkcje. Jeśli nie ma innego oznacza, że istnieje i aplikacji muszą uzyskać dostęp do kodu niezarządzanego, konieczne będzie podniesienia poziomu uprawnień dla aplikacji.  
  
 Uprawnienia do wywoływania kodu niezarządzanego umożliwia aplikacji najbardziej wykonywać żadnych czynności. W związku z tym uprawnienia do wywoływania kodu niezarządzanego powinny być przyznane tylko dla aplikacji, które pochodzą z zaufanego źródła. Alternatywnie w zależności od aplikacji, część funkcji aplikacji, który wykonuje wywołanie do kodu niezarządzanego może być opcjonalne i włączone w środowisku pełnego zaufania tylko. Aby uzyskać więcej informacji na temat niebezpiecznych uprawnień, zobacz [niebezpieczne uprawnienia i administrowanie zasadami](../../../docs/framework/misc/dangerous-permissions-and-policy-administration.md). Aby uzyskać więcej informacji na temat wzrasta uprawnień, zobacz [NIB: ogólne administrowanie zasadami zabezpieczeń](http://msdn.microsoft.com/library/5121fe35-f0e3-402c-94ab-4f35b0a87b4b).  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczniejszy dostęp do plików i danych w formularzach Windows Forms](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 [Bezpieczniejsze drukowanie w formularzach Windows Forms](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 [Przegląd zabezpieczeń w formularzach Windows Forms](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [Zabezpieczenia formularzy Windows Forms](../../../docs/framework/winforms/windows-forms-security.md)  
 [Zabezpieczanie aplikacji ClickOnce](/visualstudio/deployment/securing-clickonce-applications)
