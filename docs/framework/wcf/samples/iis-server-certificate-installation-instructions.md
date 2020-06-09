---
title: Instrukcje instalacji certyfikatu serwera Internetowych usług informacyjnych
ms.date: 03/30/2017
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
ms.openlocfilehash: 301a10c615a13a42e1a6e1b89d2724476ca4fbae
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594663"
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a>Instrukcje instalacji certyfikatu serwera Internetowych usług informacyjnych
Aby uruchomić przykłady, które bezpiecznie komunikują się z Internet Information Services (IIS), należy utworzyć i zainstalować certyfikat serwera.  
  
## <a name="step-1-creating-certificates"></a>Krok 1. Tworzenie certyfikatów  
 Aby utworzyć certyfikat dla komputera, Otwórz wiersz polecenia dla deweloperów dla programu Visual Studio z uprawnieniami administratora i uruchom setup. bat, który jest dołączony do każdego z przykładów, które używają bezpiecznej komunikacji z usługami IIS. Upewnij się, że ścieżka zawiera folder zawierający Makecert. exe przed uruchomieniem tego pliku wsadowego. Następujące polecenie służy do tworzenia certyfikatu w Setup. bat.  
  
```console  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a>Krok 2. Instalowanie certyfikatów  
 Kroki wymagane do zainstalowania właśnie utworzonych certyfikatów zależą od używanej wersji usług IIS.  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a>Aby zainstalować usługi IIS w usługach IIS 5,1 (Windows XP) i IIS 6,0 (Windows Server 2003)  
  
1. Otwórz przystawkę MMC Menedżera Internet Information Services.  
  
2. Kliknij prawym przyciskiem myszy domyślną witrynę sieci Web i wybierz pozycję **Właściwości**.  
  
3. Wybierz kartę **Zabezpieczenia katalogów** .  
  
4. Kliknij przycisk **certyfikat serwera** . Zostanie uruchomiony Kreator certyfikatu serwera sieci Web.  
  
5. Wykonaj kroki kreatora. Wybierz opcję przypisania certyfikatu. Wybierz certyfikat ServiceModelSamples-HTTPS-Server z listy certyfikatów, które są wyświetlane.  
  
     ![Kreator certyfikatów usług IIS](media/iiscertificate-wizard.GIF "IISCertificate_Wizard")  
  
6. Przetestuj dostęp do usługi w przeglądarce przy użyciu adresu HTTPS `https://localhost/servicemodelsamples/service.svc` .  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a>Jeśli protokół SSL został wcześniej skonfigurowany przy użyciu programu HttpCfg. exe  
  
1. Użyj Makecert. exe (lub uruchom plik Setup. bat), aby utworzyć certyfikat serwera.  
  
2. Uruchom Menedżera usług IIS i Zainstaluj certyfikat zgodnie z poprzednimi krokami.  
  
3. Dodaj następujący wiersz kodu do programu klienckiego.  
  
> [!IMPORTANT]
> Ten kod jest wymagany tylko w przypadku certyfikatów testowych, takich jak te utworzone przez Makecert. exe. Nie jest to zalecane w przypadku kodu produkcyjnego.  
  
```csharp  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a>Aby zainstalować usługi IIS w usługach IIS 7,0 (Windows Vista i Windows Server 2008)  
  
1. W menu **Start** kliknij polecenie **Uruchom**, a następnie wpisz **inetmgr** , aby otworzyć przystawkę MMC Internet Information Services (IIS).  
  
2. Kliknij prawym przyciskiem myszy **domyślną witrynę sieci Web** i wybierz pozycję **Edytuj powiązania...**  
  
3. Kliknij przycisk **Dodaj** w oknie dialogowym **powiązania witryny** .  
  
4. Z listy rozwijanej **Typ** wybierz pozycję **https** .  
  
5. Wybierz pozycję **ServiceModelSamples-HTTPS-Server** z listy rozwijanej **certyfikat SSL** i kliknij przycisk **OK**.  
  
6. Przetestuj dostęp do usługi w przeglądarce przy użyciu adresu HTTPS `https://localhost/servicemodelsamples/service.svc` .  
  
> [!NOTE]
> Ponieważ instalowany certyfikat testowy nie jest zaufanym certyfikatem, podczas przeglądania lokalnych adresów sieci Web zabezpieczonych za pomocą tego certyfikatu mogą wystąpić dodatkowe ostrzeżenia dotyczące zabezpieczeń programu Internet Explorer.  
  
## <a name="removing-certificates"></a>Usuwanie certyfikatów  
  
- Użyj Menedżera Internet Information Services, jak zostało to wcześniej przekazane, ale Usuń certyfikat lub powiązanie zamiast dodawać.  
  
- Usuń certyfikat komputera za pomocą następującego polecenia.  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
