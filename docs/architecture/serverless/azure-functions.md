---
title: Funkcje platformy Azure — aplikacje bezserwerowe
description: Funkcje platformy Azure zapewniają funkcje bezserwerowe w wielu językach (C#, JavaScript, Java) i platformach, aby zapewnić kod błyskawicznej skali sterowanej zdarzeniami.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 8764e6a33f3fdd53e60fa767d0fb584a9c07de7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401614"
---
# <a name="azure-functions"></a>Azure Functions

Funkcje platformy Azure zapewniają środowisko obliczeniowe bezużycia serwera. Funkcja jest wywoływana przez *wyzwalacz* (na przykład dostęp do punktu końcowego HTTP lub czasowcy) i wykonuje blok kodu lub logiki biznesowej. Funkcje obsługują również *wyspecjalizowane powiązania,* które łączą się z zasobami, takimi jak magazyn i kolejki.

![Logo funkcji platformy Azure](./media/azure-functions-logo.png)

Istnieją dwie wersje platformy Azure Functions. Starsza wersja obsługuje pełną platformę .NET Framework, a nowa wersja uruchomieniowa obsługuje aplikacje .NET Core między platformami. Obsługiwane są dodatkowe języki oprócz języka C#, takie jak JavaScript, F#i Java. Funkcje utworzone w portalu zapewniają sformatowane składni skryptów. Funkcje utworzone jako projekty autonomiczne można wdrożyć z pełną obsługą platformy i możliwościami.

Aby uzyskać więcej informacji, zobacz [dokumentację usługi Azure Functions](https://docs.microsoft.com/azure/azure-functions).

## <a name="functions-v1-vs-v2"></a>Funkcje v1 vs. v2

Istnieją dwie wersje programu Windows Functions: 1.x i 2.x. Wersja 1.x jest ogólnie dostępna (GA). Obsługuje program .NET z portalu lub komputerów z systemem Windows i używa .NET Framework. 1.x obsługuje C#, JavaScript i F#, z eksperymentalną obsługą pythona, PHP, TypeScript, Batch, Bash i PowerShell.

[Wersja 2.x jest również ogólnie dostępna teraz](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/). Wykorzystuje program .NET Core i obsługuje tworzenie wielu platform na komputerach z systemem Windows, macOS i Linux. 2.x dodaje pierwszorzędną obsługę języka Java, ale nie obsługuje jeszcze bezpośrednio żadnego z języków eksperymentalnych. Wersja 2.x używa nowego modelu rozszerzalności powiązania, który umożliwia rozszerzenia innych firm na platformie, niezależne przechowywanie wersji powiązań i usprawnione środowisko wykonywania.

> **Znany jest problem w 1.x z [obsługą przekierowania powiązania](https://github.com/Azure/azure-functions-host/issues/992).** Problem jest specyficzny dla rozwoju .NET. Mają wpływ na projekty z zależnościami od bibliotek, które są inną wersją niż biblioteki zawarte w czasie wykonywania. Zespół funkcji zobowiązał się do dokonania konkretnych postępów w tej sprawie. Zespół zajmie się powiązanie przekierowania w 2.x, zanim przejdzie do ogólnej dostępności. Oficjalne oświadczenie zespołu z sugerowanymi poprawkami i obejściami jest dostępne tutaj: [Rozpoznawanie zestawu w usłudze Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).

Aby uzyskać więcej informacji, zobacz [Porównanie 1.x i 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).

## <a name="programming-language-support"></a>Obsługa języków programowania

Następujące języki są obsługiwane w ogólnej dostępności (GA), podglądu lub eksperymentalne.

|Język      |1.x         |2.x      |
|--------------|------------|---------|
|**C #**        |Ogólna dostępność          |Wersja zapoznawcza  |
|**Javascript**|Ogólna dostępność          |Wersja zapoznawcza  |
|**F #**        |Ogólna dostępność          |         |
|**Java**      |            |Wersja zapoznawcza  |
|**Python**    |Eksperymentalne|         |
|**PHP**       |Eksperymentalne|         |
|**TypeScript**|Eksperymentalne|         |
|**Batch**     |Eksperymentalne|         |
|**Bash**      |Eksperymentalne|         |
|**Powershell**|Eksperymentalne|         |

Więcej informacji, zobacz [Obsługiwane języki](https://docs.microsoft.com/azure/azure-functions/supported-languages).

## <a name="app-service-plans"></a>Plany usług aplikacji

Funkcje są obsługiwane przez *plan usługi aplikacji*. Plan definiuje zasoby używane przez aplikację funkcji. Można przypisać plany do regionu, określić rozmiar i liczbę maszyn wirtualnych, które będą używane, i wybrać warstwę cenową. W przypadku prawdziwego podejścia bezużycia serwera aplikacje funkcji mogą używać planu **zużycia.** Plan zużycia automatycznie skaluje zaplecze na podstawie obciążenia.

Aby uzyskać więcej informacji, zobacz [Plany usług aplikacji](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).

## <a name="create-your-first-function"></a>Tworzenie pierwszej funkcji

Istnieją trzy typowe sposoby tworzenia aplikacji funkcji.

- Funkcje skryptu w portalu.
- Utwórz niezbędne zasoby przy użyciu interfejsu cli platformy Azure.
- Twórz funkcje lokalnie przy użyciu ulubionego środowiska IDE i publikuj je na platformie Azure.

Aby uzyskać więcej informacji na temat tworzenia funkcji skryptów w portalu, zobacz [Tworzenie pierwszej funkcji w witrynie Azure portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).

Aby utworzyć kompilację z interfejsu cli platformy Azure, zobacz [Tworzenie pierwszej funkcji przy użyciu interfejsu cli platformy Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).

Aby utworzyć funkcję z programu Visual Studio, zobacz [Tworzenie pierwszej funkcji przy użyciu programu Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).

## <a name="understand-triggers-and-bindings"></a>Opis wyzwalaczy i powiązań

Funkcje są wywoływane przez *wyzwalacz* i może mieć dokładnie jeden. Oprócz wywoływania funkcji, niektóre wyzwalacze również służyć jako powiązania. Oprócz wyzwalacza można również zdefiniować wiele powiązań. *Powiązania* zapewniają deklaratywny sposób łączenia danych z kodem. Mogą być przekazywane (wejściowe) lub odbierać dane (dane wyjściowe). Wyzwalacze i wiązania ułatwiają pracę z funkcjami. Powiązania usuwają obciążenie związane z ręcznym tworzeniem połączeń bazy danych lub systemu plików. Wszystkie informacje potrzebne dla powiązań jest zawarte w pliku special *functions.json* dla skryptów lub zadeklarowane z atrybutami w kodzie.

Niektóre typowe wyzwalacze obejmują:

- Magazyn obiektów Blob: wywołaj funkcję, gdy plik lub folder zostanie przekazany lub zmieniony w magazynie.
- HTTP: wywołać funkcję, takich jak interfejs API REST.
- Kolejka: wywołać funkcję, gdy elementy istnieją w kolejce.
- Timer: wywołać funkcję na regularne rytm.

Przykłady powiązań obejmują:

- CosmosDB: łatwo połączyć się z bazą danych, aby załadować lub zapisać pliki.
- Przechowywanie tabel: praca z magazynem kluczy/wartości z aplikacji funkcji.
- Magazyn kolejek: łatwo pobierać elementy z kolejki lub umieszczać nowe elementy w kolejce.

Poniższy przykład owy plik *functions.json* definiuje wyzwalacz i powiązanie:

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

W tym przykładzie funkcja jest wyzwalana przez zmianę `images` magazynu obiektów blob w kontenerze. Informacje o pliku są przekazywane, więc wyzwalacz działa również jako powiązanie. Istnieje inne powiązanie, aby umieścić `images`informacje w kolejce o nazwie .

Oto skrypt C# dla funkcji:

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

Przykład jest prostą funkcją, która przyjmuje nazwę pliku, który został zmodyfikowany lub przekazany do magazynu obiektów blob i umieszcza go w kolejce do późniejszego przetwarzania.

Aby uzyskać pełną listę wyzwalaczy i powiązań, zobacz [Usługi Azure Functions wyzwala i powiązania pojęcia](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).

## <a name="proxies"></a>Serwerów proxy

Serwery proxy zapewniają funkcje przekierowania dla aplikacji. Serwery proxy udostępniają punkt końcowy i mapują ten punkt końcowy na inny zasób. Z serwerami proxy możesz:

- Przekierowanie żądania przychodzącego do innego punktu końcowego.
- Zmodyfikuj żądanie przychodzące, zanim zostanie przekazane.
- Zmodyfikuj lub udzielij odpowiedzi.

Serwery proxy są używane w scenariuszach takich jak:

- Upraszczanie, skracanie lub zmienianie adresu URL.
- Zapewnienie spójnego prefiksu interfejsu API do wielu usług zaplecza.
- Szyderczy odpowiedzi na punkt końcowy jest rozwijany.
- Zapewnienie statycznej odpowiedzi na dobrze znany punkt końcowy.
- Utrzymywanie punktu końcowego interfejsu API spójne, gdy zaplecze jest przenoszone lub migrowane.

Serwery proxy są przechowywane jako definicje JSON. Oto przykład:

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

Serwer `Domain Redirect` proxy przyjmuje skróconą trasę i mapuje ją do dłuższego zasobu funkcyjnego. Transformacja wygląda następująco:

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

Serwer `Root` proxy pobiera wszystko, co`https://--shorturl--/`jest wysyłane do głównego adresu URL ( ) i przekierowuje go do witryny dokumentacji.

Przykład korzystania z serwerów proxy jest wyświetlany w filmie [Azure: Przenieś aplikację do chmury za pomocą bezserwerowych funkcji platformy Azure](https://channel9.msdn.com/events/Connect/2017/E102). W czasie rzeczywistym ASP.NET podstawowa aplikacja uruchomiona w lokalnym programie SQL Server jest migrowana do usługi Azure Cloud. Serwery proxy są używane do refaktoryzacji tradycyjnego projektu interfejsu API sieci Web do korzystania z funkcji.

Aby uzyskać więcej informacji na temat serwerów proxy, zobacz [Praca z serwerami proxy usługi Azure Functions .](https://docs.microsoft.com/azure/azure-functions/functions-proxies)

>[!div class="step-by-step"]
>[Poprzedni](azure-serverless-platform.md)
>[następny](application-insights.md)
