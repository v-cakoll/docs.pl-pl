---
title: '&lt;behaviorExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: d025497956715913923e839cb6c482f44f96babb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43732926"
---
# <a name="ltbehaviorextensionsgt"></a>&lt;behaviorExtensions&gt;
Rozszerzenia zachowania umożliwiają użytkownikowi utworzenie elementów zachowania zdefiniowanych przez użytkownika. Te elementy mogą być używane razem standardowych elementów zachowanie usługi Windows Communication Foundation (WCF). `behaviorExtensions` Sekcji definiuje element w taki sposób, że mogą być używane w konfiguracji. Oto przykład rozszerzenia typowe zachowanie.  
  
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
  
 Aby dodać możliwości konfiguracji do elementu, musisz napisać i zarejestrować element konfiguracji. Aby uzyskać więcej informacji na temat tego, zobacz <xref:System.Configuration> dokumentacji.  
  
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
 Zdecydowanie zaleca się, użyj w pełni kwalifikowane nazwy zestawów, zapisując typów w `machine.config` i `app.config` plików. Jeśli typ nie jest jednoznacznie zdefiniowany, modułu ładującego typu CLR szuka go w następujących lokalizacjach w określonej kolejności:  
  
 Jeśli zestaw tego typu jest znany, moduł ładujący przeszukuje plik konfiguracji przekierowania lokalizacje, pamięci podręcznej GAC, bieżący zestaw przy użyciu informacji o konfiguracji i katalog podstawowy aplikacji. Jeśli zestaw jest nieznany, moduł ładujący przeszukuje bieżącego zestawu mscorlib i lokalizacji, zwracane przez `TypeResolve` programu obsługi zdarzeń. CLR kolejności wyszukiwania mogą być modyfikowane przy użyciu punktów zaczepienia, takie jak mechanizm przekazywania dalej typów i zdarzenia AppDomain.TypeResolve.  
  
 Osoba atakująca może wykorzystać kolejność wyszukiwania CLR i wykonywać nieautoryzowanego kodu. Przy użyciu w pełni kwalifikowane nazwy (silną) unikatowo identyfikuje typ i jeszcze bardziej podkreśla zabezpieczenia systemu.  
  
 Aby uzyskać więcej informacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](https://go.microsoft.com/fwlink/?LinkId=95336) i <xref:System.AppDomain.TypeResolve>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>  
 [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
