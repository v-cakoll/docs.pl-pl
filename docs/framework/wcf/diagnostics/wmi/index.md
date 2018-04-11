---
title: Używanie Instrumentacji zarządzania Windows na potrzeby diagnostyki
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0862f747cb969a6aa2e63d86e842097260e95b56
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a>Używanie Instrumentacji zarządzania Windows na potrzeby diagnostyki
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]udostępnia dane inspekcji usługi w czasie wykonywania za pośrednictwem [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] dostawcy Instrumentacji zarządzania Windows (WMI).  
  
## <a name="enabling-wmi"></a>Włączanie usługi WMI  
 Usługa WMI stanowi implementację firmy Microsoft w sieci Web-Based Enterprise Management (WBEM) standardowa. [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]zestaw SDK usługi WMI, zobacz [Instrumentacji zarządzania Windows](https://msdn.microsoft.com/library/aa394582.aspx). Technologia WBEM jest branżowy standard jak aplikacje ujawnia Instrumentacji zarządzania do narzędzia do zarządzania zewnętrznego.  
  
 Dostawca WMI jest składnik, który ujawnia Instrumentacji w czasie wykonywania za pośrednictwem interfejsu zgodnego WBEM. Zawiera zestaw obiektów WMI, które mają pary atrybut/wartość. Pary może mieć wiele typów prostych. Narzędzia do zarządzania mogą łączyć się usługi za pomocą interfejsu w czasie wykonywania. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]udostępnia Atrybuty usług, takich jak adresy, powiązania zachowania i odbiorników.  
  
 W pliku konfiguracyjnym aplikacji można aktywować wbudowanego dostawcy WMI. Jest to zrobić za pomocą `wmiProviderEnabled` atrybutu [ \<diagnostyki >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) w [ \<system.serviceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) sekcji, jak pokazano w następującym przykładowym Konfiguracja.  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 Ten wpis konfiguracji uwidacznia interfejs WMI. Aplikacje do zarządzania można teraz łączenie się za pośrednictwem tego interfejsu i uzyskać dostęp z Instrumentacją zarządzania aplikacji.  
  
## <a name="accessing-wmi-data"></a>Uzyskiwanie dostępu do danych usługi WMI  
 Wiele różnych sposobów można uzyskać dostępu do danych usługi WMI. Firma Microsoft udostępnia interfejsy API usługi WMI dla skryptów, [!INCLUDE[vbprvb](../../../../../includes/vbprvb-md.md)] aplikacji, aplikacji C++ i [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]. Aby uzyskać więcej informacji, zobacz [za pomocą usługi WMI](http://go.microsoft.com/fwlink/?LinkId=95183).  
  
> [!CAUTION]
>  Jeśli używasz metody podane w programie .NET Framework do uzyskania programowego dostępu do danych usługi WMI, należy zwrócić uwagę, takich metod może zgłaszać wyjątki po nawiązaniu połączenia. Połączenie nie zostanie nawiązane podczas budowy <xref:System.Management.ManagementObject> wystąpienia, ale pierwszego żądania obejmujące rzeczywiste dane programu exchange. W związku z tym należy używać `try..catch` bloku catch możliwych wyjątków.  
  
 Można zmienić śledzenia i poziom rejestrowania komunikatów, a także opcje rejestrowania komunikatów dla `System.ServiceModel` źródła śledzenia w usłudze WMI. Można to zrobić po zalogowaniu się do [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) wystąpienia, która udostępnia te właściwości, wartość logiczna: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, i `TraceLevel`. W związku z tym jeśli skonfiguruj odbiornik śledzenia dla rejestrowanie komunikatów, ale ustawiona korzystać z tych opcji do `false` w konfiguracji można później zmienić ich `true` gdy aplikacja jest uruchomiona. Umożliwi to efektywne rejestrowanie komunikatów w czasie wykonywania. Podobnie po włączeniu rejestrowania w pliku konfiguracyjnym komunikatów, można ją wyłączyć w czasie wykonywania za pomocą usługi WMI.  
  
 Należy zwrócić uwagę że jeśli nie rejestrowanie komunikatów śledzenia odbiorników dla rejestrowanie komunikatów lub nie `System.ServiceModel` obiektów nasłuchujących śledzenia śledzenia są określone w pliku konfiguracji, żadne zmiany są brane pod efekt, mimo że zmiany są akceptowane przez usługę WMI. Aby uzyskać więcej informacji na temat prawidłowo konfigurowania odpowiednich odbiorników, zobacz [Konfigurowanie rejestrowania komunikatów](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) i [Konfigurowanie śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md). Poziom śledzenia wszystkich innych źródeł śledzenia określony w konfiguracji jest skuteczne, podczas uruchamiania aplikacji i nie można zmienić.  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]przedstawia `GetOperationCounterInstanceName` metod dla skryptów. Ta metoda zwraca nazwę wystąpienia licznika wydajności w przypadku udostępnienia operacji o nazwie. Dane wejściowe nie są jednak zweryfikować. W związku z tym Jeśli podasz nazwę operacji niepoprawne, zwracana jest nazwa niepoprawny licznik.  
  
 `OutgoingChannel` Właściwość `Service` wystąpienia nie będą uwzględniane kanały otwarte przez usługę, aby połączyć się z inną usługą, w przypadku [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] klienta usługi docelowej nie jest tworzony w `Service` metody.  
  
 **Uwaga** obsługuje tylko WMI <xref:System.TimeSpan> wartość 3 miejsc dziesiętnych. Na przykład, jeśli Usługa ustawia jedną z jej właściwości na <xref:System.TimeSpan.MaxValue>, jego wartość zostanie obcięta po 3 miejsc dziesiętnych, podczas wyświetlania za pomocą usługi WMI.  
  
