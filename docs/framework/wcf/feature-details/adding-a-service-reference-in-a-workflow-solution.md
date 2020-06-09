---
title: Dodawanie odwołania do usługi w rozwiązaniu usprawniającym przepływ pracy
ms.date: 03/30/2017
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
ms.openlocfilehash: 577026249e00b528cf5c6e7ccd9527e02cb22a28
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597673"
---
# <a name="add-a-service-reference-in-a-workflow-solution"></a>Dodawanie odwołania do usługi w rozwiązaniu przepływu pracy

Dodanie odwołania do usługi w aplikacji przepływu pracy działa nieco inaczej niż zwykła aplikacja WCF. Po wybraniu opcji **Dodaj**  >  **odwołanie do usługi** i określ adres URL usługi, metadane są pobierane i generowane są działania niestandardowe, które umożliwiają wywołanie tej usługi WCF lub usługi przepływu pracy WCF. Po dodaniu odwołania do usługi Skompiluj ponownie rozwiązanie, aby zostały skompilowane wygenerowane działania. Zostaną one wyświetlone w przyborniku projektanta przepływu pracy. Ta wartość będzie działała tylko w przypadku dodawania odwołania do usługi w ramach rozwiązania przepływu pracy. Poniższe Rzutowanie w sieci Web pokazuje, jak dodać odwołanie do usługi w innych typach projektów: [Wywoływanie usługi WCF z przepływu pracy w projekcie sieci Web](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow).

Dodanie co najmniej dwóch odwołań do usług, które zawierają tę samą nazwę operacji, spowoduje wystąpienie problemu. Wygenerowane działania będą wywoływały tylko pierwszą operację usługi. Aby obejść ten problem, Zmień nazwy operacji usługi tak, aby były różne, lub Zmień nazwę konfiguracji punktu końcowego w ramach każdego wygenerowanego działania.

## <a name="see-also"></a>Zobacz też

- [Usługi przepływu pracy](workflow-services.md)
- [Wywoływanie usługi WCF z przepływu pracy w projekcie sieci Web](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
