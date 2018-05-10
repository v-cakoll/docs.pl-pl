---
title: Używanie narzędzi deweloperskich programu WCF
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 41d2ee2881b79ffb086a931ec6d271d409ac66db
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="using-the-wcf-development-tools"></a>Używanie narzędzi deweloperskich programu WCF
W tej sekcji opisano narzędzia programistyczne programu Visual Studio, które mogą pomóc w tworzeniu WCFservice Twojego.  
  
 Możesz szybko tworzyć własne usługi za pomocą szablonów programu Visual Studio jako podstawę, a następnie użyj Host automatycznie usługi WCF i testowanie klienta platformy WCF do debugowania i testowania usługi. Te narzędzia razem Podaj szybkiego i łatwego debugowania i testowania cyklu i wyklucza trzeba przekazać do obsługi modelu na wczesnym etapie.  
  
## <a name="the-wcf-developer-tools"></a>Narzędzia deweloperskie programu WCF  
 [Szablony programu Visual Studio na potrzeby programu WCF](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 Wstępnie zdefiniowanych szablonów projektów i elementów programu Visual Studio w programie Visual Studio umożliwia szybkie tworzenie usług WCF i otaczającego aplikacji.  
  
 [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 Host automatycznie usługi WCF (WcfSvcHost.exe) umożliwia Uruchom debuger programu Visual Studio (F5), aby automatycznie udostępniać i testowanie usługi, które zostały zaimplementowane. Następnie można przetestować tę usługę, używając testowanie klienta WCF (wcfTestClient.exe) lub własnego klienta można znaleźć i rozwiązać wszelkie potencjalne błędy.  
  
 [Testowy klient WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 Klienta testowego WCF (WcfTestClient.exe) jest narzędziem graficznego interfejsu użytkownika, które można wprowadzić parametry dowolnego typu, że dane wejściowe do usługi i widoku, który odsyła odpowiedź usługi przesyłania. Zapewnia bezproblemowe usługi testowania doświadczenie w połączeniu z hostem automatycznie usługi WCF.  
  
 [Generowanie klas typów danych z kodu XML](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 Dane XML przechowywane w Schowku można wkleić do strony kodowej. Klas zdefiniowanych w danych zostanie przekonwertowany na typy kodu.  
  
## <a name="using-the-tools-without-administrator-privilege"></a>Za pomocą narzędzi bez uprawnień administratora  
 Aby umożliwić użytkownikom bez uprawnień administratora do opracowywania usługi WCF, list kontroli dostępu (listy kontroli dostępu) jest tworzony dla przestrzeni nazw "http://+:8731/Design_Time_Addresses" podczas instalacji programu Visual Studio. Listy ACL ustawiono (UI), która obejmuje wszystkie interaktywne użytkownicy zalogowani do komputera. Administratorzy mogą dodawać lub usuwać użytkowników z tej listy ACL lub Otwórz dodatkowych portów. Tej listy ACL umożliwia WCF i WF szablony do wysyłania i odbierania danych w domyślnej konfiguracji. Umożliwia również użytkownikom używanie Host automatycznie usługi WCF (wcfSvcHost.exe) bez przyznania im uprawnień administratora.  
  
 Można zmodyfikować dostępu za pomocą narzędzia Netsh.exe w [!INCLUDE[wv](../../../includes/wv-md.md)] przy użyciu konta administratora z podniesionymi uprawnieniami. Oto przykład użycia Netsh.exe.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Aby uzyskać więcej informacji na temat Netsh.exe, zobacz [jak używać narzędzia Netsh.exe i przełączniki wiersza polecenia](http://go.microsoft.com/fwlink/?LinkId=97877).  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony programu Visual Studio na potrzeby programu WCF](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [Testowy klient WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