## <a name="security"></a>Zabezpieczenia  
 Ponieważ [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] dostawcy WMI umożliwia odnajdywanie usług w środowisku, należy zachować wyjątkową ostrożność za udzielanie dostępu do niego. Jeśli zmniejszą domyślnego dostępu tylko do administratora, może zezwolić stron zaufanych mniej dostęp do poufnych danych w danym środowisku. W szczególności jeśli Poluzuj uprawnienia na zdalny dostęp do usługi WMI, zalewania ataków mogą wystąpić. Jeśli proces jest wypełniony nadmiernego żądania usługi WMI, jego wydajność może znacznie mniej wydajna.  
  
 Ponadto jeśli zmniejszą uprawnienia dostępu do pliku MOF, Zaufane mniej strony można manipulować zachowanie usługi WMI i alter obiektów, które są ładowane w schemacie WMI. Na przykład pola można usunąć danych o kluczowym znaczeniu jest ukrywane przez administratora lub pola, które nie wypełnić lub spowodować wyjątki są dodawane do pliku.  
  
 Domyślnie [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] dostawcy WMI przyznaje "Wykonaj metodę", "zapis dostawcy" i "Włącz konto" uprawnień administratora, a "Włącz konto" uprawnień dla platformy ASP.NET, Usługa lokalna i Usługa sieciowa. W szczególności na inną niż[!INCLUDE[wv](../../../../../includes/wv-md.md)] platform, konto ASP.NET ma dostęp do odczytu przestrzeni nazw usługi WMI ServiceModel. Jeśli nie chcesz przyznać odpowiednie uprawnienia do określonej grupy użytkowników, należy albo Dezaktywuj dostawcy usługi WMI (on jest domyślnie wyłączona) lub wyłączyć dostęp do określonej grupy użytkowników.  
  
 Ponadto podczas próby włączenia usługi WMI za pomocą konfiguracji usługi WMI może nie być włączone z powodu niewystarczających użytkownika uprawnień. Jednak brak zdarzenia są zapisywane w dzienniku zdarzeń, aby zarejestrować ten błąd.  
  
 Aby zmodyfikować poziomy uprawnień użytkownika, wykonaj następujące kroki.  
  
1.  Kliknij przycisk Start, a następnie uruchom i wpisz **compmgmt.msc**.  
  
2.  Kliknij prawym przyciskiem myszy **usług i aplikacji/WMI formanty** wybierz **właściwości**.  
  
3.  Wybierz **zabezpieczeń** kartę, a następnie przejdź do **główny/ServiceModel** przestrzeni nazw. Kliknij przycisk **zabezpieczeń** przycisku.  
  
4.  Wybierz określonej grupy lub użytkownika, który ma zostać kontroli dostępu i użycia **Zezwalaj** lub **Odmów** pole wyboru, aby skonfigurować uprawnienia.  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a>Udzielanie uprawnień rejestracji WCF WMI dodatkowym użytkownikom  
 Usługa WCF umożliwia dane zarządzania z usługą WMI. Robi to przez hosting w trakcie dostawcy WMI, czasem nazywany "odłączonego dostawcy". Dla danych zarządzania, które mają być uwidaczniane konto, które rejestruje ten dostawca musi mieć odpowiednie uprawnienia. W systemie Windows mały zestaw kont uprzywilejowanych można zarejestrować dostawcy rozdzielonymi domyślnie. Jest to problem, ponieważ użytkownicy często mają być udostępnianie danych usługi WMI z poziomu usługi WCF uruchomiony na koncie, który nie znajduje się w domyślnym zestawem.  
  
 Aby zapewnić dostęp, administrator musi Przyznaj następujące uprawnienia do dodatkowe konta w następującej kolejności:  
  
1.  Uprawnienia dostępu do usługi WCF Namespace WMI.  
  
2.  Uprawnienia do rejestrowania dostawcy instrumentacji WMI programu WCF odłączona.  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a>Aby udzielić uprawnień dostępu do przestrzeni nazw usługi WMI  
  
