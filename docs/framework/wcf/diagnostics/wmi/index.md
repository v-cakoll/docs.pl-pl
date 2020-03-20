---
title: Używanie Instrumentacji zarządzania Windows na potrzeby diagnostyki
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: 0c803e3988f7a63980d991190db87c263c992b80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185673"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a>Używanie Instrumentacji zarządzania Windows na potrzeby diagnostyki
Windows Communication Foundation (WCF) udostępnia dane inspekcji usługi w czasie wykonywania za pośrednictwem dostawcy WCF Windows Instrumentation (WMI) dostawcy.  
  
## <a name="enabling-wmi"></a>Włączanie funkcji WMI  
 WMI jest wdrożenie microsoftu web-based Enterprise Management (WBEM) standard. Aby uzyskać więcej informacji na temat zestawie WMI SDK, zobacz [Instrumentacja zarządzania windowsem](/windows/desktop/WmiSdk/wmi-start-page). WBEM jest standardem branżowym w zakresie sposobu, w jaki aplikacje narażają instrumentację zarządzania na zewnętrzne narzędzia do zarządzania.  
  
 Dostawca WMI jest składnikiem, który udostępnia instrumentacji w czasie wykonywania za pośrednictwem interfejsu zgodnego z WBEM. Składa się z zestawu obiektów WMI, które mają pary atrybutów/wartości. Pary mogą być wielu prostych typów. Narzędzia do zarządzania można połączyć się z usługami za pośrednictwem interfejsu w czasie wykonywania. WCF udostępnia atrybuty usług, takich jak adresy, powiązania, zachowania i detektory.  
  
 Wbudowany dostawca WMI można aktywować w pliku konfiguracyjnym aplikacji. Odbywa się to `wmiProviderEnabled` za pomocą atrybutu [ \<diagnostyki>](../../../configure-apps/file-schema/wcf/diagnostics.md) w [ \<sekcji system.serviceModel>,](../../../configure-apps/file-schema/wcf/system-servicemodel.md) jak pokazano w poniższej konfiguracji przykładowej.  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 Ten wpis konfiguracji udostępnia interfejs WMI. Aplikacje do zarządzania mogą teraz łączyć się za pośrednictwem tego interfejsu i uzyskiwać dostęp do instrumentacji zarządzania aplikacji.  
  
## <a name="accessing-wmi-data"></a>Uzyskiwanie dostępu do danych usługi WMI  
 Dostęp do danych usługi WMI można uzyskać na wiele różnych sposobów. Firma Microsoft udostępnia interfejsy API usługi WMI dla skryptów, aplikacji Visual Basic, aplikacji W++ i programu .NET Framework. Aby uzyskać więcej informacji, zobacz [Korzystanie z usługi WMI](/windows/win32/wmisdk/using-wmi).  
  
> [!CAUTION]
> Jeśli używasz .NET Framework pod warunkiem metody programowego dostępu do danych WMI, należy pamiętać, że takie metody mogą zgłaszać wyjątki po nawiązaniu połączenia. Połączenie nie jest ustanawiane podczas <xref:System.Management.ManagementObject> budowy wystąpienia, ale na pierwsze żądanie obejmujące rzeczywistą wymianę danych. W związku z tym `try..catch` należy użyć bloku, aby złapać możliwe wyjątki.  
  
 Można zmienić poziom śledzenia i rejestrowania wiadomości, a także `System.ServiceModel` opcje rejestrowania wiadomości dla źródła śledzenia w UMI. Można to zrobić, uzyskując dostęp do wystąpienia [AppDomainInfo,](appdomaininfo.md) które `LogMessagesAtServiceLevel` `LogMessagesAtTransportLevel`udostępnia `LogMalformedMessages`te `TraceLevel`właściwości logiczne: , , i . W związku z tym jeśli skonfigurujesz odbiornik śledzenia do `false` rejestrowania wiadomości, ale ustaw `true` te opcje w konfiguracji, można później zmienić je na gdy aplikacja jest uruchomiona. Umożliwi to skuteczne rejestrowanie komunikatów w czasie wykonywania. Podobnie po włączeniu rejestrowania wiadomości w pliku konfiguracji, można go wyłączyć w czasie wykonywania przy użyciu usługi WMI.  
  
 Należy pamiętać, że jeśli w pliku konfiguracyjnym nie `System.ServiceModel` określono żadnych odbiorników śledzenia rejestrowania komunikatów do rejestrowania komunikatów lub nie określono odbiorników śledzenia śledzenia, żadne zmiany nie zostaną wprowadzone, nawet jeśli zmiany zostaną zaakceptowane przez usługę WMI. Aby uzyskać więcej informacji na temat prawidłowego konfigurowania odpowiednich odbiorników, zobacz [Konfigurowanie rejestrowania wiadomości](../configuring-message-logging.md) i [konfigurowanie śledzenia](../tracing/configuring-tracing.md). Poziom śledzenia wszystkich innych źródeł śledzenia określonych przez konfigurację jest skuteczny po uruchomieniu aplikacji i nie można go zmienić.  
  
 WCF udostępnia `GetOperationCounterInstanceName` metodę skryptów. Ta metoda zwraca nazwę wystąpienia licznika wydajności, jeśli podasz jej nazwę operacji. Jednak nie sprawdza poprawności danych wejściowych. W związku z tym jeśli podasz niepoprawną nazwę operacji, zwracana jest nieprawidłowa nazwa licznika.  
  
 Właściwość `OutgoingChannel` `Service` wystąpienia nie zlicza kanałów otwartych przez usługę w celu połączenia się z inną usługą, jeśli klient WCF do usługi docelowej nie jest tworzony w ramach `Service` metody.  
  
 **Uwaga** WMI obsługuje <xref:System.TimeSpan> tylko wartość do 3 przecinkami po przecinku. Na przykład jeśli usługa ustawia jedną z <xref:System.TimeSpan.MaxValue>jego właściwości, jej wartość jest obcinana po 3 przecinkach po przecinku podczas wyświetlania za pośrednictwem usługi WMI.  
  
