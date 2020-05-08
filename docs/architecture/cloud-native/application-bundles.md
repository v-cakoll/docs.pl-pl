---
title: Pakiety aplikacji natywnych dla chmury
description: Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure | Zbiory natywnych aplikacji w chmurze
ms.date: 06/30/2019
ms.openlocfilehash: 6f85ca14ff4d17f9c7a90a9ace51a1448b89fcb3
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895681"
---
# <a name="cloud-native-application-bundles"></a>Pakiety aplikacji natywnych dla chmury

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Kluczowa Właściwość aplikacji natywnych w chmurze polega na tym, że wykorzystują właściwości chmury w celu przyspieszenia tworzenia oprogramowania. Często oznacza to, że pełna aplikacja korzysta z różnych rodzajów technologii. Aplikacje mogą być dostarczane w kontenerach platformy Docker, niektóre usługi mogą korzystać z Azure Functions, podczas gdy inne części mogą być uruchamiane bezpośrednio na maszynach wirtualnych przyznanych na dużych serwerach metalowych z przyspieszeniem sprzętowym procesora GPU. Żadne dwie aplikacje natywne w chmurze nie są takie same, dlatego trudno jest zapewnić jeden mechanizm do wysyłania.

Kontenery platformy Docker mogą działać na Kubernetes za pomocą wykresu Helm do wdrożenia. Azure Functions można alokować przy użyciu szablonów Terraform. Na koniec maszyny wirtualne mogą zostać przydzieloną przy użyciu Terraform, ale zostały utworzone przy użyciu rozwiązania ansible. Jest to cały problem z technologiami i nie ma możliwości spakowania ich ze sobą w rozsądny pakiet. Do tej pory.

Zbiory natywnych aplikacji w chmurze (CNABs) to wspólne wysiłki dla wielu firm korzystających z społeczności, takich jak Microsoft, Docker i HashiCorp, aby opracować specyfikację do spakowania aplikacji rozproszonych.

Wysiłek został ogłoszony w grudniu 2018, dlatego nadal istnieje sprawiedliwa część pracy, która pozwala na uwidocznienie wysiłku dla większej liczby użytkowników. Istnieje jednak już [otwarta Specyfikacja](https://github.com/deislabs/cnab-spec) i implementacja odwołania znana jako [Duffle](https://duffle.sh/). To narzędzie, które zostało utworzone w programie, stanowi wspólne wysiłki między platformą Docker i firmą Microsoft.

CNABs może zawierać różne rodzaje technologii instalacji. Pozwala to na to, że wykresy Helm, szablony Terraform i rozwiązania ansible elementy PlayBook mogą współistnieć w tym samym pakiecie. Po skompilowaniu pakiety są samodzielne i przenośne; można je instalować z naklejki USB.  Pakiety są podpisywane kryptograficznie, aby upewnić się, że pochodzą one od strony, której one dotyczą.

Rdzeń CNAB jest plikiem o nazwie `bundle.json`. Ten plik definiuje zawartość pakietu, Terraform je lub obrazy lub inne elementy. Rysunek 11-9 definiuje CNAB, który wywołuje część Terraform. Należy jednak zauważyć, że w rzeczywistości definiuje obraz wywołania, który jest używany do wywoływania Terraform. W przypadku spakowania plik platformy Docker, który znajduje się w katalogu *cnab* , jest wbudowany w obraz platformy Docker, który zostanie uwzględniony w pakiecie. Terraform zainstalowany wewnątrz kontenera Docker w zbiorze oznacza, że użytkownicy nie muszą mieć zainstalowanej Terraform na komputerze, aby można było uruchomić tę funkcję.

```json
{
    "name": "terraform",
    "version": "0.1.0",
    "schemaVersion": "v1.0.0-WD",
    "parameters": {
        "backend": {
            "type": "boolean",
            "defaultValue": false,
            "destination": {
                "env": "TF_VAR_backend"
            }
        }
    },
    "invocationImages": [
        {
        "imageType": "docker",
        "image": "cnab/terraform:latest"
        }
    ],
    "credentials": {
        "tenant_id": {
            "env": "TF_VAR_tenant_id"
        },
        "client_id": {
            "env": "TF_VAR_client_id"
        },
        "client_secret": {
            "env": "TF_VAR_client_secret"
        },
        "subscription_id": {
            "env": "TF_VAR_subscription_id"
        },
        "ssh_authorized_key": {
            "env": "TF_VAR_ssh_authorized_key"
        }
    },
    "actions": {
        "status": {
            "modifies": true
        }
    }
}
```

**Rysunek 11-13** . przykładowy plik Terraform

Definiuje `bundle.json` również zestaw parametrów, które są przesyłane do terraform. Parametryzacja pakietu umożliwia instalację w różnych środowiskach.

Format CNAB jest również elastyczny, dzięki czemu można go używać z dowolną chmurą. Może być nawet używany z rozwiązaniami lokalnymi, takimi jak [OpenStack](https://www.openstack.org/).

## <a name="devops-decisions"></a>DevOps decyzje

Istnieje wiele doskonałych narzędzi w przestrzeni DevOps w ciągu kilku dni i jeszcze bardziej fantastyczniee książki i dokumenty dotyczące sukcesu. Ulubiona Książka do rozpoczęcia podróży DevOps jest [projektem w Phoenix](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/), który następuje po przekształceniu fikcyjnej firmy od NoOps do DevOps. Jedną z rzeczy jest dla niektórych: DevOps nie jest już "całkiem" w przypadku wdrażania złożonych, natywnych aplikacji w chmurze. Jest to wymagane i powinny być planowane dla i zamierzone na początku każdego projektu.

>[!div class="step-by-step"]
>[Poprzedni](infrastructure-as-code.md)
>[Następny](summary.md)
