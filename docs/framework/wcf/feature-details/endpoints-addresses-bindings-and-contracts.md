---
title: 'Punkty końcowe: Adresy, powiązania i kontrakty'
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 3ac7f0b165b99a1ed3702628958f7d4c7702f5b1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593519"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a>Punkty końcowe: Adresy, powiązania i kontrakty

Cała komunikacja z usługą Windows Communication Foundation (WCF) odbywa się za pomocą *punktów końcowych* usługi. Punkty końcowe zapewniają klientom dostęp do funkcji oferowanych przez usługę WCF.

Każdy punkt końcowy zawiera cztery właściwości:

- Adres wskazujący, gdzie można znaleźć punkt końcowy.

- Powiązanie określające, w jaki sposób klient może komunikować się z punktem końcowym.

- Kontrakt, który identyfikuje dostępne operacje.

- Zestaw zachowań określających szczegóły implementacji lokalnej punktu końcowego.

W tym temacie omówiono tę strukturę punktu końcowego i wyjaśniono, jak jest reprezentowana w modelu obiektów WCF.

## <a name="the-structure-of-an-endpoint"></a>Struktura punktu końcowego

Każdy punkt końcowy składa się z następujących elementów:

- Address: adres jednoznacznie identyfikuje punkt końcowy i informuje potencjalnych klientów usługi o tym, gdzie się znajdują. Jest reprezentowana w modelu obiektów WCF przez <xref:System.ServiceModel.EndpointAddress> klasę. <xref:System.ServiceModel.EndpointAddress>Klasa zawiera:

  - <xref:System.ServiceModel.EndpointAddress.Uri%2A>Właściwość, która reprezentuje adres usługi.

  - <xref:System.ServiceModel.EndpointAddress.Identity%2A>Właściwość, która reprezentuje tożsamość zabezpieczeń usługi i kolekcję opcjonalnych nagłówków komunikatów. Opcjonalne nagłówki wiadomości są używane do udostępniania dodatkowych i bardziej szczegółowych informacji o adresach w celu identyfikowania punktu końcowego lub korzystania z niego.

  Aby uzyskać więcej informacji, zobacz [Określanie adresu punktu końcowego](../specifying-an-endpoint-address.md).

- Powiązanie: powiązanie określa sposób komunikacji z punktem końcowym. Obejmuje to:

  - Protokół transportowy do użycia (na przykład TCP lub HTTP).

  - Kodowanie, które ma być używane dla wiadomości (na przykład tekst lub binarny).

  - Niezbędne wymagania dotyczące zabezpieczeń (na przykład zabezpieczenia protokołu SSL lub protokołu SOAP).

  Aby uzyskać więcej informacji, zobacz temat [powiązania WCF — Omówienie](../bindings-overview.md). Powiązanie jest reprezentowane w modelu obiektów WCF przez abstrakcyjną klasę bazową <xref:System.ServiceModel.Channels.Binding> . W przypadku większości scenariuszy użytkownicy mogą korzystać z jednego z powiązań dostarczonych przez system. Aby uzyskać więcej informacji, zobacz [powiązania dostarczone przez system](../system-provided-bindings.md).

- Kontrakty: kontrakt zawiera informacje o funkcjach, które punkt końcowy uwidoczni dla klienta. Kontrakt określa:

  - Jakie operacje mogą być wywoływane przez klienta.

  - Formularz wiadomości.

  - Typ parametrów wejściowych lub danych wymaganych do wywołania operacji.

  - Jakiego typu komunikaty o przetwarzaniu lub odpowiedzi mogą oczekiwać klient.

  Aby uzyskać więcej informacji na temat definiowania kontraktu, zobacz [Projektowanie kontraktów usług](../designing-service-contracts.md).

- Zachowania: można użyć zachowań punktów końcowych, aby dostosować lokalne zachowanie punktu końcowego usługi. Zachowania punktów końcowych osiągają ten udział w procesie tworzenia środowiska uruchomieniowego WCF. Przykładem zachowania punktu końcowego jest <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> Właściwość, która umożliwia określenie innego adresu nasłuchiwania niż adres SOAP lub Web Services Description Language (WSDL). Aby uzyskać więcej informacji, zobacz [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).

## <a name="defining-endpoints"></a>Definiowanie punktów końcowych

Punkt końcowy usługi można określić za pomocą kodu lub deklaratywnie za pośrednictwem konfiguracji. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie punktu końcowego usługi w konfiguracji](how-to-create-a-service-endpoint-in-configuration.md) i [instrukcje: Tworzenie punktu końcowego usługi w kodzie](how-to-create-a-service-endpoint-in-code.md).

## <a name="in-this-section"></a>W tej sekcji

W tej sekcji wyjaśniono cel powiązań, punktów końcowych i adresów; pokazuje, jak skonfigurować powiązanie i punkt końcowy; i pokazuje, jak używać `ClientVia` zachowań i `ListenUri` właściwości.

[Adres](endpoint-addresses.md)\
Opisuje, w jaki sposób punkty końcowe są rozkierowane na platformie WCF.

[Powiązań](bindings.md)\
Opisuje, w jaki sposób powiązania są używane do określania informacji o transportach, kodowaniu i protokole wymaganych przez klientów i usługi do komunikowania się ze sobą.

[Kontraktacj](contracts.md)\
Opisuje, jak kontrakty definiują metody usługi.

[Instrukcje: Tworzenie punktu końcowego usługi w konfiguracji](how-to-create-a-service-endpoint-in-configuration.md)\
Opisuje sposób tworzenia punktu końcowego usługi w konfiguracji.

[Instrukcje: Tworzenie punktu końcowego usługi w kodzie](how-to-create-a-service-endpoint-in-code.md)\
Opisuje sposób tworzenia punktu końcowego usługi w kodzie.

[Instrukcje: użycie programu Svcutil. exe do zweryfikowania skompilowanego kodu usługi](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)\
Opisuje sposób wykrywania błędów w implementacjach i konfiguracjach usług bez udostępniania usługi przy użyciu [Narzędzia do obsługi metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie usług](../configuring-services.md)
- [Rozszerzanie powiązań](../extending/extending-bindings.md)
