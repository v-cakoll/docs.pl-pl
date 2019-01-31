---
title: <behaviorExtensions>
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: b3554db2ee037eceb43126968a02e826b65928a0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285930"
---
# <a name="behaviorextensions"></a><span data-ttu-id="84fd3-101">\<behaviorExtensions ></span><span class="sxs-lookup"><span data-stu-id="84fd3-101">\<behaviorExtensions></span></span>
<span data-ttu-id="84fd3-102">Rozszerzenia zachowania umożliwiają użytkownikowi utworzenie elementów zachowania zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="84fd3-102">Behavior extensions enable the user to create user-defined behavior elements.</span></span> <span data-ttu-id="84fd3-103">Te elementy mogą być używane razem standardowych elementów zachowanie usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="84fd3-103">These elements can be used alongside the standard Windows Communication Foundation (WCF) behavior elements.</span></span> <span data-ttu-id="84fd3-104">`behaviorExtensions` Sekcji definiuje element w taki sposób, że mogą być używane w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="84fd3-104">The `behaviorExtensions` section defines the element such that it can be used in configuration.</span></span> <span data-ttu-id="84fd3-105">Oto przykład rozszerzenia typowe zachowanie.</span><span class="sxs-lookup"><span data-stu-id="84fd3-105">Here is an example of a typical behavior extension.</span></span>  
  
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
  
 <span data-ttu-id="84fd3-106">Aby dodać możliwości konfiguracji do elementu, musisz napisać i zarejestrować element konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="84fd3-106">To add configuration abilities to the element, you need to write and register a configuration element.</span></span> <span data-ttu-id="84fd3-107">Aby uzyskać więcej informacji na temat tego, zobacz <xref:System.Configuration> dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="84fd3-107">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="84fd3-108">Po zdefiniowaniu elementu i jego typ Konfiguracja rozszerzenia może służyć, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="84fd3-108">After the element and its configuration type are defined, the extension can be used, as shown in the following example.</span></span>  
  
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
  
## <a name="security"></a><span data-ttu-id="84fd3-109">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="84fd3-109">Security</span></span>  
 <span data-ttu-id="84fd3-110">Zdecydowanie zaleca się, użyj w pełni kwalifikowane nazwy zestawów, zapisując typów w `machine.config` i `app.config` plików.</span><span class="sxs-lookup"><span data-stu-id="84fd3-110">It is strongly recommended that you use fully qualified assembly names when registering types in the `machine.config` and `app.config` files.</span></span> <span data-ttu-id="84fd3-111">Jeśli typ nie jest jednoznacznie zdefiniowany, modułu ładującego typu CLR szuka go w następujących lokalizacjach w określonej kolejności:</span><span class="sxs-lookup"><span data-stu-id="84fd3-111">If the type is not uniquely defined, the CLR type loader searches for it in the following locations in the specified order:</span></span>  
  
 <span data-ttu-id="84fd3-112">Jeśli zestaw tego typu jest znany, moduł ładujący przeszukuje plik konfiguracji przekierowania lokalizacje, pamięci podręcznej GAC, bieżący zestaw przy użyciu informacji o konfiguracji i katalog podstawowy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="84fd3-112">If the assembly of the type is known, the loader searches the configuration file's redirect locations, GAC, the current assembly using configuration information, and the application base directory.</span></span> <span data-ttu-id="84fd3-113">Jeśli zestaw jest nieznany, moduł ładujący przeszukuje bieżącego zestawu mscorlib i lokalizacji, zwracane przez `TypeResolve` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="84fd3-113">If the assembly is unknown, the loader searches the current assembly, mscorlib, and the location returned by the `TypeResolve` event handler.</span></span> <span data-ttu-id="84fd3-114">CLR kolejności wyszukiwania mogą być modyfikowane przy użyciu punktów zaczepienia, takie jak mechanizm przekazywania dalej typów i zdarzenia AppDomain.TypeResolve.</span><span class="sxs-lookup"><span data-stu-id="84fd3-114">This CLR search order can be modified with hooks such as the Type Forwarding mechanism and the AppDomain.TypeResolve event.</span></span>  
  
 <span data-ttu-id="84fd3-115">Osoba atakująca może wykorzystać kolejność wyszukiwania CLR i wykonywać nieautoryzowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="84fd3-115">An attacker can exploit the CLR search order and execute unauthorized code.</span></span> <span data-ttu-id="84fd3-116">Przy użyciu w pełni kwalifikowane nazwy (silną) unikatowo identyfikuje typ i jeszcze bardziej podkreśla zabezpieczenia systemu.</span><span class="sxs-lookup"><span data-stu-id="84fd3-116">Using fully qualified (strong) names uniquely identifies a type and further increases security of your system.</span></span>  
  
 <span data-ttu-id="84fd3-117">Aby uzyskać więcej informacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](https://go.microsoft.com/fwlink/?LinkId=95336) i <xref:System.AppDomain.TypeResolve>.</span><span class="sxs-lookup"><span data-stu-id="84fd3-117">For more information, see [How the Runtime Locates Assemblies](https://go.microsoft.com/fwlink/?LinkId=95336) and <xref:System.AppDomain.TypeResolve>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84fd3-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84fd3-118">See also</span></span>
- <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>
- [<span data-ttu-id="84fd3-119">Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań</span><span class="sxs-lookup"><span data-stu-id="84fd3-119">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
