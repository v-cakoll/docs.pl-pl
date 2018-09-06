---
title: Formaty metadanych
ms.date: 03/30/2017
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
ms.openlocfilehash: 9fa72c70940a49dbc0bf8660d23dfa33fce327e7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43732316"
---
# <a name="metadata-formats"></a>Formaty metadanych
Windows Communication Foundation (WCF) obsługuje formaty metadanych w poniższej tabeli.  
  
## <a name="metadata-specifications-and-usage"></a>Specyfikacje metadanych i użycia  
  
|Protokół|Specyfikacja i użycia|  
|--------------|-----------------------------|  
|WSDL 1.1|[Web Services Description Language (WSDL) 1.1](https://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> Usługi WCF używa usługi sieci Web Services Description Language (WSDL) do opisu usługi.|  
|schemat XML|[XML schematu część 2: Wydanie drugie typów danych](https://go.microsoft.com/fwlink/?LinkId=94861) i [XML schematu część 1: struktur wydanie drugie](https://go.microsoft.com/fwlink/?LinkId=94862)<br /><br /> Usługi WCF używa schematu XML do opisu typów danych używanych w komunikatach.|  
|Zasady protokołu WS|[Zasady dotyczące usług sieci Web 1.2 — Framework (WS-Policy)](https://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [Zasady dotyczące usług sieci Web w wersji 1.5 — struktury](https://go.microsoft.com/fwlink/?LinkId=94865)<br /><br /> WCF za pomocą usługi WS-Policy w wersji 1.2 lub specyfikacji 1,5 potwierdzenia specyficznego dla domeny do opisu wymagań usługi i możliwości.|  
|Zasady protokołu WS załączników|[Zasady dotyczące usług sieci Web 1.2 — załącznika (WS-PolicyAttachment)](https://go.microsoft.com/fwlink/?LinkId=94866)<br /><br /> Usługi WCF implementuje załącznikami WS-Policy, aby dołączyć wyrażenia zasad w różnych zakresach w języku WSDL.|  
|Wymiany metadanych WS|[Wymiany metadanych usługi sieci Web (WS-MetadataExchange) w wersji 1.1](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> Usługi WCF implementuje usługi WS-MetadataExchange, aby pobrać schemat XML, WSDL i WS-Policy.|  
|Powiązanie WSDL adresowania WS|[Eliminowanie 1.0 - Powiązanie WSDL usług sieci Web](https://go.microsoft.com/fwlink/?LinkId=94869)<br /><br /> Usługi WCF implementuje usługi WS-Addressing Powiązanie WSDL dołączyć informacje dotyczące adresowania w języku WSDL.|  
  
## <a name="see-also"></a>Zobacz też  
 [Protokoły usług internetowych obsługiwane przez wiązania współdziałania udostępnione przez system](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
 [WSDL i zasady](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
