---
title: Formaty metadanych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b7812023fbe2159daba205727e20e1b69b84686
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="metadata-formats"></a>Formaty metadanych
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]obsługuje formaty metadanych w poniższej tabeli.  
  
## <a name="metadata-specifications-and-usage"></a>Specyfikacje metadanych i użycia  
  
|Protokół|Specyfikacja i użycia|  
|--------------|-----------------------------|  
|WSDL 1.1|[Web Services Description Language (WSDL) 1.1](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]używa usługi sieci Web Services Description Language (WSDL) do opisu usługi.|  
|schemat XML|[XML schematu część 2: Wydanie drugie typów danych](http://go.microsoft.com/fwlink/?LinkId=94861) i [część schematu XML 1: struktury wydanie drugie](http://go.microsoft.com/fwlink/?LinkId=94862)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]używa schematu XML opisujący typów danych używanych w wiadomości.|  
|Zasady protokołu WS|[Zasady usługi sieci Web 1.2 - Framework (WS-Policy)](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [Zasady usługi sieci Web w wersji 1.5 — Framework](http://go.microsoft.com/fwlink/?LinkId=94865)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]używa 1.2 WS-Policy lub specyfikacji 1,5 z potwierdzeniami specyficznego dla domeny do opisu usługi wymagań i możliwości.|  
|Załączniki polityki WS|[Zasady usługi sieci Web 1.2 - załącznika (WS-PolicyAttachment)](http://go.microsoft.com/fwlink/?LinkId=94866)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje usługi WS-Policy załączników do podłączenia zasad wyrażenia w różnych zakresów w języku WSDL.|  
|Wymiany metadanych WS|[Wymiany metadanych usługi sieci Web (WS-MetadataExchange) w wersji 1.1](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje usługi WS-MetadataExchange, można pobrać schematu XML, WSDL i WS-Policy.|  
|Powiązanie WSDL adresowania WS|[Usługi sieci Web adresowanie 1.0 - Powiązanie WSDL](http://go.microsoft.com/fwlink/?LinkId=94869)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje usługi WS-Addressing Powiązanie WSDL dołączyć informacje adresowania w języku WSDL.|  
  
## <a name="see-also"></a>Zobacz też  
 [Protokoły usług internetowych obsługiwane przez wiązania współdziałania udostępnione przez system](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
 [WSDL i zasady](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
