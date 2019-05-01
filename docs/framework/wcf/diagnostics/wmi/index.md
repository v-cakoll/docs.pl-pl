---
title: Używanie Instrumentacji zarządzania Windows na potrzeby diagnostyki
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: 9acb1b280248f8552680ea3fbba831b3de53b2c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62048289"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a>Używanie Instrumentacji zarządzania Windows na potrzeby diagnostyki
Windows Communication Foundation (WCF) uwidacznia dane inspekcji usługi w czasie wykonywania za pośrednictwem dostawcy Instrumentacji zarządzania Windows (WMI) WCF.  
  
## <a name="enabling-wmi"></a>Włączanie usługi WMI  
 WMI jest implementacja firmy Microsoft opartego na sieci Web Enterprise Management (WBEM) standardowa. Aby uzyskać więcej informacji na temat zestawu SDK usługi WMI, zobacz [Instrumentacji zarządzania Windows](/windows/desktop/WmiSdk/wmi-start-page). Technologia WBEM jest branżowy standard jak aplikacje uwidocznić Instrumentacji zarządzania do narzędzi zarządzania zewnętrznego.  
  
 Dostawca WMI jest składnik, który udostępnia Instrumentacji w czasie wykonywania za pomocą interfejsu WBEM zgodne. Składa się z zestawu obiektów WMI, które mają atrybut/pary wartości. Pary może mieć wiele typów prostych. Narzędzia do zarządzania może nawiązać połączenia usług za pośrednictwem interfejsu w czasie wykonywania. Usługa WCF umożliwia atrybuty usługi, takie jak adresy, powiązania, zachowań i odbiorników.  
  
 Wbudowany dostawca usługi WMI można aktywować w pliku konfiguracyjnym aplikacji. Jest to realizowane `wmiProviderEnabled` atrybutu [ \<Diagnostyka >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) w [ \<system.serviceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) sekcji, jak pokazano w następującym przykładzie Konfiguracja.  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 Ten wpis konfiguracji udostępnia interfejs usługi WMI. Aplikacje do zarządzania można teraz nawiązać połączenie za pośrednictwem tego interfejsu i uzyskać dostęp z Instrumentacją zarządzania aplikacji.  
  
