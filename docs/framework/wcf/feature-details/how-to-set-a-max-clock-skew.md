---
title: 'Instrukcje: Ustawianie maksymalnego przesunięcia zegara'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
ms.openlocfilehash: 96afa61d32e1ba744c9f3dbbeeb7fb2e55157f4c
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141657"
---
# <a name="how-to-set-a-max-clock-skew"></a><span data-ttu-id="563f3-102">Instrukcje: Ustawianie maksymalnego przesunięcia zegara</span><span class="sxs-lookup"><span data-stu-id="563f3-102">How to: Set a Max Clock Skew</span></span>
<span data-ttu-id="563f3-103">Funkcje o kluczowym znaczeniu można wykolejić, jeśli ustawienia zegara na dwóch komputerach są różne.</span><span class="sxs-lookup"><span data-stu-id="563f3-103">Time-critical functions can be derailed if the clock settings on two computers are different.</span></span> <span data-ttu-id="563f3-104">Aby wyeliminować tę możliwość, można ustawić właściwość `MaxClockSkew` na <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="563f3-104">To mitigate this possibility, you can set the `MaxClockSkew` property to a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="563f3-105">Ta właściwość jest dostępna w dwóch klasach:</span><span class="sxs-lookup"><span data-stu-id="563f3-105">This property is available on two classes:</span></span>  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> <span data-ttu-id="563f3-106">W przypadku bezpiecznej konwersacji należy wprowadzić zmiany właściwości `MaxClockSkew` podczas uruchamiania usługi lub klienta.</span><span class="sxs-lookup"><span data-stu-id="563f3-106">For a secure conversation, changes to the `MaxClockSkew` property  must be made when the service or client is bootstrapped.</span></span> <span data-ttu-id="563f3-107">Aby to zrobić, należy ustawić właściwość na <xref:System.ServiceModel.Channels.SecurityBindingElement> zwracanej przez właściwość <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="563f3-107">To do this, you must set the property on the <xref:System.ServiceModel.Channels.SecurityBindingElement> returned by the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="563f3-108">Aby zmienić właściwość jednego z powiązań dostarczonych przez system, należy znaleźć element powiązania zabezpieczeń w kolekcji powiązań i ustawić dla właściwości `MaxClockSkew` nową wartość.</span><span class="sxs-lookup"><span data-stu-id="563f3-108">To change the property on one of the system-provided bindings, you must find the security binding element in the collection of bindings and set the `MaxClockSkew` property to a new value.</span></span> <span data-ttu-id="563f3-109">Dwie klasy pochodzą z <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> i <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="563f3-109">Two classes derive from the <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="563f3-110">Podczas pobierania powiązania zabezpieczeń z kolekcji, należy rzutować na jeden z tych typów, aby prawidłowo ustawić właściwość `MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="563f3-110">When retrieving the security binding from the collection, you must cast to one of these types in order to correctly set the `MaxClockSkew` property.</span></span> <span data-ttu-id="563f3-111">Poniższy przykład używa <xref:System.ServiceModel.WSHttpBinding>, który używa <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="563f3-111">The following example uses a <xref:System.ServiceModel.WSHttpBinding>, which uses the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="563f3-112">Aby uzyskać listę określającą typ powiązania zabezpieczeń, który ma być używany w każdym powiązaniu z systemem, zobacz [powiązania dostarczone](../../../../docs/framework/wcf/system-provided-bindings.md)przez system.</span><span class="sxs-lookup"><span data-stu-id="563f3-112">For a list that specifies which type of security binding to use in each system-provided binding, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a><span data-ttu-id="563f3-113">Aby utworzyć niestandardowe powiązanie z nową wartością przesunięcia zegara w kodzie</span><span class="sxs-lookup"><span data-stu-id="563f3-113">To create a custom binding with a new clock skew value in code</span></span>  
  
> [!WARNING]
> <span data-ttu-id="563f3-114">Dodaj odwołania do następujących przestrzeni nazw w kodzie: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>i <xref:System.ServiceModel.Security.Tokens>.</span><span class="sxs-lookup"><span data-stu-id="563f3-114">Add references to the following namespaces in your code: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, and <xref:System.ServiceModel.Security.Tokens>.</span></span>  
  
1. <span data-ttu-id="563f3-115">Utwórz wystąpienie klasy <xref:System.ServiceModel.WSHttpBinding> i ustaw jej tryb zabezpieczeń na <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="563f3-115">Create an instance of a <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="563f3-116">Utwórz nowe wystąpienie klasy <xref:System.ServiceModel.Channels.BindingElementCollection>, wywołując metodę <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A>.</span><span class="sxs-lookup"><span data-stu-id="563f3-116">Create a new instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class by calling the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3. <span data-ttu-id="563f3-117">Użyj metody <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> klasy <xref:System.ServiceModel.Channels.BindingElementCollection>, aby znaleźć element powiązania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="563f3-117">Use the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method of the <xref:System.ServiceModel.Channels.BindingElementCollection> class to find the security binding element.</span></span>  
  
4. <span data-ttu-id="563f3-118">Przy użyciu metody <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> rzutowanie na typ rzeczywisty.</span><span class="sxs-lookup"><span data-stu-id="563f3-118">When using the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method, cast to the actual type.</span></span> <span data-ttu-id="563f3-119">W poniższym przykładzie rzutowanie na typ <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="563f3-119">The example below casts to the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> type.</span></span>  
  
5. <span data-ttu-id="563f3-120">Ustaw właściwość <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> w elemencie powiązania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="563f3-120">Set the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> property on the security binding element.</span></span>  
  
6. <span data-ttu-id="563f3-121">Utwórz <xref:System.ServiceModel.ServiceHost> z odpowiednim typem usługi i adresem podstawowym.</span><span class="sxs-lookup"><span data-stu-id="563f3-121">Create a <xref:System.ServiceModel.ServiceHost> with an appropriate service type and base address.</span></span>  
  
7. <span data-ttu-id="563f3-122">Użyj metody <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>, aby dodać punkt końcowy i uwzględnić <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="563f3-122">Use the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method to add an endpoint and include the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a><span data-ttu-id="563f3-123">Aby ustawić MaxClockSkew w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="563f3-123">To set the MaxClockSkew in configuration</span></span>  
  
1. <span data-ttu-id="563f3-124">Utwórz [\<niestandardowebinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) w sekcji [\<powiązań >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="563f3-124">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) in the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section.</span></span>  
  
2. <span data-ttu-id="563f3-125">Utwórz element [> powiązań\<](../../configure-apps/file-schema/wcf/bindings.md) i ustaw odpowiednią wartość atrybutu `name`.</span><span class="sxs-lookup"><span data-stu-id="563f3-125">Create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="563f3-126">Poniższy przykład ustawia go na `MaxClockSkewBinding`.</span><span class="sxs-lookup"><span data-stu-id="563f3-126">The following example sets it to `MaxClockSkewBinding`.</span></span>  
  
3. <span data-ttu-id="563f3-127">Dodaj element kodowania.</span><span class="sxs-lookup"><span data-stu-id="563f3-127">Add an encoding element.</span></span> <span data-ttu-id="563f3-128">Poniższy przykład dodaje [\<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="563f3-128">The example below adds a [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
4. <span data-ttu-id="563f3-129">Dodaj element [> zabezpieczeń\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) i ustaw dla atrybutu `authenticationMode` odpowiednie ustawienie.</span><span class="sxs-lookup"><span data-stu-id="563f3-129">Add a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element and set the `authenticationMode` attribute to an appropriate setting.</span></span> <span data-ttu-id="563f3-130">W poniższym przykładzie ustawiono atrybut `Kerberos`, aby określić, że usługa używa uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="563f3-130">The following example set the attribute to `Kerberos` to specify that the service use Windows authentication.</span></span>  
  
5. <span data-ttu-id="563f3-131">Dodaj [\<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) i ustaw atrybut `maxClockSkew` na wartość w postaci `"##:##:##"`.</span><span class="sxs-lookup"><span data-stu-id="563f3-131">Add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to a value in the form of `"##:##:##"`.</span></span> <span data-ttu-id="563f3-132">Poniższy przykład ustawia go na 7 minut.</span><span class="sxs-lookup"><span data-stu-id="563f3-132">The following example sets it to 7 minutes.</span></span> <span data-ttu-id="563f3-133">Opcjonalnie można dodać [\<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) i ustawić atrybut `maxClockSkew` na odpowiednie ustawienie.</span><span class="sxs-lookup"><span data-stu-id="563f3-133">Optionally, add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to an appropriate setting.</span></span>  
  
6. <span data-ttu-id="563f3-134">Dodaj element transportowy.</span><span class="sxs-lookup"><span data-stu-id="563f3-134">Add a transport element.</span></span> <span data-ttu-id="563f3-135">Poniższy przykład używa [\<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span><span class="sxs-lookup"><span data-stu-id="563f3-135">The following example uses an [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
7. <span data-ttu-id="563f3-136">W przypadku bezpiecznej konwersacji ustawienia zabezpieczeń muszą następować po stronie Bootstrap w\<elementu [> secureConversationBootstrap](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) .</span><span class="sxs-lookup"><span data-stu-id="563f3-136">For a secure conversation, the security settings must occur at the bootstrap in the [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="MaxClockSkewBinding">  
            <textMessageEncoding />  
            <security authenticationMode="Kerberos">  
               <localClientSettings maxClockSkew="00:07:00" />  
               <localServiceSettings maxClockSkew="00:07:00" />  
               <secureConversationBootstrap>  
                  <localClientSettings maxClockSkew="00:30:00" />  
                  <localServiceSettings maxClockSkew="00:30:00" />  
               </secureConversationBootstrap>  
            </security>  
            <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="563f3-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="563f3-137">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="563f3-138">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="563f3-138">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
