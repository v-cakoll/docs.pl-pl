---
title: "Aktywacja oparta na konfiguracji w usługach IIS i WAS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0938b98a3f079d03653df55f10c26a4a62db5bf3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="configuration-based-activation-in-iis-and-was"></a>Aktywacja oparta na konfiguracji w usługach IIS i WAS
Zwykle odnośnie do hostowania [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi Internet Information Services (IIS) lub usługi aktywacji procesów systemu Windows (WAS), należy podać pliku svc. W pliku svc zawiera nazwę usługi i opcjonalne niestandardowe usługi fabryka hostów. Ten plik dodatkowe zwiększa możliwości zarządzania obciążenia. Aktywacja oparta na konfiguracji funkcji eliminuje konieczność pliku svc i w związku z tym skojarzone koszty.  
  
## <a name="configuration-based-activation"></a>Aktywacja oparta na konfiguracji  
 Aktywacja oparta na konfiguracji ma metadane używane do umieszczenia w pliku svc i umieszcza je w pliku Web.config. W ramach <`serviceHostingEnvironment`> istnieje element <`serviceActivations`> elementu. W ramach <`serviceActivations`> elementu są co najmniej jeden <`add`> elementy, dla każdej usługi hostowanej. <`add`> Element zawiera atrybuty, które pozwalają na ustawienie adres względny dla typu usługi i fabryki hostów usług lub usługi. Poniższy przykładowy kod konfiguracji pokazuje, jak jest używany w tej sekcji.  
  
> [!NOTE]
>  Każdy <`add`> element musi określać usługi lub atrybut factory. Określenie zarówno usługi i fabryki atrybutów jest dozwolone.  
  
```xml  
<serviceHostingEnvironment>  
  <serviceActivations>  
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>  
  </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
 Z tym w pliku Web.config można umieścić usługi kodu źródłowego w katalogu App_Code aplikacji lub skompilowane zestawu w katalogu Bin aplikacji.  
  
> [!NOTE]
>  -   Korzystając z aktywację w oparciu o konfiguracji, wbudowanego kodu w plikach SVC nie jest obsługiwane.  
> -   `relativeAddress` Atrybut musi być ustawiony na adres względny takich jak "\<podkatalogu > / service.svc" lub "~ /\<podrzędne directory/service.svc".  
> -   Wyjątek konfiguracji jest generowany, jeśli zarejestrujesz adresem względnym, który nie ma znane rozszerzenie skojarzone z programem WCF.  
> -   Podany adres względny jest względem katalogu głównego aplikacji wirtualnej.  
> -   Z powodu hierarchiczny model konfiguracji względne adresy zarejestrowane na poziomie maszyny i lokacji są dziedziczone przez aplikacje wirtualne.  
> -   Rejestracje w pliku konfiguracji mają pierwszeństwo przed ustawienia w SVC, .xamlx, xoml lub innego pliku.  
> -   Wszelkie "\" (Używanie ukośników odwrotnych) w identyfikatorze URI wysyłane do usług IIS / WAS automatycznie są konwertowane na "/" (ukośnik). Jeśli adres względny zostanie dodany, który zawiera "\" i wysyłanie IIS identyfikator URI, który używa adres względny, kreska ułamkowa odwrócona jest konwertowana na ukośnik, oraz usług IIS nie może być zgodny z jego adres względny. Usługi IIS wysyła informacje o śledzeniu, która wskazuje, że nie ma żadnych dopasowań.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>  
 [Usługi hostingowe](../../../../docs/framework/wcf/hosting-services.md)  
 [Przegląd hostowania usług przepływu pracy](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [\<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)  
 [Windows Server AppFabric funkcje hostingu](http://go.microsoft.com/fwlink/?LinkId=201276)
