---
title: "Zabezpieczenia powiązania niestandardowego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
caps.latest.revision: "30"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 94c43586606f42cca120ded59637a998d113d229
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="custom-binding-security"></a>Zabezpieczenia powiązania niestandardowego
W tym przykładzie pokazano, jak skonfigurować zabezpieczenia przy użyciu niestandardowego powiązania. Widoczny jest sposób umożliwiają niestandardowego powiązania zabezpieczeń na poziomie komunikatu wraz z bezpiecznego transportu. Jest to przydatne, gdy do przesyłania wiadomości między klientem a usługą jest wymagane bezpieczne transportu i jednocześnie wiadomości musi być bezpieczny na poziomie wiadomości. Ta konfiguracja nie jest obsługiwana przez powiązania dostarczane przez system.  
  
 W tym przykładzie składa się z konsoli klienta programu (EXE) i usługi konsoli programu (EXE). Usługa implementuje kontraktu dwukierunkowego. Kontrakt jest definiowana za pomocą `ICalculatorDuplex` interfejsu, który udostępnia operacji matematycznych (Dodawanie, odjąć mnożenia i dzielenia). `ICalculatorDuplex` Interfejs umożliwia klientowi wykonywania operacji matematycznych, obliczania wyniku uruchomiona przez sesję. Niezależnie od siebie, usługa może zwrócić wyniki na `ICalculatorDuplexCallback` interfejsu. Kontrakt dupleksowy wymaga elementu session, ponieważ kontekst muszą być ustalane do skorelowania zestaw komunikatów przesyłanych między klientem a usługą. Powiązania niestandardowego zdefiniowano obsługującego komunikację dupleksową, który jest bezpieczne.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Konfiguracja usługi definiuje niestandardowego powiązania, który obsługuje następujące funkcje:  
  
-   Komunikacja TCP chronione za pomocą protokołu TLS/SSL.  
  
-   Zabezpieczenia komunikatów systemu Windows.  
  
 Konfiguracja wiązania niestandardowego pozwala bezpiecznego transportu równocześnie umożliwiając zabezpieczeń na poziomie wiadomości. Kolejność elementów wiązania jest ważne podczas definiowania niestandardowego powiązania, ponieważ każdy reprezentuje warstwę stosu kanał (zobacz [niestandardowego powiązania](../../../../docs/framework/wcf/extending/custom-bindings.md)). Niestandardowego powiązania jest zdefiniowany w plikach konfiguracji usługi i klienta, jak pokazano w poniższych Przykładowa konfiguracja.  
  
