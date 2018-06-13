---
title: Aktywacja XAML
ms.date: 03/30/2017
ms.assetid: 486760e2-bb10-4ed5-8c02-fe7472498d2d
ms.openlocfilehash: 8621b0ea7b390c81e76ac7eeedb0b547b44320d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517715"
---
# <a name="xaml-activation"></a>Aktywacja XAML
W tym przykładzie pokazano, jak udostępniać deklaracyjnego przepływu pracy w programie IIS. Próbka jest podstawowy przepływ pracy o nazwie `EchoService` mający jednej operacji.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do (stronę pobierania) można pobrać wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLActivation`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Otwórz rozwiązanie XAMLActivation.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj rozwiązanie, naciskając klawisz **F5**.  
  
3.  Uruchom WcfTestClient.exe. W wierszu polecenia wpisz następujące:  
  
    1.  CD %SystemDrive%\Program Files\Microsoft 10.0\Common7\IDE programu Visual Studio  
  
    2.  Uruchom WcfTestClient.exe.  
  
4.  Ustaw adres usługi na WcfTestClient.exe naciskając klawisz CTRL + SHIFT + A, a ustawienie adresu usługi http://localhost:56133/Service.xamlx.  
  
5.  Operacja echo testować usługę.  
  
6.  Wdrażanie usługi w usługach IIS przy użyciu DeployToIIS.Bat w wierszu polecenia z uprawnieniami administratora.  
  
7.  Zaktualizuj adres usługi w kliencie programu http://localhost/XAMLActivation/Service.xamlx i testować usługę ponownie, używając WcfTestClient.exe.
