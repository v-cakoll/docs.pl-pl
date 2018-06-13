---
title: 'Instrukcje: Określanie typu poświadczeń klienta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
ms.openlocfilehash: 5e1ff85d8a0bd45c87786f98c2cafe06472052b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499340"
---
# <a name="how-to-specify-the-client-credential-type"></a><span data-ttu-id="09b1e-102">Instrukcje: Określanie typu poświadczeń klienta</span><span class="sxs-lookup"><span data-stu-id="09b1e-102">How to: Specify the Client Credential Type</span></span>
<span data-ttu-id="09b1e-103">Po ustawieniu trybu zabezpieczeń (transportu lub wiadomości), istnieje możliwość ustawienia typu poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="09b1e-103">After setting a security mode (either transport or message), you have the option of setting the client credential type.</span></span> <span data-ttu-id="09b1e-104">Ta właściwość określa, jaki typ poświadczenia, klient musi dostarczyć z usługą uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="09b1e-104">This property specifies what type of credential the client must provide to the service for authentication.</span></span> <span data-ttu-id="09b1e-105">Aby uzyskać więcej informacji na temat ustawiania trybu zabezpieczeń (krokiem przed ustawieniem Typ poświadczeń klienta), zobacz [porady: Ustawianie trybu zabezpieczeń](../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="09b1e-105">For more information about setting the security mode (a necessary step before setting the client credential type), see [How to: Set the Security Mode](../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span></span>  
  
### <a name="to-set-the-client-credential-type-in-code"></a><span data-ttu-id="09b1e-106">Aby ustawić typ poświadczeń klienta w kodzie</span><span class="sxs-lookup"><span data-stu-id="09b1e-106">To set the client credential type in code</span></span>  
  
1.  <span data-ttu-id="09b1e-107">Utwórz wystąpienie powiązania, które będzie używane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="09b1e-107">Create an instance of the binding that the service will use.</span></span> <span data-ttu-id="09b1e-108">W tym przykładzie użyto <xref:System.ServiceModel.WSHttpBinding> powiązania.</span><span class="sxs-lookup"><span data-stu-id="09b1e-108">This example uses the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
2.  <span data-ttu-id="09b1e-109">Ustaw <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> właściwości odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="09b1e-109">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to an appropriate value.</span></span> <span data-ttu-id="09b1e-110">W tym przykładzie tryb wiadomości.</span><span class="sxs-lookup"><span data-stu-id="09b1e-110">This example uses the Message mode.</span></span>  
  
3.  <span data-ttu-id="09b1e-111">Ustaw <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> właściwości odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="09b1e-111">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="09b1e-112">W tym przykładzie go do korzystania z uwierzytelniania systemu Windows (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span><span class="sxs-lookup"><span data-stu-id="09b1e-112">This example sets it to use Windows authentication (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span></span>  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a><span data-ttu-id="09b1e-113">Aby ustawić typ poświadczeń klienta w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="09b1e-113">To set the client credential type in configuration</span></span>  
  
1.  <span data-ttu-id="09b1e-114">Dodaj [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="09b1e-114">Add a [\<system.serviceModel>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element to the configuration file.</span></span>  
  
2.  <span data-ttu-id="09b1e-115">Dodanie elementu podrzędnego [ \<powiązania >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="09b1e-115">As a child element, add a [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
3.  <span data-ttu-id="09b1e-116">Dodaj odpowiednie powiązanie.</span><span class="sxs-lookup"><span data-stu-id="09b1e-116">Add an appropriate binding.</span></span> <span data-ttu-id="09b1e-117">W tym przykładzie użyto [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="09b1e-117">This example uses the [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>  
  
4.  <span data-ttu-id="09b1e-118">Dodaj [ \<powiązania >](../../../docs/framework/misc/binding.md) element i ustaw `name` atrybutu odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="09b1e-118">Add a [\<binding>](../../../docs/framework/misc/binding.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="09b1e-119">W tym przykładzie używane są nazwy "SecureBinding".</span><span class="sxs-lookup"><span data-stu-id="09b1e-119">This example uses the name "SecureBinding".</span></span>  
  
5.  <span data-ttu-id="09b1e-120">Dodaj `<security>` powiązania.</span><span class="sxs-lookup"><span data-stu-id="09b1e-120">Add a `<security>` binding.</span></span> <span data-ttu-id="09b1e-121">Ustaw `mode` atrybutu odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="09b1e-121">Set the `mode` attribute to an appropriate value.</span></span> <span data-ttu-id="09b1e-122">W tym przykładzie ustawia ją na `"Message"`.</span><span class="sxs-lookup"><span data-stu-id="09b1e-122">This example sets it to `"Message"`.</span></span>  
  
6.  <span data-ttu-id="09b1e-123">Dodaj albo `<message>` lub `<transport>` element, zgodnie z ustaleniami trybu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="09b1e-123">Add either a `<message>` or `<transport>` element, as determined by the security mode.</span></span> <span data-ttu-id="09b1e-124">Ustaw `clientCredentialType` atrybutu odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="09b1e-124">Set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="09b1e-125">W tym przykładzie użyto `"Windows"`.</span><span class="sxs-lookup"><span data-stu-id="09b1e-125">This example uses `"Windows"`.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="SecureBinding">  
            <security mode="Message">  
                 <message clientCredentialType="Windows" />  
             </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="09b1e-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="09b1e-126">See Also</span></span>  
 [<span data-ttu-id="09b1e-127">Zabezpieczanie usług</span><span class="sxs-lookup"><span data-stu-id="09b1e-127">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="09b1e-128">Instrukcje: ustawianie trybu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="09b1e-128">How to: Set the Security Mode</span></span>](../../../docs/framework/wcf/how-to-set-the-security-mode.md)
