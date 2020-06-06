---
title: <behaviorExtensions>
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: 39dc92d65a41d223ebd39aec3dc59871ad1fd101
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "77448688"
---
# \<behaviorExtensions>
<span data-ttu-id="63bd6-101">Rozszerzenia zachowań umożliwiają użytkownikowi tworzenie elementów zachowania zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="63bd6-101">Behavior extensions enable the user to create user-defined behavior elements.</span></span> <span data-ttu-id="63bd6-102">Te elementy mogą być używane obok standardowych elementów zachowań Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="63bd6-102">These elements can be used alongside the standard Windows Communication Foundation (WCF) behavior elements.</span></span> <span data-ttu-id="63bd6-103">`behaviorExtensions`Sekcja definiuje element, który może być używany w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="63bd6-103">The `behaviorExtensions` section defines the element such that it can be used in configuration.</span></span> <span data-ttu-id="63bd6-104">Oto przykład typowego rozszerzenia zachowania.</span><span class="sxs-lookup"><span data-stu-id="63bd6-104">Here is an example of a typical behavior extension.</span></span>  
  
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
  
 <span data-ttu-id="63bd6-105">Aby dodać możliwości konfiguracji do elementu, należy napisać i zarejestrować element konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="63bd6-105">To add configuration abilities to the element, you need to write and register a configuration element.</span></span> <span data-ttu-id="63bd6-106">Aby uzyskać więcej informacji na ten temat, zapoznaj się z <xref:System.Configuration> dokumentacją.</span><span class="sxs-lookup"><span data-stu-id="63bd6-106">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="63bd6-107">Po zdefiniowaniu elementu i jego typu konfiguracji można użyć rozszerzenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="63bd6-107">After the element and its configuration type are defined, the extension can be used, as shown in the following example.</span></span>  
  
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
  
## <a name="security"></a><span data-ttu-id="63bd6-108">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="63bd6-108">Security</span></span>  
 <span data-ttu-id="63bd6-109">Zdecydowanie zaleca się używanie w pełni kwalifikowanych nazw zestawów podczas rejestrowania typów w `machine.config` `app.config` plikach i.</span><span class="sxs-lookup"><span data-stu-id="63bd6-109">It is strongly recommended that you use fully qualified assembly names when registering types in the `machine.config` and `app.config` files.</span></span> <span data-ttu-id="63bd6-110">Jeśli typ nie jest zdefiniowany jednoznacznie, moduł ładujący typu CLR wyszukuje go w następujących lokalizacjach w określonej kolejności:</span><span class="sxs-lookup"><span data-stu-id="63bd6-110">If the type is not uniquely defined, the CLR type loader searches for it in the following locations in the specified order:</span></span>  
  
 <span data-ttu-id="63bd6-111">Jeśli zestaw typu jest znany, moduł ładujący przeszukuje lokalizacje przekierowań pliku konfiguracji, GAC, bieżący zestaw przy użyciu informacji o konfiguracji i katalogu podstawowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="63bd6-111">If the assembly of the type is known, the loader searches the configuration file's redirect locations, GAC, the current assembly using configuration information, and the application base directory.</span></span> <span data-ttu-id="63bd6-112">Jeśli zestaw jest nieznany, moduł ładujący przeszukuje bieżący zestaw, mscorlib i lokalizację zwróconą przez `TypeResolve` program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="63bd6-112">If the assembly is unknown, the loader searches the current assembly, mscorlib, and the location returned by the `TypeResolve` event handler.</span></span> <span data-ttu-id="63bd6-113">Ta kolejność wyszukiwania CLR może być modyfikowana za pomocą punktów zaczepienia, takich jak mechanizm przekazywania typów i zdarzenie AppDomain. TypeResolve.</span><span class="sxs-lookup"><span data-stu-id="63bd6-113">This CLR search order can be modified with hooks such as the Type Forwarding mechanism and the AppDomain.TypeResolve event.</span></span>  
  
 <span data-ttu-id="63bd6-114">Osoba atakująca może wykorzystać kolejność wyszukiwania CLR i wykonać nieautoryzowany kod.</span><span class="sxs-lookup"><span data-stu-id="63bd6-114">An attacker can exploit the CLR search order and execute unauthorized code.</span></span> <span data-ttu-id="63bd6-115">Używanie w pełni kwalifikowanych (silnie) nazw jednoznacznie identyfikuje typ i zwiększa bezpieczeństwo systemu.</span><span class="sxs-lookup"><span data-stu-id="63bd6-115">Using fully qualified (strong) names uniquely identifies a type and further increases security of your system.</span></span>  
  
 <span data-ttu-id="63bd6-116">Aby uzyskać więcej informacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../../../deployment/how-the-runtime-locates-assemblies.md) i <xref:System.AppDomain.TypeResolve> .</span><span class="sxs-lookup"><span data-stu-id="63bd6-116">For more information, see [How the Runtime Locates Assemblies](../../../deployment/how-the-runtime-locates-assemblies.md) and <xref:System.AppDomain.TypeResolve>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63bd6-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63bd6-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>
- [<span data-ttu-id="63bd6-118">Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań</span><span class="sxs-lookup"><span data-stu-id="63bd6-118">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
