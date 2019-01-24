---
title: Dodawanie odwołania do usługi w rozwiązaniu usprawniającym przepływ pracy
ms.date: 03/30/2017
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
ms.openlocfilehash: 8f1fa4604f1a1873c7063ec3c9dccf08bd0aa0ee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549044"
---
# <a name="adding-a-service-reference-in-a-workflow-solution"></a>Dodawanie odwołania do usługi w rozwiązaniu usprawniającym przepływ pracy

Dodawanie odwołania do usługi w aplikacji przepływu pracy działa nieco inaczej niż regularne aplikacji WCF. Po wybraniu **Dodaj > odwołanie do usługi** i określ adres URL usługi metadanych jest pobierana i działania niestandardowe są generowane, które umożliwią wywoływanie usługi WCF lub dodać odwołanie do usługi przepływu pracy WCF. Po dodaniu odwołania do usługi, należy ponownie skompiluj rozwiązanie, dzięki czemu wygenerowane działania są tworzone. Następnie pojawią się one w przyborniku projektanta przepływu pracy. Należy jednak pamiętać, że ta opcja zadziała tylko w przypadku dodawania odwołania do usługi w rozwiązaniu usprawniającym przepływ pracy. Następujące rzutowania w sieci web pokazuje, jak dodać odwołanie do usługi w innych rodzajów projektów: [Wywołanie usługi WCF z przepływu pracy w projekcie sieci Web](https://go.microsoft.com/fwlink/?LinkId=207725).

Dodawanie dwóch lub więcej odwołań do usług do usług, które zawierać taką samą nazwę operacji spowoduje, że problem. Wygenerowane działania będzie wywoływać tylko pierwszej operacji usługi. Aby obejść ten problem zmiany nazwy operacji usługi więc one różnią się lub zmień nazwę konfiguracji punktu końcowego w ramach każdego wygenerowane działania.

## <a name="see-also"></a>Zobacz także

- [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Wywołanie usługi WCF z przepływu pracy w projekcie sieci Web](https://go.microsoft.com/fwlink/?LinkId=207725)
