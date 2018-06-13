---
title: Pojęcia zabezpieczeń użyte dla programu WCF
ms.date: 03/30/2017
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ac76f1742ab72de9f5180d1ea2fcbc668ec2140c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497636"
---
# <a name="security-concepts-used-in-wcf"></a>Pojęcia zabezpieczeń użyte dla programu WCF
Zabezpieczenia usług Windows Communication Foundation (WCF) jest wbudowane w system pojęcia już w użyciu i wdrożone w różnych infrastruktur zabezpieczeń.  
  
 Usługi WCF obsługuje niektóre z tych infrastruktury, takich jak Secure Sockets Layer (SSL) za pośrednictwem protokołu HTTP (HTTPS). Jednak WCF wykracza poza obsługi istniejącej infrastruktury zabezpieczeń zaimplementowanie nowszej standardów zabezpieczeń interoperacyjne (na przykład WS-Security) za pośrednictwem kodowanymi komunikatami SOAP. Zarówno w przypadku korzystania z mechanizmów istniejącego lub nowego interoperacyjne standardów zabezpieczeń pojęć zarówno są takie same. Opis pojęć dotyczących istniejącej infrastruktury i nowszej standardów jest podstawą do implementowania modelu zabezpieczeń najlepsze dla aplikacji.  
  
## <a name="introduction-to-security-for-wcf-web-services"></a>Wprowadzenie do zabezpieczeń dla usług sieci Web programu WCF  
 Grupę Microsoft Patterns and Practices szczegółowe oficjalny dokument został napisany na WCF wskazówki dotyczące zabezpieczeń, które można pobrać tutaj: [Przewodnik po zabezpieczeniach WCF](http://go.microsoft.com/fwlink/?LinkId=210210). Ten dokument zawiera opis podstawowych pojęć dotyczących zabezpieczeń w odniesieniu do usług sieci web, podstawowe pojęcia zabezpieczeń WCF środowisk intranetowych w aplikacji i scenariusze aplikacji internetowych.  
  
## <a name="industry-wide-security-specifications"></a>Specyfikacje branżowym zabezpieczeń  
  
### <a name="public-key-infrastructure"></a>Infrastruktura kluczy publicznych  
 Infrastruktura kluczy publicznych (PKI) to system certyfikaty cyfrowe, urzędy certyfikacji i innych urzędów rejestracji, które sprawdzają i uwierzytelniania każdej Strony biorącej udział w operacji elektronicznej za pomocą kryptografii klucza publicznego. Aby uzyskać więcej informacji, zobacz [usług certyfikatów systemu Windows Server 2008 R2](http://go.microsoft.com/fwlink/?LinkId=210211).  
  
### <a name="kerberos-protocol"></a>Protokół Kerberos  
 *Protokołu Kerberos* jest specyfikacją dla tworzenia mechanizm zabezpieczeń, który uwierzytelnia użytkowników w domenie systemu Windows. Umożliwia użytkownikowi ustanowić bezpiecznego kontekst z innymi jednostkami w domenie. Windows 2000 lub nowszych platformach domyślnie używają protokołu Kerberos. Zrozumienie mechanizmów systemu jest przydatne, gdy tworzenie usługi, która będzie współpracować z klienci w intranecie. Ponadto, ponieważ *powiązania protokołu Kerberos zabezpieczeń usług sieci Web* jest powszechnie opublikowana, można użyć protokołu Kerberos do komunikacji z klientami internetowymi (protokół Kerberos jest współpraca). Aby uzyskać więcej informacji na temat implementowania protokołu Kerberos w systemie Windows, zobacz [Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkId=210212).  
  
### <a name="x509-certificates"></a>Certyfikaty X.509  
 Certyfikaty X.509 są formularza podstawowego poświadczeń używanych w aplikacjach zabezpieczeń. Aby uzyskać więcej informacji na temat X.509 Zobacz certyfikaty [certyfikatów kluczy publicznych X.509](http://go.microsoft.com/fwlink/?LinkId=210213). Certyfikaty X.509 są przechowywane w magazynie certyfikatów. Komputer z systemem Windows ma kilka rodzajów magazynów certyfikatów, każde z nich innym celu. Aby uzyskać więcej informacji o różnych magazynach, zobacz [magazynów certyfikatów](http://go.microsoft.com/fwlink/?LinkID=87787).  
  
## <a name="web-services-security-specifications"></a>Specyfikacje zabezpieczeń usług sieci Web  
 Powiązania zdefiniowane przez system obsługi wielu specyfikacji zabezpieczenia usługi sieci web często używane. Aby uzyskać pełną listę powiązania dostarczane przez system i specyfikacji usługi sieci web obsługuje zobacz: [sieci Web usług protokoły obsługiwane przez wiązania współdziałania System-Provided](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
  
## <a name="access-control-mechanisms"></a>Mechanizmy kontroli dostępu  
 Usługi WCF oferuje następujące sposoby kontrolowania dostępu do usługi lub operacji. Między nimi są  
  
1.  <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2.  Dostawca członkostwa programu ASP.NET  
  
3.  Dostawcy ról ASP.NET  
  
4.  Menedżer autoryzacji  
  
5.  Modelu tożsamości  
  
 Aby uzyskać więcej informacji na temat, zobacz następujące tematy [mechanizmy kontroli dostępu](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Model zabezpieczeń systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
