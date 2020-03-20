---
title: Używanie narzędzi deweloperskich programu WCF
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 82bb7e225492bcdba4d2e611de405a09571355c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183082"
---
# <a name="using-the-wcf-development-tools"></a>Używanie narzędzi deweloperskich programu WCF
W tej sekcji opisano narzędzia programistyczne programu Visual Studio, które mogą pomóc w tworzeniu usługi WCFservice.  
  
 Szablony programu Visual Studio można użyć jako podstawa do szybkiego tworzenia własnej usługi, a następnie użyć WCF Service Auto Host i WCF Test Client do debugowania i testowania usługi. Te narzędzia razem zapewniają szybki i bezproblemowy cykl debugowania i testowania i wykluczają konieczność zatwierdzania modelu hostingu na wczesnym etapie.  

 > [!NOTE]
 > Począwszy od programu Visual Studio 2017 narzędzia programistyczne WCF nie są instalowane domyślnie. Aby korzystać z tych funkcji, należy upewnić się, że składnik Programu Windows Communication Foundation jest wybrany w instalatorze programu Visual Studio.
  
## <a name="the-wcf-developer-tools"></a>Narzędzia programistyczne WCF  
 [Szablony programu Visual Studio na potrzeby programu WCF](wcf-vs-templates.md)  
  
 Można użyć wstępnie zdefiniowanych szablonów projektu i elementów programu Visual Studio w programie Visual Studio, aby szybko utworzyć usługi WCF i otaczające aplikacje.  
  
 [Host usługi WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)  
  
 WCF Service Auto Host (WcfSvcHost.exe) umożliwia uruchomienie debugera programu Visual Studio (F5), aby automatycznie hostować i testować zaimplementowana usługa. Następnie można przetestować usługę przy użyciu klienta testowego WCF (wcfTestClient.exe) lub własnego klienta, aby znaleźć i naprawić wszelkie potencjalne błędy.  
  
 [Testowy klient WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)  
  
 WCF Test Client (WcfTestClient.exe) to narzędzie GUI, które umożliwia wprowadzanie parametrów dowolnego typu, przesyłanie tego danych wejściowych do usługi i wyświetlanie odpowiedzi, którą usługa wysyła z powrotem. Zapewnia bezproblemowe testowanie usług w połączeniu z auto hostem usługi WCF.  
  
 [Generowanie klas typów danych z kodu XML](generating-data-type-classes-from-xml.md)  
  
 Dane XML przechowywane w schowku można wkleić na stronę kodową. Klasy zdefiniowane w danych zostaną przekonwertowane na typy kodu.  
  
## <a name="using-the-tools-without-administrator-privilege"></a>Korzystanie z narzędzi bez uprawnień administratora  
 Aby umożliwić użytkownikom bez uprawnień administratora tworzenie usług WCF, acl (Listahttp://+:8731/Design_Time_Addresseskontroli dostępu) jest tworzony dla obszaru nazw " " " podczas instalacji programu Visual Studio. Listy ACL jest ustawiona na (UI), który obejmuje wszystkich użytkowników interaktywnych zalogowanych do komputera. Administratorzy mogą dodawać lub usuwać użytkowników z tej listy ACL lub otwierać dodatkowe porty. Ta acl umożliwia WCF lub WF szablonów do wysyłania i odbierania danych w konfiguracji domyślnej. Umożliwia również użytkownikom korzystanie z automatycznego hosta usługi WCF (wcfSvcHost.exe) bez przyznania im uprawnień administratora.  
  
 Dostęp można modyfikować za pomocą narzędzia Netsh.exe w systemie Windows Vista w obszarze podwyższonego poziomu konta administratora. Poniżej przedstawiono przykład użycia programu Netsh.exe.  
  
```console  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Aby uzyskać więcej informacji na temat programu Netsh.exe, zobacz [Jak korzystać z przełączników narzędzia Netsh.exe i wiersza polecenia](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10)).  
  
## <a name="see-also"></a>Zobacz też

- [Szablony programu Visual Studio na potrzeby programu WCF](wcf-vs-templates.md)
- [Host usługi WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [Testowy klient WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
