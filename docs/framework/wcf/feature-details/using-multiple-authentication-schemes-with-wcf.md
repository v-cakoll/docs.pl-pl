---
title: "Używanie wielu schematów uwierzytelniania z programem WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: db2545470c416fe066226124fb7833ef5d9e5d13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a><span data-ttu-id="c1a52-102">Używanie wielu schematów uwierzytelniania z programem WCF</span><span class="sxs-lookup"><span data-stu-id="c1a52-102">Using Multiple Authentication Schemes with WCF</span></span>
<span data-ttu-id="c1a52-103">WCF można teraz określić wielu schematów uwierzytelniania w jednym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="c1a52-103">WCF now allows you to specify multiple authentication schemes on a single endpoint.</span></span> <span data-ttu-id="c1a52-104">Ponadto usługi sieci web hostowanej może dziedziczyć ustawień uwierzytelniania bezpośrednio za pomocą programu IIS.</span><span class="sxs-lookup"><span data-stu-id="c1a52-104">Furthermore web hosted services can inherit their authentication settings directly from IIS.</span></span> <span data-ttu-id="c1a52-105">Hostowanie Samoobsługowe usługi można określić rodzaju uwierzytelniania schematy może służyć.</span><span class="sxs-lookup"><span data-stu-id="c1a52-105">Self-hosted services can specify what authentication schemes can be used.</span></span> <span data-ttu-id="c1a52-106">Aby uzyskać więcej informacji na temat ustawiania ustawienia uwierzytelniania w usługach IIS, zobacz [uwierzytelniania usług IIS](http://go.microsoft.com/fwlink/?LinkId=232458)</span><span class="sxs-lookup"><span data-stu-id="c1a52-106">For more information about setting authentication settings in IIS, see [IIS Authentication](http://go.microsoft.com/fwlink/?LinkId=232458)</span></span>  
  
## <a name="iis-hosted-services"></a><span data-ttu-id="c1a52-107">Usług hostowanych przez usługi IIS</span><span class="sxs-lookup"><span data-stu-id="c1a52-107">IIS-Hosted Services</span></span>  
 <span data-ttu-id="c1a52-108">W przypadku usług hostowanych przez usługi IIS należy ustawić schematy uwierzytelniania, który ma zostać użyty w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="c1a52-108">For IIS-hosted services, set the authentication schemes you wish to use in IIS.</span></span> <span data-ttu-id="c1a52-109">Następnie w pliku web.config z usługą, w konfiguracji powiązania Określ typu poświadczeń klienta jako "InheritedFromHost" jak pokazano w następujący fragment kodu XML:</span><span class="sxs-lookup"><span data-stu-id="c1a52-109">Then in your service’s web.config file, in your binding configuration specify clientCredential type as "InheritedFromHost" as shown in the following XML snippet:</span></span>  
  
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
  
 <span data-ttu-id="c1a52-110">Można określić, że mają podzbiór schematy uwierzytelniania do użycia z usługą przy użyciu ServiceAuthenticationBehavior lub \<serviceAuthenticationManager > elementu.</span><span class="sxs-lookup"><span data-stu-id="c1a52-110">You can specify that you only want a subset of authentication schemes to be used with your service using the ServiceAuthenticationBehavior or the \<serviceAuthenticationManager> element.</span></span> <span data-ttu-id="c1a52-111">Podczas konfigurowania to w kodzie Użyj ServiceAuthenticationBehavior, jak pokazano w poniższy fragment kodu.</span><span class="sxs-lookup"><span data-stu-id="c1a52-111">When configuring this in code use the ServiceAuthenticationBehavior as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="c1a52-112">Podczas konfigurowania w pliku konfiguracji, użyj \<serviceAuthenticationManager > element, jak pokazano w następujący fragment kodu XML.</span><span class="sxs-lookup"><span data-stu-id="c1a52-112">When configuring this in a config file, use the \<serviceAuthenticationManager> element as shown in the following XML snippet.</span></span>  
  
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
  
 <span data-ttu-id="c1a52-113">Daje to pewność, że tylko podzestaw schematy uwierzytelniania przedstawione w tym miejscu będą uznawane za stosowania dla punktu końcowego usługi, w zależności od wybranej usług IIS.</span><span class="sxs-lookup"><span data-stu-id="c1a52-113">This will ensure that only a subset of the authentication schemes listed here will be considered for applying on the service endpoint, depending on what is selected in the IIS.</span></span> <span data-ttu-id="c1a52-114">Oznacza to, które można wykluczyć dewelopera powiedzieć uwierzytelnianie podstawowe z listy, pomijając go z listy serviceAuthenticationManager i nawet, jeśli jest włączone w usługach IIS, nie zostanie zastosowana na punkt końcowy usługi</span><span class="sxs-lookup"><span data-stu-id="c1a52-114">This means that a developer can exclude say Basic auth from the list by omitting it from the serviceAuthenticationManager listing and even if it is enabled in IIS, it will not be applied on the service endpoint</span></span>  
  
## <a name="self-hosted-services"></a><span data-ttu-id="c1a52-115">Hostowanie Samoobsługowe usług</span><span class="sxs-lookup"><span data-stu-id="c1a52-115">Self-Hosted Services</span></span>  
 <span data-ttu-id="c1a52-116">Samodzielnie hostowane usługi są skonfigurowane nieco inaczej, ponieważ nie istnieje żadne usług IIS, aby odziedziczyć ustawienia z.</span><span class="sxs-lookup"><span data-stu-id="c1a52-116">Self-hosted services are configured a bit differently since there is no IIS to inherit settings from.</span></span> <span data-ttu-id="c1a52-117">W tym miejscu użyć \<serviceAuthenticationManager > elementu lub ServiceAuthenticationBehavior, aby określić ustawienia uwierzytelniania, które będą dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="c1a52-117">Here you use the \<serviceAuthenticationManager> element or ServiceAuthenticationBehavior to specify the authentication settings that will be inherited.</span></span> <span data-ttu-id="c1a52-118">W kodzie wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="c1a52-118">In code it looks like this:</span></span>  
  
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
  
 <span data-ttu-id="c1a52-119">W konfiguracji wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="c1a52-119">In config, it looks like this:</span></span>  
  
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
  
 <span data-ttu-id="c1a52-120">A następnie można określić InheritFromHost w ustawieniach powiązanie, jak pokazano w następujący fragment kodu XML.</span><span class="sxs-lookup"><span data-stu-id="c1a52-120">And then you can specify InheritFromHost in your binding settings as shown in the following XML snippet.</span></span>  
  
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
  
 <span data-ttu-id="c1a52-121">Alternatywnie możesz określić schematy uwierzytelniania niestandardowego powiązania, ustawiając schematy uwierzytelniania HTTP transportu element powiązania, jak pokazano w poniższy fragment konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c1a52-121">Alternatively, you can specify the authentication schemes in a custom binding, by setting the authentication schemes on the HTTP transport binding element, as shown in the following config snippet.</span></span>  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1a52-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1a52-122">See Also</span></span>  
 [<span data-ttu-id="c1a52-123">Powiązania i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="c1a52-123">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [<span data-ttu-id="c1a52-124">Punkty końcowe: Adresy powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="c1a52-124">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [<span data-ttu-id="c1a52-125">Konfigurowanie powiązań dostarczanych przez System</span><span class="sxs-lookup"><span data-stu-id="c1a52-125">Configuring System-Provided Bindings</span></span>](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="c1a52-126">Możliwości zabezpieczeń wiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="c1a52-126">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="c1a52-127">Powiązania</span><span class="sxs-lookup"><span data-stu-id="c1a52-127">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [<span data-ttu-id="c1a52-128">Powiązania</span><span class="sxs-lookup"><span data-stu-id="c1a52-128">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [<span data-ttu-id="c1a52-129">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="c1a52-129">Custom Bindings</span></span>](../../../../docs/framework/wcf/extending/custom-bindings.md)
