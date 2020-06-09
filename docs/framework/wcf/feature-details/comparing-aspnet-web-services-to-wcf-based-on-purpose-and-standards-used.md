---
title: Porównanie usług sieci Web platformy ASP.NET i architektury WCF na podstawie przeznaczenia oraz stosowanych standardów
ms.date: 03/30/2017
ms.assetid: d3890278-fa9b-4902-91ea-8da73b7143cc
ms.openlocfilehash: b27f3516868ec70319ce37fbbd774a29347b0bc8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597582"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used"></a>Porównanie usług sieci Web platformy ASP.NET i architektury WCF na podstawie przeznaczenia oraz stosowanych standardów
Usługi sieci Web ASP.NET zostały opracowane do tworzenia aplikacji wysyłających i odbierających komunikaty przy użyciu Simple Object Access Protocol (SOAP) za pośrednictwem protokołu HTTP. Strukturę komunikatów można zdefiniować za pomocą schematu XML, a narzędzie jest udostępniane, aby ułatwić Serializowanie komunikatów do i z obiektów .NET Framework. Technologia może automatycznie generować metadane opisujące usługi sieci Web w Web Services Description Language (WSDL), a drugie narzędzie do generowania klientów dla usług sieci Web z poziomu języka WSDL.  
  
 Usługa WCF służy do włączania .NET Framework aplikacji do wymiany komunikatów z innymi jednostkami oprogramowania. Protokół SOAP jest używany domyślnie, ale komunikaty mogą być w dowolnym formacie i przekazywane przy użyciu dowolnego protokołu transportowego. Strukturę komunikatów można zdefiniować przy użyciu schematu XML, a istnieją różne opcje serializowania komunikatów do i z obiektów .NET Framework. Funkcja WCF może automatycznie generować metadane, aby opisywać Aplikacje skompilowane przy użyciu technologii w języku WSDL, a także udostępnia narzędzie do generowania klientów dla tych aplikacji z poziomu języka WSDL.  
  
 Standardy obsługiwane przez usługi sieci Web ASP.NET są udokumentowane w [zalety usług sieci Web XML utworzonych przy użyciu ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0859ebft(v=vs.100)). Bardziej obszerna lista standardów obsługiwanych przez usługę WCF znajduje się w [protokołach usług sieci Web obsługiwanych przez powiązania współdziałania dostarczone przez system](web-services-protocols-supported-by-system-provided-interoperability-bindings.md).  
  
## <a name="see-also"></a>Zobacz też

- [Porównywanie usług internetowych platformy ASP.NET z programem WCF na podstawie procesów programistycznych](comparing-aspnet-web-services-to-wcf-based-on-development.md)
