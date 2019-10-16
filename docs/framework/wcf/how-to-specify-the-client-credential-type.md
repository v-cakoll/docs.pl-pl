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
ms.openlocfilehash: d62011728b6b03023ef4039480cea8dfa0ec8f02
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321284"
---
# <a name="how-to-specify-the-client-credential-type"></a><span data-ttu-id="d6111-102">Instrukcje: Określanie typu poświadczeń klienta</span><span class="sxs-lookup"><span data-stu-id="d6111-102">How to: Specify the Client Credential Type</span></span>
<span data-ttu-id="d6111-103">Po ustawieniu trybu zabezpieczeń (transport lub wiadomość) można ustawić typ poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="d6111-103">After setting a security mode (either transport or message), you have the option of setting the client credential type.</span></span> <span data-ttu-id="d6111-104">Ta właściwość określa typ poświadczeń, które klient musi przekazać do usługi w celu uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="d6111-104">This property specifies what type of credential the client must provide to the service for authentication.</span></span> <span data-ttu-id="d6111-105">Aby uzyskać więcej informacji na temat ustawiania trybu zabezpieczeń (wymaganego kroku przed ustawieniem typu poświadczeń klienta), zobacz [How to: Set a Security Mode](how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="d6111-105">For more information about setting the security mode (a necessary step before setting the client credential type), see [How to: Set the Security Mode](how-to-set-the-security-mode.md).</span></span>  
  
### <a name="to-set-the-client-credential-type-in-code"></a><span data-ttu-id="d6111-106">Aby ustawić typ poświadczeń klienta w kodzie</span><span class="sxs-lookup"><span data-stu-id="d6111-106">To set the client credential type in code</span></span>  
  
1. <span data-ttu-id="d6111-107">Utwórz wystąpienie powiązania, które będzie używane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="d6111-107">Create an instance of the binding that the service will use.</span></span> <span data-ttu-id="d6111-108">W tym przykładzie jest stosowane powiązanie <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="d6111-108">This example uses the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
2. <span data-ttu-id="d6111-109">Ustaw właściwość <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="d6111-109">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to an appropriate value.</span></span> <span data-ttu-id="d6111-110">W tym przykładzie jest stosowany tryb wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d6111-110">This example uses the Message mode.</span></span>  
  
3. <span data-ttu-id="d6111-111">Ustaw właściwość <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="d6111-111">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="d6111-112">Ten przykład służy do ustawiania uwierzytelniania systemu Windows (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span><span class="sxs-lookup"><span data-stu-id="d6111-112">This example sets it to use Windows authentication (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span></span>  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a><span data-ttu-id="d6111-113">Aby ustawić typ poświadczeń klienta w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d6111-113">To set the client credential type in configuration</span></span>  
  
1. <span data-ttu-id="d6111-114">Dodaj element [\<System. serviceModel >](../configure-apps/file-schema/wcf/system-servicemodel.md) do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d6111-114">Add a [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) element to the configuration file.</span></span>  
  
2. <span data-ttu-id="d6111-115">Jako element podrzędny Dodaj element [\<bindings >](../configure-apps/file-schema/wcf/bindings.md) .</span><span class="sxs-lookup"><span data-stu-id="d6111-115">As a child element, add a [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
3. <span data-ttu-id="d6111-116">Dodaj odpowiednie powiązanie.</span><span class="sxs-lookup"><span data-stu-id="d6111-116">Add an appropriate binding.</span></span> <span data-ttu-id="d6111-117">W tym przykładzie używa elementu [\<wsHttpBinding >](../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="d6111-117">This example uses the [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>  
  
4. <span data-ttu-id="d6111-118">Dodaj element [\<binding >](../misc/binding.md) i ustaw dla atrybutu `name` odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="d6111-118">Add a [\<binding>](../misc/binding.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="d6111-119">Ten przykład używa nazwy "SecureBinding".</span><span class="sxs-lookup"><span data-stu-id="d6111-119">This example uses the name "SecureBinding".</span></span>  
  
5. <span data-ttu-id="d6111-120">Dodaj powiązanie `<security>`.</span><span class="sxs-lookup"><span data-stu-id="d6111-120">Add a `<security>` binding.</span></span> <span data-ttu-id="d6111-121">Ustaw dla atrybutu `mode` odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="d6111-121">Set the `mode` attribute to an appropriate value.</span></span> <span data-ttu-id="d6111-122">Ten przykład ustawia go na `"Message"`.</span><span class="sxs-lookup"><span data-stu-id="d6111-122">This example sets it to `"Message"`.</span></span>  
  
6. <span data-ttu-id="d6111-123">Dodaj element `<message>` lub `<transport>`, zgodnie z trybem zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d6111-123">Add either a `<message>` or `<transport>` element, as determined by the security mode.</span></span> <span data-ttu-id="d6111-124">Ustaw dla atrybutu `clientCredentialType` odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="d6111-124">Set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="d6111-125">W tym przykładzie używa `"Windows"`.</span><span class="sxs-lookup"><span data-stu-id="d6111-125">This example uses `"Windows"`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d6111-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6111-126">See also</span></span>

- [<span data-ttu-id="d6111-127">Zabezpieczanie usług</span><span class="sxs-lookup"><span data-stu-id="d6111-127">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="d6111-128">Instrukcje: ustawianie trybu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d6111-128">How to: Set the Security Mode</span></span>](how-to-set-the-security-mode.md)
