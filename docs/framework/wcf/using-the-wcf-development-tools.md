---
title: Używanie narzędzi deweloperskich programu WCF
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 3eb349fd795b2067d4d75ff138fd9b5922110bd3
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741120"
---
# <a name="using-the-wcf-development-tools"></a>Używanie narzędzi deweloperskich programu WCF
W tej sekcji opisano narzędzia programistyczne programu Visual Studio, które mogą pomóc w rozwoju Twojej WCFservice.  
  
 Możesz szybko tworzyć własne usługi za pomocą szablonów programu Visual Studio jako podstawa, a następnie użyj hostów Auto usługi WCF i WCF przetestować klienta do debugowania i testowania usługi. Razem te narzędzia zapewniają szybkie i bezproblemowe debugowanie i cyklu testowania i wyklucza trzeba przekazać do modelu hostowania na wczesnym etapie.  
  
## <a name="the-wcf-developer-tools"></a>Narzędzi deweloperskich programu WCF  
 [Szablony programu Visual Studio na potrzeby programu WCF](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 Wstępnie zdefiniowane szablony projektów i elementów programu Visual Studio w programie Visual Studio umożliwia szybkie tworzenie usług WCF i otaczającego aplikacji.  
  
 [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 Host automatycznie usługi WCF (WcfSvcHost.exe) można uruchomić debugera programu Visual Studio (F5), aby automatycznie obsługiwać i przetestować usługę, w których zaimplementowano. Następnie można testować usługę za pomocą testu klient WCF (wcfTestClient.exe) lub własnego klienta można znaleźć i naprawić wszelkie potencjalne błędy.  
  
 [Testowy klient WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 Testowy klient WCF (WcfTestClient.exe) jest narzędziem graficznego interfejsu użytkownika, które pozwala na arbitralnie wybrane typy parametrów wejściowych, przesyłanie te dane wejściowe do usługi i widok, który odsyła odpowiedź usługi. Zapewnia bezproblemowe usługi testowania doświadczenie w połączeniu z hostów Auto usługi WCF.  
  
 [Generowanie klas typów danych z kodu XML](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 XML — dane przechowywane w Schowku można wkleić do strony kodowej. Klas zdefiniowanych w danych zostaną przekonwertowane na typy kodu.  
  
## <a name="using-the-tools-without-administrator-privilege"></a>Za pomocą narzędzi bez uprawnień administratora  
 Aby umożliwić użytkownikom bez uprawnień administratora do tworzenia usług WCF, (listę kontroli dostępu) jest tworzony dla przestrzeni nazw "http://+:8731/Design_Time_Addresses" podczas instalacji programu Visual Studio. Lista ACL jest równa (UI), która obejmuje wszystkie interaktywne użytkownicy zalogowani na maszynie. Administratorzy mogą dodawać lub usuwać użytkowników z tej listy ACL lub otwarcie dodatkowych portów. Ta lista ACL umożliwia WCF lub WF szablonów do wysyłania i odbierania danych w konfiguracji domyślnej. Umożliwia również użytkownikom używanie Host automatycznie usługi WCF (wcfSvcHost.exe) bez nadawania im uprawnień administratora.  
  
 Możesz zmodyfikować dostępu przy użyciu narzędzia Netsh.exe w [!INCLUDE[wv](../../../includes/wv-md.md)] przy użyciu konta administratora z podniesionymi uprawnieniami. Oto przykład użycia Netsh.exe.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Aby uzyskać więcej informacji na temat Netsh.exe zobacz [sposób użycia narzędzia Netsh.exe i przełączniki wiersza polecenia](https://go.microsoft.com/fwlink/?LinkId=97877).  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony programu Visual Studio na potrzeby programu WCF](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [Testowy klient WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
