---
title: Pojęcia zabezpieczeń użyte dla programu WCF
ms.date: 03/30/2017
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
ms.openlocfilehash: 3ef2b9c104fa15de17a769c9ca9354e5cef085bf
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295552"
---
# <a name="security-concepts-used-in-wcf"></a>Pojęcia zabezpieczeń użyte dla programu WCF
Zabezpieczenia usług Windows Communication Foundation (WCF) jest utworzonych na podstawie pojęcia już w użyciu i wdrożone w różnych infrastrukturach zabezpieczeń.  
  
 Usługi WCF obsługuje niektóre z tych infrastruktury, takich jak Secure Sockets Layer (SSL) za pośrednictwem protokołu HTTPS (HTTP). Jednak WCF wykracza poza obsługi istniejącej infrastruktury zabezpieczeń poprzez implementację nowszej standardów zabezpieczeń międzyoperacyjnych (na przykład WS-Security) za pośrednictwem kodowanymi komunikatami SOAP. Czy używasz istniejących mechanizmów lub nowych standardów interoperacyjne pojęcia zabezpieczeń, oba są takie same. Opis pojęć dotyczących istniejącymi infrastrukturami i nowszej standardów stanowi podstawę do wdrażania najlepszy model zabezpieczeń dla aplikacji.  
  
## <a name="introduction-to-security-for-wcf-web-services"></a>Wprowadzenie do zabezpieczeń dla usług sieci Web WCF  
 Grupę Microsoft Patterns and Practices napisał szczegółowy oficjalny dokument na wskazówki dotyczące zabezpieczeń programu WCF, która jest dostępna do pobrania w tym miejscu: [Przewodnik po zabezpieczeniach WCF](https://go.microsoft.com/fwlink/?LinkId=210210). Ten oficjalny dokument zawiera opis podstawowych pojęć dotyczących zabezpieczeń w odniesieniu do usług sieci web, kluczowe pojęcia dotyczące zabezpieczeń programu WCF, scenariuszy dotyczących aplikacji w sieci intranet i internet scenariuszy aplikacji.  
  
## <a name="industry-wide-security-specifications"></a>Specyfikacje całej branży zabezpieczeń  
  
### <a name="public-key-infrastructure"></a>Infrastruktura kluczy publicznych  
 Infrastruktura kluczy publicznych (PKI) to system certyfikaty cyfrowe, urzędy certyfikacji i innych urzędów rejestracji, które sprawdzają i uwierzytelniania poszczególnych biorącego udział w transakcji elektronicznej za pomocą kryptografii klucza publicznego. Aby uzyskać więcej informacji, zobacz [usługach certyfikatów systemu Windows Server 2008 R2](https://go.microsoft.com/fwlink/?LinkId=210211).  
  
### <a name="kerberos-protocol"></a>Protokół Kerberos  
 *Protokołu Kerberos* to specyfikacja dla tworzenia mechanizmu zabezpieczeń, która uwierzytelnia użytkowników w domenie Windows. Umożliwia użytkownikowi na ustanowienie bezpiecznego kontekstu z innymi jednostkami w domenie. Windows 2000 i nowszych platform domyślnie używają protokołu Kerberos. Zrozumienie mechanizmów systemu jest przydatne podczas tworzenia usługi, która wchodzi w interakcje z klienci w intranecie. Ponadto, ponieważ *powiązanie protokołu Kerberos zabezpieczeń usług sieci Web* jest szeroko opublikowane, można użyć protokołu Kerberos do komunikacji z klientami internetowymi (czyli protokołu Kerberos jest współpracujący). Aby uzyskać więcej informacji na temat implementacji protokołu Kerberos w Windows, zobacz [Microsoft Kerberos](https://go.microsoft.com/fwlink/?LinkId=210212).  
  
### <a name="x509-certificates"></a>Certyfikaty X.509  
 Certyfikaty X.509 są używane w zastosowaniach zabezpieczeń formularza podstawowej credential. Aby uzyskać więcej informacji na temat X.509 certyfikatów Zobacz [klucz publiczny certyfikatu X.509](https://go.microsoft.com/fwlink/?LinkId=210213). Certyfikaty X.509 są przechowywane w magazynie certyfikatów. Komputer z systemem Windows ma kilka rodzajów magazynów certyfikatów, każdy z innego celu. Aby uzyskać więcej informacji na temat różnych sklepach zobacz [magazynów certyfikatów](https://go.microsoft.com/fwlink/?LinkID=87787).  
  
## <a name="web-services-security-specifications"></a>Specyfikacje zabezpieczeń usług sieci Web  
 Powiązania zdefiniowane przez system obsługuje wiele powszechnie używanych w sieci web usług zabezpieczeń specyfikacji. Aby uzyskać pełną listę powiązania dostarczane przez system i specyfikacji usługi sieci web obsługują one, zobacz: [Protokoły usług internetowych obsługiwane przez wiązania współdziałania udostępnione przez system](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
  
## <a name="access-control-mechanisms"></a>Mechanizmy kontroli dostępu  
 Usługi WCF zapewnia szereg sposobów kontrolowania dostępu do usługi lub operacji. Między nimi są  
  
1. <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2. Dostawcy członkostwa platformy ASP.NET  
  
3. Dostawcy ról ASP.NET  
  
4. Menedżer autoryzacji  
  
5. Modelu tożsamości  
  
 Aby uzyskać więcej informacji na temat, zobacz następujące tematy [mechanizmy kontroli dostępu](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Model zabezpieczeń dla systemu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
