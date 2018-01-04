---
title: "Dodawanie odwołania do usługi w rozwiązaniu usprawniającym przepływ pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee974ee5a9f4564b0e44256bc4773f9898d89fc6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="adding-a-service-reference-in-a-workflow-solution"></a>Dodawanie odwołania do usługi w rozwiązaniu usprawniającym przepływ pracy
Dodawanie odwołania do usługi w aplikacji przepływ pracy działa w sposób nieco inaczej niż regularne aplikacji WCF. Po wybraniu Dodaj odwołanie do usługi i podaj adres URL do usługi metadanych jest pobierany i działań niestandardowych są generowane, które umożliwią wywoływanie usługi WCF lub usługi przepływu pracy WCF dodać odwołanie do. Po dodaniu odwołania do usługi, należy ponownie skompiluj rozwiązanie, więc wygenerowanego działania są tworzone. Pojawi się one w przyborniku projektanta przepływów pracy. Należy jednak pamiętać, że działa tylko w przypadku dodawania odwołania do usługi w ramach rozwiązania przepływu pracy. Następujące rzutowania web przedstawiono sposób dodawania odwołania do usługi w innych typów projektów: [wywoływania usługi WCF z przepływu pracy w projekcie sieci Web](http://go.microsoft.com/fwlink/?LinkId=207725).  
  
 Dodawanie dwóch lub więcej odwołań do usługi do usług, które zawierają taką samą nazwę operacji spowoduje, że problem. Wygenerowany działania wywoła tylko pierwszej operacji usługi. Aby obejść ten problem zmiany nazwy operacji usługi różnią się od siebie lub zmień nazwę konfiguracji punktu końcowego w każdym działaniu wygenerowanego.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Instrukcje: tworzenie usługi przepływu pracy wywołującej inną usługę przepływu pracy](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-that-calls-another-workflow-service.md)  
 [Wywołanie usługi WCF z przepływu pracy w projekcie sieci Web](http://go.microsoft.com/fwlink/?LinkId=207725)
