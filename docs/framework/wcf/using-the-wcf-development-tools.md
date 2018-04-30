---
title: Używanie narzędzi deweloperskich programu WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7ec09b6b99b831245d11d858f90c27de05d1e21f
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="using-the-wcf-development-tools"></a>Używanie narzędzi deweloperskich programu WCF
W tej sekcji opisano narzędzia programistyczne programu Visual Studio, które mogą pomóc w tworzeniu sieci [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]usługi.  
  
 Szablony Visual Studio jako podstawę służy do szybkiego budowania własne usługi, a następnie użyj [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hosta usługi automatycznie i [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] testowanie klienta do debugowania i testowania usługi. Te narzędzia razem Podaj szybkiego i łatwego debugowania i testowania cyklu i wyklucza trzeba przekazać do obsługi modelu na wczesnym etapie.  
  
## <a name="the-wcf-developer-tools"></a>Narzędzia deweloperskie programu WCF  
 [Szablony programu Visual Studio na potrzeby programu WCF](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 Można użyć wstępnie zdefiniowanych szablonów projektów i elementów programu Visual Studio w programie Visual Studio można szybko utworzyć [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi i aplikacje otaczającego.  
  
 [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hosta usługi automatycznie (WcfSvcHost.exe) umożliwia Uruchom debuger programu Visual Studio (F5), aby automatycznie udostępniać i testowanie usługi zostały zaimplementowane. Następnie można testować przy użyciu usługi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] testowanie klienta (wcfTestClient.exe) lub własnego klienta, aby znaleźć i rozwiązać wszelkie potencjalne błędy.  
  
 [Testowy klient WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Klient testowy (WcfTestClient.exe) to narzędzie graficznego interfejsu użytkownika, które można wprowadzić parametry dowolnego typu, że dane wejściowe do usługi i widoku, który odsyła odpowiedź usługi przesyłania. Zapewnia bezproblemowe usługi testowania czynności w połączeniu z [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hosta usługi automatycznie.  
  
 [Generowanie klas typów danych z kodu XML](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 Dane XML przechowywane w Schowku można wkleić do strony kodowej. Klas zdefiniowanych w danych zostanie przekonwertowany na typy kodu.  
  
## <a name="using-the-tools-without-administrator-privilege"></a>Za pomocą narzędzi bez uprawnień administratora  
 Aby umożliwić użytkownikom bez uprawnień administratora do opracowywania [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usług, list kontroli dostępu (listy kontroli dostępu) jest tworzony dla przestrzeni nazw "http://+:8731/Design_Time_Addresses" podczas instalacji programu Visual Studio. Listy ACL ustawiono (UI), która obejmuje wszystkie interaktywne użytkownicy zalogowani do komputera. Administratorzy mogą dodawać lub usuwać użytkowników z tej listy ACL lub Otwórz dodatkowych portów. Tej listy ACL umożliwia WCF i WF szablony do wysyłania i odbierania danych w domyślnej konfiguracji. Umożliwia również użytkownikom używanie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] automatycznie hosta usługi (wcfSvcHost.exe) bez przyznania im uprawnień administratora.  
  
 Można zmodyfikować dostępu za pomocą narzędzia Netsh.exe w [!INCLUDE[wv](../../../includes/wv-md.md)] przy użyciu konta administratora z podniesionymi uprawnieniami. Oto przykład użycia Netsh.exe.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Aby uzyskać więcej informacji na temat Netsh.exe, zobacz [jak używać narzędzia Netsh.exe i przełączniki wiersza polecenia](http://go.microsoft.com/fwlink/?LinkId=97877).  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony programu Visual Studio na potrzeby programu WCF](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [Testowy klient WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
