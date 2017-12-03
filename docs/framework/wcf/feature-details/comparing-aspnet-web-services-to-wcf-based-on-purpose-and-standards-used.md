---
title: "Porównanie usług sieci Web platformy ASP.NET i architektury WCF na podstawie przeznaczenia oraz stosowanych standardów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3890278-fa9b-4902-91ea-8da73b7143cc
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f3fec18cb93486dfe9d2b09582ad263d19b00617
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used"></a>Porównanie usług sieci Web platformy ASP.NET i architektury WCF na podstawie przeznaczenia oraz stosowanych standardów
Usługi sieci Web platformy ASP.NET został opracowany do tworzenia aplikacji, które wysyłać i odbierać wiadomości przy użyciu obiektu dostępu protokołu SOAP (Simple) za pośrednictwem protokołu HTTP. Struktura komunikaty mogą być definiowane przy użyciu schematu XML, a narzędzie jest dostarczany w celu ułatwienia serializacji komunikatów do i z obiektami środowiska .NET Framework. Technologia może automatycznie generować metadane do opisu usługi sieci Web w sieci Web Services Description Language (WSDL), a drugi narzędzie jest dostępne w celu generowania klientów dla usług sieci Web z pliku WSDL.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]jest dotyczące włączania aplikacji .NET Framework do wymiany wiadomości z innym podmiotom oprogramowania. Domyślnie jest używany protokół SOAP, ale komunikaty można w dowolnym formacie i przekazywanych przy użyciu dowolnego protokołu transportu. Struktura komunikaty mogą być definiowane przy użyciu schematu XML, a istnieją różne opcje dla serializacji komunikatów do i z obiektami środowiska .NET Framework. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]może automatycznie generować metadane do opisywania aplikacje utworzone przy użyciu technologii w języku WSDL, a także udostępnia narzędzia generowania klientów dla tych aplikacji z pliku WSDL.  
  
 Standardów obsługiwanych przez usługi sieci Web ASP.NET są udokumentowane w artykule [XML sieci Web usług utworzone za pomocą programu ASP.NET](http://go.microsoft.com/fwlink/?LinkId=94872). Bardziej rozległych listę standardów obsługiwanych przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] znajduje się w [sieci Web usług protokoły obsługiwane przez wiązania współdziałania System-Provided](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porównanie usług sieci Web ASP.NET do programu WCF na podstawie procesów programistycznych](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
