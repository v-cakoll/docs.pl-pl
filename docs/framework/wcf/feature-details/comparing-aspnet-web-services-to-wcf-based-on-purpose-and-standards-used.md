---
title: Porównanie usług sieci Web platformy ASP.NET i architektury WCF na podstawie przeznaczenia oraz stosowanych standardów
ms.date: 03/30/2017
ms.assetid: d3890278-fa9b-4902-91ea-8da73b7143cc
ms.openlocfilehash: 60f2e9ccbfd5dbf205f3ed570ece1d4169f21e3a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used"></a>Porównanie usług sieci Web platformy ASP.NET i architektury WCF na podstawie przeznaczenia oraz stosowanych standardów
Usługi sieci Web platformy ASP.NET został opracowany do tworzenia aplikacji, które wysyłać i odbierać wiadomości przy użyciu obiektu dostępu protokołu SOAP (Simple) za pośrednictwem protokołu HTTP. Struktura komunikaty mogą być definiowane przy użyciu schematu XML, a narzędzie jest dostarczany w celu ułatwienia serializacji komunikatów do i z obiektami środowiska .NET Framework. Technologia może automatycznie generować metadane do opisu usługi sieci Web w sieci Web Services Description Language (WSDL), a drugi narzędzie jest dostępne w celu generowania klientów dla usług sieci Web z pliku WSDL.  
  
 Funkcja WCF została dotyczące włączania aplikacji .NET Framework do wymiany wiadomości z innym podmiotom oprogramowania. Domyślnie jest używany protokół SOAP, ale komunikaty można w dowolnym formacie i przekazywanych przy użyciu dowolnego protokołu transportu. Struktura komunikaty mogą być definiowane przy użyciu schematu XML, a istnieją różne opcje dla serializacji komunikatów do i z obiektami środowiska .NET Framework. WCF może automatycznie generować metadane do opisywania aplikacje utworzone przy użyciu technologii w języku WSDL, a także udostępnia narzędzia generowania klientów dla tych aplikacji z pliku WSDL.  
  
 Standardów obsługiwanych przez usługi sieci Web ASP.NET są udokumentowane w artykule [XML sieci Web usług utworzone za pomocą programu ASP.NET](http://go.microsoft.com/fwlink/?LinkId=94872). Bardziej rozległych lista standardów obsługiwanych przez usługę WCF znajduje się w [sieci Web usług protokoły obsługiwane przez wiązania współdziałania System-Provided](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porównywanie usług internetowych platformy ASP.NET z programem WCF na podstawie procesów programistycznych](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
