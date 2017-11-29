---
title: "Używanie narzędzi deweloperskich programu WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f752d2aa2621ff650c864b2aca0928c5244c4917
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-wcf-development-tools"></a>Używanie narzędzi deweloperskich programu WCF
W tej sekcji opisano [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] narzędzi programistycznych, które mogą pomóc w tworzeniu sieci [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]usługi.  
  
 Można użyć [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] następnie użyć szablonów jako podstawę do szybko tworzyć własne usługi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hosta usługi automatycznie i [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] testowanie klienta do debugowania i testowania usługi. Te narzędzia razem Podaj szybkiego i łatwego debugowania i testowania cyklu i wyklucza trzeba przekazać do obsługi modelu na wczesnym etapie.  
  
## <a name="the-wcf-developer-tools"></a>Narzędzia deweloperskie programu WCF  
 [Szablony Visual Studio WCF](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 Można użyć wstępnie zdefiniowane [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] szablonów projektów i elementów w [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] można szybko utworzyć [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi i aplikacje otaczającego.  
  
 [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hosta usługi automatycznie (WcfSvcHost.exe) pozwala na uruchamianie [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] debugera (F5), aby automatycznie udostępniać i testowanie usługi zostały zaimplementowane. Następnie można testować przy użyciu usługi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] testowanie klienta (wcfTestClient.exe) lub własnego klienta, aby znaleźć i rozwiązać wszelkie potencjalne błędy.  
  
 [Klienta testowego WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Klient testowy (WcfTestClient.exe) to narzędzie graficznego interfejsu użytkownika, które można wprowadzić parametry dowolnego typu, że dane wejściowe do usługi i widoku, który odsyła odpowiedź usługi przesyłania. Zapewnia bezproblemowe usługi testowania czynności w połączeniu z [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hosta usługi automatycznie.  
  
 [Generowanie klas typów danych z pliku XML](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 Dane XML przechowywane w Schowku można wkleić do strony kodowej. Klas zdefiniowanych w danych zostanie przekonwertowany na typy kodu.  
  
## <a name="using-the-tools-without-administrator-privilege"></a>Za pomocą narzędzi bez uprawnień administratora  
 Aby umożliwić użytkownikom bez uprawnień administratora do opracowywania [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usług, list kontroli dostępu (listy kontroli dostępu) jest tworzona podczas instalacji dla przestrzeni nazw "http://+:8731/Design_Time_Addresses" [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. Listy ACL ustawiono (UI), która obejmuje wszystkie interaktywne użytkownicy zalogowani do komputera. Administratorzy mogą dodawać lub usuwać użytkowników z tej listy ACL lub Otwórz dodatkowych portów. Tej listy ACL umożliwia WCF i WF szablony do wysyłania i odbierania danych w domyślnej konfiguracji. Umożliwia również użytkownikom używanie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] automatycznie hosta usługi (wcfSvcHost.exe) bez przyznania im uprawnień administratora.  
  
 Można zmodyfikować dostępu za pomocą narzędzia Netsh.exe w [!INCLUDE[wv](../../../includes/wv-md.md)] przy użyciu konta administratora z podniesionymi uprawnieniami. Oto przykład użycia Netsh.exe.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]Netsh.exe, zobacz [jak używać narzędzia Netsh.exe i przełączniki wiersza polecenia](http://go.microsoft.com/fwlink/?LinkId=97877).  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony Visual Studio WCF](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [Klienta testowego WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
