---
title: Używanie Instrumentacji zarządzania Windows na potrzeby diagnostyki
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: 90aae0e22feec5d26fa7ee4c690904ed893489b4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795915"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a>Używanie Instrumentacji zarządzania Windows na potrzeby diagnostyki
Windows Communication Foundation (WCF) ujawnia dane inspekcji usługi w czasie wykonywania za pomocą dostawcy Instrumentacja zarządzania Windows WCF (WMI).  
  
## <a name="enabling-wmi"></a>Włączanie usługi WMI  
 Usługa WMI to implementacja standardu opartego na sieci Web (WBEM) firmy Microsoft. Aby uzyskać więcej informacji na temat zestawu WMI SDK, zobacz [Instrumentacja zarządzania Windows](/windows/desktop/WmiSdk/wmi-start-page). WBEM to standardowy branża, w której aplikacje uwidaczniają Instrumentację zarządzania w zewnętrznych narzędziach do zarządzania.  
  
 Dostawca usługi WMI to składnik, który udostępnia instrumentację w czasie wykonywania za pomocą interfejsu zgodnego z pakietem WBEM. Składa się z zestawu obiektów usługi WMI, które mają pary atrybut/wartość. Pary mogą mieć różne typy proste. Narzędzia do zarządzania programu mogą łączyć się z usługami za pomocą interfejsu w czasie wykonywania. Funkcja WCF udostępnia atrybuty usług, takie jak adresy, powiązania, zachowania i odbiorniki.  
  
 Wbudowanego dostawcę usługi WMI można aktywować w pliku konfiguracji aplikacji. Odbywa się to za pomocą `wmiProviderEnabled` atrybutu [ \<diagnostyki >](../../../configure-apps/file-schema/wcf/diagnostics.md) w [ \<sekcji > System. ServiceModel](../../../configure-apps/file-schema/wcf/system-servicemodel.md) , jak pokazano w poniższej konfiguracji przykładowej.  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 Ten wpis konfiguracji uwidacznia interfejs WMI. Aplikacje zarządzania mogą teraz łączyć się za pomocą tego interfejsu i uzyskiwać dostęp do Instrumentacji zarządzania aplikacji.  
  
