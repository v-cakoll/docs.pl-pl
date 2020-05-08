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
# <a name="cloud-native-application-bundles"></a><span data-ttu-id="cb285-103">Pakiety aplikacji natywnych dla chmury</span><span class="sxs-lookup"><span data-stu-id="cb285-103">Cloud Native Application Bundles</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="cb285-104">Kluczowa Właściwość aplikacji natywnych w chmurze polega na tym, że wykorzystują właściwości chmury w celu przyspieszenia tworzenia oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="cb285-104">A key property of cloud-native applications is that they leverage the properties of the cloud to speed up development.</span></span> <span data-ttu-id="cb285-105">Często oznacza to, że pełna aplikacja korzysta z różnych rodzajów technologii.</span><span class="sxs-lookup"><span data-stu-id="cb285-105">This often means that a full application uses different kinds of technologies.</span></span> <span data-ttu-id="cb285-106">Aplikacje mogą być dostarczane w kontenerach platformy Docker, niektóre usługi mogą korzystać z Azure Functions, podczas gdy inne części mogą być uruchamiane bezpośrednio na maszynach wirtualnych przyznanych na dużych serwerach metalowych z przyspieszeniem sprzętowym procesora GPU.</span><span class="sxs-lookup"><span data-stu-id="cb285-106">Applications may be shipped in Docker containers, some services may use Azure Functions while other parts may run directly on virtual machines allocated on large metal servers with hardware GPU acceleration.</span></span> <span data-ttu-id="cb285-107">Żadne dwie aplikacje natywne w chmurze nie są takie same, dlatego trudno jest zapewnić jeden mechanizm do wysyłania.</span><span class="sxs-lookup"><span data-stu-id="cb285-107">No two cloud-native applications are the same, so it's been difficult to provide a single mechanism for shipping them.</span></span>

<span data-ttu-id="cb285-108">Kontenery platformy Docker mogą działać na Kubernetes za pomocą wykresu Helm do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="cb285-108">The Docker containers may run on Kubernetes using a Helm Chart for deployment.</span></span> <span data-ttu-id="cb285-109">Azure Functions można alokować przy użyciu szablonów Terraform.</span><span class="sxs-lookup"><span data-stu-id="cb285-109">The Azure Functions may be allocated using Terraform templates.</span></span> <span data-ttu-id="cb285-110">Na koniec maszyny wirtualne mogą zostać przydzieloną przy użyciu Terraform, ale zostały utworzone przy użyciu rozwiązania ansible.</span><span class="sxs-lookup"><span data-stu-id="cb285-110">Finally, the virtual machines may be allocated using Terraform but built out using Ansible.</span></span> <span data-ttu-id="cb285-111">Jest to cały problem z technologiami i nie ma możliwości spakowania ich ze sobą w rozsądny pakiet.</span><span class="sxs-lookup"><span data-stu-id="cb285-111">This is a whole mess of technologies and there has been no way to package them all together into a reasonable package.</span></span> <span data-ttu-id="cb285-112">Do tej pory.</span><span class="sxs-lookup"><span data-stu-id="cb285-112">Until now.</span></span>

<span data-ttu-id="cb285-113">Zbiory natywnych aplikacji w chmurze (CNABs) to wspólne wysiłki dla wielu firm korzystających z społeczności, takich jak Microsoft, Docker i HashiCorp, aby opracować specyfikację do spakowania aplikacji rozproszonych.</span><span class="sxs-lookup"><span data-stu-id="cb285-113">Cloud Native Application Bundles (CNABs) are a joint effort of a number of community-minded companies such as Microsoft, Docker, and HashiCorp to develop a specification to package distributed applications.</span></span>

