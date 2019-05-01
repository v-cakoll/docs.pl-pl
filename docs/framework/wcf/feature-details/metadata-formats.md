---
title: Formaty metadanych
ms.date: 03/30/2017
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
ms.openlocfilehash: 55f68f4b56e50b19da19ecc941e9ec537b846006
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038574"
---
# <a name="metadata-formats"></a>Formaty metadanych
Windows Communication Foundation (WCF) obsługuje formaty metadanych w poniższej tabeli.  
  
## <a name="metadata-specifications-and-usage"></a>Specyfikacje metadanych i użycia  
  
|Protokół|Specyfikacja i użycia|  
|--------------|-----------------------------|  
|WSDL 1.1|[Web Services Description Language (WSDL) 1.1](https://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> Usługi WCF używa usługi sieci Web Services Description Language (WSDL) do opisu usługi.|  
|schemat XML|[XML Schema Part 2: Wydanie drugie typy danych](https://go.microsoft.com/fwlink/?LinkId=94861) i [XML schematu część 1: Wydanie drugie struktury](https://go.microsoft.com/fwlink/?LinkId=94862)<br /><br /> Usługi WCF używa schematu XML do opisu typów danych używanych w komunikatach.|  
|Zasady protokołu WS|[Zasady dotyczące usług sieci Web 1.2 — Framework (WS-Policy)](https://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [Zasady dotyczące usług sieci Web w wersji 1.5 — struktury](https://go.microsoft.com/fwlink/?LinkId=94865)<br /><br /> WCF za pomocą usługi WS-Policy w wersji 1.2 lub specyfikacji 1,5 potwierdzenia specyficznego dla domeny do opisu wymagań usługi i możliwości.|  
|Zasady protokołu WS załączników|[Zasady dotyczące usług sieci Web 1.2 — załącznika (WS-PolicyAttachment)](https://go.microsoft.com/fwlink/?LinkId=94866)<br /><br /> Usługi WCF implementuje załącznikami WS-Policy, aby dołączyć wyrażenia zasad w różnych zakresach w języku WSDL.|  
|WS Metadata Exchange|[Wymiany metadanych usługi sieci Web (WS-MetadataExchange) w wersji 1.1](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> Usługi WCF implementuje usługi WS-MetadataExchange, aby pobrać schemat XML, WSDL i WS-Policy.|  
|Powiązanie WSDL adresowania WS|[Eliminowanie 1.0 - Powiązanie WSDL usług sieci Web](https://go.microsoft.com/fwlink/?LinkId=94869)<br /><br /> Usługi WCF implementuje usługi WS-Addressing Powiązanie WSDL dołączyć informacje dotyczące adresowania w języku WSDL.|  
  
## <a name="see-also"></a>Zobacz także

- [Protokoły usług internetowych obsługiwane przez wiązania współdziałania udostępnione przez system](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)
- [WSDL i zasady](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
