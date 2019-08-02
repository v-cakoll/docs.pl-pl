---
title: Azure Functions — aplikacje bezserwerowe
description: Usługa Azure Functions zapewnia bezserwerowe funkcje wC#wielu językach (, JavaScript, Java) i na platformach, aby zapewnić błyskawiczny kod skalowania sterowanego zdarzeniami.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 4febcc01eebf3efce3fc1eb42e19c2ec6c0baa52
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676806"
---
# <a name="azure-functions"></a>Azure Functions

Usługa Azure Functions zapewnia środowisko obliczeniowe bezserwerowe. Funkcja jest wywoływana przez *wyzwalacz* (taki jak dostęp do punktu końcowego http lub Timer) i wykonuje blok kodu lub logiki biznesowej. Funkcje obsługują także wyspecjalizowane *powiązania* , które łączą się z zasobami, takimi jak magazyn i kolejki.

![Logo usługi Azure Functions](./media/azure-functions-logo.png)

Istnieją dwie wersje platformy Azure Functions. Starsza wersja obsługuje pełne .NET Framework a nowe środowisko uruchomieniowe obsługuje aplikacje platformy .NET Core dla wielu platform. Obsługiwane są dodatkowe C# Języki, takie jak F#JavaScript, i Java. Funkcje utworzone w portalu zawierają rozbudowaną składnię skryptów. Funkcje utworzone jako projekty autonomiczne mogą być wdrażane z pełną obsługą platformy i możliwościami.

