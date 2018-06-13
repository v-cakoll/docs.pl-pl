---
title: Korzystanie z personifikacji z zabezpieczeniami transportu
ms.date: 03/30/2017
ms.assetid: 426df8cb-6337-4262-b2c0-b96c2edf21a9
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 5a4b05031061183cf0dddd82c900065155b1e561
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501697"
---
# <a name="using-impersonation-with-transport-security"></a>Korzystanie z personifikacji z zabezpieczeniami transportu
*Personifikacja* to funkcja aplikacji serwera do podjęcia tożsamości klienta. Jest typowe dla usługi, aby podczas sprawdzania dostępu do zasobów należy używać personifikacji. Aplikacja zostanie uruchomiona przy użyciu konta usługi, ale gdy serwer akceptuje połączenia klienta, personifikuje klienta, dzięki czemu kontroli dostępu są wykonywane przy użyciu poświadczeń klienta. Zabezpieczenia transportu jest to mechanizm przekazywania poświadczeń i zabezpieczania komunikacji przy użyciu tych poświadczeń. W tym temacie opisano, za pomocą zabezpieczeń transportu w systemie Windows Communication Foundation (WCF) z funkcją personifikacji. Aby uzyskać więcej informacji o personifikacji korzystanie z zabezpieczeń komunikatów, zobacz [delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="five-impersonation-levels"></a>Pięć poziomów personifikacji  
 Zabezpieczenia transportu korzysta z pięciu poziomów personifikacji, zgodnie z opisem w poniższej tabeli.  
  
|Poziom personifikacji|Opis|  
|-------------------------|-----------------|  
|Brak|Aplikacja serwera nie próbuje dokonać personifikacji klienta.|  
|Anonimowe|Aplikacja serwera może wykonywać kontroli dostępu przed poświadczenia klienta, ale nie otrzymuje żadnych informacji o tożsamości klienta. Ten poziom personifikacji ma znaczenie tylko do komunikacji na komputerze, takich jak nazwanych potoków. Przy użyciu `Anonymous` z połączenia zdalnego wspiera poziom personifikacji identyfikowanie.|  
|Zidentyfikuj|Aplikacja serwera zna tożsamości klienta i przeprowadzić weryfikację dostępu pod kątem poświadczenia klienta, ale nie można spersonifikować klienta. Zidentyfikuj jest to domyślny poziom personifikacji używane z poświadczeniami SSPI w programie WCF, chyba że dostawcę tokenów zapewnia poziom personifikacji inny.|  
|Impersonate|Aplikacja serwera może uzyskiwać dostęp do zasobów na komputerze z serwerem jako klienta oprócz przeprowadzania kontroli dostępu. Aplikacja serwera nie może uzyskać dostęp do zasobów na komputerach zdalnych przy użyciu tożsamości klienta, ponieważ token personifikowanej nie ma poświadczeń sieciowych|  
|Delegate|Oprócz mających takie same możliwości jak `Impersonate`, poziomu personifikacji delegowanie umożliwia również aplikacji serwera na dostęp do zasobów na komputerach zdalnych przy użyciu tożsamości klienta i do przekazania tożsamości do innych aplikacji.<br /><br /> **Ważne** konto domeny serwera muszą być oznaczone jako zaufane dla delegowania na kontrolerze domeny, aby korzystać z dodatkowych funkcji. Ten poziom personifikacji nie można używać z konta domeny klienta oznaczony jako poufne.|  
  
 Poziomy najczęściej używane z zabezpieczeń transportu są `Identify` i `Impersonate`. Poziomy `None` i `Anonymous` nie są zalecane w przypadku typowych, i z uwierzytelnianiem przy użyciu tych poziomów nie obsługują wiele transportów. `Delegate` Poziom jest zaawansowaną funkcją, które mają być używane z rozwagą. Tylko zaufanych serwerów aplikacji należy nadać uprawnienia do delegowania poświadczeń.  
  
 Korzystanie z personifikacji na `Impersonate` lub `Delegate` poziomy wymaga aplikacji serwera, aby `SeImpersonatePrivilege` uprawnień. Aplikacja ma to uprawnienie domyślnie, jeśli została uruchomiona przy użyciu konta w grupie Administratorzy lub przy użyciu konta o identyfikatorze SID Service (Usługa sieciowa, Usługa lokalna lub systemu lokalnego). Personifikacja nie wymaga wzajemnego uwierzytelniania klienta i serwera. Nie można używać niektórych schematy uwierzytelniania, które obsługuje personifikacji, takich jak uwierzytelnianie NTLM i przez uwierzytelnianie wzajemne.  
  
## <a name="transport-specific-issues-with-impersonation"></a>Problemy specyficzne dla transportu z personifikacji  
 Wybór transportu programu WCF wpływa na możliwe opcje personifikacji. Ta sekcja zawiera opis zagadnień wpływających na standardowego protokołu HTTP i nazwanych potoków transporty w programie WCF. Niestandardowe transportów mają własne ograniczeń na obsługę personifikacji.  
  
### <a name="named-pipe-transport"></a>O nazwie transportu potoku  
 Następujące elementy są używane z transportu nazwanego potoku:  
  
-   Transportu nazwanego potoku jest przeznaczony do użytku tylko na komputerze lokalnym. Transportu nazwanego potoku w programie WCF nie jawnie zezwala na połączenia między komputerami.  
  
-   Nazwane potoki nie można używać z `Impersonate` lub `Delegate` poziom personifikacji. Nazwany potok nie można wymusić na komputerze gwarancji te poziomy personifikacji.  
  
 Aby uzyskać więcej informacji o nazwanych potoków, zobacz [Wybieranie transportu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
### <a name="http-transport"></a>HTTP Transport  
 Powiązania, które używają protokołu HTTP (<xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.BasicHttpBinding>) obsługuje wielu schematów uwierzytelniania, zgodnie z objaśnieniem w [opis uwierzytelniania HTTP](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md). Personifikacja obsługiwany poziom zależy od schematu uwierzytelniania. Następujące elementy są używane z transportu HTTP:  
  
-   `Anonymous` Schemat uwierzytelniania ignoruje personifikacji.  
  
-   `Basic` Schemat uwierzytelniania obsługuje tylko `Delegate` poziom. Wszystkie niższe poziomy personifikacji są uaktualniane.  
  
-   `Digest` Schemat uwierzytelniania obsługuje tylko `Impersonate` i `Delegate` poziomów.  
  
-   `NTLM` Schemat uwierzytelniania wybieranych bezpośrednio lub za pośrednictwem negocjacji, obsługuje tylko `Delegate` poziomu na komputerze lokalnym.  
  
-   Schemat uwierzytelniania Kerberos, który można wybrać tylko za pośrednictwem negocjacji, może służyć o dowolnym poziomie personifikacji obsługiwane.  
  
 Aby uzyskać więcej informacji na temat protokołu HTTP, zobacz [Wybieranie transportu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 [Autoryzacja](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [Instrukcje: personifikowanie klienta w usłudze](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)  
 [Opis uwierzytelniania HTTP](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md)
