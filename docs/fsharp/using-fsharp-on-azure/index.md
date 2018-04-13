---
title: 'Przy użyciu języka F # na platformie Azure'
description: 'Przewodnik po użyciu usług Azure F #'
keywords: Azure, cloud, visual f#, f#, functional programming, .NET, .NET Core
author: sylvanc
ms.author: phcart
ms.date: 09/22/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: FAD4D11E-703A-42D4-9F72-893D9E0F569B
ms.openlocfilehash: fdb2378a731a13894cf71356a2713c62a5c2064e
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="using-f-on-azure"></a>Przy użyciu języka F # na platformie Azure

F # jest obracanym język programowania chmury i jest często używany do zapisywania aplikacji sieci web, usługi w chmurze hostowanej chmurze mikrousług i skalowalne przetwarzania danych.

W poniższych sekcjach znajdziesz zasoby dotyczące sposobu używania usługi zakresu Azure języku F #.

> [!NOTE]
> Jeśli w tym zestawie dokumentacji nie ma określonej usługi Azure, zapoznaj się dokumentacją funkcji Azure albo .NET dla tej usługi. Niektóre usługi Azure są niezależne od języka i wymagają dokumentacji nie specyficzny dla języka, a nie są wyświetlane tutaj.

## <a name="using-azure-virtual-machines-with-f"></a>Przy użyciu maszyn wirtualnych platformy Azure w języku F # #

