---
title: grpc
description: Dowiedz się więcej o gRPC, jego roli w aplikacjach natywnych dla chmury i o tym, czym różni się od komunikacji HTTP RESTful.
author: robvet
ms.date: 03/31/2020
ms.openlocfilehash: 28a07ad5ec105d3fc5b65e4cf0ac0cd85eb16627
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80524174"
---
# <a name="grpc"></a>grpc

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Do tej pory w tej książce skupiliśmy się na komunikacji opartej na [REST.](https://docs.microsoft.com/azure/architecture/best-practices/api-design) Widzieliśmy, że REST jest elastyczny styl architektoniczny, który definiuje operacji opartych na CRUD względem zasobów jednostki. Klienci współdziałają z zasobami w interfejsie HTTP za pomocą modelu komunikacji żądanie/odpowiedzi. Podczas gdy REST jest szeroko wdrażany, nowsza technologia komunikacyjna, gRPC, nabrała ogromnego rozpędu w całej społeczności natywnej chmury.

## <a name="what-is-grpc"></a>Co to jest gRPC?

gRPC to nowoczesna, wysokowydajna struktura, która rozwija odwieczny protokół [zdalnego wywołania procedury (RPC).](https://en.wikipedia.org/wiki/Remote_procedure_call) Na poziomie aplikacji gRPC usprawnia komunikację między klientami a usługami zaplecza. Pochodzący z Google gRPC jest open source i częścią ekosystemu [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) ofert natywnych dla chmury. CNCF uważa gRPC za [projekt inkubujący.](https://github.com/cncf/toc/blob/master/process/graduation_criteria.adoc) Inkubacja oznacza, że użytkownicy końcowi korzystają z tej technologii w zastosowaniach produkcyjnych, a projekt ma zdrową liczbę uczestników.

Typowa aplikacja kliencka gRPC udostępni lokalną funkcję w procesie, która implementuje operację biznesową. W obszarze obejmuje tej funkcji lokalnej wywołuje inną funkcję na komputerze zdalnym. To, co wydaje się być wywołaniem lokalnym, zasadniczo staje się przezroczystym wywołaniem poza procesem usługi zdalnej. Instalacja wodno-kanalizacyjna RPC streszcza komunikację sieciową typu point-to-point, serializację i wykonywanie między komputerami.

W aplikacjach natywnych dla chmury deweloperzy często pracują w różnych językach programowania, strukturach i technologiach. Ta *interoperacyjność* komplikuje kontrakty komunikatów i instalację wodno-kanalizacyjną wymaganą do komunikacji między platformami.  gRPC zapewnia "jednolitą warstwę poziomą", która streszcza te obawy. Kod programistów na ich natywnej platformie koncentruje się na funkcjonalności biznesowej, podczas gdy gRPC obsługuje instalację wodno-kanalizacyjną komunikacji.

gRPC oferuje kompleksowe wsparcie w większości popularnych stosów deweloperskich, w tym Java, JavaScript, C#, Go, Swift i NodeJS.

## <a name="grpc-benefits"></a>Korzyści gRPC

GRPC używa protokołu HTTP/2 dla swojego protokołu transportu. Chociaż jest kompatybilny z protokołem HTTP 1.1, HTTP/2 oferuje wiele zaawansowanych funkcji:

- Protokół binarny do transportu danych — w przeciwieństwie do PROTOKOŁU HTTP 1.1, który wysyła dane jako tekst bezwyzowy.
- Obsługa multipleksowania dla wysyłania wielu równoległych żądań za pośrednictwem tego samego połączenia — HTTP 1.1 ogranicza przetwarzanie do jednej wiadomości żądania/odpowiedzi naraz.
- Dwukierunkowa komunikacja pełnodupleksowa do jednoczesnego wysyłania żądań klientów i odpowiedzi serwera.
- Wbudowane przesyłanie strumieniowe umożliwiające żądania i odpowiedzi na asynchronicznie strumienia dużych zestawów danych.

gRPC jest lekki i bardzo wydajny. Może być nawet 8 razy szybszy niż serializacja JSON z wiadomościami o 60-80% mniejszymi. W żargonie Microsoft [Windows Communication Foundation (WCF)](https://docs.microsoft.com/dotnet/framework/wcf/whats-wcf) wydajność gRPC przekracza szybkość i wydajność wysoce zoptymalizowanych [powiązań NetTCP](https://docs.microsoft.com/dotnet/api/system.servicemodel.nettcpbinding?view=netframework-4.8). W przeciwieństwie do NetTCP, który faworyzuje stos Microsoft, gRPC jest wieloplatformowy.

## <a name="protocol-buffers"></a>Bufory protokołu

gRPC obejmuje technologię open source o nazwie [Bufory protokołów.](https://developers.google.com/protocol-buffers/docs/overview) Zapewniają one wysoce wydajny i neutralny dla platformy format serializacji do serializacji wiadomości strukturalnych, które usługi wysyłają do siebie nawzajem. Za pomocą języka definicji interfejsu między platformami (IDL), deweloperzy zdefiniować umowę serwisową dla każdej mikrousługi. Umowa, zaimplementowana jako `.proto` plik tekstowy, opisuje metody, dane wejściowe i wyjściowe dla każdej usługi. Ten sam plik umowy może być używany dla klientów gRPC i usług zbudowanych na różnych platformach programisty.

Za pomocą pliku proto, kompilator `protoc`Protobuf, generuje zarówno kod klienta i usługi dla platformy docelowej. Kod zawiera następujące składniki:

- Silnie typizowane obiekty, współużytkowane przez klienta i usługi, które reprezentują operacje usługi i elementy danych dla wiadomości.
- Silnie typizowana klasa podstawowa z wymaganą siecią wodno-kanalizacyjną, którą może dziedziczyć i rozszerzać zdalna usługa gRPC.
- Wycinek klienta, który zawiera wymagane instalacji wodno-kanalizacyjnej do wywołania zdalnej usługi gRPC.

W czasie wykonywania każda wiadomość jest serializowana jako standardowa reprezentacja Protobuf i wymieniana między klientem a usługą zdalną. W przeciwieństwie do JSON lub XML, protobuf wiadomości są serializowane jako skompilowane bajtów binarnych.

Książka, [gRPC dla WCF Developers](https://docs.microsoft.com/dotnet/architecture/grpc-for-wcf-developers/), dostępna w witrynie Microsoft Architecture, zapewnia szczegółowe pokrycie gRPC i buforów protokołów.

## <a name="grpc-support-in-net"></a>Obsługa gRPC w .NET

GRPC jest zintegrowany z .NET Core 3.0 SDK lub nowszym. Obsługują go następujące narzędzia:

- Visual Studio 2019, wersja 16.3 lub nowsza, z zainstalowanym obciążeniem tworzenia sieci Web.
- Visual Studio Code
- dotnet CLI

Zestaw SDK zawiera narzędzia do routingu punktów końcowych, wbudowanego ioC i rejestrowania. Serwer internetowy Kestrel typu open source obsługuje połączenia HTTP/2. Rysunek 4-20 przedstawia szablon programu Visual Studio 2019, który szkielet projektu dla usługi gRPC. Zwróć uwagę, jak program .NET Core w pełni obsługuje systemy Windows, Linux i macOS.

![Obsługa gRPC w programie Visual Studio 2019](./media/visual-studio-2019-grpc-template.png)

**Rysunek 4-20**. Obsługa gRPC w programie Visual Studio 2019
  
Rysunek 4-21 przedstawia usługę szkieletu gRPC wygenerowaną z wbudowanych szkieletów zawartych w programie Visual Studio 2019.  

![Projekt gRPC w programie Visual Studio 2019](./media/grpc-project.png  )

**Rysunek 4-21**. Projekt gRPC w programie Visual Studio 2019

Na poprzednim rysunku zanotuj plik opisu proto i kod usługi. Jak zobaczysz wkrótce, Visual Studio generuje dodatkową konfigurację w klasie uruchamiania i pliku projektu źródłowego.

## <a name="grpc-usage"></a>Użycie gRPC

Uprzywilejowanie gRPC dla następujących scenariuszy:

- Synchroniczne wewnętrznej bazy danych mikrousług do mikrousług komunikacji, gdzie natychmiastowa odpowiedź jest wymagana do kontynuowania przetwarzania.
- Środowiska polyglota, które muszą obsługiwać mieszane platformy programowania.
- Małe opóźnienia i wysoka przepustowość komunikacji, gdzie wydajność ma kluczowe znaczenie.
- Komunikacja w czasie rzeczywistym typu point-to-point - gRPC może wypychać wiadomości w czasie rzeczywistym bez sondowania i ma doskonałe wsparcie dla dwukierunkowego przesyłania strumieniowego.
- Środowiska ograniczone siecią — binarne komunikaty gRPC są zawsze mniejsze niż równoważny tekstowy komunikat JSON.

W tym czasie, z tego pisania, gRPC jest używany głównie z usługami zaplecza. Większość nowoczesnych przeglądarek nie może zapewnić poziomu kontroli HTTP/2 wymaganego do obsługi klienta gRPC front-end. To powiedziawszy, istnieje [wczesna inicjatywa,](https://devblogs.microsoft.com/aspnet/grpc-web-experiment/) która umożliwia komunikację gRPC z aplikacji opartych na przeglądarce zbudowanych za pomocą technologii JavaScript lub Blazor WebAssembly. [GRPC-Web for .NET](https://github.com/grpc/grpc/blob/master/doc/PROTOCOL-WEB.md) umożliwia ASP.NET aplikacji Core gRPC do obsługi funkcji gRPC w aplikacjach przeglądarki:

- Klienci silnie typizowani generowani przez kod
- Kompaktowe komunikaty Protobuf
- Przesyłanie strumieniowe serwera

## <a name="grpc-implementation"></a>Implementacja gRPC

Architektura referencyjna mikrousług, [eShop on Containers](https://github.com/dotnet-architecture/eShopOnContainers)od firmy Microsoft, pokazuje, jak zaimplementować usługi gRPC w aplikacjach .NET Core. Rysunek 4-22 przedstawia architekturę zaplecza.

![Architektura zaplecza dla sklepu eShop na kontenerach](./media/eshop-with-aggregators.png)

**Rysunek 4-22**. Architektura zaplecza dla sklepu eShop na kontenerach

Na poprzednim rysunku należy zwrócić uwagę, jak sklep internetowy obejmuje [wzorzec wewnętrznej bazy dla frontendów](https://docs.microsoft.com/azure/architecture/patterns/backends-for-frontends) (BFF), udostępniając wiele bram interfejsu API. Omówiliśmy wzór BFF wcześniej w tym rozdziale. Należy zwrócić szczególną uwagę na mikrousługi agregatora (w kolorze szarym), który znajduje się między bramą interfejsu API zakupów sieci Web i wewnętrznej bazy danych zakupy mikrousług. Agregator odbiera pojedyncze żądanie od klienta, wysyła go do różnych mikrousług, agreguje wyniki i wysyła je z powrotem do klienta żądającego. Takie operacje zazwyczaj wymagają komunikacji synchroniczowej, aby uzyskać natychmiastową odpowiedź. W sklepie internetowym wywołania zaplecza z agregatora są wykonywane przy użyciu gRPC, jak pokazano na rysunku 4-23.

![gRPC w eShop na kontenerach](./media/grpc-implementation.png)

**Rysunek 4-23**. gRPC w eShop na kontenerach

Komunikacja gRPC wymaga zarówno składników klienta, jak i serwera. Na poprzednim rysunku należy zwrócić uwagę na sposób, w jaki agregator zakupów implementuje klienta gRPC. Klient wykonuje synchroniczne wywołania gRPC (na czerwono) do mikrousług wewnętrznej bazy danych, z których każda implementuje serwer gRPC. Zarówno klient, jak i serwer korzystają z wbudowanej instalacji wodno-kanalizacyjnej gRPC z pliku .NET Core 3.0 SDK. *Wycinki* po stronie klienta zapewniają instalację wodno-kanalizacyjną do wywoływania zdalnych wywołań gRPC. Składniki po stronie serwera zapewniają gRPC instalacji wodno-kanalizacyjne, które klasy usług niestandardowych można dziedziczyć i zużywać.

Mikrousługi, które udostępniają zarówno restful interfejsu API i gRPC komunikacji wymagają wielu punktów końcowych do zarządzania ruchem. Należy otworzyć punkt końcowy, który nasłuchuje ruchu HTTP dla wywołań RESTful i innego dla wywołań gRPC. Punkt końcowy gRPC musi być skonfigurowany dla protokołu HTTP/2, który jest wymagany do komunikacji gRPC.

Podczas gdy staramy się oddzielić mikrousług za pomocą wzorców komunikacji asynchronicznie, niektóre operacje wymagają bezpośrednich wywołań. gRPC powinien być podstawowym wyborem dla bezpośredniej synchroniczowej komunikacji między mikrousługami. Jego wysokowydajny protokół komunikacyjny, oparty na HTTP/2 i buforach protokołów, sprawia, że jest to doskonały wybór.

## <a name="looking-ahead"></a>Patrzenie w przyszłość

Patrząc w przyszłość, gRPC będzie nadal zyskiwać przyczepność dla systemów natywnych dla chmury. Korzyści z wydajności i łatwość rozwoju są atrakcyjne. Jednak REST będzie prawdopodobnie wokół przez długi czas. Wyróżnia się publicznie narażonych interfejsów API i ze względu na zgodność z powrotem.

>[!div class="step-by-step"]
>[Poprzedni](service-to-service-communication.md)
>[następny](service-mesh-communication-infrastructure.md)
