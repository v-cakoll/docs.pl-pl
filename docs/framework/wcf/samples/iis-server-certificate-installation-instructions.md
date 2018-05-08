---
title: Instrukcje instalacji certyfikatu serwera Internetowych usług informacyjnych
ms.date: 03/30/2017
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
ms.openlocfilehash: 46d1acf758dd50b881527a16570a1e4a45933958
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a>Instrukcje instalacji certyfikatu serwera Internetowych usług informacyjnych
Aby uruchomić przykłady, które bezpiecznego komunikowania się z programu Internet Information Services (IIS), należy utworzyć i instalowania certyfikatu serwera.  
  
## <a name="step-1-creating-certificates"></a>Krok 1. Tworzenie certyfikatów  
 Aby utworzyć certyfikat komputera, otwórz wiersz polecenia programu Visual Studio z uprawnieniami administratora i uruchom pliku Setup.bat, który znajduje się w każdym przykłady, które bezpiecznej komunikacji za pomocą usług IIS. Upewnij się, że ścieżka zawiera folder zawierający Makecert.exe przed uruchomieniem tego pliku wsadowego. Następujące polecenie służy do utworzenia certyfikatu w pliku Setup.bat.  
  
```  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a>Krok 2. Instalowanie certyfikatów  
 Kroki wymagane do zainstalowania certyfikatów utworzonego zależą od tego, używając wersji programu IIS.  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a>Aby zainstalować usługi IIS w wersji 5.1 usług IIS (z systemem Windows XP) i usług IIS 6.0 (Windows Server 2003)  
  
1.  Otwórz Internet Information Services przystawki programu MMC Menedżer.  
  
2.  Kliknij prawym przyciskiem myszy domyślnej witryny sieci Web i wybierz **właściwości**.  
  
3.  Wybierz **zabezpieczenia katalogu** kartę.  
  
4.  Kliknij przycisk **certyfikatu serwera** przycisku. Zostanie uruchomiony Kreator certyfikatu serwera sieci Web.  
  
5.  Ukończ pracę kreatora. Wybierz opcję, aby przypisać certyfikat. Wybierz certyfikat serwera ServiceModelSamples-HTTPS z listy certyfikatów, które są wyświetlane.  
  
     ![Kreator certyfikatów usług IIS](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")  
  
6.  Testowanie dostępu do usługi w przeglądarce przy użyciu adresu HTTPS https://localhost/servicemodelsamples/service.svc.  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a>Jeśli protokół SSL został uprzednio skonfigurowany przy użyciu Httpcfg.exe  
  
1.  Użyj Makecert.exe (lub wykonywania pliku Setup.bat) można utworzyć certyfikatu serwera.  
  
2.  Uruchom Menedżera usług IIS i instalowania certyfikatu zgodnie z poprzednich kroków.  
  
3.  Dodaj następujący wiersz kodu do programu klienta.  
  
> [!IMPORTANT]
>  Ten kod jest wymagana tylko dla certyfikaty, takich jak te utworzone przez Makecert.exe testów. Nie jest zalecane dla kodu produkcyjnego.  
  
```  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a>Aby zainstalować usługi IIS w programie IIS 7.0 (system Windows Vista i Windows Server 2008)  
  
1.  Z **Start** menu, kliknij przycisk **Uruchom**, wpisz **inetmgr** do otwierania przystawki MMC usług Internet Information Services (IIS).  
  
2.  Kliknij prawym przyciskiem myszy **domyślna witryna sieci Web** i wybierz **Edytuj powiązania...**  
  
3.  Kliknij przycisk **Dodaj** przycisku **powiązania witryny** okno dialogowe.  
  
4.  Wybierz **HTTPS** z **typu** listy rozwijanej.  
  
5.  Wybierz **ServiceModelSamples HTTPS serwera** z **certyfikat SSL** listy rozwijanej i kliknij przycisk **OK**.  
  
6.  Testowanie dostępu do usługi w przeglądarce przy użyciu adresu HTTPS https://localhost/servicemodelsamples/service.svc.  
  
> [!NOTE]
>  Ponieważ certyfikat testowy, który został właśnie zainstalowany, nie jest zaufany certyfikat, mogą wystąpić dodatkowe ostrzeżenia dotyczące zabezpieczeń programu Internet Explorer podczas przeglądania do lokalnego adresy sieci Web zabezpieczone przy użyciu tego certyfikatu.  
  
## <a name="removing-certificates"></a>Usuwanie certyfikatów  
  
-   Zgodnie z wcześniej skierowany, ale usunąć certyfikat lub powiązanie zamiast opcji dodawania go, użyj Menedżera internetowych usług informacyjnych.  
  
-   Usuń certyfikat komputera za pomocą następującego polecenia.  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