1.  Uruchom następujący skrypt programu PowerShell.  
  
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
  
     Ten skrypt programu PowerShell używa definicji języka SDDL (Security Descriptor), aby udzielić dostępu grupy wbudowane użytkowników do obszaru nazw WMI "główny/servicemodel". Określa on następujące listy ACL:  
  
    -   Wbudowanego konta administratora (BA) — już dostępu.  
  
    -   Usługa nazw (NS) - sieciowa ma już dostępu.  
  
    -   System lokalny (LS) - ma już dostępu.  
  
    -   Wbudowanych użytkownicy — grupa, aby udzielić dostępu do.  
  
#### <a name="to-grant-provider-registration-access"></a>Aby przyznać dostawcy dostęp do rejestracji  
  
1.  Uruchom następujący skrypt programu PowerShell.  
  
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
 Przykład w tej sekcji przyznaje uprawnienia rejestracji dostawcy WMI do wszystkich użytkowników lokalnych. Jeśli chcesz udzielić dostępu do użytkownika lub grupę, która nie korzysta z wbudowanej w, następnie należy uzyskać tego użytkownika lub grupy identyfikator zabezpieczeń (SID). Nie istnieje prosty sposób można pobrać identyfikatora SID dla dowolnego użytkownika. Jedna z metod jest Zaloguj się jako odpowiedniego użytkownika, a następnie wystawiania następujące polecenia powłoki.  
  
```  
Whoami /user  
```  
  
 Zapewnia to identyfikator SID bieżącego użytkownika, ale nie można użyć tej metody można pobrać identyfikatora SID dla dowolnego użytkownika. Innej metody, aby uzyskać identyfikator SID jest użycie [getsid.exe](http://go.microsoft.com/fwlink/?LinkId=186467) narzędzia z [narzędzi systemu Windows 2000 Resource Kit dla zadań administracyjnych](http://go.microsoft.com/fwlink/?LinkId=178660). To narzędzie porównuje SID dwóch użytkowników (lokalnego lub domeny), a po stronie efekt drukuje dwa identyfikatory SID do wiersza polecenia. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Dobrze znane identyfikatory SID](http://go.microsoft.com/fwlink/?LinkId=186468).  
  
## <a name="accessing-remote-wmi-object-instances"></a>Uzyskiwanie dostępu do wystąpienia obiektu zdalną usługę WMI  
 Jeśli chcesz uzyskać dostęp do [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] wystąpienia usługi WMI na komputerze zdalnym, należy włączyć prywatność pakietów narzędzia używane dla dostępu. W poniższej sekcji opisano jak to osiągnąć przy użyciu usługi WMI CIM Studio, Tester oprzyrządowania Instrumentacji zarządzania Windows, jak również .NET SDK 2.0.  
  
### <a name="wmi-cim-studio"></a>WMI CIM Studio  
 Jeśli zainstalowano [narzędzia administracyjne WMI](http://go.microsoft.com/fwlink/?LinkId=95185), można użyć WMI CIM Studio do wystąpień WMI dostępu. Narzędzia znajdują się w folderze  
  
 **Narzędzia Files\WMI %Windir%\Program\\**  
  
1.  W **Połącz z przestrzeni nazw:** wpisz **root\ServiceModel** i kliknij przycisk **OK.**  
  
2.  W **WMI CIM Studio logowania** okna, kliknij przycisk **Opcje >>** przycisk, aby rozwinąć okna. Wybierz **prywatność pakietów** dla **poziom uwierzytelniania**i kliknij przycisk **OK**.  
  
### <a name="windows-management-instrumentation-tester"></a>Tester oprzyrządowania Instrumentacji zarządzania Windows  
 To narzędzie jest instalowane przez system Windows. Aby go uruchomić, należy uruchomić konsoli poleceń, wpisując **cmd.exe** w **Start/Uruchom** okno dialogowe i kliknij przycisk **OK**. Następnie wpisz **wbemtest.exe** w oknie wiersza polecenia. Następnie zostanie uruchomione Narzędzie Tester oprzyrządowania Instrumentacji zarządzania Windows.  
  
1.  Kliknij przycisk **Connect** przycisk w prawym górnym rogu okna.  
  
2.  W nowym oknie, wprowadź **root\ServiceModel** dla **Namespace** pola i wybierz pozycję **prywatność pakietów** dla **poziom uwierzytelniania**. Kliknij przycisk **Połącz**.  
  
### <a name="using-managed-code"></a>Za pomocą kodu zarządzanego  
 Można również przejść zdalnego wystąpień WMI programowo przy użyciu klasy podał <xref:System.Management> przestrzeni nazw. Poniższy przykład kodu pokazuje, jak to zrobić.  
  
```  
String wcfNamespace = String.Format(@"\\{0}\Root\ServiceModel",      
   this.serviceMachineName);  
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
