---
title: Powiązania i transporty WCF — gRPC dla deweloperów WCF
description: Dowiedz się, jak różne powiązania I transporty WCF porównać do gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 3a295268b486578c70c2c98f1d05f89070daaeb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147727"
---
# <a name="wcf-bindings-and-transports"></a>Transporty i powiązania WCF

Windows Communication Foundation (WCF) ma wbudowane *powiązania,* które określają różne protokoły sieciowe, formaty przewodów i inne szczegóły implementacji. gRPC skutecznie ma tylko jeden protokół sieciowy i jeden format przewodowy. (Technicznie *można* dostosować format przewodu, ale to wykracza poza zakres tej książki.) Prawdopodobnie odkryjesz, że gRPC oferuje najlepsze rozwiązanie w większości przypadków.

Poniżej znajduje się krótka dyskusja na temat najbardziej odpowiednich powiązań WCF i jak porównują się one do ich odpowiedników w gRPC.

## <a name="nettcp"></a>Protokół NetTCP

Powiązanie NetTCP w cf umożliwia połączenia trwałe, małe wiadomości i dwukierunkowe wiadomości. Ale to działa tylko między klientami .NET i serwerów. gRPC umożliwia taką samą funkcjonalność, ale jest obsługiwana w wielu językach programowania i platformach.

gRPC ma wiele funkcji powiązania NetTCP WCF, ale nie zawsze są one implementowane w ten sam sposób. Na przykład w WCF szyfrowanie jest kontrolowane za pomocą konfiguracji i obsługiwane w ramach. W gRPC szyfrowanie jest osiągane na poziomie połączenia za pośrednictwem PROTOKOŁU HTTP/2 przez TLS.

## <a name="http"></a>HTTP

Powiązanie WCF o nazwie BasicHttpBinding jest zwykle oparte na tekście i używa protokołu SOAP jako formatu przewodowego. Jest powolny w porównaniu do powiązania NetTCP. Zazwyczaj służy do zapewnienia interoperacyjności między platformami lub połączenia przez infrastrukturę internetową.

Odpowiednik w gRPC używa HTTP/2 jako podstawowej warstwy transportowej z binarnym formatem przewodu Protobuf dla wiadomości. Dzięki nim można zaoferować wydajność na poziomie usług NetTCP i pełną współdziałanie między platformami ze wszystkimi nowoczesnymi językami programowania i strukturami.

## <a name="named-pipes"></a>Nazwane potoki

WCF pod *warunkiem, nazwane potoki* powiązania do komunikacji między procesami na tej samej maszynie fizycznej. Pierwsza wersja ASP.NET Core gRPC nie obsługuje nazwanych potoków. Dodanie obsługi klienta i serwera dla nazwanych potoków (i gniazd domenu Uniksa) jest celem przyszłej wersji.

## <a name="msmq"></a>Usługa MSMQ

Usługa MSMQ to zastrzeżona kolejka komunikatów systemu Windows. Powiązanie WCF z msmq umożliwia "fire and forget" żądania od klientów, które mogą być przetwarzane w dowolnym momencie w przyszłości. gRPC nie udostępnia natywnie żadnych funkcji kolejki komunikatów.

Najlepszą alternatywą jest bezpośrednie użycie systemu obsługi wiadomości, takiego jak usługa Azure Service Bus, RabbitMQ lub Kafka. Można to zaimplementować z klientem wprowadzania wiadomości bezpośrednio do kolejki lub usługi przesyłania strumieniowego klienta gRPC, który umieszcza w kolejce wiadomości.

## <a name="webhttpbinding"></a>Powiązanie w sieci WebHttp

WebHttpBinding (znany również jako WCF `WebGet` `WebInvoke` REST), z i atrybutów, umożliwia tworzenie interfejsów API RESTful, które mogą mówić JSON w czasie, gdy było to mniej powszechne. Jeśli masz restful interfejsu API zbudowany z WCF REST, należy rozważyć migrację go do regularnych ASP.NET core MVC aplikacji Web API. Ta migracja zapewni taką samą funkcjonalność jak konwersja do gRPC.

>[!div class="step-by-step"]
>[Poprzedni](wcf-endpoints-grpc-methods.md)
>[następny](rpc-types.md)
