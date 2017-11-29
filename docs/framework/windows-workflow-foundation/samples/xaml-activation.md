---
title: Aktywacja XAML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 486760e2-bb10-4ed5-8c02-fe7472498d2d
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f513b10c84de968d5a18b800037b512aad90399e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="xaml-activation"></a>Aktywacja XAML
W tym przykładzie pokazano, jak udostępniać deklaracyjnego przepływu pracy w programie IIS. Próbka jest podstawowy przepływ pracy o nazwie `EchoService` mający jednej operacji.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do (stronę pobierania), aby pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLActivation`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Otwórz rozwiązanie XAMLActivation.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj rozwiązanie, naciskając klawisz **F5**.  
  
3.  Uruchom WcfTestClient.exe. W wierszu polecenia wpisz następujące:  
  
    1.  CD %SystemDrive%\Program Files\Microsoft 10.0\Common7\IDE programu Visual Studio  
  
    2.  Uruchom WcfTestClient.exe.  
  
4.  Ustaw adres usługi na WcfTestClient.exe, naciskając klawisze CTRL + SHIFT + A i ustawienie adresu usługi http://localhost:56133/Service.xamlx.  
  
5.  Operacja echo testować usługę.  
  
6.  Wdrażanie usługi w usługach IIS przy użyciu DeployToIIS.Bat w wierszu polecenia z uprawnieniami administratora.  
  
7.  Zaktualizuj adres usługi na komputerze klienckim http://localhost/XAMLActivation/Service.xamlx, a następnie testować usługę ponownie, używając WcfTestClient.exe.
