---
title: Odnajdywanie przepływu pracy — przykład
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: b3a2d88028f3854746d4e1d2fad80aae4f6be7be
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143489"
---
# <a name="workflow-discovery-sample"></a>Odnajdywanie przepływu pracy — przykład
W tym przykładzie pokazano, jak sprawić, aby usługa przepływu pracy była wykrywalna i jak tworzyć niestandardowe działanie kodu, które wyszukuje określoną usługę.  
  
## <a name="demonstrates"></a>Demonstracje  
 Odnajdowanie Znajdowanie aktywności i użycia przepływu pracy  
  
## <a name="discussion"></a>Dyskusji  
 W pierwszej części próbki usługa przepływu pracy jest wykrywalna przy użyciu konfiguracji. Konfiguracja może również służyć do stosowania usługi odpowiednio z metadanych niestandardowych (takich jak zakresy). Na kliencie przykład używa działania kodu niestandardowego, który używa odnajdywania do wyszukiwania usługi pasującej do określonego kontraktu. Działanie kodu wyprowadza identyfikator URI, który jest później używany przez działanie wysyłania.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. W tym przykładzie użyto punktów końcowych HTTP, które muszą mieć odpowiednie listy ACL URL do uruchomienia (zobacz [Konfigurowanie protokołu HTTP i HTTPS,](../feature-details/configuring-http-and-https.md) aby uzyskać szczegółowe informacje). Wykonywanie następującego polecenia w wierszu polecenia z podwyższonym poziomem uprawnień należy dodać odpowiednie listy ACL. Jeśli powłoka nie rozumie formatu zmiennej, zastąp domenę i nazwę użytkownika następującymi argumentami.  
  
     **netsh http dodaj urlacl url=http://+:8000/ \\użytkownik=%DOMENA% %UserName%**  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
