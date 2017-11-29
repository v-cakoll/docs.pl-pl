---
title: "Instrukcje: Instalowanie i konfigurowanie składników aktywacji programu WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 77dec85ee12250080fc487d120749892a148ef17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a>Instrukcje: Instalowanie i konfigurowanie składników aktywacji programu WCF
W tym temacie opisano kroki wymagane do skonfigurowania Windows Process Activation Service (znanej także jako Usługa WAS) na [!INCLUDE[wv](../../../../includes/wv-md.md)] hosta [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] protokoły sieciowe usług, które nie komunikują się za pośrednictwem protokołu HTTP. W poniższych sekcjach opisano czynności dla tej konfiguracji:  
  
-   Zainstaluj (lub potwierdź instalacji) [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] składników aktywacji.  
  
-   Skonfiguruj WAS do obsługi protokołu innego niż HTTP. Poniższa procedura umożliwia skonfigurowanie [!INCLUDE[wv](../../../../includes/wv-md.md)] aktywacji TCP.  
  
 Po zainstalowaniu i skonfigurowaniu WAS, zobacz [porady: hostowanie usługi WCF w WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) dla procedury tworzenia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi udostępniającej punktu końcowego protokołu HTTP, który wykorzystuje WAS.  
  
### <a name="to-install-the-wcf-non-http-activation-components"></a>Aby zainstalować składniki Aktywacja bez HTTP programu WCF  
  
1.  Kliknij przycisk **Start** przycisk, a następnie kliknij przycisk **Panelu sterowania**.  
  
2.  Kliknij przycisk **programy**, a następnie kliknij przycisk **programy i funkcje**.  
  
3.  Na **zadania** menu, kliknij przycisk **Włącz lub wyłącz funkcje systemu Windows**.  
  
4.  Znajdź [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] węzła, wybierz, a następnie rozwiń węzeł.  
  
5.  Wybierz **składników aktywacji programu WCF bez Http** i Zapisz ustawienia.  
  
### <a name="to-configure-the-was-to-support-tcp-activation"></a>Aby skonfigurować usługi WAS do obsługi aktywacji TCP  
  
1.  Aby zapewnić obsługę aktywacji net.tcp, domyślnej witryny sieci Web musi zostać powiązana do portów net.tcp. Można to zrobić za pomocą Appcmd.exe, który jest instalowany z [!INCLUDE[iisver](../../../../includes/iisver-md.md)] narzędzi zarządzania. W oknie wiersza polecenia uprawnień administratora uruchom następujące polecenie.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  To polecenie jest pojedynczy wiersz tekstu. To polecenie dodaje powiązania witryny net.tcp, do domyślnej witryny sieci Web nasłuchiwanie na porcie TCP 808 z żadną nazwą hosta.  
  
2.  Mimo że wszystkie aplikacje w obrębie lokacji korzystają wspólnej powiązanie net.tcp, każdej aplikacji można włączyć obsługę net.tcp pojedynczo. Aby włączyć net.tcp dla aplikacji, uruchom następujące polecenie z wiersza polecenia z uprawnieniami administratora na poziomie.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app   
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp  
    ```  
  
    > [!NOTE]
    >  To polecenie jest pojedynczy wiersz tekstu. To polecenie włącza /\<*aplikacja WCF*> aplikacji, aby uzyskać dostęp za pomocą obu http://localhost*/\<aplikacja WCF >* i net.tcp:// localhost /*\<aplikacja WCF >*.  
  
     Usuń powiązanie witryny net.tcp, dodane dla tego przykładu.  
  
     Dla wygody następujące dwa kroki są implementowane w pliku wsadowym o nazwie RemoveNetTcpSiteBinding.cmd znajduje się w katalogu próbki.  
  
    1.  Usuń net.tcp z listy włączonych protokołów, uruchamiając następujące polecenie w oknie wiersza polecenia poziomie administratora.  
  
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
  
### <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a>Aby usunąć z listy włączonych protokołów net.tcp  
  
1.  Aby usunąć net.tcp z listy włączonych protokołów, uruchom następujące polecenie w oknie wiersza polecenia poziomie administratora.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
    ```  
  
    > [!NOTE]
    >  To polecenie jest pojedynczy wiersz tekstu.  
  
### <a name="to-remove-the-nettcp-site-binding"></a>Aby usunąć powiązanie witryny usługi net.tcp  
  
1.  Aby usunąć lokację net.tcp powiązanie uruchom następujące polecenie w oknie wiersza polecenia poziomie administratora.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
    -bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  To polecenie jest pojedynczy wiersz tekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [Aktywacja TCP](../../../../docs/framework/wcf/samples/tcp-activation.md)  
 [Aktywacja usługi MSMQ](../../../../docs/framework/wcf/samples/msmq-activation.md)  
 [Aktywowanie elementu Namedpipe](../../../../docs/framework/wcf/samples/namedpipe-activation.md)  
 [Windows Server AppFabric funkcje hostingu](http://go.microsoft.com/fwlink/?LinkId=201276)
