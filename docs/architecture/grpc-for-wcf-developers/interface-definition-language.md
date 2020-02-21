---
title: Język definicji interfejsu — gRPC dla deweloperów WCF
description: Wprowadzenie do buforów protokołu IDL.
ms.date: 09/02/2019
ms.openlocfilehash: 841f041ae350e76e648c71f9d6d113b9d39e0d3b
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543212"
---
# <a name="interface-definition-language"></a>Język definicji interfejsu

Dzięki Windows Communication Foundation (WCF) usługi mogą uwidaczniać metadane opisu przy użyciu języka definicji usługi sieci Web (WSDL). WSDL jest generowana dynamicznie przy użyciu odbicia platformy .NET w czasie wykonywania. Deweloperzy mogą używać tych metadanych do generowania klientów dla tych usług, potencjalnie w innych językach, jeśli korzystają z powiązań neutralnych dla platformy, takich jak SOAP za pośrednictwem protokołu HTTP.

gRPC używa języka definicji interfejsu (IDL) z buforów protokołu. Bufory protokołu IDL to niestandardowy, niezależny od platformy język z otwartą specyfikacją. Deweloperzy tworzą `.proto` pliki do opisywania usług wraz z ich danymi wejściowymi i wyjściowymi. Te pliki `.proto` mogą być następnie używane do generowania wycinków specyficznych dla języka lub platformy dla klientów i serwerów, co umożliwia komunikację wielu różnych platform. Udostępniając pliki `.proto`, zespoły mogą generować kod do korzystania z usług innych osób, bez potrzeby podejmowania zależności kodu.

Jedną z zalet protobuf IDL jest to, że jest to język niestandardowy, dzięki czemu gRPC być całkowicie językiem i platformą, a nie nie preferuje żadnej technologii.

Program protobuf IDL jest również przeznaczony dla ludzi zarówno do odczytu, jak i do zapisu, natomiast WSDL jest przeznaczony do odczytywania z komputera lub do zapisu. Zmiana WSDL usługi WCF zwykle wymaga zmiany usługi, uruchomienia usługi i ponownego wygenerowania pliku WSDL z serwera. W przeciwieństwie do pliku `.proto`, zmiany są proste do zastosowania w edytorze tekstów i automatycznie przepływają przez wygenerowany kod. Program Visual Studio 2019 kompiluje pliki `.proto` w tle podczas ich zapisywania. W przypadku innych edytorów, takich jak VS Code, zmiany są stosowane podczas kompilowania projektu.

W porównaniu z XML, a szczególnie protokołu SOAP, komunikaty kodowane przy użyciu protobuf mają wiele zalet. Komunikaty protobuf są mniejsze niż te same dane serializowane w formacie XML protokołu SOAP, a kodowanie, dekodowanie i przekazywanie ich za pośrednictwem sieci może być szybsze.

Potencjalną wadą protobuf w porównaniu z protokołem SOAP jest to, że ponieważ wiadomości nie są odczytywane przez ludzi, do debugowania zawartości wiadomości są wymagane dodatkowe narzędzia.

> [!TIP]
> Program *gRPC obsługuje* odbicie serwera na potrzeby dynamicznego dostępu do usług bez wstępnie skompilowanych wycinków, chociaż nie jest to zamierzone dla narzędzi ogólnego przeznaczenia niż w przypadku klientów specyficznych dla aplikacji. Aby uzyskać więcej informacji, zobacz [GRPC Server odbić Protocol](https://github.com/grpc/grpc/blob/master/doc/server-reflection.md) w serwisie GitHub.

> [!NOTE]
> Format binarny WCF używany z powiązaniem NetTCP jest znacznie bardziej zbliżony do protobuf w zakresie kompaktowania i wydajności. Jednak NetTCP można używać tylko między klientami i serwerami platformy .NET, a protobuf to rozwiązanie dla wielu platform.

>[!div class="step-by-step"]
>[Poprzednie](approach.md)
>[dalej](network-protocols.md)
