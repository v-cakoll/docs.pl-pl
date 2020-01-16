---
title: 'Instrukcje: Instalowanie i konfigurowanie składników aktywacji programu WCF'
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: e71664b4361ba28a50b29499585b20a8adbaefd2
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964463"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a>Instrukcje: Instalowanie i konfigurowanie składników aktywacji programu WCF

W tym temacie opisano kroki wymagane do skonfigurowania usługi aktywacji procesów systemu Windows (znanej także jako) w systemie Windows Vista do hostowania usług Windows Communication Foundation (WCF), które nie komunikują się za pośrednictwem protokołów sieciowych protokołu HTTP. W poniższych sekcjach opisano kroki tej konfiguracji:

- Zainstaluj program (lub Potwierdź instalację) składników aktywacji WCF.

- Skonfigurowano obsługę protokołu innego niż HTTP. Poniższa procedura umożliwia skonfigurowanie aktywacji systemu Windows Vista do protokołu TCP.

Po zainstalowaniu i skonfigurowaniu programu zapoznaj się z tematem [jak: Hostowanie usługi WCF w usłudze was](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) , aby poznać procedury tworzenia usługi WCF, która uwidacznia punkt końcowy inny niż http.

## <a name="to-install-the-wcf-non-http-activation-components"></a>Aby zainstalować składniki aktywacji programu WCF inne niż HTTP

1. Kliknij przycisk **Start** , a następnie kliknij pozycję **Panel sterowania**.

2. Kliknij pozycję **programy**, a następnie kliknij pozycję **programy i funkcje**.

3. W menu **zadania** kliknij pozycję **Włącz lub wyłącz funkcje systemu Windows**.

4. Znajdź węzeł WinFX, wybierz go, a następnie rozwiń.

5. Zaznacz pole **Składniki aktywacji programu WCF inne niż http** i Zapisz ustawienie.

## <a name="to-configure-the-was-to-support-tcp-activation"></a>Aby skonfigurować obsługę aktywacji przy użyciu protokołu TCP

1. Aby można było obsługiwać aktywację net. TCP, domyślną witryną sieci Web należy najpierw powiązać z portem net. TCP. Można to zrobić za pomocą programu Appcmd. exe, który jest instalowany za pomocą zestawu narzędzi do zarządzania usługami IIS 7,0. W oknie wiersza polecenia na poziomie administratora uruchom następujące polecenie.

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > To polecenie jest pojedynczym wierszem tekstu. To polecenie dodaje powiązanie witryny net. TCP do domyślnej witryny sieci Web nasłuchiwanie na porcie TCP 808 z dowolną nazwą hosta.

2. Mimo że wszystkie aplikacje w lokacji współdzielą wspólne powiązanie net. TCP, każda aplikacja może włączać pojedynczą obsługę protokołu net. TCP. Aby włączyć usługę net. TCP dla aplikacji, uruchom następujące polecenie w wierszu polecenia na poziomie administratora.

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp
    ```

    > [!NOTE]
    > To polecenie jest pojedynczym wierszem tekstu. To polecenie umożliwia dostęp do\<aplikacji *WCF*> aplikacji przy użyciu obu `http://localhost/<WCF Application>` i `net.tcp://localhost/<WCF Application>`.

     Usuń powiązanie witryny net. TCP dodane do tego przykładu.

     Jako wygoda, następujące dwa kroki są zaimplementowane w pliku wsadowym o nazwie RemoveNetTcpSiteBinding. cmd znajdującym się w przykładowym katalogu.

    1. Usuń usługę net. TCP z listy włączonych protokołów, uruchamiając następujące polecenie w oknie wiersza polecenia administratora.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
        ```

        > [!NOTE]
        > To polecenie jest pojedynczym wierszem tekstu.

    2. Usuń powiązanie witryny net. TCP, uruchamiając następujące polecenie w oknie wiersza polecenia z podwyższonym poziomem uprawnień:

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > To polecenie jest pojedynczym wierszem tekstu.

## <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a>Aby usunąć usługę net. TCP z listy włączonych protokołów

1. Aby usunąć usługę net. TCP z listy włączonych protokołów, uruchom następujące polecenie w oknie wiersza polecenia na poziomie administratora.

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
    ```

    > [!NOTE]
    > To polecenie jest pojedynczym wierszem tekstu.

## <a name="to-remove-the-nettcp-site-binding"></a>Aby usunąć powiązanie witryny net. TCP

1. Aby usunąć powiązanie witryny net. TCP, uruchom następujące polecenie w oknie wiersza polecenia na poziomie administratora.

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
    -bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > To polecenie jest pojedynczym wierszem tekstu.

## <a name="see-also"></a>Zobacz także

- [Aktywacja TCP](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [Aktywacja usługi MSMQ](../../../../docs/framework/wcf/samples/msmq-activation.md)
- [Aktywowanie elementu NamedPipe](../../../../docs/framework/wcf/samples/namedpipe-activation.md)
- [Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
