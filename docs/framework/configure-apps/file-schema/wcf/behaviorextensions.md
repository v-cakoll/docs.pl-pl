---
title: '&lt;behaviorExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: bb59ceeb478d0324fddc98a206a00dbd170b5ac9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749585"
---
# <a name="ltbehaviorextensionsgt"></a><span data-ttu-id="8f1d8-102">&lt;behaviorExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="8f1d8-102">&lt;behaviorExtensions&gt;</span></span>
<span data-ttu-id="8f1d8-103">Dzięki rozszerzeniom zachowania użytkownika do tworzenia elementów zachowanie zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8f1d8-103">Behavior extensions enable the user to create user-defined behavior elements.</span></span> <span data-ttu-id="8f1d8-104">Te elementy można używać razem standardowe elementy zachowanie Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="8f1d8-104">These elements can be used alongside the standard Windows Communication Foundation (WCF) behavior elements.</span></span> <span data-ttu-id="8f1d8-105">`behaviorExtensions` Sekcja definiuje element w taki sposób, że mogą być używane w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8f1d8-105">The `behaviorExtensions` section defines the element such that it can be used in configuration.</span></span> <span data-ttu-id="8f1d8-106">Oto przykład rozszerzenia typowe zachowanie.</span><span class="sxs-lookup"><span data-stu-id="8f1d8-106">Here is an example of a typical behavior extension.</span></span>  
  
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
  
 <span data-ttu-id="8f1d8-107">Aby dodać możliwości konfiguracji do elementu, należy zapisać i zarejestrować element konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8f1d8-107">To add configuration abilities to the element, you need to write and register a configuration element.</span></span> <span data-ttu-id="8f1d8-108">Aby uzyskać więcej informacji o tym, zobacz <xref:System.Configuration> dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="8f1d8-108">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="8f1d8-109">Po zdefiniowaniu elementu i jego typ Konfiguracja rozszerzenia może służyć, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8f1d8-109">After the element and its configuration type are defined, the extension can be used, as shown in the following example.</span></span>  
  
```xml  
<behaviors>  
    <behavior configurationName="testChannelBehavior">  
        <myBehavior />  
        <channelSecurity cacheCookies="false" detectReplays="false" maxCachedNonces="9"  
            maxClockSkew="00:00:03" maxCookieCachingTime="00:07:24" replayWindow="00:07:22.2190000" />  
    </behavior>  
</behaviors>  
```  
  
## <a name="security"></a><span data-ttu-id="8f1d8-110">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="8f1d8-110">Security</span></span>  
 <span data-ttu-id="8f1d8-111">Zalecane jest użycie zestawu w pełni kwalifikowanej nazwy podczas rejestrowania typów w `machine.config` i `app.config` plików.</span><span class="sxs-lookup"><span data-stu-id="8f1d8-111">It is strongly recommended that you use fully qualified assembly names when registering types in the `machine.config` and `app.config` files.</span></span> <span data-ttu-id="8f1d8-112">Jeśli typ nie jest unikatowo zdefiniowane, moduł ładujący typ CLR wyszukuje go w następujących lokalizacjach w podanej kolejności:</span><span class="sxs-lookup"><span data-stu-id="8f1d8-112">If the type is not uniquely defined, the CLR type loader searches for it in the following locations in the specified order:</span></span>  
  
 <span data-ttu-id="8f1d8-113">Jeśli zestawu typu jest znany, moduł ładujący wyszukuje plik konfiguracji przekierowania lokalizacjach, GAC, bieżącego zestawu przy użyciu informacji o konfiguracji i podstawowego katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8f1d8-113">If the assembly of the type is known, the loader searches the configuration file's redirect locations, GAC, the current assembly using configuration information, and the application base directory.</span></span> <span data-ttu-id="8f1d8-114">Jeśli zestaw jest nieznany, moduł ładujący wyszukuje bieżącego zestawu, mscorlib i lokalizację zwrócony przez `TypeResolve` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8f1d8-114">If the assembly is unknown, the loader searches the current assembly, mscorlib, and the location returned by the `TypeResolve` event handler.</span></span> <span data-ttu-id="8f1d8-115">Ta kolejność wyszukiwania CLR może być modyfikowany z punkty zaczepienia, takich jak mechanizm przekazywania typu i zdarzenia AppDomain.TypeResolve.</span><span class="sxs-lookup"><span data-stu-id="8f1d8-115">This CLR search order can be modified with hooks such as the Type Forwarding mechanism and the AppDomain.TypeResolve event.</span></span>  
  
 <span data-ttu-id="8f1d8-116">Osoba atakująca może wykorzystać CLR kolejność wyszukiwania i wykonywać nieautoryzowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="8f1d8-116">An attacker can exploit the CLR search order and execute unauthorized code.</span></span> <span data-ttu-id="8f1d8-117">Przy użyciu w pełni kwalifikowane nazwy (silne) unikatowo identyfikuje typ i jeszcze bardziej podkreśla zabezpieczenia systemu.</span><span class="sxs-lookup"><span data-stu-id="8f1d8-117">Using fully qualified (strong) names uniquely identifies a type and further increases security of your system.</span></span>  
  
 <span data-ttu-id="8f1d8-118">Aby uzyskać więcej informacji, zobacz [jak zestawy środowiska wykonawczego lokalizuje](http://go.microsoft.com/fwlink/?LinkId=95336) i <xref:System.AppDomain.TypeResolve>.</span><span class="sxs-lookup"><span data-stu-id="8f1d8-118">For more information, see [How the Runtime Locates Assemblies](http://go.microsoft.com/fwlink/?LinkId=95336) and <xref:System.AppDomain.TypeResolve>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f1d8-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f1d8-119">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>  
 [<span data-ttu-id="8f1d8-120">Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań</span><span class="sxs-lookup"><span data-stu-id="8f1d8-120">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
