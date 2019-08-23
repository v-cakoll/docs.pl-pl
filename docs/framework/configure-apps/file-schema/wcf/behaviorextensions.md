---
title: <behaviorExtensions>
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: bcf1f1dcdba50c3e7fba8eb170132d0cf47c4271
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919819"
---
# <a name="behaviorextensions"></a>\<behaviorExtensions >
Rozszerzenia zachowań umożliwiają użytkownikowi tworzenie elementów zachowania zdefiniowanych przez użytkownika. Te elementy mogą być używane obok standardowych elementów zachowań Windows Communication Foundation (WCF). `behaviorExtensions` Sekcja definiuje element, który może być używany w konfiguracji. Oto przykład typowego rozszerzenia zachowania.  
  
```xml  
<system.serviceModel>
  <extensions>
    <behaviorExtensions>
      <add name="myBehavior"
           type="Microsoft.ServiceModel.Samples.MyBehaviorSection, MyBehavior,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </behaviorExtensions>
  </extensions>
</system.serviceModel>
```  
  
 Aby dodać możliwości konfiguracji do elementu, należy napisać i zarejestrować element konfiguracji. Aby uzyskać więcej informacji na ten temat, <xref:System.Configuration> zapoznaj się z dokumentacją.  
  
 Po zdefiniowaniu elementu i jego typu konfiguracji można użyć rozszerzenia, jak pokazano w poniższym przykładzie.  
  
```xml  
<behaviors>
  <behavior configurationName="testChannelBehavior">
    <myBehavior />
    <channelSecurity cacheCookies="false"
                     detectReplays="false"
                     maxCachedNonces="9"
                     maxClockSkew="00:00:03"
                     maxCookieCachingTime="00:07:24"
                     replayWindow="00:07:22.2190000" />
  </behavior>
</behaviors>
```  
  
## <a name="security"></a>Zabezpieczenia  
 Zdecydowanie zaleca się używanie w pełni kwalifikowanych nazw zestawów podczas rejestrowania typów w `machine.config` plikach i. `app.config` Jeśli typ nie jest zdefiniowany jednoznacznie, moduł ładujący typu CLR wyszukuje go w następujących lokalizacjach w określonej kolejności:  
  
 Jeśli zestaw typu jest znany, moduł ładujący przeszukuje lokalizacje przekierowań pliku konfiguracji, GAC, bieżący zestaw przy użyciu informacji o konfiguracji i katalogu podstawowego aplikacji. Jeśli zestaw jest nieznany, moduł ładujący przeszukuje bieżący zestaw, mscorlib i lokalizację zwróconą przez `TypeResolve` program obsługi zdarzeń. Ta kolejność wyszukiwania CLR może być modyfikowana za pomocą punktów zaczepienia, takich jak mechanizm przekazywania typów i zdarzenie AppDomain. TypeResolve.  
  
 Osoba atakująca może wykorzystać kolejność wyszukiwania CLR i wykonać nieautoryzowany kod. Używanie w pełni kwalifikowanych (silnie) nazw jednoznacznie identyfikuje typ i zwiększa bezpieczeństwo systemu.  
  
 Aby uzyskać więcej informacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](https://go.microsoft.com/fwlink/?LinkId=95336) i <xref:System.AppDomain.TypeResolve>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>
- [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
