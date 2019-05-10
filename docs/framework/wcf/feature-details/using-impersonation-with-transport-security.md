---
title: Korzystanie z personifikacji z zabezpieczeniami transportu
ms.date: 03/30/2017
ms.assetid: 426df8cb-6337-4262-b2c0-b96c2edf21a9
ms.openlocfilehash: f392dbe5806532eba181adef4ba3c8bebce9eddd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64637444"
---
# <a name="using-impersonation-with-transport-security"></a>Korzystanie z personifikacji z zabezpieczeniami transportu
*Personifikacja* to zdolność aplikacji serwera, na potrzeby tożsamości klienta. Jest to typowe dla usługi, aby podczas weryfikacji dostępu do zasobów należy używać personifikacji. Aplikacja zostanie uruchomiona przy użyciu konta usługi, ale gdy serwer akceptuje połączenia klienta, personifikuje klienta, tak, aby sprawdzanie uprawnień dostępu są wykonywane przy użyciu poświadczeń klienta. Zabezpieczenia transportu jest mechanizm przekazywania poświadczeń i zabezpieczenia komunikacji przy użyciu tych poświadczeń. W tym temacie opisano, za pomocą zabezpieczeń transportu w Windows Communication Foundation (WCF) z funkcją personifikacji. Aby uzyskać więcej informacji na temat personifikacji korzystanie z zabezpieczeń komunikatów, zobacz [delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="five-impersonation-levels"></a>Pięć poziomów personifikacji  
 Transport security korzysta z pięciu poziomów personifikacji, zgodnie z opisem w poniższej tabeli.  
  
|Poziom personifikacji|Opis|  
|-------------------------|-----------------|  
|Brak|Aplikacja serwera nie podjęto próby personifikacji klienta.|  
|Anonimowe|Aplikacja serwera można wykonywać sprawdzanie uprawnień dostępu przed poświadczenia klienta, ale nie otrzymano informacji o tożsamości klienta. Ten poziom personifikacji ma znaczenie tylko w przypadku komunikacji na komputerze, na przykład do potoków nazwanych. Za pomocą `Anonymous` z połączenia zdalnego podwyższa poziom personifikacji tożsamością.|  
|Identyfikowanie|Aplikacja serwera wie, tożsamość klienta i można wykonywać sprawdzanie poprawności dostępu do względem poświadczenia klienta, ale nie można spersonifikować klienta. Identyfikowanie jest to domyślny poziom personifikacji, który jest używany przy użyciu poświadczeń SSPI w programie WCF, chyba że dostawcy tokenu, który zapewnia poziom personifikacji różnych.|  
|Impersonate|Aplikacja serwera może uzyskiwać dostęp do zasobów na komputerze z serwerem, jako klienta oprócz przeprowadzania kontroli dostępu. Aplikacja serwera nie może uzyskiwać dostęp do zasobów na maszyny zdalne przy użyciu tożsamości klienta, ponieważ spersonifikowanego tokenu nie ma poświadczeń sieciowych|  
|Delegate|Oprócz mających takie same możliwości jak `Impersonate`, poziom personifikacji delegata umożliwia również aplikacji serwera, które uzyskują dostęp do zasobów na maszyny zdalne przy użyciu tożsamości klienta i do przekazywania tożsamość do innych aplikacji.<br /><br /> **Ważne** konto domeny serwera musi być oznaczona jako zaufane dla delegowania na kontrolerze domeny, aby korzystać z dodatkowych funkcji. Ten poziom personifikacji nie można używać z konta domeny klienta oznaczone jako poufne.|  
  
 Dostępne są następujące poziomy najczęściej używane z zabezpieczeniami transportu `Identify` i `Impersonate`. Poziomy `None` i `Anonymous` nie są zalecane w przypadku typowego użycia i przy użyciu uwierzytelniania za pomocą tych poziomów nie obsługują wielu transportów. `Delegate` Poziom jest zaawansowaną funkcją, która powinna być stosowana z rozwagą. Tylko zaufanych serwerów aplikacji, należy nadać uprawnienia do delegowania poświadczeń.  
  
 Korzystanie z personifikacji w `Impersonate` lub `Delegate` poziomy wymaga aplikacji serwera, aby `SeImpersonatePrivilege` uprawnień. Aplikacja ma to uprawnienie domyślnie, jeśli jest uruchomiony przy użyciu konta w grupie Administratorzy lub przy użyciu konta z identyfikatorem SID usługi (Usługa sieciowa, Usługa lokalna lub systemu lokalnego). Personifikacja nie wymaga wzajemnego uwierzytelniania klienta i serwera. Niektóre schematy uwierzytelniania, które obsługuje personifikacji, takich jak NTLM, nie można używać z wzajemnego uwierzytelniania.  
  
## <a name="transport-specific-issues-with-impersonation"></a>Problemy specyficzne dla transportu dla personifikacji  
 Wybór transportu programu WCF wpływa na możliwościami personifikacji. W tej sekcji opisano problemy wpływające na standardowego protokołu HTTP i nazwanych potoków transporty w programie WCF. Niestandardowe transportów ma swoje własne żadnych ograniczeń dotyczących pomocy technicznej dla personifikacji.  
  
### <a name="named-pipe-transport"></a>O nazwie transportu potoku  
 Następujące elementy są używane za pomocą transportu nazwanego potoku:  
  
- Transportu nazwanego potoku jest przeznaczony do użytku tylko na komputerze lokalnym. Transportu nazwanego potoku w programie WCF nie wyraźnie zezwala na połączenia między komputerami.  
  
- Nie można używać do potoków nazwanych `Impersonate` lub `Delegate` poziom personifikacji. Nazwany potok nie może wymusić gwarancji na komputerze, na tych poziomach personifikacji.  
  
 Aby uzyskać więcej informacji na temat potoków nazwanych, zobacz [Wybieranie transportu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
### <a name="http-transport"></a>HTTP Transport  
 Powiązania, które używają protokołu HTTP (<xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.BasicHttpBinding>) obsługują kilka schematy uwierzytelniania, jak wyjaśniono w [opis uwierzytelniania HTTP](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md). Personifikacja obsługiwany poziom zależy od schematu uwierzytelniania. Następujące elementy są używane przy użyciu protokołu http:  
  
- `Anonymous` Schematu uwierzytelniania ignoruje personifikacji.  
  
- `Basic` Schematu uwierzytelniania obsługuje tylko `Delegate` poziom. Uaktualniane są wszystkie niższe poziomy personifikacji.  
  
- `Digest` Schematu uwierzytelniania obsługuje tylko `Impersonate` i `Delegate` poziomów.  
  
- `NTLM` Schematu uwierzytelniania, można wybierać bezpośrednio lub za pomocą negocjowania, obsługuje tylko `Delegate` poziomu na komputerze lokalnym.  
  
- Schemat uwierzytelniania Kerberos, który można wybierać wyłącznie przy użyciu negocjacji, może służyć o dowolnym poziomie personifikacji obsługiwane.  
  
 Aby uzyskać więcej informacji na temat protokołu HTTP, zobacz [Wybieranie transportu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
## <a name="see-also"></a>Zobacz także

- [Delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
- [Autoryzacja](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
- [Instrukcje: Personifikowanie klienta w usłudze](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)
- [Opis uwierzytelniania HTTP](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md)
