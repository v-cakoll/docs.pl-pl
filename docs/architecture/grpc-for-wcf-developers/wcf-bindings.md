---
title: Powiązania i transporty WCF — gRPC dla deweloperów programu WCF
description: Dowiedz się, w jaki sposób różne powiązania i transporty WCF są porównywane z gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 50bac73ee68d7156fc5fed55dfffb3ba7f2de924
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184058"
---
# <a name="wcf-bindings-and-transports"></a>Powiązania i transporty WCF

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Funkcja WCF ma wiele różnych wbudowanych *powiązań* , które określają różne protokoły sieciowe, formaty przewodowe i inne szczegóły implementacji. gRPC wydajnie ma tylko jeden protokół sieciowy i jeden format sieci (technicznie można *dostosować format przewodu* , ale jest on poza zakresem tej książki). Prawdopodobnie odkryjesz, że gRPC oferuje najlepsze rozwiązanie w większości przypadków. Poniżej przedstawiono krótką dyskusję na temat najbardziej odpowiednich powiązań WCF oraz sposób ich porównania z ich odpowiednikiem w gRPC.

## <a name="nettcp"></a>NetTCP

Powiązanie NetTCP programu WCF umożliwia tworzenie trwałych połączeń, małych komunikatów i komunikatów dwukierunkowych, ale tylko między klientami i serwerami platformy .NET. gRPC umożliwia korzystanie z tych samych funkcji, ale jest obsługiwana w wielu językach programowania i platformach. gRPC ma wiele funkcji powiązania NetTCP WCF, chociaż nie zawsze są zaimplementowane w ten sam sposób. Na przykład w programie WCF szyfrowanie jest kontrolowane przez konfigurację i obsługiwane w strukturze. W programie gRPC szyfrowanie jest uzyskiwane na poziomie połączenia przy użyciu protokołu HTTP/2 za pośrednictwem protokołu TLS.

## <a name="http"></a>HTTP

BasicHttpBinding WCF jest ogólnie oparta na tekście, przy użyciu protokołu SOAP jako formatu sieci i jest bardzo powolny przez standardy nowoczesnych aplikacji sieciowych. Jest on naprawdę używany tylko w celu zapewnienia współdziałania międzyplatformowego lub połączenia przez infrastrukturę internetową. Odpowiednik w gRPC — ponieważ używa protokołu HTTP/2 jako podstawowej warstwy transportu z binarnym formatem sieci protobuf dla komunikatów — może oferować NetTCP wydajność na poziomie usług, ale z pełną współdziałaniem międzyplatformowym ze wszystkimi nowoczesnymi językami programowania i platform.

## <a name="named-pipes"></a>Nazwane potoki

Funkcja WCF dostarczyła powiązanie nazwanych potoków na potrzeby komunikacji między procesami na tym samym komputerze fizycznym. Nazwane potoki nie są obsługiwane przez pierwszą wersję ASP.NET Core gRPC.

Poza systemem Windows funkcje udostępniane przez nazwane potoki są zwykle dostarczane przez gniazda domen systemu UNIX. Te gniazda są regularnymi sieciami podobnymi do protokołu TCP, które są reprezentowane przez `/var/run/docker.sock`adresy systemu plików, takie jak, które gRPC mogą współpracowały zarówno jako klient, jak i serwer. Jeśli potrzebujesz użyć funkcji stylu nazwanych potoków w systemie Windows, Następna aktualizacja systemu Windows 10 i Windows Server w 2019 kwartale, dodaje gniazda domeny jako w pełni obsługiwaną funkcję natywną w systemie Windows. W związku z tym usługi gRPC Services działające w tych i nowszych wersjach systemu Windows (lub Linux) mogą używać gniazd domen zamiast potoków nazwanych. Jeśli jednak zespół nie jest w stanie zaktualizować do najnowszej wersji systemu Windows, należy użyć hosta lokalnego TCP Sockets. Zagadnienia dotyczące zabezpieczeń dotyczące używania lokalnych gniazd TCP można rozwiązać przy użyciu uwierzytelniania certyfikatów między klientem i serwerem.

## <a name="msmq"></a>Usługa MSMQ

Usługa MSMQ jest zastrzeżoną kolejką komunikatów systemu Windows. Powiązanie WCF z usługą MSMQ umożliwia "pożar i zapomnij" żądań od klientów, które mogą być przetwarzane w dowolnym momencie w przyszłości. gRPC nie zapewnia natywnej żadnej funkcjonalności kolejki komunikatów. Najlepszą alternatywą byłoby bezpośrednie użycie systemu obsługi komunikatów, takiego jak Azure Service Bus, RabbitMQ lub Kafka. Może to zostać zaimplementowane przy użyciu klienta umieszczania komunikatów bezpośrednio w kolejce lub gRPC usługi przesyłania strumieniowego klienta, która enqueues komunikaty.

## <a name="webhttpbinding"></a>WebHttpBinding

WebHttpBinding (znana także jako REST WCF) z `WebGet` atrybutami i `WebInvoke` , które umożliwiają opracowywanie interfejsów API ReSTful, które mogą wypowiedzieć kod JSON w czasie, gdy był to mniej powszechny niż teraz. W związku z tym, jeśli masz interfejs API RESTful utworzony za pomocą usługi WCF REST, rozważ migrację go do zwykłej aplikacji interfejsu API sieci Web MVC ASP.NET Core, która zapewni funkcję podobną, a nie konwertowanie na gRPC.

>[!div class="step-by-step"]
>[Poprzedni](wcf-endpoints-grpc-methods.md)
>[Następny](rpc-types.md)