## <a name="accessing-wmi-data"></a>Uzyskiwanie dostępu do danych usługi WMI  
 Dane usługi WMI są dostępne na wiele różnych sposobów. Firma Microsoft udostępnia interfejsy API usługi WMI dla skryptów, aplikacji Visual Basic, aplikacji w języku C++ i [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]. Aby uzyskać więcej informacji, zobacz [przy użyciu usługi WMI](https://go.microsoft.com/fwlink/?LinkId=95183).  
  
> [!CAUTION]
>  Jeśli używasz programu .NET Framework, pod warunkiem metody do programowego dostępu do danych usługi WMI, należy pamiętać, że tych metod może zgłaszają wyjątki, gdy połączenie zostanie nawiązane. Połączenie nie zostanie nawiązane podczas konstruowania <xref:System.Management.ManagementObject> wystąpienia, ale pierwszego żądania obejmujące rzeczywiste dane programu exchange. Dlatego należy używać `try..catch` bloku catch możliwych wyjątków.  
  
 Można zmienić, śledzenia i poziom rejestrowania wiadomości, a także opcje rejestrowania komunikatów dla `System.ServiceModel` źródła śledzenia w usłudze WMI. Można to zrobić, uzyskując dostęp do [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) wystąpienia, który uwidacznia następujące właściwości logiczne: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, i `TraceLevel`. W związku z tym, jeśli Konfigurowanie odbiornika śledzenia dla rejestrowania komunikatów, ale ustawiony korzystać z tych opcji do `false` w konfiguracji można później zmienić ich `true` gdy aplikacja jest uruchomiona. Umożliwi to efektywne rejestrowanie komunikatów w czasie wykonywania. Podobnie jeśli włączysz rejestrowanie w pliku konfiguracyjnym komunikatów, można ją wyłączyć w czasie wykonywania przy użyciu usługi WMI.  
  
 Należy pamiętać, że jeśli nie rejestrowania komunikatów śledzenia, detektory rejestrowanie komunikatów lub nie `System.ServiceModel` detektorów śledzenia do śledzenia są określone w pliku konfiguracji, żadne zmiany wykonane w życie, nawet jeśli zmiany zostaną zaakceptowane przez usługę WMI. Aby uzyskać więcej informacji na temat prawidłowo konfigurowania odpowiednich odbiorników, zobacz [Konfigurowanie rejestrowania komunikatów](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) i [Konfigurowanie śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md). Poziom śledzenia wszystkie inne źródła śledzenia określony w konfiguracji jest efektywne, podczas uruchamiania aplikacji i nie można zmienić.  
  
 Usługa WCF umożliwia `GetOperationCounterInstanceName` metody dla skryptów. Ta metoda zwraca nazwę wystąpienia licznika wydajności, jeśli podasz operacji o nazwie. Dane wejściowe nie są jednak zweryfikować. W związku z tym Jeśli podasz nazwę operacji niepoprawne, zwracana jest nazwa licznika niepoprawne.  
  
 `OutgoingChannel` Właściwość `Service` wystąpienia nie są liczone otwierane przez usługę, aby nawiązać połączenie z innej usługi, jeśli klient WCF w usłudze docelowej nie jest tworzony w ramach kanałów `Service` metody.  
  
 **Ostrzeżenie** obsługuje tylko WMI <xref:System.TimeSpan> wartość maksymalnie 3 separatorów dziesiętnych. Na przykład, jeśli Usługa ustawia jeden z jego właściwości w celu <xref:System.TimeSpan.MaxValue>, jego wartość zostanie obcięta po 3 dziesiętnymi, po wyświetleniu za pomocą usługi WMI.  
  
## <a name="security"></a>Zabezpieczenia  
 Ponieważ dostawca WCF WMI umożliwia odnajdowanie usług w środowisku, należy zachować ostrożność extreme przyznawania dostępu do niego. Odpoczynku domyślnego dostępu tylko administrator może zezwolić na niższym poziomie zaufania strony dostępu do poufnych danych w danym środowisku. W szczególności jeśli uprawnienia dostępu zdalnego WMI jest Poluzuj, przepełnieniu ataków mogą wystąpić. Jeśli proces jest wypełniony nadmierne żądań WMI, jego wydajność może być niższa.  
  
 Ponadto jeśli odpoczynku uprawnienia dostępu do pliku MOF niższym poziomie zaufania strony można manipulować zachowanie usługi WMI i zmienianie obiektów, które są ładowane w schemacie usługi WMI. Na przykład pola można usunąć w taki sposób, że krytyczne dane są ukrywane przez administratora lub pola, które nie wypełnić lub spowodować, że wyjątki są dodawane do pliku.  
  
 Domyślnie dostawca WMI programu WCF zapewnia "wykonania metody", "Zapisywanie dostawcy" i "Włącz konto" uprawnień administratora i uprawnienia "Włącz konto" dla platformy ASP.NET, Usługa lokalna i Usługa sieciowa. W szczególności na non -[!INCLUDE[wv](../../../../../includes/wv-md.md)] platform, konto ASP.NET ma dostęp do odczytu do przestrzeni nazw usługi WMI elementu ServiceModel. Jeśli użytkownik nie chce przyznać te uprawnienia do określonej grupy użytkowników, należy albo Dezaktywuj dostawca usługi WMI (go jest domyślnie wyłączona) lub wyłączenie dostępu do określonej grupy użytkowników.  
  
 Ponadto podczas próby włączenia usługi WMI za pomocą konfiguracji usługi WMI może nie być włączona ze względu na niewystarczające użytkownika uprawnień. Jednak żadne zdarzenie jest zapisywane w dzienniku zdarzeń, aby zarejestrować tego błędu.  
  
 Aby zmodyfikować poziomach uprawnień użytkownika, użyj następujących kroków.  
  
1. Kliknij przycisk Uruchom, uruchom i wpisz **compmgmt.msc**.  
  
2. Kliknij prawym przyciskiem myszy **usług i aplikacji/WMI kontrolki** wybrać **właściwości**.  
  
3. Wybierz **zabezpieczeń** karcie i przejdź do **główny/ServiceModel** przestrzeni nazw. Kliknij przycisk **zabezpieczeń** przycisku.  
  
4. Wybierz konkretną grupę lub użytkownika, który ma być kontroli dostępu i użycia **Zezwalaj** lub **Odmów** pole wyboru, aby skonfigurować uprawnienia.  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a>Udzielanie uprawnień rejestracji WCF WMI do dodatkowych użytkowników  
 Usługa WCF umożliwia danych zarządzania usługą WMI. Robi to dzięki hostowaniu dostawcę WMI w procesie, czasami nazywane "dostawca odłączony". W przypadku danych zarządzania ujawnianie konta, które rejestruje ten dostawca musi mieć odpowiednie uprawnienia. W Windows tylko niewielki zestaw uprzywilejowanych kont można zarejestrować dostawcy odłączeni domyślnie. Jest to problem, ponieważ użytkownicy często chcą udostępnianie z usługi WCF, uruchomiony w ramach konta, które nie znajduje się w domyślnym zestawem danych usługi WMI.  
  
 Aby zapewnić dostęp, administrator musi Przyznaj następujące uprawnienia do dodatkowe konta w następującej kolejności:  
  
1. Uprawnienie do dostępu do usług WCF Namespace WMI.  
  
2. Uprawnienia do rejestrowania dostawcy WMI odłączone WCF.  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a>Aby udzielić uprawnień dostępu do przestrzeni nazw usługi WMI  
  
1. Uruchom poniższy skrypt programu PowerShell.  
  
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
  
     Ten skrypt programu PowerShell używa definicji języka SDDL (Security Descriptor), aby udzielić dostępu grupy wbudowane użytkowników do obszaru nazw WMI "główny/servicemodel". Określa następujące listy ACL:  
  
    - Wbudowanego konta administratora (BA) — już masz dostęp.  
  
    - (NS) — Usługa sieciowa ma już dostęp.  
  
    - System lokalny (LS) - już masz dostęp.  
  
    - Wbudowani użytkownicy — grupy, aby udzielić dostępu do.  
  
#### <a name="to-grant-provider-registration-access"></a>Aby udzielić dostawcy dostępu rejestracji  
  
1. Uruchom poniższy skrypt programu PowerShell.  
  
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
 W przykładzie w tej sekcji spowoduje przydzielenie uprawnień rejestracji dostawcy WMI dla wszystkich użytkowników lokalnych. Jeśli chcesz udzielić dostępu do użytkownika lub grupy, która nie jest wbudowany, następnie należy uzyskać tego użytkownika lub grupy identyfikator zabezpieczeń (SID). Nie jest prostym sposobem pobrania identyfikatora SID dla dowolnego użytkownika. Jedną z metod jest zalogowanie się jako odpowiedniego użytkownika i następnie należy wydać następujące polecenie powłoki.  
  
```  
Whoami /user  
```  
  
 Zapewnia to identyfikator SID bieżącego użytkownika, ale ta metoda nie może służyć do pobrania identyfikatora SID dla dowolnego użytkownika. Inną metodą do pobrania identyfikatora SID jest użycie [getsid.exe](https://go.microsoft.com/fwlink/?LinkId=186467) narzędzia z [Windows 2000 Resource Kit Tools do wykonywania zadań administracyjnych](https://go.microsoft.com/fwlink/?LinkId=178660). To narzędzie porównuje identyfikator SID dwóch użytkowników (lokalnego lub domeny), a po stronie efekt drukuje dwa identyfikatory SID w wierszu polecenia. Aby uzyskać więcej informacji, zobacz [dobrze znane identyfikatory SID](https://go.microsoft.com/fwlink/?LinkId=186468).  
  
## <a name="accessing-remote-wmi-object-instances"></a>Uzyskiwanie dostępu do wystąpienia obiektu zdalną usługę WMI  
 Jeśli potrzebujesz dostępu do wystąpień usługi WCF WMI na komputerze zdalnym, należy włączyć prywatność pakietów w menu Narzędzia, których używasz do dostępu. W poniższej sekcji opisano sposób osiągnięcia je przy użyciu usługi WMI CIM Studio, Tester oprzyrządowania Instrumentacji zarządzania Windows, jak również zestaw .NET SDK 2.0.  
  
### <a name="wmi-cim-studio"></a>WMI CIM Studio  
 Jeśli zainstalowano [narzędzia administracyjne WMI](https://go.microsoft.com/fwlink/?LinkId=95185), można użyć WMI CIM Studio do wystąpień WMI dostępu. Narzędzia znajdują się w następującym folderze  
  
 **Narzędzia Files\WMI %Windir%\Program\\**  
  
1. W **nawiązywanie połączenia z przestrzeni nazw:** okna, typ **root\ServiceModel** i kliknij przycisk **OK.**  
  
2. W **WMI CIM Studio logowania** okna, kliknij przycisk **Opcje >>** przycisk, aby rozwinąć w oknie. Wybierz **prywatność pakietów** dla **poziom uwierzytelniania**i kliknij przycisk **OK**.  
  
### <a name="windows-management-instrumentation-tester"></a>Tester oprzyrządowania Instrumentacji zarządzania Windows  
 To narzędzie jest instalowane przez Windows. Aby je uruchomić, należy uruchomić konsoli poleceń, wpisując polecenie **cmd.exe** w **uruchomienia/Start** dialogowym i kliknij przycisk **OK**. Następnie wpisz **wbemtest.exe** w oknie wiersza polecenia. Następnie zostanie uruchomione Narzędzie Tester oprzyrządowania Instrumentacji zarządzania Windows.  
  
1. Kliknij przycisk **Connect** przycisk w prawym górnym rogu okna.  
  
2. W nowym oknie wprowadź **root\ServiceModel** dla **Namespace** i wybierz przycisk **prywatność pakietów** dla **poziom uwierzytelniania**. Kliknij przycisk **Połącz**.  
  
### <a name="using-managed-code"></a>Przy użyciu kodu zarządzanego  
 Można również przejść zdalnego wystąpień WMI programowo przy użyciu klas dostarczonych przez <xref:System.Management> przestrzeni nazw. Poniższy przykład kodu pokazuje, jak to zrobić.  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
