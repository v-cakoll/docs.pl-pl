---
title: Korzystanie z personifikacji z zabezpieczeniami transportu
ms.date: 03/30/2017
ms.assetid: 426df8cb-6337-4262-b2c0-b96c2edf21a9
ms.openlocfilehash: 1d33bfbbb74266aefa538166b4e1aca7d7e315ef
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594975"
---
# <a name="using-impersonation-with-transport-security"></a>Korzystanie z personifikacji z zabezpieczeniami transportu
*Personifikacja* to możliwość, aby aplikacja serwera mogła przejąć tożsamość klienta. Podczas sprawdzania poprawności dostępu do zasobów często używane są personifikacje usług. Aplikacja serwera jest uruchamiana przy użyciu konta usługi, ale gdy serwer zaakceptuje połączenie klienta, personifikuje klienta, aby testy dostępu były wykonywane przy użyciu poświadczeń klienta. Zabezpieczenia transportu to mechanizm przekazywania poświadczeń i zabezpieczania komunikacji przy użyciu tych poświadczeń. W tym temacie opisano korzystanie z zabezpieczeń transportu w programie Windows Communication Foundation (WCF) z funkcją personifikacji. Aby uzyskać więcej informacji na temat personifikacji przy użyciu zabezpieczeń wiadomości, zobacz [delegowanie i personifikacja](delegation-and-impersonation-with-wcf.md).  
  
## <a name="five-impersonation-levels"></a>Pięć poziomów personifikacji  
 Zabezpieczenia transportu korzystają z pięciu poziomów personifikacji, zgodnie z opisem w poniższej tabeli.  
  
|Poziom personifikacji|Opis|  
|-------------------------|-----------------|  
|Brak|Aplikacja serwera nie próbuje personifikować klienta.|  
|Anonimowe|Aplikacja serwera może przeprowadzać testy dostępu względem poświadczeń klienta, ale nie otrzymuje żadnych informacji o tożsamości klienta. Ten poziom personifikacji ma znaczenie tylko w przypadku komunikacji na komputerze, na przykład nazwanych potoków. Użycie programu `Anonymous` z połączeniem zdalnym podnosi poziom personifikacji do identyfikacji.|  
|Ustalenia|Aplikacja serwera wie tożsamość klienta i może przeprowadzić walidację dostępu względem poświadczeń klienta, ale nie może personifikować klienta. Identyfikuj to domyślny poziom personifikacji używany z poświadczeniami interfejsu SSPI w programie WCF, chyba że Dostawca tokenu udostępnia inny poziom personifikacji.|  
|Impersonate|Aplikacja serwerowa może uzyskać dostęp do zasobów na komputerze serwera jako klient programu oprócz kontroli dostępu. Aplikacja serwera nie może uzyskać dostępu do zasobów na komputerach zdalnych przy użyciu tożsamości klienta, ponieważ personifikowany token nie ma poświadczeń sieciowych|  
|Delegat|Oprócz posiadania takich samych możliwości jak `Impersonate` , poziom personifikacji delegata umożliwia również aplikacji serwera dostęp do zasobów na komputerach zdalnych przy użyciu tożsamości klienta i przekazywanie tożsamości do innych aplikacji.<br /><br /> **Ważne** Konto domeny serwera musi być oznaczone jako zaufane dla delegowania na kontrolerze domeny, aby można było korzystać z tych dodatkowych funkcji. Tego poziomu personifikacji nie można używać z kontami domeny klienta oznaczonymi jako poufne.|  
  
 Poziomy najczęściej używane z zabezpieczeniami transportu to `Identify` i `Impersonate` . Poziomy `None` i `Anonymous` nie są zalecane w przypadku typowego użycia, a wiele transportów nie obsługuje korzystania z tych poziomów z uwierzytelnianiem. `Delegate`Poziom to zaawansowana funkcja, która powinna być używana z opieką. Tylko zaufane aplikacje serwera powinny mieć przyznane uprawnienia do delegowania poświadczeń.  
  
 Użycie personifikacji na `Impersonate` `Delegate` poziomach lub wymaga, aby aplikacja serwera miała to `SeImpersonatePrivilege` uprawnienie. Aplikacja ma to uprawnienie domyślnie, jeśli jest uruchomiona na koncie w grupie Administratorzy lub na koncie z identyfikatorem SID usługi (usługa sieciowa, Usługa lokalna lub system lokalny). Personifikacja nie wymaga wzajemnego uwierzytelniania klienta i serwera. Niektóre schematy uwierzytelniania obsługujące personifikację, takie jak NTLM, nie mogą być używane z uwierzytelnianiem obustronnym.  
  
## <a name="transport-specific-issues-with-impersonation"></a>Problemy związane z transportem dotyczące personifikacji  
 Wybór transportu w programie WCF ma wpływ na możliwe opcje personifikacji. W tej sekcji opisano problemy mające wpływ na transporty standardowego protokołu HTTP i nazwanego potoku w programie WCF. Niestandardowe transporty mają własne ograniczenia dotyczące obsługi personifikacji.  
  
### <a name="named-pipe-transport"></a>Transport nazwanych potoków  
 Następujące elementy są używane z transportem nazwanego potoku:  
  
- Transport nazwanego potoku jest przeznaczony do użycia tylko na komputerze lokalnym. Transport potoków nazwanych w usłudze WCF jawnie nie zezwala na połączenia między maszynami.  
  
- Nazwane potoki nie mogą być używane `Impersonate` z `Delegate` poziomem personifikacji lub. Nazwany potok nie może wymusić gwarancji na komputerze na tych poziomach personifikacji.  
  
 Aby uzyskać więcej informacji na temat nazwanych potoków, zobacz [Wybieranie transportu](choosing-a-transport.md).  
  
### <a name="http-transport"></a>Transport HTTP  
 Powiązania korzystające z transportu HTTP ( <xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.BasicHttpBinding> ) obsługują kilka schematów uwierzytelniania, zgodnie z opisem w temacie [uwierzytelnianie HTTP](understanding-http-authentication.md). Obsługiwany poziom personifikacji zależy od schematu uwierzytelniania. Następujące elementy są używane z transportem HTTP:  
  
- `Anonymous`Schemat uwierzytelniania ignoruje personifikację.  
  
- `Basic`Schemat uwierzytelniania obsługuje tylko `Delegate` poziom. Wszystkie niższe poziomy personifikacji są uaktualniane.  
  
- `Digest`Schemat uwierzytelniania obsługuje tylko `Impersonate` `Delegate` poziomy i.  
  
- `NTLM`Schemat uwierzytelniania, który można wybrać bezpośrednio lub przez negocjowanie, obsługuje tylko `Delegate` poziom na komputerze lokalnym.  
  
- Schemat uwierzytelniania Kerberos, który można wybrać tylko za pośrednictwem negocjacji, może być używany z dowolnym obsługiwanym poziomem personifikacji.  
  
 Aby uzyskać więcej informacji na temat transportu HTTP, zobacz [Wybieranie transportu](choosing-a-transport.md).  
  
## <a name="see-also"></a>Zobacz też

- [Delegowanie i personifikacja](delegation-and-impersonation-with-wcf.md)
- [Autoryzacja](authorization-in-wcf.md)
- [Instrukcje: Personifikowanie klienta w usłudze](../how-to-impersonate-a-client-on-a-service.md)
- [Opis uwierzytelniania HTTP](understanding-http-authentication.md)
