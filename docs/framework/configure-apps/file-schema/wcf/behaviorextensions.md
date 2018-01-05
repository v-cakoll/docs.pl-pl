---
title: '&lt;behaviorExtensions&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c5d359e05e04a98e0c5855ba4d78e8e63c1e6a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltbehaviorextensionsgt"></a>&lt;behaviorExtensions&gt;
Dzięki rozszerzeniom zachowania użytkownika do tworzenia elementów zachowanie zdefiniowane przez użytkownika. Te elementy można używać razem standardowe elementy zachowanie Windows Communication Foundation (WCF). `behaviorExtensions` Sekcja definiuje element w taki sposób, że mogą być używane w konfiguracji. Oto przykład rozszerzenia typowe zachowanie.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="myBehavior" type="Microsoft.ServiceModel.Samples.MyBehaviorSection, MyBehavior,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
       </behaviorExtensions>  
    </extensions>  
</system.serviceModel>  
```  
  
 Aby dodać możliwości konfiguracji do elementu, należy zapisać i zarejestrować element konfiguracji. Aby uzyskać więcej informacji o tym, zobacz <xref:System.Configuration> dokumentacji.  
  
 Po zdefiniowaniu elementu i jego typ Konfiguracja rozszerzenia może służyć, jak pokazano w poniższym przykładzie.  
  
```xml  
<behaviors>  
    <behavior configurationName="testChannelBehavior">  
        <myBehavior />  
        <channelSecurity cacheCookies="false" detectReplays="false" maxCachedNonces="9"  
            maxClockSkew="00:00:03" maxCookieCachingTime="00:07:24" replayWindow="00:07:22.2190000" />  
    </behavior>  
</behaviors>  
```  
  
## <a name="security"></a>Zabezpieczenia  
 Zalecane jest użycie zestawu w pełni kwalifikowanej nazwy podczas rejestrowania typów w `machine.config` i `app.config` plików. Jeśli typ nie jest unikatowo zdefiniowane, moduł ładujący typ CLR wyszukuje go w następujących lokalizacjach w podanej kolejności:  
  
 Jeśli zestawu typu jest znany, moduł ładujący wyszukuje plik konfiguracji przekierowania lokalizacjach, GAC, bieżącego zestawu przy użyciu informacji o konfiguracji i podstawowego katalogu aplikacji. Jeśli zestaw jest nieznany, moduł ładujący wyszukuje bieżącego zestawu, mscorlib i lokalizację zwrócony przez `TypeResolve` obsługi zdarzeń. Ta kolejność wyszukiwania CLR może być modyfikowany z punkty zaczepienia, takich jak mechanizm przekazywania typu i zdarzenia AppDomain.TypeResolve.  
  
 Osoba atakująca może wykorzystać CLR kolejność wyszukiwania i wykonywać nieautoryzowanego kodu. Przy użyciu w pełni kwalifikowane nazwy (silne) unikatowo identyfikuje typ i jeszcze bardziej podkreśla zabezpieczenia systemu.  
  
 Aby uzyskać więcej informacji, zobacz [jak zestawy środowiska wykonawczego lokalizuje](http://go.microsoft.com/fwlink/?LinkId=95336) i <xref:System.AppDomain.TypeResolve>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>  
 [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