```xml  
<bindings>  
  <!-- Configure a custom binding. -->  
  <customBinding>  
    <binding name="Binding1">  
      <security authenticationMode="SecureConversation"  
                 requireSecurityContextCancellation="true">  
      </security>  
      <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
      <sslStreamSecurity requireClientCertificate="false"/>  
      <tcpTransport/>  
    </binding>  
  </customBinding>  
</bindings>  
```  
  
 Wiązanie niestandardowe używa certyfikatu usługi do uwierzytelniania usługi na poziomie transportu oraz chronić przed komunikaty podczas transmisji między klientem a usługą. Jest to osiągane przez `sslStreamSecurity` element powiązania. Certyfikat usługi jest skonfigurowany przy użyciu zachowania usługi, jak pokazano w poniższych Przykładowa konfiguracja.  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 Ponadto niestandardowego powiązania używa zabezpieczenia komunikatów z typu poświadczeń systemu Windows — jest to domyślny typ poświadczeń. Jest to osiągane przez `security` element powiązania. Zarówno klient, jak i usługa są uwierzytelniane przy użyciu zabezpieczeń na poziomie komunikatu, jeśli mechanizmu uwierzytelniania Kerberos jest dostępne. Dzieje się tak, jeśli próbka jest uruchamiany w środowisku usługi Active Directory. Jeśli mechanizm uwierzytelniania Kerberos jest niedostępna, jest używane uwierzytelnianie NTLM. NTLM uwierzytelnia klienta do usługi, ale nie uwierzytelnienia usługi dla klienta. `security` Element powiązania jest skonfigurowana do używania `SecureConversation``authenticationType`, które powoduje utworzenia sesji zabezpieczeń zarówno klient, jak i usługi. Jest to wymagane do włączenia usługi kontraktu dwukierunkowego do pracy.  
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Press <ENTER> to terminate client.  
Result(100)  
Result(50)  
Result(882.5)  
Result(441.25)  
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)  
```  
  
 Po uruchomieniu próbki, zobacz wiadomości zwracana do klienta na interfejs wywołania zwrotnego wysyłane z usługi. Zostanie wyświetlona poszczególnych pośrednia wynik, następuje całe równanie po zakończeniu wszystkich operacji. Naciśnij klawisz ENTER, aby zamknąć klienta.  
  
 Dołączony pliku Setup.bat umożliwia konfigurowanie klienta i serwera z certyfikatem odpowiedniej usługi uruchamianie hostowanej aplikacji, która wymaga zabezpieczeń oparte na certyfikatach. Ten plik wsadowy muszą zostać zmodyfikowane, aby pracować na komputerach lub do pracy w przypadku z systemem innym niż obsługiwany.  
  
 Poniżej przedstawiono krótkie omówienie różnych sekcji pliki wsadowe, które dotyczą tego przykładu tak, aby można modyfikować w prawidłowej konfiguracji:  
  
-   Tworzenie certyfikatu serwera.  
  
     Następujące wiersze z pliku pliku Setup.bat utworzenie certyfikatu serwera do użycia. `%SERVER_NAME%` Zmiennej określa nazwę serwera. Zmień tę wartość, aby określić nazwę serwera. Ten plik wsadowy domyślnie nazwę serwera, aby localhost.  
  
     Certyfikat jest przechowywany w magazynie CurrentUser usług hostowanych w sieci Web.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta.  
  
     Następujące wiersze w pliku Setup.bat kopii pliku certyfikatu serwera do klienta zaufanych osób magazynu. Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu klienta. Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład certyfikat wystawiony przez Microsoft — ten krok zapełnianie magazynu certyfikatów klienta przy użyciu certyfikatu serwera nie jest wymagane.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  Plik wsadowy pliku Setup.bat jest przeznaczony do uruchamiania z programu Visual Studio 2010 wiersz polecenia. Wymaga ona, że zmienna środowiskowa MSSDK odwołują się do katalogu, w którym jest zainstalowany zestaw SDK. Ta zmienna środowiskowa jest automatycznie ustawiana w Visual Studio 2010 wiersz polecenia.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Otwórz okno Wiersz polecenia programu Visual Studio z uprawnieniami administratora i uruchom pliku Setup.bat z folderu instalacyjnego próbki. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.  
  
    > [!NOTE]
    >  Plik wsadowy pliku Setup.bat jest przeznaczony do uruchamiania z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia. Wartość zmiennej środowiskowej PATH w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wskazuje katalog zawierający pliki wykonywalne wymagane przez pliku Setup.bat skryptu wiersza polecenia.  
  
2.  Uruchom Service.exe z \service\bin.  
  
3.  Uruchom Client.exe z \client\bin. Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.  
  
4.  Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na komputerach  
  
1.  Na komputerze usługi:  
  
    1.  Utwórz katalog wirtualny o nazwie servicemodelsamples na komputerze usługi.  
  
    2.  Skopiuj pliki programu usługi z \inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi. Upewnij się, skopiuj pliki w podkatalogu \bin.  
  
    3.  Skopiuj pliki pliku Setup.bat i Cleanup.bat komputer usługi.  
  
    4.  Uruchom następujące polecenie w wierszu polecenia programu Visual Studio została otwarta z uprawnieniami administratora: `Setup.bat service`. Spowoduje to utworzenie certyfikatu usługi z nazwą podmiotu pasującego do nazwy komputera, na którym uruchomiono plik wsadowy na.  
  
        > [!NOTE]
        >  Plik wsadowy pliku Setup.bat jest przeznaczony do uruchamiania z programu Visual Studio 2010 wiersz polecenia. Wymaga, aby zmiennej środowiskowej path punktu do katalogu, w którym jest zainstalowany zestaw SDK. Ta zmienna środowiskowa jest automatycznie ustawiana w Visual Studio 2010 wiersz polecenia.  
  
    5.  Zmień [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) wewnątrz pliku Service.exe.config w celu odzwierciedlenia nazwy podmiotu certyfikatu generowane w poprzednim kroku.  
  
    6.  Uruchom Service.exe z wiersza polecenia.  
  
2.  Na komputerze klienckim:  
  
    1.  Skopiuj pliki programu klienta z folderu \client\bin\ na komputerze klienckim. Również skopiować plik Cleanup.bat.  
  
    2.  Uruchom Cleanup.bat, aby usunąć wszelkie stare certyfikaty z poprzedniej próbki.  
  
    3.  Wyeksportuj certyfikat usługi, otwierając wiersz polecenia programu Visual Studio z uprawnieniami administracyjnymi i uruchom następujące polecenie na komputerze usługi (Zastąp `%SERVER_NAME%` z w pełni kwalifikowaną nazwę komputera, na którym usługa jest uruchomiona):  
  
        ```  
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer  
        ```  
  
    4.  Skopiuj %SERVER_NAME%.cer na komputerze klienckim (substitute nazwa_serwera % z w pełni kwalifikowaną nazwę komputera, na którym jest uruchomiona usługa).  
  
    5.  Zaimportuj certyfikat usługi, otwierając wiersz polecenia programu Visual Studio z uprawnieniami administracyjnymi i uruchom następujące polecenie na komputerze klienckim (substitute nazwa_serwera % z w pełni kwalifikowaną nazwę komputera, na którym usługa jest uruchomiona):  
  
        ```  
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople  
        ```  
  
         Kroki nie są konieczne, jeśli certyfikat został wystawiony przez zaufany wystawcy c, d i e.  
  
    6.  Zmodyfikuj plik App.config klienta w następujący sposób:  
  
        ```xml  
        <client>  
            <endpoint name="default"  
                address="net.tcp://ReplaceThisWithServiceMachineName:8000/ServiceModelSamples/Service"   
                binding="customBinding"   
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex"  
        behaviorConfiguration="CalculatorClientBehavior" />  
        </client>  
        ```  
  
    7.  Jeśli usługa jest uruchomiona w ramach konta innego niż Usługa sieciowa lub konta System lokalny w środowisku domeny, może być konieczne zmodyfikowanie tożsamość punktu końcowego dla punktu końcowego usługi w pliku App.config klienta można ustawić odpowiednie nazwy UPN lub nazwy SPN na podstawie konta używanego do uruchamiania usługi. Aby uzyskać więcej informacji o tożsamości punktu końcowego, zobacz [uwierzytelnianie i tożsamość usługi](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) tematu.  
  
    8.  Uruchom Client.exe z wiersza polecenia.  
  
### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po próbki  
  
-   Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki.  
  
## <a name="see-also"></a>Zobacz też
