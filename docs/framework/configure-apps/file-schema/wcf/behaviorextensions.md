---
title: <behaviorExtensions>
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: 39dc92d65a41d223ebd39aec3dc59871ad1fd101
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77448688"
---
# <a name="behaviorextensions"></a><span data-ttu-id="978e8-101">\<behaviorExtensions ></span><span class="sxs-lookup"><span data-stu-id="978e8-101">\<behaviorExtensions></span></span>
<span data-ttu-id="978e8-102">Rozszerzenia zachowań umożliwiają użytkownikowi tworzenie elementów zachowania zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="978e8-102">Behavior extensions enable the user to create user-defined behavior elements.</span></span> <span data-ttu-id="978e8-103">Te elementy mogą być używane obok standardowych elementów zachowań Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="978e8-103">These elements can be used alongside the standard Windows Communication Foundation (WCF) behavior elements.</span></span> <span data-ttu-id="978e8-104">Sekcja `behaviorExtensions` definiuje element, który może być używany w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="978e8-104">The `behaviorExtensions` section defines the element such that it can be used in configuration.</span></span> <span data-ttu-id="978e8-105">Oto przykład typowego rozszerzenia zachowania.</span><span class="sxs-lookup"><span data-stu-id="978e8-105">Here is an example of a typical behavior extension.</span></span>  
  
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
  
 <span data-ttu-id="978e8-106">Aby dodać możliwości konfiguracji do elementu, należy napisać i zarejestrować element konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="978e8-106">To add configuration abilities to the element, you need to write and register a configuration element.</span></span> <span data-ttu-id="978e8-107">Aby uzyskać więcej informacji na ten temat, zobacz dokumentację <xref:System.Configuration>.</span><span class="sxs-lookup"><span data-stu-id="978e8-107">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="978e8-108">Po zdefiniowaniu elementu i jego typu konfiguracji można użyć rozszerzenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="978e8-108">After the element and its configuration type are defined, the extension can be used, as shown in the following example.</span></span>  
  
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
  
## <a name="security"></a><span data-ttu-id="978e8-109">Bezpieczeństwo</span><span class="sxs-lookup"><span data-stu-id="978e8-109">Security</span></span>  
 <span data-ttu-id="978e8-110">Zdecydowanie zaleca się używanie w pełni kwalifikowanych nazw zestawów podczas rejestrowania typów w plikach `machine.config` i `app.config`.</span><span class="sxs-lookup"><span data-stu-id="978e8-110">It is strongly recommended that you use fully qualified assembly names when registering types in the `machine.config` and `app.config` files.</span></span> <span data-ttu-id="978e8-111">Jeśli typ nie jest zdefiniowany jednoznacznie, moduł ładujący typu CLR wyszukuje go w następujących lokalizacjach w określonej kolejności:</span><span class="sxs-lookup"><span data-stu-id="978e8-111">If the type is not uniquely defined, the CLR type loader searches for it in the following locations in the specified order:</span></span>  
  
 <span data-ttu-id="978e8-112">Jeśli zestaw typu jest znany, moduł ładujący przeszukuje lokalizacje przekierowań pliku konfiguracji, GAC, bieżący zestaw przy użyciu informacji o konfiguracji i katalogu podstawowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="978e8-112">If the assembly of the type is known, the loader searches the configuration file's redirect locations, GAC, the current assembly using configuration information, and the application base directory.</span></span> <span data-ttu-id="978e8-113">Jeśli zestaw jest nieznany, moduł ładujący przeszukuje bieżący zestaw, mscorlib i lokalizację zwróconą przez program obsługi zdarzeń `TypeResolve`.</span><span class="sxs-lookup"><span data-stu-id="978e8-113">If the assembly is unknown, the loader searches the current assembly, mscorlib, and the location returned by the `TypeResolve` event handler.</span></span> <span data-ttu-id="978e8-114">Ta kolejność wyszukiwania CLR może być modyfikowana za pomocą punktów zaczepienia, takich jak mechanizm przekazywania typów i zdarzenie AppDomain. TypeResolve.</span><span class="sxs-lookup"><span data-stu-id="978e8-114">This CLR search order can be modified with hooks such as the Type Forwarding mechanism and the AppDomain.TypeResolve event.</span></span>  
  
 <span data-ttu-id="978e8-115">Osoba atakująca może wykorzystać kolejność wyszukiwania CLR i wykonać nieautoryzowany kod.</span><span class="sxs-lookup"><span data-stu-id="978e8-115">An attacker can exploit the CLR search order and execute unauthorized code.</span></span> <span data-ttu-id="978e8-116">Używanie w pełni kwalifikowanych (silnie) nazw jednoznacznie identyfikuje typ i zwiększa bezpieczeństwo systemu.</span><span class="sxs-lookup"><span data-stu-id="978e8-116">Using fully qualified (strong) names uniquely identifies a type and further increases security of your system.</span></span>  
  
 <span data-ttu-id="978e8-117">Aby uzyskać więcej informacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../../../deployment/how-the-runtime-locates-assemblies.md) i <xref:System.AppDomain.TypeResolve>.</span><span class="sxs-lookup"><span data-stu-id="978e8-117">For more information, see [How the Runtime Locates Assemblies](../../../deployment/how-the-runtime-locates-assemblies.md) and <xref:System.AppDomain.TypeResolve>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="978e8-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="978e8-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>
- [<span data-ttu-id="978e8-119">Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań</span><span class="sxs-lookup"><span data-stu-id="978e8-119">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
