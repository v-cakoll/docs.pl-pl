---
title: '&lt;behaviorExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: bb59ceeb478d0324fddc98a206a00dbd170b5ac9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
