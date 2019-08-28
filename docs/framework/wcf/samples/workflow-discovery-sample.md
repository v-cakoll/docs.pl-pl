---
title: Odnajdywanie przepływu pracy — przykład
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: 56437607d6e940b59698641ad3305c525d8f7095
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045395"
---
# <a name="workflow-discovery-sample"></a>Odnajdywanie przepływu pracy — przykład
Ten przykład pokazuje, jak umożliwić odnajdywanie usługi przepływu pracy oraz sposób tworzenia niestandardowego działania kodu, które wyszukuje określoną usługę.  
  
## <a name="demonstrates"></a>Demonstracje  
 Odnajdywanie — wyszukiwanie działań i przepływów pracy  
  
## <a name="discussion"></a>Dyskusji  
 W pierwszej części przykładu usługa przepływu pracy jest wykrywalna przy użyciu konfiguracji. Konfiguracji można także użyć do odpowiedniego zastosowania usługi przy użyciu niestandardowych metadanych (takich jak zakresy). Na kliencie przykład używa niestandardowego działania kodu, które używa odnajdywania w celu wyszukania usługi zgodnej z konkretną umową. Działanie Code generuje identyfikator URI, który jest później używany przez działanie wysyłania.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Ten przykład korzysta z punktów końcowych HTTP, które muszą mieć odpowiednie listy ACL adresów URL do uruchomienia (zobacz [Konfigurowanie protokołu HTTP i https](https://go.microsoft.com/fwlink/?LinkId=70353) , aby uzyskać szczegółowe informacje). Wykonanie następującego polecenia w wierszu polecenia z podwyższonym poziomem uprawnień powinno spowodować dodanie odpowiednich list kontroli dostępu. Zastąp domenę i nazwę użytkownika dla następujących argumentów, jeśli powłoka nie zrozumie formatu zmiennej.  
  
     **netsh http Add urlacl URL =http://+:8000/ użytkownik =% domena%\\ % username%**  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
