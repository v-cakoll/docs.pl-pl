---
title: Używanie wielu schematów uwierzytelniania z programem WCF
ms.date: 03/30/2017
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
ms.openlocfilehash: cdf40d6c0ca25a21cbdac07abab04d2bc144bf69
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521702"
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a><span data-ttu-id="ae88e-102">Używanie wielu schematów uwierzytelniania z programem WCF</span><span class="sxs-lookup"><span data-stu-id="ae88e-102">Using Multiple Authentication Schemes with WCF</span></span>
<span data-ttu-id="ae88e-103">Usługi WCF umożliwia teraz określenie wielu schematów uwierzytelniania w jednym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="ae88e-103">WCF now allows you to specify multiple authentication schemes on a single endpoint.</span></span> <span data-ttu-id="ae88e-104">Ponadto usługi sieci web hostowanych może dziedziczyć ustawień uwierzytelniania bezpośrednio za pomocą programu IIS.</span><span class="sxs-lookup"><span data-stu-id="ae88e-104">Furthermore web hosted services can inherit their authentication settings directly from IIS.</span></span> <span data-ttu-id="ae88e-105">Samodzielnie hostowanej usługi można określić rodzaju uwierzytelniania może służyć schematów.</span><span class="sxs-lookup"><span data-stu-id="ae88e-105">Self-hosted services can specify what authentication schemes can be used.</span></span> <span data-ttu-id="ae88e-106">Aby uzyskać więcej informacji na temat ustawiania ustawienia uwierzytelniania w usługach IIS, zobacz [uwierzytelnianie usług IIS](https://go.microsoft.com/fwlink/?LinkId=232458)</span><span class="sxs-lookup"><span data-stu-id="ae88e-106">For more information about setting authentication settings in IIS, see [IIS Authentication](https://go.microsoft.com/fwlink/?LinkId=232458)</span></span>  
  
## <a name="iis-hosted-services"></a><span data-ttu-id="ae88e-107">Usług hostowanych przez usługi IIS</span><span class="sxs-lookup"><span data-stu-id="ae88e-107">IIS-Hosted Services</span></span>  
 <span data-ttu-id="ae88e-108">W przypadku usług hostowanych przez usługi IIS należy ustawić schematy uwierzytelniania, które mają być używane w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="ae88e-108">For IIS-hosted services, set the authentication schemes you wish to use in IIS.</span></span> <span data-ttu-id="ae88e-109">Następnie w pliku web.config usługi w konfiguracji powiązania Określ typ clientCredential jako "InheritedFromHost" jak pokazano w poniższym fragmencie kodu XML:</span><span class="sxs-lookup"><span data-stu-id="ae88e-109">Then in your service’s web.config file, in your binding configuration specify clientCredential type as "InheritedFromHost" as shown in the following XML snippet:</span></span>  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 <span data-ttu-id="ae88e-110">Można określić tylko mają podzbiór schematów uwierzytelniania do użycia z usługą za pomocą ServiceAuthenticationBehavior lub \<serviceAuthenticationManager > element.</span><span class="sxs-lookup"><span data-stu-id="ae88e-110">You can specify that you only want a subset of authentication schemes to be used with your service using the ServiceAuthenticationBehavior or the \<serviceAuthenticationManager> element.</span></span> <span data-ttu-id="ae88e-111">Podczas konfigurowania to w kodzie należy użyć ServiceAuthenticationBehavior, jak pokazano w poniższym fragmencie kodu.</span><span class="sxs-lookup"><span data-stu-id="ae88e-111">When configuring this in code use the ServiceAuthenticationBehavior as shown in the following code snippet.</span></span>  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 <span data-ttu-id="ae88e-112">Podczas konfigurowania to w pliku konfiguracji, użyj \<serviceAuthenticationManager > elementu, jak pokazano w poniższym fragmencie kodu XML.</span><span class="sxs-lookup"><span data-stu-id="ae88e-112">When configuring this in a config file, use the \<serviceAuthenticationManager> element as shown in the following XML snippet.</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 <span data-ttu-id="ae88e-113">Pozwoli to zagwarantować, że tylko podzbiór schematy uwierzytelniania, wymienione w tym miejscu będą uznawane za do stosowania w punkcie końcowym usługi, w zależności od tego, co jest wybrane w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="ae88e-113">This will ensure that only a subset of the authentication schemes listed here will be considered for applying on the service endpoint, depending on what is selected in the IIS.</span></span> <span data-ttu-id="ae88e-114">Oznacza to, że deweloper można wykluczyć powiedz uwierzytelnianie podstawowe z listy, pomijając go z listy serviceAuthenticationManager, a nawet, jeśli jest włączone w usługach IIS, nie zostanie zastosowana na punkt końcowy usługi</span><span class="sxs-lookup"><span data-stu-id="ae88e-114">This means that a developer can exclude say Basic auth from the list by omitting it from the serviceAuthenticationManager listing and even if it is enabled in IIS, it will not be applied on the service endpoint</span></span>  
  
## <a name="self-hosted-services"></a><span data-ttu-id="ae88e-115">Usługi samodzielnie hostowane</span><span class="sxs-lookup"><span data-stu-id="ae88e-115">Self-Hosted Services</span></span>  
 <span data-ttu-id="ae88e-116">Samodzielnie hostowanej usługi są konfigurowane nieco inaczej, ponieważ nie istnieje żadne usługi IIS mają dziedziczyć ustawienia z.</span><span class="sxs-lookup"><span data-stu-id="ae88e-116">Self-hosted services are configured a bit differently since there is no IIS to inherit settings from.</span></span> <span data-ttu-id="ae88e-117">W tym miejscu możesz użyć \<serviceAuthenticationManager > element lub ServiceAuthenticationBehavior do określania ustawień uwierzytelniania, które będą dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="ae88e-117">Here you use the \<serviceAuthenticationManager> element or ServiceAuthenticationBehavior to specify the authentication settings that will be inherited.</span></span> <span data-ttu-id="ae88e-118">W kodzie wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="ae88e-118">In code it looks like this:</span></span>  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 <span data-ttu-id="ae88e-119">W pliku konfiguracyjnym wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="ae88e-119">In config, it looks like this:</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 <span data-ttu-id="ae88e-120">A następnie można określić InheritFromHost w ustawieniach powiązania, jak pokazano w poniższym fragmencie kodu XML.</span><span class="sxs-lookup"><span data-stu-id="ae88e-120">And then you can specify InheritFromHost in your binding settings as shown in the following XML snippet.</span></span>  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 <span data-ttu-id="ae88e-121">Alternatywnie można określić schematów uwierzytelniania w niestandardowym powiązaniu, ustawiając schematów uwierzytelniania na HTTP transportu elementu powiązania, jak pokazano w poniższym fragmencie kodu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ae88e-121">Alternatively, you can specify the authentication schemes in a custom binding, by setting the authentication schemes on the HTTP transport binding element, as shown in the following config snippet.</span></span>  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae88e-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae88e-122">See Also</span></span>  
 [<span data-ttu-id="ae88e-123">Powiązania i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="ae88e-123">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [<span data-ttu-id="ae88e-124">Punkty końcowe: adresy, powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="ae88e-124">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [<span data-ttu-id="ae88e-125">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="ae88e-125">Configuring System-Provided Bindings</span></span>](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="ae88e-126">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="ae88e-126">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="ae88e-127">Powiązania</span><span class="sxs-lookup"><span data-stu-id="ae88e-127">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [<span data-ttu-id="ae88e-128">Powiązania</span><span class="sxs-lookup"><span data-stu-id="ae88e-128">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [<span data-ttu-id="ae88e-129">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="ae88e-129">Custom Bindings</span></span>](../../../../docs/framework/wcf/extending/custom-bindings.md)
