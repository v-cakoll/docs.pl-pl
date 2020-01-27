---
title: Pojęcia zabezpieczeń użyte dla programu WCF
ms.date: 03/30/2017
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
ms.openlocfilehash: faf7b44c0ff1b207a7b017163ad2b032f26199b8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743878"
---
# <a name="security-concepts-used-in-wcf"></a>Pojęcia zabezpieczeń użyte dla programu WCF
Zabezpieczenia Windows Communication Foundation (WCF) są tworzone w oparciu o koncepcje już używane i wdrożone w różnych infrastrukturach zabezpieczeń.  
  
 Usługa WCF obsługuje niektóre z tych infrastruktur, takich jak SSL (SSL) za pośrednictwem protokołu HTTP (HTTPS). Jednak platforma WCF przekroczy obsługę istniejących infrastruktur zabezpieczeń, implementując nowsze standardy zabezpieczeń interoperacyjności (takie jak WS-Security) za pośrednictwem komunikatów szyfrowanych przy użyciu protokołu SOAP. Niezależnie od tego, czy korzystasz z istniejących mechanizmów, czy nowe standardy interoperacyjności, koncepcje zabezpieczeń w tle są takie same. Zrozumienie pojęć związanych z istniejącymi infrastrukturami i nowszymi standardami jest podstawą wdrożenia najlepszego modelu zabezpieczeń aplikacji.  
  
## <a name="introduction-to-security-for-wcf-web-services"></a>Wprowadzenie do zabezpieczeń usług sieci Web WCF  

Grupa Microsoft Patterns and Practices została zapisana w szczegółowym dokumencie o nazwie [Przewodnik po zabezpieczeniach WCF](https://archive.codeplex.com/?p=wcfsecurityguide). Ten oficjalny dokument zawiera opis podstawowych pojęć związanych z bezpieczeństwem, które dotyczą usług sieci Web, kluczowych koncepcji dotyczących zabezpieczeń WCF, scenariuszy aplikacji intranetowych i scenariuszy aplikacji internetowych.  
  
## <a name="industry-wide-security-specifications"></a>Specyfikacje zabezpieczeń w całej branży  
  
### <a name="public-key-infrastructure"></a>Infrastruktura kluczy publicznych  

Infrastruktura kluczy publicznych (PKI) to system certyfikatów cyfrowych, urzędów certyfikacji i innych urzędów rejestracyjnych, które weryfikują i uwierzytelniają poszczególne strony związane z transakcjami elektronicznymi przy użyciu kryptografii klucza publicznego.
  
### <a name="kerberos-protocol"></a>Protokół Kerberos  
 *Protokół Kerberos* to specyfikacja służąca do tworzenia mechanizmu zabezpieczeń, który uwierzytelnia użytkowników w domenie systemu Windows. Umożliwia użytkownikowi ustanowienie bezpiecznego kontekstu z innymi jednostkami w domenie. System Windows 2000 i nowsze platformy domyślnie korzystają z protokołu Kerberos. Zrozumienie mechanizmów systemu jest przydatne podczas tworzenia usługi, która będzie współdziałać z klientami intranetowymi. Ponadto, ponieważ *zabezpieczenia usług w sieci Web powiązania Kerberos* jest szeroko publikowany, można użyć protokołu Kerberos do komunikacji z klientami internetowymi (oznacza to, że protokół Kerberos jest interoperacyjny). Aby uzyskać więcej informacji o sposobie implementacji protokołu Kerberos w systemie Windows, zobacz [Microsoft Kerberos](/windows/win32/secauthn/microsoft-kerberos).  
  
### <a name="x509-certificates"></a>Certyfikaty X. 509  
 Certyfikaty X. 509 są głównym formularzem poświadczeń używanym w aplikacjach zabezpieczeń. Aby uzyskać więcej informacji na temat certyfikatów X. 509, zobacz [Certyfikaty klucza publicznego x. 509](/windows/win32/seccertenroll/about-x-509-public-key-certificates). Certyfikaty X. 509 są przechowywane w magazynie certyfikatów. Komputer z systemem Windows ma kilka rodzajów magazynów certyfikatów, z których każdy ma inny cel. Aby uzyskać więcej informacji na temat różnych magazynów, zobacz [magazyny certyfikatów](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc757138(v=ws.10)).  
  
## <a name="web-services-security-specifications"></a>Specyfikacje zabezpieczenia usług w sieci Web  
 Powiązania zdefiniowane przez system obsługują wiele powszechnie używanych specyfikacji zabezpieczeń usług sieci Web. Aby uzyskać pełną listę powiązań dostarczanych przez system i specyfikacji usług sieci Web, które są przez nie obsługiwane przez program, zobacz: [Protokoły usług sieci Web obsługiwanych przez powiązania współdziałania dostarczone przez system](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
  
## <a name="access-control-mechanisms"></a>Mechanizmy kontroli dostępu  
 Funkcja WCF zapewnia wiele sposobów kontroli dostępu do usługi lub operacji. Wśród nich są  
  
1. <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2. Dostawca członkostwa ASP.NET  
  
3. Dostawca roli ASP.NET  
  
4. Menedżer autoryzacji  
  
5. Model tożsamości  
  
 Aby uzyskać więcej informacji na temat tych tematów, zobacz [mechanizmy Access Control](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
