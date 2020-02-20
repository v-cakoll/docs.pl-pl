---
title: Powiązania i transporty WCF — gRPC dla deweloperów programu WCF
description: Dowiedz się, w jaki sposób różne powiązania i transporty WCF są porównywane z gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: ebe324eace8f5f418b920c59f6d72eaaa686ef02
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503350"
---
# <a name="wcf-bindings-and-transports"></a>Transporty i powiązania WCF

Windows Communication Foundation (WCF) ma wbudowane *powiązania* określające różne protokoły sieciowe, formaty przewodowe i inne szczegóły implementacji. gRPC wydajnie ma tylko jeden protokół sieciowy i jeden format transmisji. (Technicznie *można* dostosować format sieci, ale jest on poza zakresem tej książki). Prawdopodobnie wiesz, że gRPC oferuje najlepsze rozwiązanie w większości przypadków. 

Poniżej znajduje się krótka dyskusja dotycząca najbardziej odpowiednich powiązań WCF oraz sposób ich porównania z ich odpowiednikami w gRPC.

## <a name="nettcp"></a>NetTCP

Powiązanie NetTCP programu WCF umożliwia tworzenie trwałych połączeń, małych komunikatów i komunikatów dwukierunkowych. Działa jednak tylko między klientami i serwerami platformy .NET. gRPC umożliwia korzystanie z tych samych funkcji, ale jest obsługiwana w wielu językach programowania i platformach. 

gRPC ma wiele funkcji powiązania NetTCP usługi WCF, ale nie zawsze są zaimplementowane w ten sam sposób. Na przykład w programie WCF szyfrowanie jest kontrolowane przez konfigurację i obsługiwane w strukturze. W programie gRPC szyfrowanie jest uzyskiwane na poziomie połączenia za pośrednictwem protokołu HTTP/2 za pośrednictwem protokołu TLS.

## <a name="http"></a>HTTP

Powiązanie WCF o nazwie BasicHttpBinding jest zwykle oparte na tekście i używa protokołu SOAP jako formatu sieci. Jest to powolne w porównaniu do powiązania NetTCP. Jest on zazwyczaj używany do zapewnienia współdziałania międzyplatformowego lub połączenia przez infrastrukturę internetową. 

Odpowiednik w gRPC używa protokołu HTTP/2 jako podstawowej warstwy transportu z binarnym formatem sieci protobuf dla komunikatów. Pozwala to na oferowanie wydajności na poziomie usługi NetTCP oraz pełne współdziałanie Międzyplatformowe ze wszystkimi nowoczesnymi językami programowania i strukturami.

## <a name="named-pipes"></a>Nazwane potoki

Funkcja WCF dostarczyła powiązanie *nazwanych potoków* na potrzeby komunikacji między procesami na tym samym komputerze fizycznym. Pierwsze wydanie ASP.NET Core gRPC nie obsługuje nazwanych potoków. Dodawanie obsługi klienta i serwera dla potoków nazwanych (i gniazd domen systemu UNIX) jest celem przyszłej wersji.

## <a name="msmq"></a>Usługa MSMQ

Usługa MSMQ jest zastrzeżoną kolejką komunikatów systemu Windows. Powiązanie WCF z usługą MSMQ umożliwia "pożar i zapomnij" żądań od klientów, które mogą być przetwarzane w dowolnym momencie w przyszłości. gRPC nie zapewnia natywnej żadnej funkcjonalności kolejki komunikatów. 

Najlepszą alternatywą jest bezpośrednie użycie systemu obsługi komunikatów, takiego jak Azure Service Bus, RabbitMQ lub Kafka. Można zaimplementować ten program przy użyciu klienta umieszczania komunikatów bezpośrednio w kolejce lub gRPC usługi przesyłania strumieniowego klienta, która enqueues komunikaty.

## <a name="webhttpbinding"></a>WebHttpBinding

WebHttpBinding (znanego również jako REST WCF) z atrybutami `WebGet` i `WebInvoke` umożliwiają opracowywanie interfejsów API RESTful, które mogą wypowiadać kod JSON w czasie, gdy był to mniej typowy. Jeśli masz interfejs API RESTful utworzony za pomocą usługi WCF REST, rozważ migrację go do zwykłej aplikacji interfejsu API sieci Web MVC ASP.NET Core. Ta migracja zapewnia te same funkcje co konwersja do gRPC.

>[!div class="step-by-step"]
>[Poprzednie](wcf-endpoints-grpc-methods.md)
>[dalej](rpc-types.md)
