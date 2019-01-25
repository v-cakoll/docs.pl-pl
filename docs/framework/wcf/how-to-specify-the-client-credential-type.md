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
ms.openlocfilehash: 9fe999c4ee27d4a78bfad185fa3bcc065d74708a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643383"
---
# <a name="how-to-specify-the-client-credential-type"></a><span data-ttu-id="a4896-102">Instrukcje: Określanie typu poświadczeń klienta</span><span class="sxs-lookup"><span data-stu-id="a4896-102">How to: Specify the Client Credential Type</span></span>
<span data-ttu-id="a4896-103">Po ustawieniu trybu zabezpieczeń (transportu lub wiadomości), istnieje możliwość ustawienia typu poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="a4896-103">After setting a security mode (either transport or message), you have the option of setting the client credential type.</span></span> <span data-ttu-id="a4896-104">Ta właściwość określa, jakiego typu poświadczeń klienta należy podać usługi na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a4896-104">This property specifies what type of credential the client must provide to the service for authentication.</span></span> <span data-ttu-id="a4896-105">Aby uzyskać więcej informacji na temat ustawiania trybu zabezpieczeń (niezbędne krok przed ustawieniem typu poświadczeń klienta), zobacz [jak: Ustawianie trybu zabezpieczeń](../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="a4896-105">For more information about setting the security mode (a necessary step before setting the client credential type), see [How to: Set the Security Mode](../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span></span>  
  
### <a name="to-set-the-client-credential-type-in-code"></a><span data-ttu-id="a4896-106">Aby ustawić typ poświadczeń klienta w kodzie</span><span class="sxs-lookup"><span data-stu-id="a4896-106">To set the client credential type in code</span></span>  
  
1.  <span data-ttu-id="a4896-107">Utwórz wystąpienie powiązania, które będzie używane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="a4896-107">Create an instance of the binding that the service will use.</span></span> <span data-ttu-id="a4896-108">W tym przykładzie użyto <xref:System.ServiceModel.WSHttpBinding> powiązania.</span><span class="sxs-lookup"><span data-stu-id="a4896-108">This example uses the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
2.  <span data-ttu-id="a4896-109">Ustaw <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> właściwość do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="a4896-109">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to an appropriate value.</span></span> <span data-ttu-id="a4896-110">W tym przykładzie użyto trybu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a4896-110">This example uses the Message mode.</span></span>  
  
3.  <span data-ttu-id="a4896-111">Ustaw <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> właściwość do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="a4896-111">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="a4896-112">W tym przykładzie go do korzystania z uwierzytelniania Windows (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span><span class="sxs-lookup"><span data-stu-id="a4896-112">This example sets it to use Windows authentication (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span></span>  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a><span data-ttu-id="a4896-113">Aby ustawić typ poświadczeń klienta w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a4896-113">To set the client credential type in configuration</span></span>  
  
1.  <span data-ttu-id="a4896-114">Dodaj [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a4896-114">Add a [\<system.serviceModel>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element to the configuration file.</span></span>  
  
2.  <span data-ttu-id="a4896-115">Dodanie elementu podrzędnego [ \<powiązania >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="a4896-115">As a child element, add a [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
3.  <span data-ttu-id="a4896-116">Dodaj odpowiednie powiązanie.</span><span class="sxs-lookup"><span data-stu-id="a4896-116">Add an appropriate binding.</span></span> <span data-ttu-id="a4896-117">W tym przykładzie użyto [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="a4896-117">This example uses the [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>  
  
4.  <span data-ttu-id="a4896-118">Dodaj [ \<powiązania >](../../../docs/framework/misc/binding.md) element i ustaw `name` atrybutu do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="a4896-118">Add a [\<binding>](../../../docs/framework/misc/binding.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="a4896-119">W tym przykładzie używa nazwy "SecureBinding".</span><span class="sxs-lookup"><span data-stu-id="a4896-119">This example uses the name "SecureBinding".</span></span>  
  
5.  <span data-ttu-id="a4896-120">Dodaj `<security>` powiązania.</span><span class="sxs-lookup"><span data-stu-id="a4896-120">Add a `<security>` binding.</span></span> <span data-ttu-id="a4896-121">Ustaw `mode` atrybutu do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="a4896-121">Set the `mode` attribute to an appropriate value.</span></span> <span data-ttu-id="a4896-122">W tym przykładzie ustawia ją na `"Message"`.</span><span class="sxs-lookup"><span data-stu-id="a4896-122">This example sets it to `"Message"`.</span></span>  
  
6.  <span data-ttu-id="a4896-123">Dodaj opcję `<message>` lub `<transport>` elementu, zgodnie z ustaleniami tryb zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="a4896-123">Add either a `<message>` or `<transport>` element, as determined by the security mode.</span></span> <span data-ttu-id="a4896-124">Ustaw `clientCredentialType` atrybutu do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="a4896-124">Set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="a4896-125">W tym przykładzie użyto `"Windows"`.</span><span class="sxs-lookup"><span data-stu-id="a4896-125">This example uses `"Windows"`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a4896-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4896-126">See also</span></span>
- [<span data-ttu-id="a4896-127">Zabezpieczanie usług</span><span class="sxs-lookup"><span data-stu-id="a4896-127">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)
- [<span data-ttu-id="a4896-128">Instrukcje: Ustawianie trybu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="a4896-128">How to: Set the Security Mode</span></span>](../../../docs/framework/wcf/how-to-set-the-security-mode.md)
