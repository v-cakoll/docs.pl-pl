---
title: 'Punkty końcowe: Adresy, powiązania i kontrakty'
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 0909d1d10ab8932f27f7ca6cba6207d57fa4f4cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493751"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a>Punkty końcowe: Adresy, powiązania i kontrakty
Cała komunikacja z usługą Windows Communication Foundation (WCF) odbywa się przez *punkty końcowe* usługi. Punkty końcowe zapewnić klientom dostęp do funkcji oferowanych przez usługi WCF.  
  
 Każdy punkt końcowy składa się z czterech właściwości:  
  
-   Adres, który wskazuje, gdzie można znaleźć punktu końcowego.  
  
-   Wiązanie, który określa, jak klient może komunikować się z punktem końcowym.  
  
-   Kontrakt określa operacje dostępne.  
  
-   Zestaw zachowań, które określają szczegóły implementacji lokalnego punktu końcowego.  
  
 W tym temacie tej struktury punktu końcowego i opisano, jak są reprezentowane w modelu obiektów programu WCF.  
  
## <a name="the-structure-of-an-endpoint"></a>Struktura punktu końcowego  
 Każdy punkt końcowy składa się z następujących czynności:  
  
-   Adres: Adres unikatowo identyfikuje punkt końcowy i informuje potencjalne korzystającym z usług, w którym znajduje się. Jest reprezentowana w modelu obiektów programu WCF przez <xref:System.ServiceModel.EndpointAddress> klasy. <xref:System.ServiceModel.EndpointAddress> Klasa zawiera:  
  
    -   A <xref:System.ServiceModel.EndpointAddress.Uri%2A> właściwość, która reprezentuje adres usługi.  
  
    -   <xref:System.ServiceModel.EndpointAddress.Identity%2A> Właściwość, która reprezentuje tożsamości zabezpieczeń usługi i kolekcję nagłówków komunikatów opcjonalne. Nagłówki komunikatów opcjonalne służą do zapewniania dodatkowe i bardziej szczegółowych informacji o adresach do identyfikacji użytkownika lub interakcji z punktem końcowym.  
  
     Aby uzyskać więcej informacji, zobacz [Określanie adresu punktu końcowego](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
-   Powiązanie: Powiązanie określa sposób komunikowania się z punktem końcowym. Możliwości obejmują:  
  
    -   Protokół transportu do użycia (np. TCP lub HTTP).  
  
    -   Szyfrowanie do użycia dla wiadomości (na przykład tekst lub binarny).  
  
    -   Niezbędne wymagania dotyczące zabezpieczeń (na przykład protokołu SSL lub protokołu SOAP wiadomości zabezpieczeń).  
  
     Aby uzyskać więcej informacji, zobacz [omówienie powiązań WCF](../../../../docs/framework/wcf/bindings-overview.md). Powiązanie jest reprezentowana w modelu obiektów programu WCF przez abstrakcyjna klasa podstawowa <xref:System.ServiceModel.Channels.Binding>. W przypadku większości scenariuszy użytkownicy mogą używać jednego powiązania dostarczane przez system. Aby uzyskać więcej informacji, zobacz [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
-   Kontrakty: Kontrakt przedstawiono funkcje punktu końcowego udostępnia do klienta. Kontrakt określa:  
  
    -   Jakie operacje może zostać wywołany przez klienta.  
  
    -   Formularz wiadomości.  
  
    -   Typ parametrów wejściowych lub danych wymaganych do wywołania operacji.  
  
    -   Jakiego typu Przetwarzanie lub odpowiedzi wiadomości przez klienta może spodziewać się.  
  
     Aby uzyskać więcej informacji na temat definiowania kontrakt, zobacz [projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
-   Zachowania: Aby dostosować zachowanie lokalnego punktu końcowego usługi można użyć zachowania punktu końcowego. Zachowania punktu końcowego można to osiągnąć przez uczestnictwa w procesie tworzenia WCFruntime. Przykład zachowania punktu końcowego <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> właściwość, która pozwala na określenie nasłuchiwania inny adres niż adres SOAP lub Web Services Description Language (WSDL). Aby uzyskać więcej informacji, zobacz [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).  
  
## <a name="defining-endpoints"></a>Definiowanie punktów końcowych  
 Można określić punktu końcowego usługi za pomocą kodu imperatively lub deklaratywnie przy użyciu konfiguracji. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie punktu końcowego usługi w konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) i [porady: Tworzenie punktu końcowego usługi w kodzie](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 W tej sekcji opisano w celu powiązania, punktów końcowych i adresy; Pokazuje, jak skonfigurować powiązania i punktu końcowego; i przedstawiono sposób użycia `ClientVia` zachowania i `ListenUri` właściwości.  
  
 [Adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 W tym artykule opisano, jak punkty końcowe są opisane w programie WCF.  
  
 [Powiązania](../../../../docs/framework/wcf/feature-details/bindings.md)  
 Opisuje sposób powiązania są używane do określania transportu, kodowanie i szczegóły protokołu wymagane dla klientów i usług komunikować się ze sobą.  
  
 [Kontrakty](../../../../docs/framework/wcf/feature-details/contracts.md)  
 W tym artykule opisano, jak kontrakty definiować metody usługi.  
  
 [Instrukcje: tworzenie punktu końcowego usługi w konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 Opisuje sposób tworzenia punktu końcowego usługi w konfiguracji.  
  
 [Instrukcje: tworzenie punktu końcowego usługi w kodzie](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 Opisuje sposób tworzenia punktu końcowego usługi w kodzie.  
  
 [Instrukcje: weryfikacja skompilowanego kodu usługi za pomocą programu Svcutil.exe](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 Opisuje sposób wykrywania błędów w implementacji usługi i konfiguracji bez hostingu za pomocą usługi [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie usług](../../../../docs/framework/wcf/configuring-services.md)  
 [Rozszerzanie powiązań](../../../../docs/framework/wcf/extending/extending-bindings.md)
