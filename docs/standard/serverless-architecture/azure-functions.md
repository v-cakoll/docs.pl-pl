---
title: Usługa Azure Functions — aplikacje niekorzystające z serwera
description: Usługa Azure functions udostępnia funkcje bezserwerowe w wielu językach, (C#, JavaScript i Java) i platformy, aby zapewnić oparte na zdarzeniach błyskawiczne skalowanie kodu.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 4febcc01eebf3efce3fc1eb42e19c2ec6c0baa52
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "63807903"
---
# <a name="azure-functions"></a>Azure Functions

Usługa Azure functions udostępnia środowisko bezserwerowe środowisko obliczeniowe. Funkcja jest wywoływana przez *wyzwalacza* (takich jak dostęp do punktu końcowego HTTP lub czasomierza) i wykonuje blok kod lub logikę biznesową. Również obsługę wyspecjalizowane funkcje *powiązania* , łączenie z zasobami, takich jak storage i kolejki.

![Logo usługi Azure functions](./media/azure-functions-logo.png)

Istnieją dwie wersje w ramach usługi Azure Functions. Starszą wersją obsługuje pełny program .NET Framework oraz nowe środowisko uruchomieniowe aplikacji dla wielu platform .NET Core. Dodatkowe języki, oprócz C# takich jak JavaScript, F#, i są obsługiwane w języku Java. Funkcje nie powstały w portalu zapewniają bogate składni skryptu. Funkcje nie powstały jako projekty na autonomiczne można wdrożyć z obsługą całej platformy i możliwości.

Aby uzyskać więcej informacji, zobacz [dokumentacji usługi Azure Functions](https://docs.microsoft.com/azure/azure-functions).

## <a name="functions-v1-vs-v2"></a>Funkcje v1 i v2

Istnieją dwie wersje środowiska uruchomieniowego usługi Azure Functions: w wersji 1.x i 2.x. W wersji 1.x jest ogólnie dostępna (GA). Go obsługuje programowanie na platformie .NET z portalu lub maszyn Windows i programu .NET Framework. obsługuje 1.x C#, JavaScript, a F#, eksperymentalna Obsługa języka Python, PHP, TypeScript, Batch, Bash i programu PowerShell.

[W wersji 2.x jest ogólnie dostępna teraz również](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/). On korzysta z platformy .NET Core i obsługuje wiele platform Windows, macOS i maszyn z systemem Linux. 2.x dodaje najwyższej jakości pomoc techniczna dla języka Java, ale jeszcze nie bezpośrednio obsługuje wszystkich języków eksperymentalnych. W wersji 2.x używa nowy model extensibility powiązania, który umożliwia korzystanie z rozszerzeń innych firm do korzystania z platformy, niezależnie od wersji powiązań, i usprawniony środowiska wykonawczego.

> **Jest to znany problem w 1.x z [obsługę przekierowywania powiązań](https://github.com/Azure/azure-functions-host/issues/992).** Ten problem dotyczy programowanie na platformie .NET. Dotyczy to projektów z zależnościami od bibliotek, które są nieco innej z bibliotek uwzględnione w środowisku uruchomieniowym. Zespół funkcji zobowiązał się do konkretnych postępy na problem. Zespół będzie dotyczyć przekierowania powiązań w 2.x, zanim usługa zostanie wprowadzona do ogólnej dostępności. Instrukcja oficjalne zespołu z sugerowanymi poprawkami i ich obejść jest dostępna tutaj: [Rozpoznawania zestawu w usłudze Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).

Aby uzyskać więcej informacji, zobacz [Porównanie wersji 1.x i 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).

## <a name="programming-language-support"></a>Obsługa języków programowania

Są obsługiwane następujące języki albo ogólnie rzecz biorąc dostępność (GA) w wersji zapoznawczej, lub eksperymentalnych.

|Język      |1.x         |2.x      |
|--------------|------------|---------|
|**C#**        |OGÓLNA DOSTĘPNOŚĆ          |Wersja zapoznawcza  |
|**JavaScript**|OGÓLNA DOSTĘPNOŚĆ          |Wersja zapoznawcza  |
|**F#**        |OGÓLNA DOSTĘPNOŚĆ          |         |
|**Java**      |            |Wersja zapoznawcza  |
|**Python**    |Eksperymentalne|         |
|**PHP**       |Eksperymentalne|         |
|**TypeScript**|Eksperymentalne|         |
|**Batch**     |Eksperymentalne|         |
|**Bash**      |Eksperymentalne|         |
|**Program PowerShell**|Eksperymentalne|         |

Aby uzyskać więcej informacji, zobacz [obsługiwane języki](https://docs.microsoft.com/azure/azure-functions/supported-languages).

## <a name="app-service-plans"></a>Plany usługi App service

Funkcje są wspierane przez *plan usługi app service*. Plan określa zasoby używane przez aplikację funkcji. Można przypisać planów w regionie, określ rozmiar i liczba maszyn wirtualnych, które będą używane, a następnie wybierz warstwę cenową. Wartość true, podejście bez użycia serwera, może używać aplikacji funkcji **zużycie** planu. Plan zużycie będzie skalowana zaplecza automatycznie na podstawie obciążenia.

Aby uzyskać więcej informacji, zobacz [planów usługi App service](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).

## <a name="create-your-first-function"></a>Tworzenie pierwszej funkcji

Istnieją trzy typowe sposoby tworzenia aplikacji funkcji.

* Funkcji skryptu w portalu.
* Utwórz niezbędne zasoby przy użyciu interfejsu wiersza polecenia platformy Azure (CLI).
* Tworzenie funkcji lokalnie przy użyciu ulubionego środowiska IDE i opublikuj je na platformie Azure.

Aby uzyskać więcej informacji na temat tworzenia funkcji inicjowanych przez skrypty w portalu, zobacz [tworzenie pierwszej funkcji w witrynie Azure portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).

Aby skompilować z wiersza polecenia platformy Azure, zobacz [tworzenie pierwszej funkcji przy użyciu wiersza polecenia platformy Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).

Aby utworzyć funkcję w programie Visual Studio, zobacz [tworzenie pierwszej funkcji przy użyciu programu Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).

## <a name="understand-triggers-and-bindings"></a>Zrozumienie wyzwalaczy i powiązań

Funkcje wywoływane przez *wyzwalacza* i może zawierać dokładnie jeden. Oprócz wywołanie funkcji, pewnych wyzwalaczy również służyć jako powiązania. Można również zdefiniować wiele powiązań, oprócz wyzwalacza. *Powiązania* zapewniają deklaratywną metodę, aby połączyć dane w kodzie. One mogą być przekazywane (dane wejściowe), lub odbierać dane (dane wyjściowe). Wyzwalacze i powiązania zapewnić działanie proste w użyciu. Powiązania należy usunąć z obciążeniem związanym z ręcznego tworzenia bazy danych lub pliku połączenia systemu. Wszystkie informacje potrzebne do powiązania jest zawarty w specjalnej *pliku functions.json* plików skryptów lub zadeklarowane za pomocą atrybutów w kodzie.

Niektóre typowe wyzwalacze obejmują:

* Magazyn obiektów blob: wywołania funkcji, gdy plik lub folder zostanie przekazany lub zmienione w magazynie.
* HTTP: wywoływanie funkcji takich jak interfejs API REST.
* Kolejka: wywołania funkcji, gdy istnieją elementy z kolejki.
* Czasomierz: wywoływanie funkcji w regularnych cyklach.

Przykłady powiązania:

* Cosmos DB: łatwo połączyć z bazą danych do załadowania lub zapisania plików.
* Magazyn tabel: Praca z magazynu klucz/wartość z Twojej aplikacji funkcji.
* Usługa Queue Storage: łatwo pobierania elementów z kolejki lub umieść nowych elementów w kolejce.

Poniższy przykład *pliku functions.json* plik definiuje wyzwalacz i powiązania:

```json
{
  "bindings": [
    {
      "name": "myBlob",
      "type": "blobTrigger",
      "direction": "in",
      "path": "images/{name}",
      "connection": "AzureWebJobsStorage"
    },
    {
      "name": "$return",
      "type": "queue",
      "direction": "out",
      "queueName": "images",
      "connection": "AzureWebJobsStorage"
    }
  ],
  "disabled": false
}
```

W tym przykładzie funkcja jest wyzwalana przez zmianę do magazynu obiektów blob w `images` kontenera. Informacje dotyczące pliku jest przekazywana, więc wyzwalacz działa również jako powiązania. Innym wiązaniu istnieje, aby umieścić informacje na kolejkę o nazwie `images`.

Poniżej przedstawiono skrypt języka C# dla funkcji:

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

W przykładzie występuje prostej funkcji, który przyjmuje nazwę pliku, który został zmodyfikowany lub przekazany do magazynu obiektów blob i umieszcza je w kolejce do późniejszego przetwarzania.

Aby uzyskać pełną listę wyzwalaczy i powiązań, zobacz [pojęcia powiązania i Wyzwalacze usługi Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).

## <a name="proxies"></a>Serwery proxy

Serwery proxy zapewniają funkcje przekierowania dla aplikacji. Serwery proxy uwidocznić punkt końcowy i zamapuj tego punktu końcowego do innego zasobu. Za pomocą serwerów proxy możesz wykonywać następujące czynności:

* Przekierowywanie żądań przychodzących do innego punktu końcowego.
* Przed przekazaniem wzdłuż, należy zmodyfikować żądania przychodzącego.
* Modyfikowanie lub podać odpowiedzi.

Serwery proxy są używane w scenariuszach takich jak:

* Upraszczanie, skrócenie go lub zmiana adresu URL.
* Zapewnienie spójnego prefiksu interfejsu API do wielu usług zaplecza.
* Pozorowanie odpowiedzi do punktu końcowego opracowywane.
* Dostarczanie odpowiedzi statycznej do znanego punktu końcowego.
* Zachowywanie zgodnie punkt końcowy interfejsu API, podczas gdy zaplecza jest przeniesiona lub nastąpi migracja.

Serwery proxy są przechowywane jako definicji JSON. Oto przykład:

```json
{
  "$schema": "http://json.schemastore.org/proxies",
  "proxies": {
    "Domain Redirect": {
      "matchCondition": {
        "route": "/{shortUrl}"
      },
      "backendUri": "http://%WEBSITE_HOSTNAME%/api/UrlRedirect/{shortUrl}"
    },
    "Root": {
      "matchCondition": {
        "route": "/"
      },
      "responseOverrides": {
        "response.statusCode": "301",
        "response.statusReason": "Moved Permanently",
        "response.headers.location": "https://docs.microsoft.com/"
      }
    }
  }
}
```

`Domain Redirect` Proxy przyjmuje skróconą trasy i mapuje go dłużej zasobów funkcji. Transformacja wygląda następująco:

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

`Root` Proxy przyjmuje niczego wysyłane do adresu URL katalogu głównego (`https://--shorturl--/`) i przekierowuje go w witrynie dokumentacji.

Przykład użycia serwerów proxy jest przedstawiony w wideo [platformy Azure: Udostępnij swoją aplikację w chmurze przy użyciu bezserwerowej usługi Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102). W czasie rzeczywistym aplikacji platformy ASP.NET Core uruchomionej na lokalnym serwerze SQL Server jest migracji do chmury platformy Azure. Serwery proxy służą do refaktoryzacji tradycyjny projekt interfejsu API sieci Web za pomocą funkcji.

Aby uzyskać więcej informacji na temat serwerów proxy, zobacz [pracy za pomocą usługi Azure Functions Proxies](https://docs.microsoft.com/azure/azure-functions/functions-proxies).

>[!div class="step-by-step"]
>[Poprzednie](azure-serverless-platform.md)
>[dalej](application-insights.md)
