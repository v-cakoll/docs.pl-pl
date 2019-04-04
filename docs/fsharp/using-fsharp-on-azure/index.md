---
title: Używanie języka F# na platformie Azure
description: Przewodnik dotyczący korzystania z usług Azure za pomocąF#
author: sylvanc
ms.date: 09/22/2016
ms.openlocfilehash: 8243c021b8bc3ea9b067b278a5d9c6e3619232b7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371055"
---
# <a name="using-f-on-azure"></a>Używanie języka F# na platformie Azure

F#jest obracanym język programowania w chmurze i często służy do pisania aplikacji sieci web, usług w chmurze, w przypadku mikrousługi hostowane w chmurze i skalowalna przetwarzania danych.

W poniższych sekcjach znajdziesz zasoby dotyczące korzystania z usług platformy Azure w programie F#.

> [!NOTE]
> Jeśli w tym zestawie dokumentacji nie ma określonej usługi platformy Azure, zapoznaj się dokumentacją usługi Azure Functions lub platformy .NET dla danej usługi. Niektórych usług platformy Azure są niezależne od języka i wymagać dokumentacji nie określonego języka i nie są tutaj wymienione.

## <a name="using-azure-virtual-machines-with-f"></a>Maszyny wirtualne platformy Azure przy użyciu F\#