<span data-ttu-id="cb285-114">Wysiłek został ogłoszony w grudniu 2018, dlatego nadal istnieje sprawiedliwa część pracy, która pozwala na uwidocznienie wysiłku dla większej liczby użytkowników.</span><span class="sxs-lookup"><span data-stu-id="cb285-114">The effort was announced in December of 2018, so there's still a fair bit of work to do to expose the effort to the greater community.</span></span> <span data-ttu-id="cb285-115">Istnieje jednak już [otwarta Specyfikacja](https://github.com/deislabs/cnab-spec) i implementacja odwołania znana jako [Duffle](https://duffle.sh/).</span><span class="sxs-lookup"><span data-stu-id="cb285-115">However, there's already an [open specification](https://github.com/deislabs/cnab-spec) and a reference implementation known as [Duffle](https://duffle.sh/).</span></span> <span data-ttu-id="cb285-116">To narzędzie, które zostało utworzone w programie, stanowi wspólne wysiłki między platformą Docker i firmą Microsoft.</span><span class="sxs-lookup"><span data-stu-id="cb285-116">This tool, which was written in Go, is a joint effort between Docker and Microsoft.</span></span>

<span data-ttu-id="cb285-117">CNABs może zawierać różne rodzaje technologii instalacji.</span><span class="sxs-lookup"><span data-stu-id="cb285-117">The CNABs can contain different kinds of installation technologies.</span></span> <span data-ttu-id="cb285-118">Pozwala to na to, że wykresy Helm, szablony Terraform i rozwiązania ansible elementy PlayBook mogą współistnieć w tym samym pakiecie.</span><span class="sxs-lookup"><span data-stu-id="cb285-118">This allows things like Helm Charts, Terraform templates, and Ansible Playbooks to coexist in the same package.</span></span> <span data-ttu-id="cb285-119">Po skompilowaniu pakiety są samodzielne i przenośne; można je instalować z naklejki USB.</span><span class="sxs-lookup"><span data-stu-id="cb285-119">Once built, the packages are self-contained and portable; they can be installed from a USB stick.</span></span>  <span data-ttu-id="cb285-120">Pakiety są podpisywane kryptograficznie, aby upewnić się, że pochodzą one od strony, której one dotyczą.</span><span class="sxs-lookup"><span data-stu-id="cb285-120">The packages are cryptographically signed to ensure they originate from the party they claim.</span></span>

<span data-ttu-id="cb285-121">Rdzeń CNAB jest plikiem o nazwie `bundle.json`.</span><span class="sxs-lookup"><span data-stu-id="cb285-121">The core of a CNAB is a file called `bundle.json`.</span></span> <span data-ttu-id="cb285-122">Ten plik definiuje zawartość pakietu, Terraform je lub obrazy lub inne elementy.</span><span class="sxs-lookup"><span data-stu-id="cb285-122">This file defines the contents of the bundle, be they Terraform or images or anything else.</span></span> <span data-ttu-id="cb285-123">Rysunek 11-9 definiuje CNAB, który wywołuje część Terraform.</span><span class="sxs-lookup"><span data-stu-id="cb285-123">Figure 11-9 defines a CNAB that invokes some Terraform.</span></span> <span data-ttu-id="cb285-124">Należy jednak zauważyć, że w rzeczywistości definiuje obraz wywołania, który jest używany do wywoływania Terraform.</span><span class="sxs-lookup"><span data-stu-id="cb285-124">Notice, however, that it actually defines an invocation image that is used to invoke the Terraform.</span></span> <span data-ttu-id="cb285-125">W przypadku spakowania plik platformy Docker, który znajduje się w katalogu *cnab* , jest wbudowany w obraz platformy Docker, który zostanie uwzględniony w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="cb285-125">When packaged up, the Docker file that is located in the *cnab* directory is built into a Docker image, which will be included in the bundle.</span></span> <span data-ttu-id="cb285-126">Terraform zainstalowany wewnątrz kontenera Docker w zbiorze oznacza, że użytkownicy nie muszą mieć zainstalowanej Terraform na komputerze, aby można było uruchomić tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="cb285-126">Having Terraform installed inside a Docker container in the bundle means that users don't need to have Terraform installed on their machine to run the bundling.</span></span>

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

<span data-ttu-id="cb285-127">**Rysunek 11-13** . przykładowy plik Terraform</span><span class="sxs-lookup"><span data-stu-id="cb285-127">**Figure 11-13** - An example Terraform file</span></span>

<span data-ttu-id="cb285-128">Definiuje `bundle.json` również zestaw parametrów, które są przesyłane do terraform.</span><span class="sxs-lookup"><span data-stu-id="cb285-128">The `bundle.json` also defines a set of parameters that are passed down into the Terraform.</span></span> <span data-ttu-id="cb285-129">Parametryzacja pakietu umożliwia instalację w różnych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="cb285-129">Parameterization of the bundle allows for installation in a variety of different environments.</span></span>

<span data-ttu-id="cb285-130">Format CNAB jest również elastyczny, dzięki czemu można go używać z dowolną chmurą.</span><span class="sxs-lookup"><span data-stu-id="cb285-130">The CNAB format is also flexible, allowing it to be used against any cloud.</span></span> <span data-ttu-id="cb285-131">Może być nawet używany z rozwiązaniami lokalnymi, takimi jak [OpenStack](https://www.openstack.org/).</span><span class="sxs-lookup"><span data-stu-id="cb285-131">It can even be used against on-premises solutions such as [OpenStack](https://www.openstack.org/).</span></span>

## <a name="devops-decisions"></a><span data-ttu-id="cb285-132">DevOps decyzje</span><span class="sxs-lookup"><span data-stu-id="cb285-132">DevOps Decisions</span></span>

<span data-ttu-id="cb285-133">Istnieje wiele doskonałych narzędzi w przestrzeni DevOps w ciągu kilku dni i jeszcze bardziej fantastyczniee książki i dokumenty dotyczące sukcesu.</span><span class="sxs-lookup"><span data-stu-id="cb285-133">There are so many great tools in the DevOps space these days and even more fantastic books and papers on how to succeed.</span></span> <span data-ttu-id="cb285-134">Ulubiona Książka do rozpoczęcia podróży DevOps jest [projektem w Phoenix](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/), który następuje po przekształceniu fikcyjnej firmy od NoOps do DevOps.</span><span class="sxs-lookup"><span data-stu-id="cb285-134">A favorite book to get started on the DevOps journey is [The Phoenix Project](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/), which follows the transformation of a fictional company from NoOps to DevOps.</span></span> <span data-ttu-id="cb285-135">Jedną z rzeczy jest dla niektórych: DevOps nie jest już "całkiem" w przypadku wdrażania złożonych, natywnych aplikacji w chmurze.</span><span class="sxs-lookup"><span data-stu-id="cb285-135">One thing is for certain: DevOps is no longer a "nice to have" when deploying complex, Cloud Native Applications.</span></span> <span data-ttu-id="cb285-136">Jest to wymagane i powinny być planowane dla i zamierzone na początku każdego projektu.</span><span class="sxs-lookup"><span data-stu-id="cb285-136">It's a requirement and should be planned for and resourced at the start of any project.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="cb285-137">[Poprzedni](infrastructure-as-code.md)
>[Następny](summary.md)</span><span class="sxs-lookup"><span data-stu-id="cb285-137">[Previous](infrastructure-as-code.md)
[Next](summary.md)</span></span>
