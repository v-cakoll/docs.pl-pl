---
title: Architektura aktywacji WAS
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 2dd11ec9d642f5bfdd08c71487e82a8cb5133520
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557110"
---
# <a name="was-activation-architecture"></a>Architektura aktywacji WAS
W tym temacie wyszczególniono oraz omówienie składników usługi aktywacji procesów systemu Windows (znany także jako WAS).  
  
## <a name="activation-components"></a>Składniki aktywacji  
 ZOSTAŁ składa się z kilku składników architektury:  
  
-   Odbiornik kart. Usługi Windows odbierać wiadomości od określonych protokołów sieciowych, które komunikują się z WAS do rozsyłania wiadomości przychodzących do procesu roboczego poprawne.  
  
-   BYŁO. Usługa Windows, która zarządza tworzeniem i okresem istnienia procesów roboczych.  
  
-   Ogólny proces pliku wykonywalnego procesu roboczego (w3wp.exe).  
  
-   Menedżer aplikacji. Zarządza tworzeniem i okresem istnienia domen aplikacji, które przetwarzają hostowanie aplikacji w ramach procesu roboczego.  
  
-   Programy obsługi protokołu. Składniki związane z protokołem, które są uruchamiane w procesie roboczym i zarządzania komunikacją między procesu roboczego i kart odbiornika. Istnieją dwa typy obsługi protokołu: procesu obsługi protokołu i programy obsługi protokołu obiektu AppDomain.  
  
 Gdy WAS aktywuje wystąpienia procesu roboczego ładuje obsługi protokołu procesu, które są wymagane do procesu roboczego i używa Menedżera aplikacji, aby utworzyć domenę aplikacji do hostowania aplikacji. Domeny aplikacji, ładuje kod aplikacji, a także obsługi protokołu domeny aplikacji, które protokoły sieciowe używane przez wymagają aplikacji.  
  
 ![Architektura WAS](../../../../docs/framework/wcf/feature-details/media/wasarchitecture.gif "WASArchitecture")  
  
### <a name="listener-adapters"></a>Odbiornik kart  
 Odbiornik karty są poszczególnych usług Windows, które implementują logikę komunikacji sieciowej używaną do odbierania komunikatów za pomocą protokołu sieciowego, na którym się one nasłuchiwanie. W poniższej tabeli wymieniono kart odbiornika protokołu Windows Communication Foundation (WCF).  
  
|Nazwa usługi karty odbiornika|Protokół|Uwagi|  
|-----------------------------------|--------------|-----------|  
|W3SVC|http|Typowe składnik, który zapewnia Aktywacja HTTP dla usług IIS 7.0 i WCF.|  
|NetTcpActivator|net.tcp|Zależy od usługi NetTcpPortSharing.|  
|NetPipeActivator|net.pipe||  
|NetMsmqActivator|net.msmq|Do użytku z aplikacjami usługi WCF na podstawie usługi kolejkowania komunikatów.|  
|NetMsmqActivator|msmq.formatname|Udostępnia wstecznej zgodności z istniejącymi aplikacjami usługi kolejkowania komunikatów.|  
  
 Karty odbiornika dla określonych protokołów są rejestrowane podczas instalacji w pliku applicationHost.config, jak pokazano w poniższym przykładzie XML.  
  
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
 Proces i obsługi protokołu AppDomain dla określonych protokołów są rejestrowane w pliku Web.config poziomie komputera.  
  
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
  
## <a name="see-also"></a>Zobacz także
- [Konfigurowanie usługi WAS do użycia z programem WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [Windows Server AppFabric funkcje hostingu](https://go.microsoft.com/fwlink/?LinkId=201276)