Aby uzyskać więcej informacji, zobacz [dokumentację Azure Functions](https://docs.microsoft.com/azure/azure-functions).

## <a name="functions-v1-vs-v2"></a>Funkcje V1 i v2

Istnieją dwie wersje środowiska uruchomieniowego Azure Functions: 1. x i 2. x. Wersja 1. x jest ogólnie dostępna (GA). Obsługuje ona programowanie na platformie .NET z poziomu portalu lub maszyn z systemem Windows i używa .NET Framework. 1. x obsługuje C#, JavaScript i F#, z eksperymentalną obsługą języków Python, php, TypeScript, Batch, bash i PowerShell.

W [wersji 2. x jest również ogólnie dostępna](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/). Wykorzystuje platformę .NET Core i obsługuje programowanie na wielu platformach na maszynach z systemami Windows, macOS i Linux. 2. x dodaje obsługę pierwszej klasy dla języka Java, ale nie obsługuje jeszcze bezpośrednio żadnego z języków eksperymentalnych. Wersja 2. x używa nowego modelu rozszerzalności powiązania, który umożliwia korzystanie z rozszerzeń innych firm na platformie, niezależnej wersji powiązań i bardziej usprawnione środowisko wykonawcze.

> **Występuje znany problem w 1. x z obsługą [przekierowywania powiązań](https://github.com/Azure/azure-functions-host/issues/992).** Problem jest specyficzny dla projektowania platformy .NET. Dotyczy to projektów z zależnościami w bibliotekach, które są różnymi wersjami z bibliotek uwzględnionych w środowisku uruchomieniowym. Zespół ds. funkcji zatwierdził konkretny postęp dla problemu. Zespół będzie kierował przekierowaniami powiązań w 2. x przed przeprowadzeniem ogólnej dostępności. Oficjalna instrukcja zespołu z sugerowanymi poprawkami i obejściami jest dostępna tutaj: [Rozpoznawanie zestawu w Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).

Aby uzyskać więcej informacji, zobacz [porównanie 1. x i 2. x](https://docs.microsoft.com/azure/azure-functions/functions-versions).

## <a name="programming-language-support"></a>Obsługa języków programowania

Następujące języki są obsługiwane w ogólnej dostępności (GA), w wersji zapoznawczej lub eksperymentalnej.

|Język      |1.x         |2.x      |
|--------------|------------|---------|
|**C#**        |POWSZECHNE          |Wersja zapoznawcza  |
|**JavaScript**|POWSZECHNE          |Wersja zapoznawcza  |
|**F#**        |POWSZECHNE          |         |
|**Java**      |            |Wersja zapoznawcza  |
|**Python**    |Eksperymentalne|         |
|**PHP**       |Eksperymentalne|         |
|**TypeScript**|Eksperymentalne|         |
|**Sekwencja**     |Eksperymentalne|         |
|**Bash**      |Eksperymentalne|         |
|**Program PowerShell**|Eksperymentalne|         |

Aby uzyskać więcej informacji, zobacz [obsługiwane języki](https://docs.microsoft.com/azure/azure-functions/supported-languages).

## <a name="app-service-plans"></a>Plany usługi App Service

Funkcje są obsługiwane przez *plan usługi App Service*. Plan definiuje zasoby używane przez aplikację Functions. Można przypisać plany do regionu, określić rozmiar i liczbę maszyn wirtualnych, które będą używane, i wybrać warstwę cenową. W przypadku prawdziwej metody bezserwerowej aplikacje funkcji mogą korzystać z planu **zużycia** . Plan zużycia spowoduje automatyczne skalowanie zaplecza na podstawie obciążenia.

Aby uzyskać więcej informacji, zobacz [plany usługi App Service](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).

## <a name="create-your-first-function"></a>Tworzenie pierwszej funkcji

Istnieją trzy typowe sposoby tworzenia aplikacji funkcji.

* Funkcje skryptów w portalu.
* Tworzenie niezbędnych zasobów przy użyciu interfejsu wiersza polecenia platformy Azure (CLI).
* Twórz funkcje lokalnie przy użyciu ulubionego środowiska IDE i publikuj je na platformie Azure.

Aby uzyskać więcej informacji na temat tworzenia funkcji skryptowej w portalu, zobacz [Tworzenie pierwszej funkcji w Azure Portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).

Aby skompilować z poziomu interfejsu wiersza polecenia platformy Azure, zobacz [Tworzenie pierwszej funkcji przy użyciu interfejsu wiersza polecenia platformy Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).

Aby utworzyć funkcję z programu Visual Studio, zobacz [Tworzenie pierwszej funkcji przy użyciu programu Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).

## <a name="understand-triggers-and-bindings"></a>Omówienie wyzwalaczy i powiązań

Funkcje są wywoływane przez *wyzwalacz* i mogą mieć dokładnie jeden. Oprócz wywoływania funkcji, niektóre wyzwalacze również pełnią rolę powiązań. Oprócz wyzwalacza można również zdefiniować wiele powiązań. *Powiązania* zapewniają deklaratywny sposób łączenia danych z kodem. Mogą być przekazywane (dane wejściowe) lub odbierać dane (dane wyjściowe). Wyzwalacze i powiązania ułatwiają korzystanie z funkcji. Powiązania usuwają koszty ręcznego tworzenia połączeń bazy danych lub systemu plików. Wszystkie informacje dotyczące powiązań są zawarte w specjalnym pliku *Functions. JSON* dla skryptów lub zadeklarowane z atrybutami w kodzie.

Niektóre typowe wyzwalacze obejmują:

* Blob Storage: wywołaj funkcję, gdy plik lub folder zostanie przekazany lub zmieniony w magazynie.
* HTTP: wywoływanie funkcji, takiej jak interfejs API REST.
* Kolejka: wywoływanie funkcji, gdy istnieją elementy w kolejce.
* Czasomierz: wywołaj funkcję na zwykłych erze.

Przykłady powiązań obejmują:

* CosmosDB: łatwo Nawiązuj połączenie z bazą danych w celu załadowania lub zapisania plików.
* Table Storage: Pracuj z magazynem kluczy/wartości z aplikacji funkcji.
* Queue Storage: łatwo Pobieraj elementy z kolejki lub umieszczaj nowe elementy w kolejce.

Poniższy przykładowy plik *Functions. JSON* definiuje wyzwalacz i powiązanie:

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

W tym przykładzie funkcja jest wyzwalana przez zmianę w magazynie obiektów BLOB w `images` kontenerze. Informacje dotyczące pliku są przesyłane, więc wyzwalacz działa również jako powiązanie. Istnieje inne powiązanie, aby umieścić informacje w kolejce o `images`nazwie.

Oto C# skrypt dla funkcji:

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

Przykładem jest prosta funkcja, która przyjmuje nazwę pliku, który został zmodyfikowany lub przekazany do usługi BLOB Storage, i umieszcza go w kolejce do późniejszego przetwarzania.

Aby zapoznać się z pełną listą wyzwalaczy i powiązań, zobacz temat [Azure Functions wyzwalacze i koncepcje powiązań](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).

## <a name="proxies"></a>Serwery proxy

Serwery proxy zapewniają funkcję przekierowywania dla aplikacji. Serwery proxy uwidaczniają punkt końcowy i mapują ten punkt końcowy na inny zasób. Dzięki serwerom proxy można:

* Przekieruj żądanie przychodzące do innego punktu końcowego.
* Zmodyfikuj żądanie przychodzące przed jego przekazaniem.
* Zmodyfikuj lub Podaj odpowiedź.

Serwery proxy są używane w scenariuszach takich jak:

* Uproszczenie, skrócenie lub zmiana adresu URL.
* Zapewnianie spójnego prefiksu interfejsu API dla wielu usług zaplecza.
* Imitacja odpowiedzi na opracowywany punkt końcowy.
* Dostarczanie statycznej odpowiedzi do dobrze znanego punktu końcowego.
* Utrzymywanie spójności punktu końcowego interfejsu API podczas przenoszenia lub migrowania zaplecza.

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

`Domain Redirect` Serwer proxy przyjmuje skróconą trasę i mapuje go do zasobu o większej funkcji. Transformacja wygląda następująco:

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

Serwer proxy wykonuje wszystkie czynności wysyłane do głównego adresu URL`https://--shorturl--/`() i przekierowuje go do witryny dokumentacji. `Root`

Przykład korzystania z serwerów proxy przedstawiono na platformie Azure wideo [: Przenieś swoją aplikację do chmury, korzystając z bezserwerowego Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102). W czasie rzeczywistym aplikacja ASP.NET Core uruchomiona na lokalnym SQL Server jest migrowana do chmury platformy Azure. Serwery proxy służą do refaktoryzacji tradycyjnego projektu interfejsu API sieci Web do korzystania z funkcji.

Aby uzyskać więcej informacji na temat serwerów proxy, zobacz [Work with serwery proxy usługi Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-proxies).

>[!div class="step-by-step"]
>[Poprzedni](azure-serverless-platform.md)Następny
>[](application-insights.md)
