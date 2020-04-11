---
title: Szybki start (usługi danych WCF)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: f945d33a4fc789b3c73c1c80040fc8527301758b
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121223"
---
# <a name="quickstart-wcf-data-services"></a>Szybki start (usługi danych WCF)

Ten przewodnik Szybki start ułatwia zapoznanie się z usługami WCF Data Services i protokołem OData (Open Data Protocol) za pomocą szeregu zadań, które obsługują tematy w [obszarze Wprowadzenie.](getting-started-with-wcf-data-services.md)

## <a name="what-youll-learn"></a>Zawartość

Pierwsze zadanie w tym przewodniku Szybki start pokazuje, jak utworzyć usługę danych, aby udostępnić źródło danych OData z przykładowej bazy danych Northwind. W późniejszych tematach można uzyskać dostęp do źródła danych OData za pomocą przeglądarki sieci Web, a także utworzyć aplikację kliencką Windows Presentation Foundation (WPF), która zużywa źródło danych OData przy użyciu bibliotek klienckich.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten szybki start, zainstaluj następujące składniki:

- Visual Studio

- Wystąpienie programu SQL Server. Obejmuje to program SQL Server Express, który jest uwzględniony w domyślnej instalacji programu Visual Studio 2015 lub jako część obciążenia **magazynu i przetwarzania danych** w programie Visual Studio 2017 lub nowszym.

- Przykładowa bazy danych Northwind. Aby zainstalować bazę danych, uruchom skrypt Transact-SQL z [northwind i pubów przykładowych baz danych dla programu Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).

## <a name="wcf-data-services-quickstart-tasks"></a>Zadania szybkiego startu usług danych WCF

 [Tworzenie usługi danych](creating-the-data-service.md)

 Zdefiniuj ASP.NET aplikacji, zdefiniuj model danych, utwórz usługę danych i włącz dostęp do zasobów.

 [Dostęp do usługi za pomocą przeglądarki sieci Web](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 Uruchom usługę z programu Visual Studio i uzyskać dostęp do usługi, przesyłając żądania HTTP GET za pośrednictwem przeglądarki sieci Web do udostępnianego źródła danych.

 [Tworzenie aplikacji klienckiej programu .NET Framework](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 Utwórz aplikację WPF, aby korzystać z źródła danych OData, powiązać dane z formantami systemu Windows, zmienić dane w formantach powiązanych, a następnie wysłać zmiany z powrotem do usługi danych.

> [!NOTE]
> Pliki projektu z ukończonej wersji przewodnika Szybki start można pobrać z [gitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client)).

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Uruchamianie przewodnika Szybki start](creating-the-data-service.md)

## <a name="see-also"></a>Zobacz też

- [Program Entity Framework na platformie ADO.NET](../adonet/ef/index.md)
