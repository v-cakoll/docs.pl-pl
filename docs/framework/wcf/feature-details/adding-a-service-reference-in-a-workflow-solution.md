---
title: Dodawanie odwołania do usługi w rozwiązaniu usprawniającym przepływ pracy
ms.date: 03/30/2017
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
ms.openlocfilehash: 7197ae991207efd60ea398794c7c23f427f6b0cc
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964215"
---
# <a name="adding-a-service-reference-in-a-workflow-solution"></a>Dodawanie odwołania do usługi w rozwiązaniu usprawniającym przepływ pracy

Dodanie odwołania do usługi w aplikacji przepływu pracy działa nieco inaczej niż zwykła aplikacja WCF. Po wybraniu opcji **dodaj > odwołanie do usługi** i określ adres URL usługi, metadane są pobierane i generowane są działania niestandardowe, które umożliwiają wywołanie usługi WCF lub usługi przepływu pracy WCF, do której dodano odwołanie. Po dodaniu odwołania do usługi Skompiluj ponownie rozwiązanie, aby zostały skompilowane wygenerowane działania. Zostaną one wyświetlone w przyborniku projektanta przepływu pracy. Należy jednak pamiętać, że ta wartość będzie działała tylko wtedy, gdy dodajesz odwołanie do usługi w ramach rozwiązania przepływu pracy. Poniższe Rzutowanie w sieci Web pokazuje, jak dodać odwołanie do usługi w innych typach projektów: [Wywoływanie usługi WCF z przepływu pracy w projekcie sieci Web](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow).

Dodanie co najmniej dwóch odwołań do usług, które zawierają tę samą nazwę operacji, spowoduje wystąpienie problemu. Wygenerowane działania będą wywoływały tylko pierwszą operację usługi. Aby obejść ten problem, Zmień nazwę operacji usługi, aby były różne, lub Zmień nazwę konfiguracji punktu końcowego w ramach każdego wygenerowanego działania.

## <a name="see-also"></a>Zobacz także

- [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Wywoływanie usługi WCF z przepływu pracy w projekcie sieci Web](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
