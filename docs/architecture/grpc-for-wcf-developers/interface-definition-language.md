---
title: Język definicji interfejsu — gRPC dla deweloperów WCF
description: Wprowadzenie do buforów protokołu IDL.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 71bdf8bf488e0a5bed177817343051bcd7847d25
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184429"
---
# <a name="interface-definition-language"></a>Język definicji interfejsu

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Dzięki platformie WCF usługi mogą uwidaczniać metadane opisu przy użyciu języka definicji usługi sieci Web (WSDL), który jest generowany dynamicznie przy użyciu odbicia platformy .NET w czasie wykonywania. Deweloperzy mogą używać tych metadanych do generowania klientów dla tych usług, potencjalnie w innych językach, jeśli używane jest powiązanie niezależne od platformy, takie jak SOAP za pośrednictwem protokołu HTTP.

gRPC używa języka definicji interfejsu (IDL) z buforów protokołu. Bufory protokołu IDL to niestandardowy, niezależny od platformy język z otwartą specyfikacją. Deweloperzy mogą odkodować `.proto` pliki, aby opisywać usługi wraz z ich danymi wejściowymi i wyjściowymi. Te `.proto` pliki mogą być następnie używane do generowania wycinków charakterystycznych dla języka lub platformy dla klientów i serwerów, co umożliwia komunikację wielu różnych platform. Udostępnianie `.proto` plików, zespoły mogą generować kod do korzystania z usług innych osób, bez potrzeby podejmowania zależności kodu.

Jedną z zalet protobuf IDL jest to, że językiem niestandardowym jest umożliwienie gRPC w pełni języków i platform niezależny od, a nie nie preferuje żadnej technologii.

Program protobuf IDL jest również przeznaczony dla ludzi zarówno do odczytu, jak i do zapisu, natomiast WSDL jest przeznaczony do odczytywania z komputera lub do zapisu. Zmiana języka WSDL usługi WCF zwykle wymaga wprowadzenia zmian w kodzie usługi, uruchomienia usługi i ponownego wygenerowania pliku WSDL z serwera. W przeciwieństwie `.proto` do pliku, zmiany są proste do zastosowania w edytorze tekstów i automatycznie przepływają przez wygenerowany kod. Program Visual Studio 2019 `.proto` kompiluje pliki w tle podczas ich zapisywania; w przypadku używania innych edytorów, takich jak vs Code zmiany zostaną zastosowane po skompilowaniu projektu.

W porównaniu z XML, a szczególnie protokołu SOAP, komunikaty kodowane przy użyciu protobuf mają wiele zalet. Komunikaty protobuf są mniejsze niż te same dane serializowane w formacie XML protokołu SOAP, a kodowanie, dekodowanie i przekazywanie ich przez sieć może być szybsze.

Potencjalną wadą protobuf w porównaniu z protokołem SOAP jest to, że ponieważ komunikaty nie są czytelne, wymagane są dodatkowe narzędzia do debugowania zawartości komunikatów.

> [!TIP]
> Program *gRPC obsługuje* odbicie serwera na potrzeby dynamicznego uzyskiwania dostępu do usług bez wstępnie skompilowanych wycinków, chociaż jest on przeznaczony dla narzędzi ogólnego przeznaczenia niż w przypadku klientów specyficznych dla aplikacji. Aby uzyskać więcej informacji na temat odbicia serwera gRPC, zobacz repozytorium [gRPC/gRPC](https://github.com/grpc/grpc/blob/master/doc/server-reflection.md) w witrynie GitHub.

> [!NOTE]
> Format binarny WCF używany z powiązaniem NetTCP jest znacznie bardziej zbliżony do protobuf w zakresie kompaktowania i wydajności, ale NetTCP jest dostępny tylko dla klientów i serwerów platformy .NET, a protobuf jest rozwiązaniem dla wielu platform.

>[!div class="step-by-step"]
>[Poprzedni](approach.md)
>[Następny](network-protocols.md)
