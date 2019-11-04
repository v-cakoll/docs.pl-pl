---
title: REST i gRPC
description: Dowiedz się więcej na temat gRPC, jego roli w aplikacjach natywnych w chmurze i jak różni się od protokołu HTTP REST
author: robvet
ms.date: 09/08/2019
ms.openlocfilehash: 80960a9042b1514fb78e7a8c993a1854067407e8
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73417134"
---
# <a name="rest-and-grpc"></a>REST i gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Do tej pory ta książka koncentruje się na komunikacji [opartej na protokole REST](https://docs.microsoft.com/azure/architecture/best-practices/api-design) . REST to styl architektury, który promuje współdziałanie między rozproszonymi systemami komputerowymi. Używa modelu żądania/odpowiedzi, gdzie każda odpowiedź z serwera jest żądaniem od klienta. Chociaż jest to bardzo popularne, nie jest to idealne rozwiązanie dla każdego problemu. Nowsza Technologia komunikacji, zatytułowana gRPC, umożliwia szybkie uzyskanie popularności i przekazanie jej do świata w chmurze.

## <a name="grpc"></a>gRPC

gRPC to komunikacja "open source", która pochodzi od firmy Google. Jest on oparty na modelu [zdalnego wywołania procedury (RPC)](https://en.wikipedia.org/wiki/Remote_procedure_call) , popularnym w ramach przetwarzania rozproszonego. Zgodnie z tym modelem, lokalny program kliencki uwidacznia metodę w procesie, aby wykonać operację. W tle to wywołanie jest wywoływane na mikrousługach pozaprocesowych w sieci rozproszonej. Deweloper koduje operację jako wywołanie procedury lokalnej. Bazowa platforma umożliwia podwyższenie poziomu komunikacji sieciowej, serializacji i wykonania w sieci punkt-punkt.

gRPC to nowoczesne środowisko RPC, które jest lekkie i wysoce wydajne. Protokół transportowy używa protokołu HTTP/2. Chociaż zgodne z protokołem HTTP 1,1, usługa HTTP/2 oferuje wiele zaawansowanych możliwości:

- Gdy HTTP 1,1 wysyła dane jako zwykły tekst, HTTP/2 jest protokołem binarnym. Umożliwia ona szybsze analizowanie danych przy użyciu mniejszej ilości pamięci, zmniejsza opóźnienie sieci dzięki powiązanym ulepszeniom, a także wydajniej zarządza zasobami sieci.
- Mimo że protokół HTTP 1,1 jest ograniczony do przetwarzania jednego żądania/odpowiedzi rundy w czasie, protokół HTTP/2 obsługuje multipleksowanie lub wiele żądań równoległych w ramach tego samego połączenia.
- Protokół HTTP/2 obsługuje komunikację w trybie pełnego dupleksu lub dwukierunkowego, w którym zarówno klient, jak i serwer i mogą komunikować się w tym samym czasie. Klient może przekazywać dane żądania w tym samym czasie, gdy serwer wysyła dane odpowiedzi z powrotem.
- Transmisja strumieniowa jest wbudowana w protokół HTTP/2, co oznacza, że oba żądania i odpowiedzi mogą asynchronicznie przesyłać strumieniowo duże zestawy danych.
- Łączenie gRPC i HTTP/2 powoduje znaczne zwiększenie wydajności. W [Windows Communication Foundation (WCF)](https://docs.microsoft.com/dotnet/framework/wcf/whats-wcf) sprzężeniem wydajność gRPC jest zgodna i przekracza szybkość i wydajność [powiązań NetTCP](https://docs.microsoft.com/dotnet/api/system.servicemodel.nettcpbinding?view=netframework-4.8). Jednak w przeciwieństwie do NetTCP, gRPC nie jest ograniczone do języków firmy Microsoft, C# takich jak lub VB.NET.

gRPC jest obsługiwany na większości popularnych platform, w tym Java C#,, golang i NodeJS.

## <a name="protocol-buffers"></a>Bufory protokołu

gRPC obejmuje inną technologię "open source" o nazwie [bufory protokołu](https://developers.google.com/protocol-buffers/docs/overview) lub komunikaty protobuf do wysyłania i odbierania danych. Podobnie jak w przypadku [kontraktu danych programu WCF](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-data-contracts), protobuf deserializacji dane strukturalne dla systemów do odczytu i zapisu. Zmniejsza to obciążenie, które można odczytać przez człowieka, np. XML lub JSON.

Wiele technik serializacji obiektów odzwierciedla strukturę obiektów danych w czasie wykonywania. Protobuf wymaga zdefiniowania struktury z góry w języku niezależny od Language (Language buffering Protocol). Każda definicja jest przechowywana w pliku ". proto". Następnie przy użyciu kompilatora protobuf "Proton" generowany jest kod klienta i serwera dla dowolnej z obsługiwanych platform. Wygenerowany kod jest zoptymalizowany pod kątem szybkiego serializacji/deserializacji danych. W środowisku uruchomieniowym każdy komunikat jest opakowany w kontrakt usługi o jednoznacznie określonym typie i serializowany w standardowej reprezentacji protobuf.

## <a name="grpc-support-in-net"></a>Obsługa gRPC w programie .NET

Microsoft .NET Core Framework 3,0 zawiera narzędzia i natywną obsługę gRPC. Rysunek 4-20 pokazuje szablon programu Visual Studio 2019, który tworzy szkielet projektu szkieletu gRPC dla usługi gRPC. Zwróć uwagę, jak platforma .NET Core obsługuje platformy Windows, Linux i macOS.

![Obsługa gRPC w programie Visual Studio 2019](./media/visual-studio-2019-grpc-template.png)

**Rysunek 4-20**. Obsługa gRPC w programie Visual Studio 2019

Program .NET Core 3,0 bezproblemowo integruje gRPC z platformą, w tym Routing punktów końcowych, wbudowaną obsługę IoC i rejestrowanie. Serwer sieci Web Kestrel "open source" w pełni obsługuje połączenia HTTP/2.

Rysunek 4-21 przedstawia strukturę usługi gRPC w programie Visual Studio 2019. Zwróć uwagę, jak struktura folderów zawiera foldery dla plików PROTO i kodu usługi.

![projekt gRPC w programie Visual Studio 2019](./media/grpc-project.png  )

**Rysunek 4-21**. projekt gRPC w programie Visual Studio 2019

## <a name="grpc-usage"></a>gRPC użycie

gRPC są odpowiednie dla następujących scenariuszy:

- Niska opóźnienia i komunikacja o dużej przepływności. gRPC doskonale nadaje się do lekkich mikrousług, w których wydajność jest krytyczna.
- Komunikacja punkt-punkt w czasie rzeczywistym. gRPC ma doskonałą obsługę przesyłania strumieniowego dwukierunkowego. usługi gRPC umożliwiają wypychanie komunikatów w czasie rzeczywistym bez sondowania.
- Środowiska Polyglot — narzędzia gRPC obsługują większość popularnych języków programistycznych, co sprawia, że jest to dobry wybór w środowiskach wielojęzycznych.
- Środowiska ograniczone przez sieć — komunikaty gRPC są serializowane z protobuf, formatem uproszczonego komunikatu. Komunikat gRPC jest zawsze krótszy niż odpowiedni komunikat JSON.

W momencie pisania tej książki większość przeglądarek ma ograniczoną obsługę gRPC. gRPC intensywnie używa funkcji protokołu HTTP/2 i żadna przeglądarka nie zapewnia poziomu kontroli wymaganego w przypadku żądań sieci Web do obsługi klienta gRPC. gRPC jest zazwyczaj używany do komunikacji wewnętrznej mikrousługi z mikrousługą. Rysunek 4-22 pokazuje prosty, ale typowy wzorzec użycia.

![Wzorce użycia gRPC](./media/grpc-usage.png)

**Rysunek 4-22**. wzorce użycia gRPC

Zwróć uwagę na powyższym rysunku, w jaki sposób wywoływany jest ruch frontonu przy użyciu protokołu HTTP, a wewnętrzna mikrousługa do mikrousług używa gRPC.

Patrząc na przyszłość, gRPC może odgrywać główną rolę w dethroning dominacji dla systemów natywnych w chmurze. Zalety wydajności i łatwość programowania są zbyt dobre. Jednak nie należy wprowadzać żadnych błędu, reszta będzie nadal przez długi czas. Nadal są dostępne publicznie udostępniane interfejsy API i ze względu na zgodność z poprzednimi wersjami.

>[!div class="step-by-step"]
>[Poprzedni](service-to-service-communication.md)
>[dalej](service-mesh-communication-infrastructure.md)
