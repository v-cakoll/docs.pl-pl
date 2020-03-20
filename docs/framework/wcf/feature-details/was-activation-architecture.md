---
title: Architektura aktywacji WAS
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 67ddcd97ac75ddeb0765c38bb9ce7b5e8f039272
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184250"
---
# <a name="was-activation-architecture"></a>Architektura aktywacji WAS
W tym temacie wyszczególnia i omówiono składniki usługi aktywacji procesów systemu Windows (znanej również jako WAS).  
  
## <a name="activation-components"></a>Składniki aktywacji  
 WAS składa się z kilku elementów architektonicznych:  
  
- Adaptery odbiornika. Usługi systemu Windows, które odbierają wiadomości na określonych protokołach sieciowych i komunikują się z usługą WAS w celu kierowania wiadomości przychodzących do właściwego procesu roboczego.  
  
- Został. Usługa systemu Windows, która zarządza tworzeniem i okresem istnienia procesów roboczych.  
  
- Ogólny proces roboczy wykonywalny (w3wp.exe).  
  
- Menedżer aplikacji. Zarządza tworzeniem i okresem istnienia domen aplikacji, które hostuje aplikacje w procesie roboczym.  
  
- Programy obsługi protokołu. Składniki specyficzne dla protokołu, które działają w procesie roboczym i zarządzają komunikacją między procesem roboczym a poszczególnymi kartami odbiornika. Istnieją dwa typy programów obsługi protokołów: programy obsługi protokołów procesów i programy obsługi protokołu AppDomain.  
  
 Gdy usługa WAS aktywuje wystąpienie procesu roboczego, ładuje programy obsługi protokołu procesu wymagane do procesu roboczego i używa menedżera aplikacji do utworzenia domeny aplikacji do obsługi aplikacji. Domena aplikacji ładuje kod aplikacji, a także programy obsługi protokołu AppDomain, których wymagają protokoły sieciowe używane przez aplikację.  
  
 ![Zrzut ekranu przedstawiający architekturę WAS.](./media/was-activation-architecture/windows-process-application-service-architecture.gif)  
  
### <a name="listener-adapters"></a>Adaptery odbiornika  
 Karty odbiornika to pojedyncze usługi systemu Windows, które implementują logikę komunikacji sieciowej używaną do odbierania wiadomości przy użyciu protokołu sieciowego, na który nasłuchują. W poniższej tabeli wymieniono karty odbiornika dla protokołów Programu Windows Communication Foundation (WCF).  
  
|Nazwa usługi karty odbiornika|Protocol (Protokół)|Uwagi|  
|-----------------------------------|--------------|-----------|  
|W3svc|http|Typowy składnik, który zapewnia aktywację HTTP dla usług IIS 7.0 i WCF.|  
|NetTcpActivator (NetTcpActivator)|net.tcp|Zależy od usługi NetTcpPortSharing.|  
|NetPipeActivator (NetPipeActivator)|net.pipe||  
|NetMsmqActivator (Aktywizm NetMsmq)|Net.msmq|Do użytku z aplikacjami usługi kolejkowania wiadomości opartymi na WCF.|  
|NetMsmqActivator (Aktywizm NetMsmq)|nazwa msmq.format|Zapewnia zgodność z powrotem z istniejącymi aplikacjami Usługi kolejkowania wiadomości.|  
  
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
  
### <a name="protocol-handlers"></a>Programy obsługi protokołów  
 Programy obsługi protokołów Process i AppDomain dla określonych protokołów są rejestrowane w pliku Web.config na poziomie komputera.  
  
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

- [Konfigurowanie usługi WAS do użycia z programem WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
