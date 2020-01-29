---
title: Architektura aktywacji WAS
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 01c30db1182ece6dd968b69cc4efcaa2d9fabd79
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737514"
---
# <a name="was-activation-architecture"></a>Architektura aktywacji WAS
W tym temacie wyszczególniono i omówiono składniki usługi aktywacji procesów systemu Windows (nazywanej także usługą WAS).  
  
## <a name="activation-components"></a>Składniki aktywacji  
 Składa się z kilku składników architektury:  
  
- Adaptery odbiornika. Usługi systemu Windows, które odbierają komunikaty z określonych protokołów sieciowych i komunikują się z usługą, przekierować komunikaty przychodzące do poprawnego procesu roboczego.  
  
- Błędu. Usługa systemu Windows, która zarządza tworzeniem i okresem istnienia procesów roboczych.  
  
- Plik wykonywalny ogólnego procesu roboczego (w3wp. exe).  
  
- Menedżer aplikacji. Zarządza tworzeniem i okresem istnienia domen aplikacji, które obsługują aplikacje w ramach procesu roboczego.  
  
- Procedury obsługi protokołu. Składniki specyficzne dla protokołu, które są uruchamiane w procesie roboczym i zarządzają komunikacją między procesem roboczym a poszczególnymi kartami odbiornika. Istnieją dwa typy obsługi protokołów: procedury obsługi protokołu przetwarzania i procedury obsługi protokołu AppDomain.  
  
 Gdy program został aktywowany wystąpienie procesu roboczego, ładuje do procesu roboczego programy obsługi protokołu procesu, a następnie za pomocą Menedżera aplikacji utworzyć domenę aplikacji do hostowania aplikacji. Domena aplikacji ładuje kod aplikacji, a także obsługę protokołów AppDomain, których wymagają protokoły sieciowe używane przez aplikację.  
  
 ![Zrzut ekranu przedstawiający architekturę WAS.](./media/was-activation-architecture/windows-process-application-service-architecture.gif)  
  
### <a name="listener-adapters"></a>Adaptery odbiornika  
 Adaptery odbiorników to pojedyncze usługi systemu Windows, które implementują logikę komunikacji sieciowej służącą do odbierania komunikatów przy użyciu protokołu sieciowego, na którym nasłuchuje. W poniższej tabeli przedstawiono karty odbiorników dla protokołów Windows Communication Foundation (WCF).  
  
|Nazwa usługi adaptera odbiornika|Protokół|Uwagi|  
|-----------------------------------|--------------|-----------|  
|W3SVC|http|Wspólny składnik zapewniający aktywację HTTP dla usług IIS 7,0 i WCF.|  
|NetTcpActivator|net.tcp|Zależy od usługi NetTcpPortSharing.|  
|NetPipeActivator|net.pipe||  
|NetMsmqActivator|net.msmq|Do użytku z aplikacjami usługi kolejkowania komunikatów opartymi na platformie WCF.|  
|NetMsmqActivator|wartość MSMQ. formatname|Zapewnia zgodność z poprzednimi wersjami istniejących aplikacji usługi kolejkowania komunikatów.|  
  
 Adaptery odbiorników dla określonych protokołów są rejestrowane podczas instalacji w pliku applicationHost. config, jak pokazano w poniższym przykładzie kodu XML.  
  
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
 Procedury obsługi protokołu i programu AppDomain dla określonych protokołów są rejestrowane w pliku Web. config na poziomie komputera.  
  
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
- [Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
