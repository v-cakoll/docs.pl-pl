---
title: Język definicji interfejsu — gRPC dla deweloperów WCF
description: Wprowadzenie do buforów protokołu IDL.
ms.date: 09/02/2019
ms.openlocfilehash: 1f304502bd0091f753a3d2f7854298f4bbf983f1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967629"
---
# <a name="interface-definition-language"></a>Język definicji interfejsu

Dzięki platformie WCF usługi mogą uwidaczniać metadane opisu przy użyciu języka definicji usługi sieci Web (WSDL), który jest generowany dynamicznie przy użyciu odbicia platformy .NET w czasie wykonywania. Deweloperzy mogą używać tych metadanych do generowania klientów dla tych usług, potencjalnie w innych językach, jeśli używane jest powiązanie niezależne od platformy, takie jak SOAP za pośrednictwem protokołu HTTP.

gRPC używa języka definicji interfejsu (IDL) z buforów protokołu. Bufory protokołu IDL to niestandardowy, niezależny od platformy język z otwartą specyfikacją. Deweloperzy mogą odkodować pliki `.proto` do opisywania usług wraz z ich danymi wejściowymi i wyjściowymi. Te pliki `.proto` mogą być następnie używane do generowania wycinków specyficznych dla języka lub platformy dla klientów i serwerów, co umożliwia komunikację wielu różnych platform. Dzięki udostępnieniu plików `.proto` zespoły mogą generować kod, aby korzystać z usług każdej z nich, bez potrzeby podejmowania zależności kodu.

Jedną z zalet protobuf IDL jest to, że językiem niestandardowym jest umożliwienie gRPC w pełni języków i platform niezależny od, a nie nie preferuje żadnej technologii.

Program protobuf IDL jest również przeznaczony dla ludzi zarówno do odczytu, jak i do zapisu, natomiast WSDL jest przeznaczony do odczytywania z komputera lub do zapisu. Zmiana języka WSDL usługi WCF zwykle wymaga wprowadzenia zmian w kodzie usługi, uruchomienia usługi i ponownego wygenerowania pliku WSDL z serwera. W przeciwieństwie do pliku `.proto`, zmiany są proste do zastosowania w edytorze tekstów i automatycznie przepływają przez wygenerowany kod. Program Visual Studio 2019 kompiluje pliki `.proto` w tle podczas ich zapisywania; w przypadku korzystania z innych edytorów, takich jak VS Code zmiany zostaną zastosowane po skompilowaniu projektu.

W porównaniu z XML, a szczególnie protokołu SOAP, komunikaty kodowane przy użyciu protobuf mają wiele zalet. Komunikaty protobuf są mniejsze niż te same dane serializowane w formacie XML protokołu SOAP, a kodowanie, dekodowanie i przekazywanie ich przez sieć może być szybsze.

Potencjalną wadą protobuf w porównaniu z protokołem SOAP jest to, że ponieważ komunikaty nie są czytelne, wymagane są dodatkowe narzędzia do debugowania zawartości komunikatów.

> [!TIP]
> Program *gRPC obsługuje* odbicie serwera na potrzeby dynamicznego uzyskiwania dostępu do usług bez wstępnie skompilowanych wycinków, chociaż jest on przeznaczony dla narzędzi ogólnego przeznaczenia niż w przypadku klientów specyficznych dla aplikacji. Aby uzyskać więcej informacji na temat odbicia serwera gRPC, zobacz repozytorium [gRPC/gRPC](https://github.com/grpc/grpc/blob/master/doc/server-reflection.md) w witrynie GitHub.

> [!NOTE]
> Format binarny WCF używany z powiązaniem NetTCP jest znacznie bardziej zbliżony do protobuf w zakresie kompaktowania i wydajności, ale NetTCP jest dostępny tylko dla klientów i serwerów platformy .NET, a protobuf jest rozwiązaniem dla wielu platform.

>[!div class="step-by-step"]
>[Poprzedni](approach.md)
>[Następny](network-protocols.md)