## <a name="accessing-wmi-data"></a>Uzyskiwanie dostępu do danych WMI  
 Dostęp do danych usługi WMI można uzyskać na wiele różnych sposobów. Firma Microsoft udostępnia interfejsy API usługi WMI dla skryptów, C++ aplikacji Visual Basic, aplikacji i .NET Framework. Aby uzyskać więcej informacji, zobacz [Korzystanie z usługi WMI](https://go.microsoft.com/fwlink/?LinkId=95183).  
  
> [!CAUTION]
> Jeśli używasz .NET Framework dostarczonych metod do programistycznego uzyskiwania dostępu do danych WMI, należy pamiętać, że takie metody mogą generować wyjątki po ustanowieniu połączenia. Połączenie nie jest ustanawiane podczas konstruowania <xref:System.Management.ManagementObject> wystąpienia, ale przy pierwszym żądaniu obejmującym rzeczywistą wymianę danych. W związku z tym należy użyć `try..catch` bloku, aby przechwycić możliwe wyjątki.  
  
 Można zmienić poziom rejestrowania śledzenia i komunikatów, a także opcje rejestrowania komunikatów dla `System.ServiceModel` źródła śledzenia w usłudze WMI. Można to zrobić, uzyskując dostęp do wystąpienia [AppDomainInfo](appdomaininfo.md) , które uwidacznia następujące właściwości logiczne `LogMessagesAtServiceLevel`: `LogMessagesAtTransportLevel`, `LogMalformedMessages`,, `TraceLevel`i. `false` W związku z tym, jeśli skonfigurujesz odbiornik śledzenia do rejestrowania komunikatów, ale ustawisz te opcje w konfiguracji, możesz później zmienić je `true` na, gdy aplikacja jest uruchomiona. Pozwoli to efektywnie włączyć rejestrowanie komunikatów w czasie wykonywania. Podobnie, jeśli włączysz rejestrowanie komunikatów w pliku konfiguracji, możesz go wyłączyć w czasie wykonywania za pomocą usługi WMI.  
  
 Należy pamiętać, że jeśli w pliku konfiguracji nie zostaną określone detektory śledzenia komunikatów rejestrowania komunikatów `System.ServiceModel` lub żadne detektory śledzenia dla śledzenia nie zostaną uwzględnione, pomimo że zmiany są akceptowane przez usługę WMI. Aby uzyskać więcej informacji na temat prawidłowego konfigurowania odpowiednich odbiorników, zobacz [Konfigurowanie rejestrowania komunikatów](../configuring-message-logging.md) i [Konfigurowanie śledzenia](../tracing/configuring-tracing.md). Poziom śledzenia wszystkich innych źródeł śledzenia określonych przez konfigurację jest efektywny, gdy aplikacja zostanie uruchomiona i nie można jej zmienić.  
  
 Funkcja WCF udostępnia `GetOperationCounterInstanceName` metodę tworzenia skryptów. Ta metoda zwraca nazwę wystąpienia licznika wydajności, jeśli jest podano nazwę operacji. Nie sprawdza ona jednak danych wejściowych. W związku z tym, jeśli podano niepoprawną nazwę operacji, zwracana jest niepoprawna nazwa licznika.  
  
 Właściwość wystąpienia nie zawiera liczby kanałów otwartych przez usługę w celu nawiązania połączenia z inną usługą, jeśli klient programu WCF do usługi docelowej nie `Service` został utworzony w ramach metody. `Service` `OutgoingChannel`  
  
 **Przestroga** Usługa WMI obsługuje <xref:System.TimeSpan> tylko wartość do 3 punktów dziesiętnych. Na przykład, jeśli usługa ustawi jedną z jej właściwości na <xref:System.TimeSpan.MaxValue>, jej wartość jest obcinana po 3 miejscach dziesiętnych wyświetlanych za pomocą usługi WMI.  
  
## <a name="security"></a>Zabezpieczenia  
 Ponieważ dostawca usługi WCF WMI umożliwia odnajdywanie usług w środowisku, należy zachować szczególną ostrożność, aby udzielić dostępu do niego. W przypadku złagodzenia domyślnego dostępu tylko do administratora można zezwolić mniej zaufanym stronom na dostęp do poufnych danych w danym środowisku. W przypadku oddalenia uprawnień dostępu do zdalnej usługi WMI mogą wystąpić ataki z zalaniem. Jeśli proces jest zalewany przez nadmierne żądania usługi WMI, jego wydajność może być obniżona.  
  
 Ponadto w przypadku złagodzenia uprawnień dostępu do pliku MOF mniej zaufane strony mogą manipulować zachowaniem usługi WMI i zmieniać obiekty, które są ładowane w schemacie usługi WMI. Na przykład pola mogą zostać usunięte w taki sposób, że dane krytyczne są ukrywane przez administratora lub pola, które nie wypełniają lub nie powodują wyjątków, są dodawane do pliku.  
  
 Domyślnie dostawca WMI usługi WCF przypisuje uprawnienie "wykonaj metodę", "zapis dostawcy" i "Włącz konto" dla administratora oraz uprawnienie "Włączanie konta" dla usługi ASP.NET, usług lokalnych i sieciowych. W szczególności w przypadku braku[!INCLUDE[wv](../../../../../includes/wv-md.md)] na platformach konto ASP.net ma dostęp do odczytu do przestrzeni nazw usługi WMI. Jeśli nie chcesz przyznawać tych uprawnień dla określonej grupy użytkowników, należy dezaktywować dostawcę usługi WMI (jest on domyślnie wyłączony) lub wyłączyć dostęp dla określonej grupy użytkowników.  
  
 Ponadto podczas próby włączenia usługi WMI za pomocą konfiguracji usługa WMI może nie być włączona z powodu niewystarczających uprawnień użytkownika. Nie ma jednak żadnego zdarzenia w dzienniku zdarzeń w celu zarejestrowania tego błędu.  
  
 Aby zmodyfikować poziomy uprawnień użytkowników, wykonaj następujące czynności.  
  
1. Kliknij przycisk Start, a następnie polecenie Uruchom i wpisz polecenie **compmgmt. msc**.  
  
2. Kliknij prawym przyciskiem myszy pozycję **usługi i aplikacje/formanty usługi WMI** , aby wybrać **Właściwości**.  
  
3. Wybierz kartę **zabezpieczenia** i przejdź do przestrzeni nazw **root/ServiceModel** . Kliknij przycisk **zabezpieczenia** .  
  
4. Wybierz konkretną grupę lub użytkownika, do którego chcesz kontrolować dostęp, i użyj pola wyboru **Zezwalaj** lub **Odmów** , aby skonfigurować uprawnienia.  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a>Przyznawanie uprawnień rejestracji WMI usługi WCF dla dodatkowych użytkowników  
 Funkcja WCF udostępnia dane zarządzania do usługi WMI. Robi to przez hosting dostawcy usługi WMI w procesie, czasami nazywanego dostawcą oddzielonym. Aby dane zarządzania były ujawniane, konto, które rejestruje tego dostawcę, musi mieć odpowiednie uprawnienia. W systemie Windows tylko niewielki zestaw kont uprzywilejowanych może domyślnie rejestrować niepowiązane dostawcy. Jest to problem, ponieważ użytkownicy zwykle chcą uwidocznić dane usługi WMI z usługi WCF działającej w ramach konta, które nie znajduje się w domyślnym zestawie.  
  
 Aby zapewnić ten dostęp, administrator musi udzielić następujących uprawnień dodatkowemu kontu w następującej kolejności:  
  
1. Uprawnienia dostępu do przestrzeni nazw usługi WCF WMI.  
  
2. Uprawnienie do rejestrowania niepołączonego dostawcy usługi WMI programu WCF.  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a>Aby udzielić uprawnienia dostępu do przestrzeni nazw usługi WMI  
  
1. Uruchom Poniższy skrypt programu PowerShell.  
  
    ```powershell  
    write-host ""  
    write-host "Granting Access to root/servicemodel WMI namespace to built in users group"  
    write-host ""  
  
    # Create the binary representation of the permissions to grant in SDDL  
    $newPermissions = "O:BAG:BAD:P(A;CI;CCDCLCSWRPWPRCWD;;;BA)(A;CI;CC;;;NS)(A;CI;CC;;;LS)(A;CI;CC;;;BU)"  
    $converter = new-object system.management.ManagementClass Win32_SecurityDescriptorHelper  
    $binarySD = $converter.SDDLToBinarySD($newPermissions)  
    $convertedPermissions = ,$binarySD.BinarySD  
  
    # Get the object used to set the permissions  
    $security = gwmi -namespace root/servicemodel -class __SystemSecurity  
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "Previous ACL: "$outsddl.SDDL  
  
    # Change the Access Control List (ACL) using SDDL  
    $result = $security.PsBase.InvokeMethod("SetSD",$convertedPermissions)   
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "New ACL:      "$outsddl.SDDL  
    write-host ""  
    ```  
  
     Ten skrypt programu PowerShell używa języka SDDL (Security Descriptor Definition Language) do przydzielenia wbudowanej grupie użytkowników dostępu do przestrzeni nazw usługi WMI "root/ServiceModel". Określa następujące listy ACL:  
  
    - Administrator wbudowanego (BA) — ma już dostęp.  
  
    - Usługa sieciowa (NS) — ma już dostęp.  
  
    - System lokalny (LS) — ma już dostęp.  
  
    - Wbudowani użytkownicy — Grupa, do której ma zostać udzielony dostęp.  
  
#### <a name="to-grant-provider-registration-access"></a>Aby udzielić dostępu do rejestracji dostawcy  
  
1. Uruchom Poniższy skrypt programu PowerShell.  
  
    ```powershell  
    write-host ""  
    write-host "Granting WCF provider registration access to built in users group"  
    write-host ""  
    # Set security on ServiceModel provider  
    $provider = get-WmiObject -namespace "root\servicemodel" __Win32Provider  
  
    write-host "Previous ACL: "$provider.SecurityDescriptor  
    $result = $provider.SecurityDescriptor = "O:BUG:BUD:(A;;0x1;;;BA)(A;;0x1;;;NS)(A;;0x1;;;LS)(A;;0x1;;;BU)"  
  
    # Commit the changes and display it to the console  
    $result = $provider.Put()  
    write-host "New ACL:      "$provider.SecurityDescriptor  
    write-host ""  
    ```  
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a>Udzielanie dostępu do dowolnych użytkowników lub grup  
 Przykład w tej sekcji przyznaje uprawnienia rejestracji dostawcy usługi WMI wszystkim użytkownikom lokalnym. Jeśli chcesz udzielić dostępu użytkownikowi lub grupie, która nie jest wbudowana, należy uzyskać identyfikator zabezpieczeń użytkownika lub grupy (SID). Nie ma prostego sposobu na uzyskanie identyfikatora SID dla dowolnego użytkownika. Jedną z metod jest zalogowanie się jako żądany użytkownik, a następnie wystawienie poniższego polecenia powłoki.  
  
```  
Whoami /user  
```  
  
 Zapewnia to identyfikator SID bieżącego użytkownika, ale nie można użyć tej metody do uzyskania identyfikatora SID dla dowolnego użytkownika. Inną metodą uzyskania identyfikatora SID jest użycie narzędzia [Getsid. exe](https://go.microsoft.com/fwlink/?LinkId=186467) z [zestawu Resource Kit systemu Windows 2000 do zadań administracyjnych](https://go.microsoft.com/fwlink/?LinkId=178660). To narzędzie porównuje identyfikator SID dwóch użytkowników (lokalne lub domeny), a jako efekt uboczny drukuje dwa identyfikatory SID w wierszu polecenia. Aby uzyskać więcej informacji, zobacz [dobrze znane identyfikatory SID](https://go.microsoft.com/fwlink/?LinkId=186468).  
  
## <a name="accessing-remote-wmi-object-instances"></a>Uzyskiwanie dostępu do zdalnych wystąpień obiektów WMI  
 Jeśli musisz uzyskać dostęp do wystąpień usługi WMI platformy WCF na komputerze zdalnym, musisz włączyć ochronę prywatności pakietów w narzędziach, które są używane w celu uzyskania dostępu. W poniższej sekcji opisano, jak uzyskać te informacje za pomocą usługi WMI CIM Studio, Instrumentacja zarządzania Windows tester, a także zestawu .NET SDK 2,0.  
  
### <a name="wmi-cim-studio"></a>WMI CIM Studio  
 Jeśli zainstalowano [Narzędzia administracyjne WMI](https://go.microsoft.com/fwlink/?LinkId=95185), można użyć usługi WMI CIM Studio do uzyskiwania dostępu do wystąpień usługi WMI. Narzędzia znajdują się w następującym folderze  
  
 **Narzędzia%windir%\Program Files\WMI\\**  
  
1. W oknie **łączenie z przestrzenią nazw:** wpisz **root\ServiceModel** , a następnie kliknij przycisk **OK.**  
  
2. W oknie **logowania usługi WMI CIM Studio** kliknij przycisk **Opcje > >** , aby rozwinąć okno. Wybierz opcję **prywatność pakietu** dla **poziomu uwierzytelniania**, a następnie kliknij przycisk **OK**.  
  
### <a name="windows-management-instrumentation-tester"></a>Instrumentacja zarządzania Windows Tester  
 To narzędzie jest instalowane przez system Windows. Aby go uruchomić, uruchom konsolę poleceń, wpisując **cmd. exe** w oknie dialogowym **uruchamiania/uruchamiania** , a następnie kliknij przycisk **OK**. Następnie wpisz **WBEMTest. exe** w oknie wiersza polecenia. Zostanie uruchomione narzędzie Instrumentacja zarządzania Windows testera.  
  
1. Kliknij przycisk **Połącz** w prawym górnym rogu okna.  
  
2. W nowym oknie wprowadź **root\ServiceModel** dla pola **przestrzeń nazw** , a następnie wybierz opcję **Prywatność pakietów** dla **poziomu uwierzytelniania**. Kliknij przycisk **Połącz**.  
  
### <a name="using-managed-code"></a>Korzystanie z kodu zarządzanego  
 Możesz również uzyskać dostęp do zdalnych wystąpień usługi WMI programowo przy użyciu klas dostarczonych <xref:System.Management> przez przestrzeń nazw. Poniższy przykład kodu demonstruje, jak to zrobić.  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
