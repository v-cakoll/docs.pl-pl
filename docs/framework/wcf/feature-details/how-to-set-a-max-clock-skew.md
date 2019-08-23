---
title: 'Instrukcje: ustawianie maksymalnego przesunięcia czasowego zegara'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
ms.openlocfilehash: 3bcd128e6e9f53f662dd3fc99336b5b45faebf5f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943117"
---
# <a name="how-to-set-a-max-clock-skew"></a><span data-ttu-id="e81da-102">Instrukcje: ustawianie maksymalnego przesunięcia czasowego zegara</span><span class="sxs-lookup"><span data-stu-id="e81da-102">How to: Set a Max Clock Skew</span></span>
<span data-ttu-id="e81da-103">Funkcje o kluczowym znaczeniu można wykolejić, jeśli ustawienia zegara na dwóch komputerach są różne.</span><span class="sxs-lookup"><span data-stu-id="e81da-103">Time-critical functions can be derailed if the clock settings on two computers are different.</span></span> <span data-ttu-id="e81da-104">Aby wyeliminować tę możliwość, można ustawić `MaxClockSkew` Właściwość <xref:System.TimeSpan>na.</span><span class="sxs-lookup"><span data-stu-id="e81da-104">To mitigate this possibility, you can set the `MaxClockSkew` property to a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="e81da-105">Ta właściwość jest dostępna w dwóch klasach:</span><span class="sxs-lookup"><span data-stu-id="e81da-105">This property is available on two classes:</span></span>  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> <span data-ttu-id="e81da-106">W przypadku bezpiecznej konwersacji zmiany wprowadzane we `MaxClockSkew` właściwości muszą zostać wprowadzone podczas ładowania usługi lub klienta.</span><span class="sxs-lookup"><span data-stu-id="e81da-106">For a secure conversation, changes to the `MaxClockSkew` property  must be made when the service or client is bootstrapped.</span></span> <span data-ttu-id="e81da-107">Aby to zrobić, należy ustawić właściwość <xref:System.ServiceModel.Channels.SecurityBindingElement> zwracaną <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> przez właściwość.</span><span class="sxs-lookup"><span data-stu-id="e81da-107">To do this, you must set the property on the <xref:System.ServiceModel.Channels.SecurityBindingElement> returned by the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="e81da-108">Aby zmienić właściwość jednego z powiązań dostarczonych przez system, należy znaleźć element powiązania zabezpieczeń w kolekcji powiązań i ustawić `MaxClockSkew` właściwość na nową wartość.</span><span class="sxs-lookup"><span data-stu-id="e81da-108">To change the property on one of the system-provided bindings, you must find the security binding element in the collection of bindings and set the `MaxClockSkew` property to a new value.</span></span> <span data-ttu-id="e81da-109">Dwie klasy pochodzą z <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> i <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="e81da-109">Two classes derive from the <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="e81da-110">Podczas pobierania powiązania zabezpieczeń z kolekcji, należy rzutować na jeden z tych typów w celu poprawnego ustawienia `MaxClockSkew` właściwości.</span><span class="sxs-lookup"><span data-stu-id="e81da-110">When retrieving the security binding from the collection, you must cast to one of these types in order to correctly set the `MaxClockSkew` property.</span></span> <span data-ttu-id="e81da-111">W poniższym przykładzie używany jest <xref:System.ServiceModel.WSHttpBinding>element, który <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>używa.</span><span class="sxs-lookup"><span data-stu-id="e81da-111">The following example uses a <xref:System.ServiceModel.WSHttpBinding>, which uses the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="e81da-112">Aby uzyskać listę określającą typ powiązania zabezpieczeń, który ma być używany w każdym powiązaniu z systemem, zobacz [powiązania dostarczone](../../../../docs/framework/wcf/system-provided-bindings.md)przez system.</span><span class="sxs-lookup"><span data-stu-id="e81da-112">For a list that specifies which type of security binding to use in each system-provided binding, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a><span data-ttu-id="e81da-113">Aby utworzyć niestandardowe powiązanie z nową wartością przesunięcia zegara w kodzie</span><span class="sxs-lookup"><span data-stu-id="e81da-113">To create a custom binding with a new clock skew value in code</span></span>  
  
> [!WARNING]
> <span data-ttu-id="e81da-114">Dodaj odwołania do następujących przestrzeni nazw w <xref:System.ServiceModel.Channels>kodzie: <xref:System.Security.Permissions>, <xref:System.ServiceModel.Description>,, i <xref:System.ServiceModel.Security.Tokens>.</span><span class="sxs-lookup"><span data-stu-id="e81da-114">Add references to the following namespaces in your code: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, and <xref:System.ServiceModel.Security.Tokens>.</span></span>  
  
