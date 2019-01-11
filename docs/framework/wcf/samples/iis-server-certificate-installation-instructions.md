---
title: Instrukcje instalacji certyfikatu serwera Internetowych usług informacyjnych
ms.date: 03/30/2017
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
ms.openlocfilehash: a89d907b9be25c83a74f0c5d60d184637552f297
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221105"
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a>Instrukcje instalacji certyfikatu serwera Internetowych usług informacyjnych
Aby uruchomić przykłady, które bezpiecznego komunikowania się za pomocą programu Internet Information Services (IIS), możesz utworzyć i zainstalować certyfikat serwera.  
  
## <a name="step-1-creating-certificates"></a>Krok 1. Tworzenie certyfikatów  
 Aby utworzyć certyfikat dla tego komputera, otwórz wiersz polecenia dla deweloperów programu Visual Studio z uprawnieniami administratora i uruchom Setup.bat, który znajduje się w każdym z przykładów, które bezpiecznej komunikacji za pomocą usług IIS. Upewnij się, że ścieżka zawiera folder, który zawiera Makecert.exe, przed uruchomieniem tego pliku wsadowego. Następujące polecenie służy do utworzenia certyfikatu w Setup.bat.  
  
```  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a>Krok 2. Instalowanie certyfikatów  
 Kroki wymagane do zainstalowania certyfikatów, który został utworzony, zależą od tego, która wersja usług IIS, którego używasz.  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a>Aby zainstalować usługi IIS 5.1 usług IIS (Windows XP) i usług IIS 6.0 (Windows Server 2003)  
  
1.  Otwórz Internet Information Services Manager przystawki MMC w.  
  
2.  Kliknij prawym przyciskiem myszy domyślna witryna sieci Web, a następnie wybierz pozycję **właściwości**.  
  
3.  Wybierz **zabezpieczeń katalogu** kartę.  
  
4.  Kliknij przycisk **certyfikatu serwera** przycisku. Zostanie uruchomiony Kreator certyfikatu serwera sieci Web.  
  
5.  Ukończ pracę kreatora. Wybierz opcję, aby przypisać certyfikat. Wybierz certyfikat ServiceModelSamples HTTPS serwera z listy certyfikatów, które są wyświetlane.  
  
     ![Kreator certyfikatów usług IIS](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")  
  
6.  Testowanie dostępu do usługi w przeglądarce, korzystając z adresu HTTPS `https://localhost/servicemodelsamples/service.svc`.  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a>Jeśli uprzednio skonfigurowane połączenie SSL przy użyciu Httpcfg.exe  
  
1.  Użyj Makecert.exe (lub wykonywania Setup.bat), można utworzyć certyfikatu serwera.  
  
2.  Uruchom Menedżera usług IIS i instalowania certyfikatu zgodnie z poprzednich kroków.  
  
3.  Dodaj następujący wiersz kodu do programu klienta.  
  
> [!IMPORTANT]
>  Ten kod jest wymagana tylko w przypadku testowania certyfikaty, takich jak te utworzone przez Makecert.exe. Nie jest zalecane dla kodu produkcyjnego.  
  
```  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a>Aby zainstalować usługi IIS przez usługi IIS 7.0 (Windows Vista i Windows Server 2008)  
  
1.  Z **Start** menu, kliknij przycisk **Uruchom**, a następnie wpisz **inetmgr** aby otworzyć przystawkę MMC usług Internet Information Services (IIS).  
  
2.  Kliknij prawym przyciskiem myszy **domyślna witryna sieci Web** i wybierz **Edytuj powiązania...**  
  
3.  Kliknij przycisk **Dodaj** przycisku **powiązania witryny** okno dialogowe.  
  
4.  Wybierz **HTTPS** z **typu** listy rozwijanej.  
  
5.  Wybierz **ServiceModelSamples HTTPS serwera** z **certyfikat SSL** listy rozwijanej i kliknij przycisk **OK**.  
  
6.  Testowanie dostępu do usługi w przeglądarce, korzystając z adresu HTTPS `https://localhost/servicemodelsamples/service.svc`.  
  
> [!NOTE]
>  Ponieważ certyfikat testowy, który właśnie zainstalowałeś nie jest zaufany certyfikat, mogą wystąpić dodatkowe ostrzeżenia dotyczące zabezpieczeń programu Internet Explorer podczas przeglądania do lokalnego adresy sieci Web zabezpieczony za pomocą tego certyfikatu.  
  
## <a name="removing-certificates"></a>Usuwanie certyfikatów  
  
-   Użyj Menedżera internetowych usług informacyjnych, zgodnie z wcześniej skierowany, ale usunąć certyfikat lub powiązanie zamiast dodawania go.  
  
-   Usuwanie certyfikatu komputera za pomocą następującego polecenia.  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