## <a name="security"></a>Zabezpieczenia  
 Ponieważ dostawca WCF WMI umożliwia odnajdowanie usług w środowisku, należy zachować szczególną ostrożność podczas udzielania dostępu do niego. Jeśli rozluźnisz domyślny dostęp tylko dla administratora, możesz zezwolić mniej zaufanym stronom na dostęp do poufnych danych w danym środowisku. W szczególności, jeśli poluzujesz uprawnienia do zdalnego dostępu WMI, może wystąpić ataki zalewające. Jeśli proces jest zalany przez nadmierne żądania WMI, jego wydajność może ulec pogorszeniu.  
  
 Ponadto w przypadku rozluźnienia uprawnień dostępu do pliku MOF mniej zaufanych stron można manipulować zachowaniem usługi WMI i zmieniać obiekty, które są ładowane w schemacie WMI. Na przykład pola można usunąć w taki sposób, że dane krytyczne są ukryte przed administratorem lub że pola, które nie wypełniają lub powodują wyjątki, są dodawane do pliku.  
  
 Domyślnie dostawca WCF WMI udziela uprawnień "execute method", "provider write" i "enable account" dla administratora oraz uprawnień "włącz konto" dla ASP.NET, usługi lokalnej i usługi sieciowej. W szczególności na platformach innych niż Windows Vista konto ASP.NET ma dostęp do odczytu do przestrzeni nazw WMI ServiceModel. Jeśli nie chcesz przyznawać tych uprawnień określonej grupie użytkowników, należy dezaktywować dostawcę usługi WMI (jest on domyślnie wyłączony) lub wyłączyć dostęp dla określonej grupy użytkowników.  
  
 Ponadto podczas próby włączenia usługi WMI za pośrednictwem konfiguracji usługa WMI może nie być włączona z powodu niewystarczających uprawnień użytkownika. Jednak żadne zdarzenie nie jest zapisywane w dzienniku zdarzeń, aby zarejestrować ten błąd.  
  
 Aby zmodyfikować poziomy uprawnień użytkownika, należy wykonać następujące kroki.  
  
1. Kliknij przycisk Start, a następnie pozycję Uruchom i wpisz **plik compmgmt.msc**.  
  
2. Kliknij prawym przyciskiem myszy **pozycję Usługi i kontrolki aplikacji/WMI,** aby wybrać polecenie **Właściwości**.  
  
3. Wybierz kartę **Zabezpieczenia** i przejdź do obszaru nazw **Root/ServiceModel.** Kliknij przycisk **Zabezpieczenia.**  
  
4. Zaznacz określoną grupę lub użytkownika, do którego chcesz kontrolować dostęp, i użyj pola wyboru **Zezwalaj** lub **Odmów,** aby skonfigurować uprawnienia.  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a>Udzielanie uprawnień rejestracyjnych WCF WMI dodatkowym użytkownikom  
 WCF udostępnia dane zarządzania do WMI. Robi to, hostując w procesie dostawcę WMI, czasami nazywanego "dostawcą oddzielonym od produkcji". Aby dane zarządzania mają być udostępniane, konto, które rejestruje tego dostawcy musi mieć odpowiednie uprawnienia. W systemie Windows tylko niewielki zestaw kont uprzywilejowanych można domyślnie zarejestrować dostawców oddzielonych od produkcji. Jest to problem, ponieważ użytkownicy często chcą udostępnić dane WMI z usługi WCF uruchomionej na koncie, które nie znajduje się w zestawie domyślnym.  
  
 Aby zapewnić ten dostęp, administrator musi udzielić następujących uprawnień do dodatkowego konta w następującej kolejności:  
  
1. Uprawnienie dostępu do obszaru nazw WCF WMI.  
  
