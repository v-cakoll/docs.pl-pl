---
title: "Jak wdrożyć istniejących aplikacji .NET w usłudze Azure App Service"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Jak wdrożyć istniejących aplikacji .NET w usłudze Azure App Service"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: aefcd79574cbbf6b3759bfa6cc0f9e46a58244ce
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-deploy-existing-net-apps-to-azure-app-service"></a><span data-ttu-id="32db4-103">Jak wdrożyć istniejących aplikacji .NET w usłudze Azure App Service</span><span class="sxs-lookup"><span data-stu-id="32db4-103">How to deploy existing .NET apps to Azure App Service</span></span> 

<span data-ttu-id="32db4-104">Funkcja Web Apps w usłudze Azure App Service jest w pełni zarządzana platforma obliczeniowa zoptymalizowana pod kątem obsługi aplikacji sieci web i witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="32db4-104">The Web Apps feature of Azure App Service is a fully managed compute platform that is optimized for hosting websites and web apps.</span></span> <span data-ttu-id="32db4-105">Tej oferty PaaS w Microsoft Azure umożliwia można skupić się na logice biznesowej, podczas gdy platforma Azure jest odpowiedzialna infrastruktury do uruchamiania i skalowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="32db4-105">This PaaS offering in Microsoft Azure lets you focus on your business logic, while Azure takes care of the infrastructure to run and scale your apps.</span></span>

## <a name="validate-sites-and-migrate-to-app-service-with-azure-app-service-migration-assistant"></a><span data-ttu-id="32db4-106">Sprawdź poprawność witryn i migracji do usługi App Service przy użyciu Asystenta migracji usługi aplikacji Azure</span><span class="sxs-lookup"><span data-stu-id="32db4-106">Validate sites and migrate to App Service with Azure App Service Migration Assistant</span></span>

<span data-ttu-id="32db4-107">Podczas tworzenia nowej aplikacji w programie Visual Studio, zwykle przenoszenie aplikacji do usługi App Service jest prosta.</span><span class="sxs-lookup"><span data-stu-id="32db4-107">When you create a new application in Visual Studio, moving the app to App Service usually is straightforward.</span></span> <span data-ttu-id="32db4-108">Jednak jeśli planujesz migrację istniejącej aplikacji do usługi App Service, należy najpierw ocenić, czy zależności wszystkich aplikacji są zgodne z usługi aplikacji.</span><span class="sxs-lookup"><span data-stu-id="32db4-108">However, if you are planning to migrate an existing application to App Service, first you need to evaluate whether all your application's dependencies are compatible with App Service.</span></span> <span data-ttu-id="32db4-109">W tym zależności, takich jak system operacyjny serwera i oprogramowanie innych firm jest zainstalowany na serwerze.</span><span class="sxs-lookup"><span data-stu-id="32db4-109">This includes dependencies like server OS and any third-party software that's installed on the server.</span></span>

<span data-ttu-id="32db4-110">Można użyć [Asystenta migracji usługi aplikacji Azure](https://www.migratetoazure.net/) do analizowania witryn i następnie ich migracja z systemu Windows i Linux serwerów sieci web do usługi App Service.</span><span class="sxs-lookup"><span data-stu-id="32db4-110">You can use [Azure App Service Migration Assistant](https://www.migratetoazure.net/) to analyze sites and then migrate them from Windows and Linux web servers to App Service.</span></span> <span data-ttu-id="32db4-111">W ramach migracji narzędzie tworzy aplikacje sieci web i baz danych na platformie Azure w razie potrzeby publikuje zawartości i publikuje bazy danych.</span><span class="sxs-lookup"><span data-stu-id="32db4-111">As part of the migration, the tool creates web apps and databases on Azure as needed, publishes content, and publishes your database.</span></span>

<span data-ttu-id="32db4-112">Azure App Service Asystenta migracji obsługuje migrację z usług IIS w systemie Windows Server do chmury.</span><span class="sxs-lookup"><span data-stu-id="32db4-112">Azure App Service Migration Assistant supports migrating from IIS running on Windows Server to the cloud.</span></span> <span data-ttu-id="32db4-113">Usługi aplikacji obsługuje system Windows Server 2003 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="32db4-113">App Service supports Windows Server 2003 and later versions.</span></span>

> ![https://www.migratetoazure.net/Images/ImageCanvas.png](./media/image5.png)
>
> <span data-ttu-id="32db4-115">**Rysunek 4 – 5.**</span><span class="sxs-lookup"><span data-stu-id="32db4-115">**Figure 4-5.**</span></span> <span data-ttu-id="32db4-116">Przy użyciu Asystenta migracji usługi aplikacji Azure</span><span class="sxs-lookup"><span data-stu-id="32db4-116">Using Azure App Service Migration Assistant</span></span>

<span data-ttu-id="32db4-117">Aplikacja usługi migracji Asystent jest narzędziem do witryny sieci Web są przenoszone z serwerów sieci web w chmurze platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="32db4-117">App Service Migration Assistant is a tool that moves your websites from your web servers to the Azure cloud.</span></span>

<span data-ttu-id="32db4-118">Po przeprowadzeniu migracji witryny sieci Web do usług aplikacji, witryna zawiera wszystko, co jest potrzebne do uruchomienia bezpiecznie i wydajne.</span><span class="sxs-lookup"><span data-stu-id="32db4-118">After a website is migrated to App Service, the site has everything it needs to run safely and efficiently.</span></span> <span data-ttu-id="32db4-119">Lokacje ustawiania i automatyczne uruchamianie w usłudze PaaS w chmurze Azure (usługa aplikacji).</span><span class="sxs-lookup"><span data-stu-id="32db4-119">Sites are set up and run automatically in the Azure cloud PaaS service (App Service).</span></span>

<span data-ttu-id="32db4-120">Narzędzie migracji usługi aplikacji może analiza witryny sieci Web i raport dotyczący ich zgodność z narzędziami do przechodzenia do usługi App Service.</span><span class="sxs-lookup"><span data-stu-id="32db4-120">The App Service migration tool can analyze your websites and report on their compatibility for moving to App Service.</span></span> <span data-ttu-id="32db4-121">W przypadku modyfikowania analizy, możesz pozwolić aplikacji usługi Asystenta migracji migracji zawartości, danych i ustawień dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="32db4-121">If you're happy with the analysis, you can let App Service Migration Assistant migrate content, data, and settings for you.</span></span> <span data-ttu-id="32db4-122">Jeśli lokacja nie jest jeszcze zgodne, narzędzie do migracji informuje, należy dostosować do własnych preferencji.</span><span class="sxs-lookup"><span data-stu-id="32db4-122">If a site is not quite compatible, the migration tool tells you what you need to adjust to make it work.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="32db4-123">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="32db4-123">Additional resources</span></span>

- <span data-ttu-id="32db4-124">**Asystent migracji usługi aplikacji Azure**</span><span class="sxs-lookup"><span data-stu-id="32db4-124">**Azure App Service Migration Assistant**</span></span>

    [<span data-ttu-id="32db4-125">https://www.migratetoazure.net/</span><span class="sxs-lookup"><span data-stu-id="32db4-125">https://www.migratetoazure.net/</span></span>](https://www.migratetoazure.net/)

>[!div class="step-by-step"]
<span data-ttu-id="32db4-126">[Poprzednie](what-about-cloud-optimized-applications.md)
[dalej](deploy-existing-net-apps-as-windows-containers.md)</span><span class="sxs-lookup"><span data-stu-id="32db4-126">[Previous](what-about-cloud-optimized-applications.md)
[Next](deploy-existing-net-apps-as-windows-containers.md)</span></span>
