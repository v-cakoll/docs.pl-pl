---
title: Powiązania i transporty WCF — gRPC dla deweloperów programu WCF
description: Dowiedz się, w jaki sposób różne powiązania i transporty WCF są porównywane z gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 233e3d030bc1f4450bd5cd6a7d7770486ca9e95a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966901"
---
# <a name="wcf-bindings-and-transports"></a>Transporty i powiązania WCF

Funkcja WCF ma wiele różnych wbudowanych *powiązań* , które określają różne protokoły sieciowe, formaty przewodowe i inne szczegóły implementacji. gRPC wydajnie ma tylko jeden protokół sieciowy i jeden format sieci (technicznie można *dostosować format przewodu* , ale jest on poza zakresem tej książki). Prawdopodobnie odkryjesz, że gRPC oferuje najlepsze rozwiązanie w większości przypadków. Poniżej przedstawiono krótką dyskusję na temat najbardziej odpowiednich powiązań WCF oraz sposób ich porównania z ich odpowiednikiem w gRPC.

## <a name="nettcp"></a>NetTCP

Powiązanie NetTCP programu WCF umożliwia tworzenie trwałych połączeń, małych komunikatów i komunikatów dwukierunkowych, ale tylko między klientami i serwerami platformy .NET. gRPC umożliwia korzystanie z tych samych funkcji, ale jest obsługiwana w wielu językach programowania i platformach. gRPC ma wiele funkcji powiązania NetTCP WCF, chociaż nie zawsze są zaimplementowane w ten sam sposób. Na przykład w programie WCF szyfrowanie jest kontrolowane przez konfigurację i obsługiwane w strukturze. W programie gRPC szyfrowanie jest uzyskiwane na poziomie połączenia przy użyciu protokołu HTTP/2 za pośrednictwem protokołu TLS.

## <a name="http"></a>HTTP

BasicHttpBinding WCF jest zwykle oparty na tekście, przy użyciu protokołu SOAP jako formatu sieci i jest powolne w porównaniu do powiązania NetTCP. Jest on zazwyczaj używany do zapewnienia współdziałania międzyplatformowego lub połączenia przez infrastrukturę internetową. Odpowiednik w gRPC — ponieważ używa protokołu HTTP/2 jako podstawowej warstwy transportu z binarnym formatem sieci protobuf dla komunikatów — może oferować NetTCP wydajność na poziomie usług, ale z pełną współdziałaniem międzyplatformowym ze wszystkimi nowoczesnymi językami programowania i platform.

## <a name="named-pipes"></a>Nazwane potoki

Funkcja WCF dostarczyła powiązanie nazwanych potoków na potrzeby komunikacji między procesami na tym samym komputerze fizycznym. Nazwane potoki nie są obsługiwane przez pierwszą wersję ASP.NET Core gRPC. Dodawanie obsługi klienta i serwera dla potoków nazwanych (i gniazd domen systemu UNIX) jest celem przyszłej wersji.

## <a name="msmq"></a>Usługa MSMQ

Usługa MSMQ jest zastrzeżoną kolejką komunikatów systemu Windows. Powiązanie WCF z usługą MSMQ umożliwia "pożar i zapomnij" żądań od klientów, które mogą być przetwarzane w dowolnym momencie w przyszłości. gRPC nie zapewnia natywnej żadnej funkcjonalności kolejki komunikatów. Najlepszą alternatywą byłoby bezpośrednie użycie systemu obsługi komunikatów, takiego jak Azure Service Bus, RabbitMQ lub Kafka. Może to zostać zaimplementowane przy użyciu klienta umieszczania komunikatów bezpośrednio w kolejce lub gRPC usługi przesyłania strumieniowego klienta, która enqueues komunikaty.

## <a name="webhttpbinding"></a>WebHttpBinding

Element WebHttpBinding (znany również jako ReST WCF), z atrybutami `WebGet` i `WebInvoke`, umożliwia opracowywanie interfejsów API ReSTful, które mogą wypowiadać dane JSON w czasie, gdy były one mniej powszechne niż teraz. W związku z tym, jeśli masz interfejs API RESTful utworzony za pomocą usługi WCF REST, rozważ migrację go do zwykłej aplikacji interfejsu API sieci Web MVC ASP.NET Core, która zapewni funkcję podobną, a nie konwertowanie na gRPC.

>[!div class="step-by-step"]
>[Poprzedni](wcf-endpoints-grpc-methods.md)
>[Następny](rpc-types.md)