2. Uprawnienie do rejestracji dostawcy WMI odłączonych od produkcji WCF.  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a>Aby udzielić uprawnień dostępu do obszaru nazw WMI  
  
1. Uruchom następujący skrypt programu PowerShell.  
  
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
  
     Ten skrypt programu PowerShell używa języka definicji deskryptora zabezpieczeń (SDDL) w celu przyznania grupie wbudowanych użytkowników dostępu do obszaru nazw WMI "root/servicemodel". Określa następujące listy ACL:  
  
    - Wbudowany administrator (BA) - miał już dostęp.  
  
    - Usługa sieciowa (NS) - miał już dostęp.  
  
    - System lokalny (LS) - miał już dostęp.  
  
    - Wbudowane użytkowników — grupa, do aby udzielić dostępu do.  
  
#### <a name="to-grant-provider-registration-access"></a>Aby udzielić dostępu do rejestracji dostawcy  
  
1. Uruchom następujący skrypt programu PowerShell.  
  
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
 W tym przykładzie w tej sekcji przyznaje uprawnienia rejestracji dostawcy usługi WMI dla wszystkich użytkowników lokalnych. Jeśli chcesz udzielić dostępu do użytkownika lub grupy, która nie jest wbudowana, należy uzyskać identyfikator zabezpieczeń tego użytkownika lub grupy (SID). Nie ma prostego sposobu, aby uzyskać identyfikator SID dla dowolnego użytkownika. Jedną z metod jest zalogowanie się jako żądany użytkownik, a następnie wydanie następującego polecenia powłoki.  
  
```console
Whoami /user  
```  
  
 Zapewnia to identyfikator SID bieżącego użytkownika, ale ta metoda nie może służyć do uzyskania identyfikatora SID na dowolnego użytkownika. Inną metodą uzyskania identyfikatora SID jest użycie narzędzia [getsid.exe](/windows/win32/wmisdk/using-wmi) z narzędzi zestawu zasobów systemu Windows 2000 do wykonywania zadań administracyjnych. To narzędzie porównuje identyfikator SID dwóch użytkowników (lokalnego lub domeny) i jako efekt uboczny drukuje dwa identyfikatory SID z wierszem polecenia. Aby uzyskać więcej informacji, zobacz [Dobrze znane identyfikatory SID](https://support.microsoft.com/help/243330/well-known-security-identifiers-in-windows-operating-systems).  
  
## <a name="accessing-remote-wmi-object-instances"></a>Uzyskiwanie dostępu do zdalnych wystąpień obiektów usługi WMI  
 Jeśli chcesz uzyskać dostęp do wystąpień WCF WMI na komputerze zdalnym, należy włączyć prywatność pakietów na narzędziach, które są używane do uzyskiwania dostępu. W poniższej sekcji opisano sposób ich osiągnięcia przy użyciu programu WMI CIM Studio, testera instrumentacji zarządzania windowsem oraz narzędzia .NET SDK 2.0.  
  
### <a name="wmi-cim-studio"></a>WMI CIM Studio  
 Jeśli zainstalowano [narzędzia administracyjne WMI,](https://go.microsoft.com/fwlink/?LinkId=95185)można użyć programu WMI CIM Studio, aby uzyskać dostęp do wystąpień usługi WMI. Narzędzia znajdują się w następującym folderze  
  
 **%windir%\Pliki programów\Narzędzia WMI\\**  
  
1. W oknie **Połącz z obszarem nazw wpisz** **root\ServiceModel** i kliknij przycisk **OK.**  
  
2. W oknie **Logowania WMI CIM Studio** kliknij przycisk **Opcje >>,** aby rozwinąć okno. Wybierz **pozycję Prywatność pakietów** dla **poziomu uwierzytelniania**i kliknij przycisk **OK**.  
  
### <a name="windows-management-instrumentation-tester"></a>Tester instrumentacji zarządzania windowsem  
 To narzędzie jest instalowane przez system Windows. Aby go uruchomić, uruchom konsolę poleceń, wpisując **program cmd.exe** w oknie dialogowym **Start/Run** i kliknij przycisk **OK**. Następnie wpisz **wbemtest.exe** w oknie polecenia. Następnie uruchamiane jest narzędzie Tester instrumentacji zarządzania windowsem.  
  
1. Kliknij przycisk **Połącz** w prawym górnym rogu okna.  
  
2. W nowym oknie wprowadź **katalog główny\ServiceModel** dla pola **Obszar nazw** i wybierz pozycję **Prywatność pakietów** dla **poziomu uwierzytelniania**. Kliknij pozycję **Połącz**.  
  
### <a name="using-managed-code"></a>Korzystanie z kodu zarządzanego  
 Można również uzyskać dostęp do zdalnych wystąpień WMI <xref:System.Management> programowo przy użyciu klas dostarczonych przez obszar nazw. Poniższy przykład kodu pokazuje, jak to zrobić.  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
