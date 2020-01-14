---
title: Używanie języka F# na platformie Azure
description: Przewodnik dotyczący korzystania z usług platformy Azure z usługąF#
author: sylvanc
ms.date: 09/22/2016
ms.openlocfilehash: 6cf2951092074a7fab6707c8ed26bda125ea00b0
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935537"
---
# <a name="using-f-on-azure"></a>Używanie języka F# na platformie Azure

F#to doskonały język programowania w chmurze i jest często używany do pisania aplikacji sieci Web, usług w chmurze, mikrousług hostowanych w chmurze oraz do skalowalnego przetwarzania danych.

W poniższych sekcjach znajdują się zasoby dotyczące korzystania z różnych usług platformy Azure z programem F#.

> [!NOTE]
> Jeśli określona usługa platformy Azure nie znajduje się w tym zestawie dokumentacji, zapoznaj się z dokumentacją Azure Functions lub .NET dla tej usługi. Niektóre usługi platformy Azure są niezależne od języka i nie wymagają dokumentacji specyficznej dla języka i nie są wyświetlane w tym miejscu.

## <a name="using-azure-virtual-machines-with-f"></a>Korzystanie z usługi Azure Virtual Machines z usługą F\#

Platforma Azure obsługuje szeroką gamę konfiguracji maszyn wirtualnych, zobacz [Linux i Azure Virtual Machines](https://azure.microsoft.com/services/virtual-machines/).

Aby zainstalować F# program na maszynie wirtualnej w celu wykonania, kompilacji i/lub skryptów, zobacz [ F# używanie systemu Linux](https://fsharp.org/use/linux) i [Używanie F# go w systemie Windows](https://fsharp.org/use/windows).

## <a name="using-azure-functions-with-f"></a>Używanie Azure Functions z\# F

[Azure Functions](https://azure.microsoft.com/services/functions/) to rozwiązanie umożliwiające łatwe uruchamianie małych fragmentów kodu lub "Functions" w chmurze. Możesz napisać tylko kod rozwiązujący aktualny problem, nie martwiąc się o całą aplikację ani infrastrukturę do jej uruchomienia. Twoje funkcje są połączone ze zdarzeniami w usłudze Azure Storage i innymi zasobami obsługiwanymi w chmurze. Przepływy danych do F# funkcji za pośrednictwem argumentów funkcji. Możesz użyć wybranego języka programistycznego, aby ufać platformie Azure w miarę potrzeb.

Azure Functions obsługa F# jako język pierwszej klasy z wydajnym, reaktywnym, skalowalnym wykonaniem F# kodu. Informacje dotyczące korzystania F# z programu z usługą Azure Functions można znaleźć w dokumentacji dotyczącej [deweloperów Azure Functions F# ](/azure/azure-functions/functions-reference-fsharp) .

Inne zasoby do używania Azure Functions i F#:

* [Skalowanie w F# górę Azure Functions przy użyciu Suave](https://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/)
* [Jak utworzyć funkcję platformy Azure w programieF#](https://mnie.github.io/2016-09-08-AzureFunctions/)
* [Korzystanie z dostawcy typu platformy Azure z Azure Functions](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a>Korzystanie z usługi Azure Storage za pomocą języka F\#

Usługa Azure Storage to podstawowa warstwa usług magazynu dla nowoczesnych aplikacji, która polega na trwałości, dostępności i skalowalności, aby zaspokoić potrzeby klientów. F#programy mogą komunikować się bezpośrednio z usługami Azure Storage przy użyciu technik opisanych w poniższych artykułach.

* [Rozpoczynanie pracy z usługą Azure Blob Storage przy użyciu języka F#](blob-storage.md)
* [Rozpoczynanie pracy z usługą Azure File Storage przy użyciu języka F#](file-storage.md)
* [Rozpoczynanie pracy z usługą Azure Queue Storage przy użyciu języka F#](queue-storage.md)
* [Rozpoczynanie pracy z usługą Azure Table Storage przy użyciu języka F#](table-storage.md)

Usługi Azure Storage można także używać w połączeniu z Azure Functions za pomocą konfiguracji deklaracyjnej, a nie jawnych wywołań interfejsu API. Zobacz [Azure Functions wyzwalacze i powiązania dotyczące usługi Azure Storage, w](/azure/azure-functions/functions-bindings-storage) tym F# przykłady.

## <a name="using-azure-app-service-with-f"></a>Używanie Azure App Service z\# F

[Azure App Service](https://azure.microsoft.com/services/app-service/) to platforma w chmurze, która umożliwia tworzenie zaawansowanych aplikacji sieci Web i mobilnych, które łączą się z danymi w dowolnym miejscu, w chmurze lub lokalnie.

* [F#Przykład interfejsu API sieci Web platformy Azure](https://github.com/fsprojects/azure-webapi-example)
* [Hosting F# w aplikacji sieci Web na platformie Azure](https://github.com/isaacabraham/fsharp-demonstrator)

## <a name="using-apache-spark-with-f-with-azure-hdinsight"></a>Używanie Apache Spark z F# usługą Azure HDInsight

[Apache Spark dla usługi Azure HDInsight](https://azure.microsoft.com/services/hdinsight/apache-spark/) to platforma przetwarzania Open Source, która uruchamia aplikacje do analizy danych na dużą skalę. Platforma Azure sprawia, że wdrożenie Apache Spark łatwe i ekonomiczne. Tworzenie aplikacji platformy Spark przy F# użyciu programu [Mobius](https://github.com/Microsoft/Mobius), interfejsu API platformy .NET dla platformy Spark.

* [Implementowanie aplikacji platformy F# Spark w programie przy użyciu Mobius](https://github.com/Microsoft/Mobius/blob/master/notes/spark-fsharp-mobius.md)
* [Przykładowe F# aplikacje Spark używające Mobius](https://github.com/Microsoft/Mobius/tree/master/examples/fsharp)

## <a name="using-azure-cosmos-db-with-f"></a>Używanie Azure Cosmos DB z\# F

[Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db) to usługa NoSQL dla wysoko dostępnych, globalnie rozproszonych aplikacji.

Azure Cosmos DB można używać F# na dwa sposoby:

1. Za pomocą tworzenia F# Azure Functions, które reagują na lub powodują zmiany w kolekcjach Azure Cosmos DB. Zobacz [Azure Cosmos DB powiązania Azure Functions](/azure/azure-functions/functions-bindings-cosmosdb)lub
2. Za pomocą [interfejsu API programu Azure Cosmos DB .NET SDK](/azure/cosmos-db/sql-api-sdk-dotnet). Powiązane przykłady znajdują się C#w temacie.

## <a name="using-azure-event-hubs-with-f"></a>Korzystanie z usługi Azure Event Hubs z usługą F\#

[Usługa Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/) zapewnia pozyskiwanie danych telemetrycznych z witryn sieci Web, aplikacji i urządzeń w skali chmury.

Usługi Azure Event Hubs można używać F# na dwa sposoby:

1. Za pomocą tworzenia F# Azure Functions, które są wyzwalane przez zdarzenia. Zobacz [wyzwalacze usługi Azure Functions dla Event Hubs](/azure/azure-functions/functions-bindings-event-hubs)lub
2. Za pomocą [zestawu .NET SDK dla platformy Azure](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted). Zwróć uwagę na to, C#że przykłady znajdują się w temacie.

## <a name="using-azure-notification-hubs-with-f"></a>Korzystanie z usługi Azure Notification Hubs z usługą F\#

[Platforma Azure Notification Hubs](/azure/notification-hubs/) to wieloplatformowa, skalowana w poziomie infrastruktura wypychania, która umożliwia wysyłanie powiadomień wypychanych do urządzeń przenośnych z dowolnego zaplecza (w chmurze lub lokalnie) do dowolnej platformy mobilnej.

Usługi Azure Notification Hubs można używać F# na dwa sposoby:

1. Za pomocą tworzenia F# Azure Functions, które wysyłają wyniki do centrum powiadomień. Zobacz [wyzwalacze wyjściowe funkcji platformy Azure dla Notification Hubs](/azure/azure-functions/functions-bindings-notification-hubs)lub
2. Za pomocą [zestawu .NET SDK dla platformy Azure](https://docs.microsoft.com/archive/blogs/azuremobile/push-notifications-using-notification-hub-and-net-backend). Zwróć uwagę na to, C#że przykłady znajdują się w temacie.

## <a name="implementing-webhooks-on-azure-with-f"></a>Implementowanie elementów webhook na platformie Azure przy użyciu języka F\#

Element [webhook](https://en.wikipedia.org/wiki/Webhook) jest wywołaniem zwrotnym wyzwalanym za pośrednictwem żądania sieci Web. Elementy webhook są używane przez witryny, takie jak GitHub, do zdarzeń związanych z sygnałem.

Elementy webhook można zaimplementować w F# systemach i hostowanych na platformie Azure za pomocą [funkcji F# platformy Azure w ramach powiązania elementu webhook](/azure/azure-functions/functions-bindings-http-webhook).

## <a name="using-webjobs-with-f"></a>Używanie zadań WebJob w języku F\#

[Zadania WebJob](/azure/app-service-web/web-sites-create-web-jobs) to programy, które można uruchamiać w aplikacji internetowej App Service na trzy sposoby: na żądanie, w sposób ciągły lub zgodnie z harmonogramem.

[Przykład F# Zadania WebJob](https://github.com/jrr/webjob-project-examples)

## <a name="implementing-timers-on-azure-with-f"></a>Implementowanie czasomierzy na platformie Azure przy użyciu języka F\#

Czasomierz wyzwala funkcję wywołań na podstawie harmonogramu, jednorazowo lub cyklicznie.

Czasomierze można zaimplementować w F# systemach i hostowanych na platformie Azure za pomocą [funkcji platformy Azure w F# programie z wyzwalaczem czasomierza](/azure/azure-functions/functions-bindings-timer).

## <a name="deploying-and-managing-azure-resources-with-f-scripts"></a>Wdrażanie zasobów platformy Azure i zarządzanie F# nimi za pomocą skryptów

Maszyny wirtualne platformy Azure mogą być wdrażane programowo F# i zarządzane ze skryptów przy użyciu pakietów Microsoft. Azure. Management i interfejsów API. Na przykład zobacz [wprowadzenie do bibliotek zarządzania dla platformy .NET](https://msdn.microsoft.com/library/dn722415.aspx) i korzystanie z [Azure Resource Manager](/azure/azure-resource-manager/resource-manager-deployment-model).

Podobnie inne zasoby platformy Azure mogą być również wdrażane i zarządzane F# ze skryptów przy użyciu tych samych składników. Można na przykład utworzyć konta magazynu, wdrożyć usługę Azure Cloud Services, utworzyć wystąpienia Azure Cosmos DB i programowo zarządzać centrami usługi Azure powiadamiania F# za pomocą skryptów.

Używanie F# skryptów do wdrażania zasobów i zarządzania nimi nie jest zwykle konieczne. Na przykład zasoby platformy Azure mogą być również wdrażane bezpośrednio w opisach szablonów JSON, które mogą być sparametryzowane. Zobacz [szablony Azure Resource Manager](/azure/azure-resource-manager/resource-manager-template-best-practices) , w tym przykłady [szablonów szybkiego startu platformy Azure](https://azure.microsoft.com/resources/templates/).

## <a name="other-resources"></a>Inne zasoby

* [Pełna dokumentacja dotycząca wszystkich usług platformy Azure](/azure/)
