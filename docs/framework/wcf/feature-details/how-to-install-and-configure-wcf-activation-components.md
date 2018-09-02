---
title: 'Instrukcje: Instalowanie i konfigurowanie składników aktywacji programu WCF'
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: 8b516bb4603f33828069b5356676d8b35dc961d2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43408673"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a>Instrukcje: Instalowanie i konfigurowanie składników aktywacji programu WCF
W tym temacie opisano kroki wymagane do skonfigurowania usługi aktywacji procesów systemu Windows (znany także jako WAS) na [!INCLUDE[wv](../../../../includes/wv-md.md)] do hostowania usług Windows Communication Foundation (WCF) protokołów sieciowych usług, które nie komunikują się za pośrednictwem protokołu HTTP. W poniższych sekcjach opisano w krokach dla tej konfiguracji:  
  
-   Zainstalować (lub Potwierdź instalację) składników aktywacji programu WCF.  
  
-   Skonfiguruj WAS do obsługi protokołu innego niż HTTP. Poniższa procedura umożliwia skonfigurowanie [!INCLUDE[wv](../../../../includes/wv-md.md)] aktywacji TCP.  
  
 Gdy instalowanie i konfigurowanie usługi WAS, zobaczysz [instrukcje: hostowanie usługi WCF w WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) procedury utworzyć usługę WCF, która uwidacznia punkt końcowy protokołu HTTP, który wykorzystuje WAS.  
  
### <a name="to-install-the-wcf-non-http-activation-components"></a>Aby zainstalować składniki Aktywacja bez HTTP programu WCF  
  
1.  Kliknij przycisk **Start** przycisk, a następnie kliknij przycisk **Panelu sterowania**.  
  
2.  Kliknij przycisk **programy**, a następnie kliknij przycisk **programy i funkcje**.  
  
3.  Na **zadania** menu, kliknij przycisk **Windows Włącz lub wyłącz funkcje**.  
  
4.  Znajdź [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] węzła, wybierz, a następnie rozwiń węzeł.  
  
5.  Wybierz **składników Aktywacja bez Http programu WCF** pole, a następnie Zapisz ustawienia.  
  
### <a name="to-configure-the-was-to-support-tcp-activation"></a>Aby skonfigurować WAS do obsługi Aktywacja TCP  
  
1.  Aby zapewnić obsługę aktywacji net.tcp, domyślna witryna sieci Web musi zostać powiązana portów net.tcp. Można to zrobić za pomocą Appcmd.exe, który został zainstalowany przy użyciu [!INCLUDE[iisver](../../../../includes/iisver-md.md)] zestaw narzędzi do zarządzania. W oknie wiersza polecenia uprawnień administratora uruchom następujące polecenie.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  To polecenie jest pojedynczy wiersz tekstu. To polecenie dodaje powiązanie witryny net.tcp, do domyślnej witryny sieci Web nasłuchiwanie na porcie TCP 808 z nazwą hosta.  
  
2.  Mimo że wszystkie aplikacje w ramach lokacji mają wspólne powiązanie net.tcp, każdej aplikacji można włączyć obsługę net.tcp indywidualnie. Aby włączyć net.tcp dla aplikacji, uruchom następujące polecenie z wiersza polecenia z uprawnieniami administratora na poziomie.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app   
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp  
    ```  
  
    > [!NOTE]
    >  To polecenie jest pojedynczy wiersz tekstu. To polecenie włącza /\<*aplikacji WCF*> aplikacji można uzyskać za pomocą zarówno `http://localhost/<WCF Application>` i `net.tcp://localhost/<WCF Application>`.
  
     Usuń powiązanie witryny net.tcp, dodane dla tego przykładu.  
  
     Dla wygody następujące dwa kroki są implementowane w pliku wsadowym, o nazwie RemoveNetTcpSiteBinding.cmd znajduje się w katalogu próbki.  
  
    1.  Usuń net.tcp z listy włączone protokoły, uruchamiając następujące polecenie w oknie wiersza polecenia uprawnień administratora.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  To polecenie jest pojedynczy wiersz tekstu.  
  
    2.  Usuń powiązanie witryny net.tcp, uruchamiając następujące polecenie w oknie wiersza polecenia z podwyższonym poziomem uprawnień:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  To polecenie jest pojedynczy wiersz tekstu.  
  
### <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a>Aby usunąć net.tcp, z listy włączone protokoły  
  
1.  Aby usunąć net.tcp, z listy włączone protokoły, uruchom następujące polecenie w oknie wiersza polecenia uprawnień administratora.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
    ```  
  
    > [!NOTE]
    >  To polecenie jest pojedynczy wiersz tekstu.  
  
### <a name="to-remove-the-nettcp-site-binding"></a>Aby usunąć powiązanie witryny net.tcp  
  
1.  Aby usunąć lokację net.tcp powiązania uruchom następujące polecenie w oknie wiersza polecenia uprawnień administratora.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
    -bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  To polecenie jest pojedynczy wiersz tekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [Aktywacja TCP](../../../../docs/framework/wcf/samples/tcp-activation.md)  
 [Aktywacja usługi MSMQ](../../../../docs/framework/wcf/samples/msmq-activation.md)  
 [Aktywowanie elementu NamedPipe](../../../../docs/framework/wcf/samples/namedpipe-activation.md)  
 [Windows Server AppFabric funkcje hostingu](https://go.microsoft.com/fwlink/?LinkId=201276)
