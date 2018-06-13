---
title: Architektura aktywacji WAS
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 0c91ebd605fbe503dd11da7167512648afd86449
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498000"
---
# <a name="was-activation-architecture"></a>Architektura aktywacji WAS
W tym temacie itemizes i zawiera omówienie składników usługi Windows Process Activation Service (znanej także jako Usługa WAS).  
  
## <a name="activation-components"></a>Składniki aktywacji  
 ZOSTAŁ składa się z kilku architektury składników:  
  
-   Karta odbiornika. Usługi systemu Windows, które odbierania komunikatów od określonych protokołów sieciowych i komunikować się z WAS do kierowania wiadomości przychodzących do procesu roboczego poprawne.  
  
-   ZOSTAŁ. Usługa systemu Windows, która zarządza tworzeniem i okresem istnienia procesów roboczych.  
  
-   Wykonywalnego procesu roboczego ogólnego (w3wp.exe).  
  
-   Menedżer aplikacji. Zarządza tworzeniem i okresem istnienia domeny aplikacji, które przetwarzają hosta aplikacji w obrębie elementu roboczego.  
  
-   Programy obsługi protokołu. Oparte na protokole składniki, których są uruchamiane w procesie roboczym i zarządzania komunikacją między proces roboczy i odbiornika poszczególnych kart. Istnieją dwa typy programów obsługi protokołu: przetworzyć obsług protokołu i programy obsługi protokołu domeny aplikacji.  
  
 Gdy WAS aktywuje wystąpieniem proces roboczy ładuje obsług protokołu procesu, które są wymagane do procesu roboczego i używa Menedżera aplikacji do tworzenia domeny aplikacji w celu hostowania aplikacji. Domeny aplikacji ładuje kodu aplikacji, a także obsługi protokołu domeny aplikacji, które protokoły sieciowe używane przez wymagana.  
  
 ![Architektura została](../../../../docs/framework/wcf/feature-details/media/wasarchitecture.gif "WASArchitecture")  
  
### <a name="listener-adapters"></a>Odbiornik kart  
 Odbiornik karty są poszczególnych usług systemu Windows, które implementują logikę komunikacji sieciowej używany do odbierania wiadomości za pomocą protokołu sieciowego, na którym one nasłuchiwanie. W poniższej tabeli wymieniono kart odbiornika protokołu Windows Communication Foundation (WCF).  
  
|Nazwa usługi adapter odbiornika|Protokół|Uwagi|  
|-----------------------------------|--------------|-----------|  
|W3SVC|Http|Typowe składnik, który udostępnia Aktywacja HTTP dla usług IIS 7.0 i WCF.|  
|Usługi NetTcpActivator|net.tcp|Zależy od usługi NetTcpPortSharing usługi.|  
|NetPipeActivator|net.pipe||  
|NetMsmqActivator|NET.MSMQ|Do użytku z aplikacjami usługi WCF na podstawie usługi kolejkowania komunikatów.|  
|NetMsmqActivator|MSMQ.formatname|Udostępnia zapewnienia zgodności z istniejącymi aplikacjami usługi kolejkowania komunikatów.|  
  
 Adaptery odbiornika dla określonych protokołów są rejestrowane podczas instalacji w pliku applicationHost.config, jak pokazano w poniższym przykładzie XML.  
  
```xml  
<system.applicationHost>  
    <listenerAdapters>  
        <add name="http" />  
        <add name="net.tcp"   
          identity="S-1-5-80-3579033775-2824656752-1522793541-1960352512-462907086" />  
         <add name="net.pipe"   
           identity="S-1-5-80-2943419899-937267781-4189664001-1229628381-3982115073" />  
          <add name="net.msmq"   
            identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
           <add name="msmq.formatname"   
             identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
    </listenerAdapters>  
</system.applicationHost>  
```  
  
### <a name="protocol-handlers"></a>Programy obsługi protokołu  
 Proces i obsługi protokołu domeny aplikacji określonych protokołów są rejestrowane w pliku Web.config poziom maszyny.  
  
```xml  
<system.web>  
   <protocols>  
      <add name="net.tcp"   
        processHandlerType=  
         "System.ServiceModel.WasHosting.TcpProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.TcpAppDomainProtocolHandler"  
        validate="false" />  
      <add name="net.pipe"   
        processHandlerType=  
         "System.ServiceModel.WasHosting.NamedPipeProcessProtocolHandler"  
          appDomainHandlerType=  
           "System.ServiceModel.WasHosting.NamedPipeAppDomainProtocolHandler"/>  
      <add name="net.msmq"  
        processHandlerType=  
         "System.ServiceModel.WasHosting.MsmqProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.MsmqAppDomainProtocolHandler"  
        validate="false" />  
   </protocols>  
</system.web>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie usługi WAS do użycia z programem WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [Windows Server AppFabric funkcje hostingu](http://go.microsoft.com/fwlink/?LinkId=201276)