1. <span data-ttu-id="e81da-115">Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw dla <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>niego tryb zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e81da-115">Create an instance of a <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="e81da-116">Utwórz nowe wystąpienie <xref:System.ServiceModel.Channels.BindingElementCollection> klasy, <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> wywołując metodę.</span><span class="sxs-lookup"><span data-stu-id="e81da-116">Create a new instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class by calling the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3. <span data-ttu-id="e81da-117"><xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> Użyj metody <xref:System.ServiceModel.Channels.BindingElementCollection> klasy, aby znaleźć element powiązania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e81da-117">Use the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method of the <xref:System.ServiceModel.Channels.BindingElementCollection> class to find the security binding element.</span></span>  
  
4. <span data-ttu-id="e81da-118">W przypadku korzystania <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> z metody rzutowanie na typ rzeczywisty.</span><span class="sxs-lookup"><span data-stu-id="e81da-118">When using the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method, cast to the actual type.</span></span> <span data-ttu-id="e81da-119">W poniższym przykładzie rzutowanie na <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> typ.</span><span class="sxs-lookup"><span data-stu-id="e81da-119">The example below casts to the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> type.</span></span>  
  
5. <span data-ttu-id="e81da-120"><xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> Ustaw właściwość dla elementu powiązania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e81da-120">Set the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> property on the security binding element.</span></span>  
  
6. <span data-ttu-id="e81da-121"><xref:System.ServiceModel.ServiceHost> Utwórz z odpowiednim typem usługi i adresem podstawowym.</span><span class="sxs-lookup"><span data-stu-id="e81da-121">Create a <xref:System.ServiceModel.ServiceHost> with an appropriate service type and base address.</span></span>  
  
7. <span data-ttu-id="e81da-122">Użyj metody, aby dodać punkt końcowy i <xref:System.ServiceModel.Channels.CustomBinding>uwzględnić. <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A></span><span class="sxs-lookup"><span data-stu-id="e81da-122">Use the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method to add an endpoint and include the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a><span data-ttu-id="e81da-123">Aby ustawić MaxClockSkew w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e81da-123">To set the MaxClockSkew in configuration</span></span>  
  
1. <span data-ttu-id="e81da-124">Utwórz niestandardową [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) >Binding w sekcji powiązań > elementu. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="e81da-124">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) in the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section.</span></span>  
  
2. <span data-ttu-id="e81da-125">Utwórz powiązanie [ >elementuiustawodpowiedniąwartośćatrybutu.\<](../../../../docs/framework/misc/binding.md) `name`</span><span class="sxs-lookup"><span data-stu-id="e81da-125">Create a [\<binding>](../../../../docs/framework/misc/binding.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="e81da-126">W poniższym przykładzie jest `MaxClockSkewBinding`ustawiana wartość.</span><span class="sxs-lookup"><span data-stu-id="e81da-126">The following example sets it to `MaxClockSkewBinding`.</span></span>  
  
3. <span data-ttu-id="e81da-127">Dodaj element kodowania.</span><span class="sxs-lookup"><span data-stu-id="e81da-127">Add an encoding element.</span></span> <span data-ttu-id="e81da-128">Poniższy przykład dodaje [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="e81da-128">The example below adds a [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
4. <span data-ttu-id="e81da-129">Dodaj element [> zabezpieczeń i ustaw dla atrybutu odpowiednie ustawienie. \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) `authenticationMode`</span><span class="sxs-lookup"><span data-stu-id="e81da-129">Add a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element and set the `authenticationMode` attribute to an appropriate setting.</span></span> <span data-ttu-id="e81da-130">Poniższy przykład ustawia atrybut na `Kerberos` , aby określić, że usługa używa uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e81da-130">The following example set the attribute to `Kerberos` to specify that the service use Windows authentication.</span></span>  
  
5. <span data-ttu-id="e81da-131">Dodaj > `maxClockSkew` `"##:##:##"`localServiceSettings i ustaw dla atrybutu wartość w postaci. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="e81da-131">Add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to a value in the form of `"##:##:##"`.</span></span> <span data-ttu-id="e81da-132">Poniższy przykład ustawia go na 7 minut.</span><span class="sxs-lookup"><span data-stu-id="e81da-132">The following example sets it to 7 minutes.</span></span> <span data-ttu-id="e81da-133">Opcjonalnie Dodaj [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) i ustaw `maxClockSkew` dla atrybutu odpowiednie ustawienie.</span><span class="sxs-lookup"><span data-stu-id="e81da-133">Optionally, add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to an appropriate setting.</span></span>  
  
6. <span data-ttu-id="e81da-134">Dodaj element transportowy.</span><span class="sxs-lookup"><span data-stu-id="e81da-134">Add a transport element.</span></span> <span data-ttu-id="e81da-135">Poniższy przykład używa [ \<> httpTransport](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span><span class="sxs-lookup"><span data-stu-id="e81da-135">The following example uses an [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
7. <span data-ttu-id="e81da-136">W przypadku bezpiecznej konwersacji ustawienia zabezpieczeń muszą następować po stronie Bootstrap [ \<elementu secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) .</span><span class="sxs-lookup"><span data-stu-id="e81da-136">For a secure conversation, the security settings must occur at the bootstrap in the [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e81da-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e81da-137">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="e81da-138">Instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="e81da-138">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