Platforma Azure obsługuje szeroką gamę konfiguracji maszyny wirtualnej (VM), zobacz [systemów Linux i maszynach wirtualnych platformy Azure](https://azure.microsoft.com/services/virtual-machines/).

Aby zainstalować F# na maszynie wirtualnej do wykonania, kompilacji i/lub zobacz skryptów [Using F# w systemie Linux](https://fsharp.org/use/linux) i [Using F# na Windows](https://fsharp.org/use/windows).


## <a name="using-azure-functions-with-f"></a>Użycie usługi Azure Functions f\#

[Usługa Azure Functions](https://azure.microsoft.com/services/functions/) to rozwiązanie umożliwiające łatwe uruchamianie małych fragmentów kodu lub "funkcji" w chmurze. Można napisać tylko kod, czego potrzebujesz do problemie, nie martwiąc się o całą aplikację ani infrastrukturę do jej uruchomienia. Funkcje są połączone ze zdarzeń w usłudze Azure storage i innych zasobów hostowanych w chmurze. Dane są przesyłane z F# funkcje za pośrednictwem argumentów funkcji. Można użyć z wybranym ufającej platformy Azure, aby skalować stosownie do potrzeb języka programowania.

Obsługa usługi Azure Functions F# jako najwyższej jakości język wydajny, reaktywnych skalowalne wykonywania F# kodu. Zobacz [usługi Azure Functions F# dokumentacja dla deweloperów](/azure/azure-functions/functions-reference-fsharp) dla dokumentacji dotyczące sposobu używania F# za pomocą usługi Azure Functions.

Inne zasoby dotyczące korzystania z usługi Azure Functions i F#:

* [Skalowanie usługi Azure Functions w F# przy użyciu Suave](https://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/)
* [Jak utworzyć funkcję platformy Azure wF#](https://mnie.github.io/2016-09-08-AzureFunctions/)
* [Za pomocą dostawcy typu platformy Azure za pomocą usługi Azure Functions](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a>Korzystanie z usługi Azure Storage z F\#

Usługa Azure Storage jest podstawowy warstwy magazynowania dla nowoczesnych aplikacji, które polegają na trwałości, dostępności i skalowalności, aby spełniać potrzeby klientów. F#programy mogą wchodzić w interakcje bezpośrednio z usługami Azure storage, za pomocą metod opisanych w następujących artykułach.

* [Rozpoczynanie pracy z usługą Azure Blob Storage przy użyciu języka F#](blob-storage.md)
* [Rozpoczynanie pracy z usługą Azure File Storage przy użyciu języka F#](file-storage.md)
* [Rozpoczynanie pracy z usługą Azure Queue Storage przy użyciu języka F#](queue-storage.md)
* [Rozpoczynanie pracy z usługą Azure Table Storage przy użyciu języka F#](table-storage.md)

Usługa Azure Storage można również w połączeniu z usługą Azure Functions za pomocą deklaratywnych konfiguracji, a nie jawnych wywołań interfejsu API. Zobacz [Wyzwalacze usługi Azure Functions i powiązania dla usługi Azure Storage](/azure/azure-functions/functions-bindings-storage) zawierający F# przykłady.

## <a name="using-azure-app-service-with-f"></a>Za pomocą usługi Azure App Service przy użyciu F\#

[Usługa Azure App Service](https://azure.microsoft.com/services/app-service/) to platforma w chmurze do tworzenia zaawansowanych aplikacji internetowych i mobilnych łączących się z danymi przechowywanymi w chmurze lub lokalnie.

* [F#Przykład interfejsu API sieci Web Azure](https://github.com/fsprojects/azure-webapi-example)
* [Hosting F# w aplikacji sieci web na platformie Azure](https://github.com/isaacabraham/fsharp-demonstrator)

## <a name="using-apache-spark-with-f-with-azure-hdinsight"></a>Przy użyciu platformy Apache Spark z F# za pomocą usługi Azure HDInsight

[Platforma Apache Spark dla usługi Azure HDInsight](https://azure.microsoft.com/services/hdinsight/apache-spark/) to platforma przetwarzania typu open source, która umożliwia uruchamianie aplikacji do analizy danych na dużą skalę. Platforma Apache Spark dzięki platformie Azure, łatwe i ekonomiczne wdrażanie. Tworzenie aplikacji platformy Spark w F# przy użyciu [Mobius](https://github.com/Microsoft/Mobius), interfejs API programu .NET dla platformy Spark.

* [Wdrażanie aplikacji platformy Spark w F# przy użyciu Mobius](https://github.com/Microsoft/Mobius/blob/master/notes/spark-fsharp-mobius.md)
* [Przykład F# aplikacji Spark przy użyciu Mobius](https://github.com/Microsoft/Mobius/tree/master/examples/fsharp)

## <a name="using-azure-cosmos-db-with-f"></a>Za pomocą usługi Azure Cosmos DB przy użyciu F\#

[Usługa Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db) to usługa NoSQL dla wysoko dostępnych, globalnie rozproszonych aplikacji.

Usługa Azure Cosmos DB, mogą być używane z F# na dwa sposoby:

1. Proces tworzenia F# usługi Azure Functions, które reagują na lub sprawić, że zmiany do kolekcji usługi Azure Cosmos DB. Zobacz [powiązań usługi Azure Cosmos DB dla usługi Azure Functions](/azure/azure-functions/functions-bindings-cosmosdb), lub
2. Za pomocą [usługi Azure Cosmos DB .NET SDK interfejsu API SQL](/azure/cosmos-db/sql-api-sdk-dotnet). Powiązane przykłady znajdują się w języku C#.

## <a name="using-azure-event-hubs-with-f"></a>Za pomocą usługi Azure Event Hubs za pomocą F\#

[Usługa Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/) zapewniają przyjmowanie danych telemetrycznych w skali chmury z witryn sieci Web, aplikacji i urządzeń.

Usługa Azure Event Hubs może być używany z F# na dwa sposoby:

1. Proces tworzenia F# usługi Azure Functions, które są wyzwalane przez zdarzenia. Zobacz [wyzwala funkcję platformy Azure, usługi Event Hubs](/azure/azure-functions/functions-bindings-event-hubs), lub
2. Za pomocą [zestawu .NET SDK dla platformy Azure](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted). Należy pamiętać, że te przykłady w języku C#.

## <a name="using-azure-notification-hubs-with-f"></a>Za pomocą usługi Azure Notification Hubs za pomocą F\#

[Usługa Azure Notification Hubs](/azure/notification-hubs/) są infrastruktury powiadomień wypychanych dla wielu platform, skalowanych w poziomie, które umożliwiają wysyłanie mobilnych powiadomień wypychanych z poziomu dowolnego zaplecza (w chmurze lub lokalnie) na dowolną platformę mobilną.

Usługa Azure Notification Hubs może być używany z F# na dwa sposoby:

1. Proces tworzenia F# usługi Azure Functions, która będzie wysyłać wyniki do danego centrum powiadomień. Zobacz [wyzwalaczy dane wyjściowe funkcji platformy Azure dla usługi Notification Hubs](/azure/azure-functions/functions-bindings-notification-hubs), lub
2. Za pomocą [zestawu .NET SDK dla platformy Azure](https://blogs.msdn.microsoft.com/azuremobile/2014/04/08/push-notifications-using-notification-hub-and-net-backend/). Należy pamiętać, że te przykłady w języku C#.


## <a name="implementing-webhooks-on-azure-with-f"></a>Implementowanie elementów Webhook na platformie Azure dzięki F\#

A [elementu Webhook](https://en.wikipedia.org/wiki/Webhook) jest wywołanie zwrotne wyzwalane za pośrednictwem żądania sieci web. Elementy Webhook są używane w witrynach, takich jak GitHub sygnału zdarzenia.

Elementy Webhook, może być implementowany w F# i hostowanej na platformie Azure za pośrednictwem [funkcji platformy Azure w F# z powiązań elementów Webhook](/azure/azure-functions/functions-bindings-http-webhook).

## <a name="using-webjobs-with-f"></a>Za pomocą zadań Webjob za pomocą F\#

[Zadania Webjob](/azure/app-service-web/web-sites-create-web-jobs) są programy można uruchomić aplikacji sieci web usługi App Service na trzy sposoby: na żądanie, w sposób ciągły, lub zgodnie z harmonogramem.

[Przykład F# zadania Webjob](https://github.com/jrr/webjob-project-examples)

## <a name="implementing-timers-on-azure-with-f"></a>Implementowanie zegary na platformie Azure dzięki F\#

Czasomierz wyzwala wywołanie funkcji, na podstawie harmonogramu, jednorazowo lub cykliczne.

Czasomierze może być implementowany w F# i hostowanej na platformie Azure za pośrednictwem [funkcji platformy Azure w F# z wyzwalaczem czasomierza](/azure/azure-functions/functions-bindings-timer).

## <a name="deploying-and-managing-azure-resources-with-f-scripts"></a>Wdrażanie i zarządzanie zasobami platformy Azure przy użyciu F# skryptów

Maszyny wirtualne platformy Azure może być programowo oraz zarządzania nimi z F# skryptów za pomocą pakietów Microsoft.Azure.Management i interfejsów API. Na przykład zobacz [wprowadzenie do bibliotek zarządzania dla platformy .NET](https://msdn.microsoft.com/library/dn722415.aspx) i [przy użyciu usługi Azure Resource Manager](/azure/azure-resource-manager/resource-manager-deployment-model).

Podobnie, innych zasobów platformy Azure może również być wdrażania i zarządzania nimi z F# skryptów za pomocą tych samych składników. Na przykład możesz utworzyć konta magazynu, wdrażanie usług Azure Cloud Services, tworzenie wystąpień usługi Azure Cosmos DB i zarządzanie Azure niewłaściwa Hubs programowo z F# skryptów.

Za pomocą F# skryptów do wdrażania zasobów i zarządzanie nimi nie jest zazwyczaj konieczne. Na przykład zasoby platformy Azure również można wdrażać bezpośrednio z opisy szablonu JSON, które mogą być parametryzowane. Zobacz [szablonów usługi Azure Resource Manager](/azure/azure-resource-manager/resource-manager-template-best-practices) wraz z przykładami takich jak [szablony szybkiego startu platformy Azure](https://azure.microsoft.com/resources/templates/).

## <a name="other-resources"></a>Inne zasoby

* [Pełną dokumentację dotyczącą wszystkich usług platformy Azure](/azure/)
