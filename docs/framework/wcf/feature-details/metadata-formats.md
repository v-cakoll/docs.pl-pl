---
title: Formaty metadanych
ms.date: 03/30/2017
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
ms.openlocfilehash: e7208a8d5fd6d100ac2a2c4fb1369a571c63e7fc
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212171"
---
# <a name="metadata-formats"></a>Formaty metadanych
Windows Communication Foundation (WCF) obsługuje formaty metadanych w poniższej tabeli.  
  
## <a name="metadata-specifications-and-usage"></a>Specyfikacje i użycie metadanych  
  
|Protokół|Specyfikacja i użycie|  
|--------------|-----------------------------|  
|WSDL 1,1|[Web Services Description Language (WSDL) 1,1](https://www.w3.org/TR/wsdl/)<br /><br /> Program WCF używa Web Services Description Language (WSDL) do opisywania usług.|  
|schemat XML|[Schemat XML — część 2: typy DataTypes Second Edition](https://www.w3.org/TR/2004/REC-xmlschema-2-20041028/) i [XML schematu część 1: Structures Second Edition](https://www.w3.org/TR/2004/REC-xmlschema-1-20041028/)<br /><br /> Funkcja WCF używa schematu XML do opisywania typów danych używanych w komunikatach.|  
|Zasady WS|[Zasady usług sieci Web 1,2 — Framework (WS-Policy)](https://www.w3.org/Submission/WS-Policy/)<br /><br /> [Zasady usług sieci Web 1,5 — architektura](https://www.w3.org/TR/ws-policy/)<br /><br /> Funkcja WCF używa specyfikacji WS-Policy 1,2 lub 1,5 z potwierdzeniami specyficznymi dla domeny w celu opisywania wymagań i możliwości usługi.|  
|Załączniki zasad WS|[Zasady usług sieci Web 1,2 — załącznik (WS-PolicyAttachment)](https://www.w3.org/Submission/WS-PolicyAttachment/)<br /><br /> W programie WCF Zaimplementowane są załączniki WS-Policy, które umożliwiają dołączanie wyrażeń zasad w różnych zakresach w języku WSDL.|  
|Wymiana metadanych WS|[Wymiana metadanych usług sieci Web (WS-MetadataExchange) w wersji 1,1](https://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> Funkcja WCF implementuje usługę WS-MetadataExchange, aby pobrać schemat XML, WSDL i WS-Policy.|  
|Powiązanie adresów WS dla języka WSDL|[Usługi sieci Web adresowanie 1,0 — Powiązanie WSDL](https://www.w3.org/TR/ws-addr-wsdl/)<br /><br /> Funkcja WCF implementuje powiązanie WS-Addressing dla języka WSDL w celu dołączenia informacji dotyczących adresów w języku WSDL.|  
  
## <a name="see-also"></a>Zobacz także

- [Protokoły usług internetowych obsługiwane przez wiązania współdziałania udostępnione przez system](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)
- [WSDL i zasady](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
