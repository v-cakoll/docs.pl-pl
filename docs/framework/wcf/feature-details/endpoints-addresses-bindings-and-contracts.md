---
title: 'Punkty końcowe: adresy, wiązania i kontrakty'
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 3d345cfa3169e22e7c5e85cd1c7d11c2feef4f5f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665961"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a>Punkty końcowe: adresy, wiązania i kontrakty
Cała komunikacja z usługą Windows Communication Foundation (WCF) odbywa się przez *punktów końcowych* usługi. Punkty końcowe zapewnić klientom dostęp do funkcji oferowanych przez usługę WCF.  
  
 Każdy punkt końcowy składa się z czterech właściwości:  
  
- Adres, który wskazuje, gdzie można znaleźć punktu końcowego.  
  
- Wiązanie, który określa, jak klient może komunikować się z punktem końcowym.  
  
- Kontrakt określa operacje dostępne.  
  
- Zestaw zachowań, które określają szczegółów implementacji lokalnego punktu końcowego.  
  
 W tym temacie omówiono tej struktury punktu końcowego i wyjaśniono, jak jest reprezentowana w modelu obiektu programu WCF.  
  
## <a name="the-structure-of-an-endpoint"></a>Struktura punktu końcowego  
 Każdy punkt końcowy składa się z następujących czynności:  
  
- Adres: Adres jednoznacznie identyfikuje punkt końcowy i informuje o potencjalnych klientów usługi, w którym znajduje się. Jest reprezentowana w modelu obiektu programu WCF za <xref:System.ServiceModel.EndpointAddress> klasy. <xref:System.ServiceModel.EndpointAddress> Klasa zawiera:  
  
    - A <xref:System.ServiceModel.EndpointAddress.Uri%2A> właściwość, która reprezentuje adres usługi.  
  
    - <xref:System.ServiceModel.EndpointAddress.Identity%2A> Właściwość, która reprezentuje kolekcję nagłówków opcjonalną wiadomość, jak i tożsamości zabezpieczeń usługi. Nagłówki wiadomości opcjonalne są używane do zapewnienia dodatkowych i bardziej szczegółowe informacje dotyczące adresowania, aby zidentyfikować lub nawiązać kontakt z punktem końcowym.  
  
     Aby uzyskać więcej informacji, zobacz [Określanie adresu punktu końcowego](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
- Powiązanie: Powiązanie Określa, jak komunikować się z punktem końcowym. Możliwości obejmują:  
  
    - Protokół transportu do użycia (na przykład, TCP lub HTTP).  
  
    - Szyfrowanie do użycia dla wiadomości (na przykład tekst lub dane binarne).  
  
    - Niezbędne wymagania w zakresie zabezpieczeń (na przykład protokołu SSL lub protokołu SOAP wiadomości zabezpieczeń).  
  
     Aby uzyskać więcej informacji, zobacz [omówienie powiązań WCF](../../../../docs/framework/wcf/bindings-overview.md). Powiązanie jest reprezentowana w modelu obiektu programu WCF przez abstrakcyjna klasa bazowa <xref:System.ServiceModel.Channels.Binding>. W przypadku większości scenariuszy użytkownicy mogą użyć jednego z powiązań dostarczanych przez system. Aby uzyskać więcej informacji, zobacz [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
- Zamówień: Kontrakt opisano, jakie funkcje uwidacznia punkt końcowy, do klienta. Kontrakt określa:  
  
    - Jakie operacje mogą być wywoływane przez klienta.  
  
    - Formularz wiadomości.  
  
    - Typ parametry wejściowe i dane wymagane do wywołania operacji.  
  
    - Jakiego typu Przetwarzanie lub odpowiedzi wiadomości klienta można się spodziewać.  
  
     Aby uzyskać więcej informacji na temat definiowania kontrakt zobacz [projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
- Zachowania: Aby dostosować zachowanie lokalny punkt końcowy usługi, można użyć zachowań punktu końcowego. Zachowań punktu końcowego to osiągnąć przez uczestnictwem w procesie tworzenia WCFruntime. Na przykład zachowanie punktu końcowego <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> właściwość, która pozwala na określenie na adres nasłuchiwania inny niż adres protokołu SOAP lub Web Services Description Language (WSDL). Aby uzyskać więcej informacji, zobacz [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).  
  
## <a name="defining-endpoints"></a>Definiowanie punktów końcowych  
 Można określić punktu końcowego usługi obowiązkowo za pomocą kodu lub w sposób deklaratywny przy użyciu konfiguracji. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie punktu końcowego usługi w konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) i [jak: Tworzenie punktu końcowego usługi w kodzie](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 Ta sekcja zawiera wyjaśnienie przeznaczenia powiązania, punktów końcowych oraz adresy; Pokazuje, jak skonfigurować powiązania i punktu końcowego; i pokazuje sposób użycia `ClientVia` zachowanie i `ListenUri` właściwości.  
  
 [Adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 W tym artykule opisano, jak punkty końcowe zostały rozwiązane w programie WCF.  
  
 [Powiązania](../../../../docs/framework/wcf/feature-details/bindings.md)  
 W tym artykule opisano, jak powiązań są używane do określania, transport, kodowanie i szczegóły protokołu wymagane dla klientów i usług komunikować się ze sobą.  
  
 [Kontrakty](../../../../docs/framework/wcf/feature-details/contracts.md)  
 W tym artykule opisano, jak kontrakty definiować metody usługi.  
  
 [Instrukcje: Tworzenie punktu końcowego usługi w konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 W tym artykule opisano, jak utworzyć punkt końcowy usługi w konfiguracji.  
  
 [Instrukcje: Tworzenie punktu końcowego usługi w kodzie](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 W tym artykule opisano, jak utworzyć punkt końcowy usługi w kodzie.  
  
 [Instrukcje: Weryfikacja skompilowanego kodu usługi za pomocą programu Svcutil.exe](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 W tym artykule opisano sposób wykrywania błędów w implementacji usługi i konfiguracji bez hostingu za pomocą usługi [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie usług](../../../../docs/framework/wcf/configuring-services.md)
- [Rozszerzanie powiązań](../../../../docs/framework/wcf/extending/extending-bindings.md)