Azure obsługuje szeroką gamę konfiguracje maszyn wirtualnych (VM), zobacz [systemu Linux i maszyny wirtualne Azure](https://azure.microsoft.com/services/virtual-machines/).

Aby zainstalować F # na maszynę wirtualną do wykonania, kompilacji i/lub skryptów można znaleźć [przy użyciu F # w systemie Linux](http://fsharp.org/use/linux) i [przy użyciu F # w systemie Windows](http://fsharp.org/use/windows).


## <a name="using-azure-functions-with-f"></a>Przy użyciu funkcji platformy Azure w języku F # #

[Środowisko Azure Functions](https://azure.microsoft.com/services/functions/) to rozwiązanie umożliwiające łatwe uruchamianie małych fragmentów kodu lub "funkcji" w chmurze. Można napisać tylko kod potrzebnych dla problemu, nie martwiąc się o całą aplikację ani infrastrukturę do jego działania. Funkcje są połączone ze zdarzeń w magazynie Azure i innych zasobów hostowanych w chmurze. Przepływy danych w funkcji F # za pomocą argumentów funkcji. Korzystając z wybranego, ufających Azure można skalować zgodnie z potrzebami Twojej języka programowania.

Środowisko Azure Functions obsługuje F # jako najwyższej jakości język z wydajne, reaktywne, skalowalna wykonywanie kodu języka F #. Zobacz [funkcji Azure F # dokumentacja dla deweloperów](/azure/azure-functions/functions-reference-fsharp) dla dokumentacji dotyczące sposobu używania F # w środowisku Azure Functions.

Inne zasoby dotyczące korzystania z usługi Azure Functions i F #:

* [Skalować usługę Azure Functions w języku F # za pomocą Suave](https://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/)
* [Tworzenie funkcji platformy Azure w języku F #](https://mnie.github.io/2016-09-08-AzureFunctions/)
* [Przy użyciu dostawcy typów Azure z funkcjami platformy Azure](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a>Za pomocą usługi Azure Storage w języku F # #

Usługa Azure Storage jest warstwy podstawowej usługi magazynu dla nowoczesnych aplikacji, które polegają na trwałości, dostępności i skalowalności, aby spełniać potrzeby klientów. F # programy można bezpośrednią interakcję z usług Azure storage, przy użyciu techinques opisane w następujących artykułach.

* [Rozpoczynanie pracy z usługą Azure Blob Storage przy użyciu języka F #](blob-storage.md)
* [Rozpoczynanie pracy z usługą Azure File Storage przy użyciu języka F #](file-storage.md)
* [Rozpoczynanie pracy z usługą Azure Queue Storage przy użyciu języka F #](queue-storage.md)
* [Rozpoczynanie pracy z usługą Azure Table Storage przy użyciu języka F #](table-storage.md)

Można także magazynu Azure w połączeniu z usługi Azure Functions za pośrednictwem deklaratywne konfiguracji zamiast jawnego wywołania interfejsu API. Zobacz [usługi Azure Functions wyzwalaczy i powiązań usługi Azure Storage](/azure/azure-functions/functions-bindings-storage) w tym przykłady F #.

## <a name="using-azure-app-service-with-f"></a>Za pomocą usługi aplikacji Azure — w języku F # #

[Usługa aplikacji Azure](https://azure.microsoft.com/services/app-service/) to platforma chmury do tworzenia zaawansowanych sieci web i aplikacji mobilnych, łączący się dane w dowolnym miejscu, w chmurze lub lokalnie.

* [Przykład F # Azure interfejsu API sieci Web](https://github.com/fsprojects/azure-webapi-example)
* [Hosting F # w aplikacji sieci web na platformie Azure](https://github.com/isaacabraham/fsharp-demonstrator)

## <a name="using-apache-spark-with-f-with-azure-hdinsight"></a>Przy użyciu platformy Apache Spark w usłudze F # z usługą Azure HDInsight

[Platforma Apache Spark w usłudze Azure HDInsight](https://azure.microsoft.com/services/hdinsight/apache-spark/) jest środowisko przetwarzania typu open source, które są uruchomione aplikacje analizy danych na dużą skalę. Azure sprawia, że platforma Apache Spark łatwe i ekonomiczne do wdrożenia. Tworzenie aplikacji Spark w F # za pomocą [Mobius](https://github.com/Microsoft/Mobius), interfejs API programu .NET dla platformy Spark.

* [Wdrażanie aplikacji Spark w F # za pomocą Mobius](https://github.com/Microsoft/Mobius/blob/master/notes/spark-fsharp-mobius.md)
* [Przykład F # Spark aplikacji przy użyciu Mobius](https://github.com/Microsoft/Mobius/tree/master/examples/fsharp)

## <a name="using-azure-cosmos-db-with-f"></a>Przy użyciu rozwiązania Cosmos Azure DB w języku F # #

[Azure DB rozwiązania Cosmos](https://azure.microsoft.com/services/cosmos-db) jest usługą NoSQL dla aplikacji o wysokiej dostępności, globalnie rozproszone.

Azure DB rozwiązania Cosmos mogą być używane w języku F # na dwa sposoby:

1. Poprzez utworzenie usługi Azure Functions F # które reagują na lub powodują zmiany w kolekcjach bazy danych Azure rozwiązania Cosmos. Zobacz [bazy danych Azure rozwiązania Cosmos powiązania dla usługi Azure Functions](/azure/azure-functions/functions-bindings-cosmosdb), lub
2. Za pomocą [Azure rozwiązania Cosmos DB .NET SDK dla interfejsu API SQL](/azure/cosmos-db/sql-api-sdk-dotnet). Powiązane przykłady są w języku C#.

## <a name="using-azure-event-hubs-with-f"></a>Za pomocą usługi Azure Event Hubs w języku F # #

[Usługa Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/) Podaj skali chmury wprowadzanie danych telemetrycznych z witryn sieci Web, aplikacji i urządzeń.

Usługa Azure Event Hubs mogą być używane w języku F # na dwa sposoby:

1. Poprzez utworzenie usługi Azure Functions F # wyzwalane przez zdarzenia. Zobacz [wyzwala funkcji platformy Azure dla usługi Event Hubs](/azure/azure-functions/functions-bindings-event-hubs), lub
2. Za pomocą [zestawu .NET SDK dla platformy Azure](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted). Należy zauważyć, że te przykłady w języku C#.

## <a name="using-azure-notification-hubs-with-f"></a>Za pomocą usługi Azure Notification Hubs w języku F # #

[Centra powiadomień Azure](/azure/notification-hubs/) są wypychanych skalowanej, wieloplatformowej infrastruktury, która umożliwia wysyłanie powiadomień wypychanych przenośnych z poziomu dowolnego zaplecza (w chmurze lub lokalnie) na dowolną platformę mobilną.

Centra powiadomień Azure mogą być używane w języku F # na dwa sposoby:

1. Poprzez utworzenie usługi Azure Functions F #, który wysyła wyniki do Centrum powiadomień. Zobacz [funkcji platformy Azure wyjściowe Wyzwalacze dla usługi Notification Hubs](/azure/azure-functions/functions-bindings-notification-hubs), lub
2. Za pomocą [zestawu .NET SDK dla platformy Azure](https://blogs.msdn.microsoft.com/azuremobile/2014/04/08/push-notifications-using-notification-hub-and-net-backend/). Należy zauważyć, że te przykłady w języku C#.


## <a name="implementing-webhooks-on-azure-with-f"></a>Implementowanie elementów Webhook na platformie Azure przy użyciu języka F # #

A [Webhook](https://en.wikipedia.org/wiki/Webhook) jest wywołaniem zwrotnym wyzwalane za pomocą żądania sieci web. Elementów Webhook są używane w witrynach, takich jak GitHub sygnału zdarzenia. 

Może być zaimplementowany w języku F # i hostowanej na platformie Azure za pomocą elementów Webhook [funkcji platformy Azure w języku F # z powiązaniem element Webhook](/azure/azure-functions/functions-bindings-http-webhook).

## <a name="using-webjobs-with-f"></a>Przy użyciu zadań Webjob w języku F # #

[Zadania Webjob](/azure/app-service-web/web-sites-create-web-jobs) są programy można uruchamiać w aplikacji sieci web usługi aplikacji na trzy sposoby: na żądanie, w sposób ciągły, lub zgodnie z harmonogramem.

[Przykład F # zadania Webjob](https://github.com/andredublin/fsharp-azure-webjob)

## <a name="implementing-timers-on-azure-with-f"></a>Implementowanie czasomierze na platformie Azure przy użyciu języka F # #

Czasomierza wyzwala wywoływać funkcje na podstawie harmonogramu, jednorazowo lub cykliczne.

Czasomierze może być zaimplementowany w języku F # i hostowanej na platformie Azure za pośrednictwem [funkcji platformy Azure w języku F # z wyzwalacza bazującego na czasomierzu](/azure/azure-functions/functions-bindings-timer).

## <a name="deploying-and-managing-azure-resources-with-f-scripts"></a>Wdrażanie i zarządzanie zasobami Azure za pomocą skryptów F # #

Maszyny wirtualne platformy Azure mogą być programowane wdrożone i zarządzane przez skrypty F # za pomocą pakietów Microsoft.Azure.Management i interfejsów API. Na przykład, zobacz [Rozpoczynanie pracy z bibliotekami zarządzania dla platformy .NET](https://msdn.microsoft.com/library/dn722415.aspx) i [przy użyciu usługi Azure Resource Manager](/azure/azure-resource-manager/resource-manager-deployment-model).

Podobnie innych zasobów platformy Azure mogą również być wdrożone i zarządzane przez skrypty F # za pomocą tego samego składników. Na przykład możesz można utworzyć konta magazynu, wdrażania usługi w chmurze Azure, tworzenia wystąpień bazy danych Azure rozwiązania Cosmos i programowe zarządzanie koncentratory powiadomienia Azure ze skryptów F #.

Przy użyciu języka F # skryptów do wdrażania i zarządzania zasobami nie jest zazwyczaj konieczne. Na przykład zasobów platformy Azure można także wdrożonej międzypaństwowymi, bezpośrednio z opisy szablonu JSON, które mogą być sparametryzowana. Zobacz [szablony Menedżera zasobów Azure](/azure/azure-resource-manager/resource-manager-template-best-practices) wraz z przykładami takich jak [szablonów Szybki Start Azure](https://azure.microsoft.com/resources/templates/).

## <a name="other-resources"></a>Inne zasoby

* [Pełną dokumentację wszystkich usług platformy Azure](/azure/)
