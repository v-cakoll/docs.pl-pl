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
ms.openlocfilehash: f8231acade6821c95a76a608633fe443f4add8ab
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586919"
---
# <a name="how-to-set-a-max-clock-skew"></a><span data-ttu-id="05a63-102">Instrukcje: ustawianie maksymalnego przesunięcia czasowego zegara</span><span class="sxs-lookup"><span data-stu-id="05a63-102">How to: Set a Max Clock Skew</span></span>
<span data-ttu-id="05a63-103">Funkcje o kluczowym znaczeniu można wykolejić, jeśli ustawienia zegara na dwóch komputerach są różne.</span><span class="sxs-lookup"><span data-stu-id="05a63-103">Time-critical functions can be derailed if the clock settings on two computers are different.</span></span> <span data-ttu-id="05a63-104">Aby wyeliminować tę możliwość, można ustawić `MaxClockSkew` Właściwość na <xref:System.TimeSpan> .</span><span class="sxs-lookup"><span data-stu-id="05a63-104">To mitigate this possibility, you can set the `MaxClockSkew` property to a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="05a63-105">Ta właściwość jest dostępna w dwóch klasach:</span><span class="sxs-lookup"><span data-stu-id="05a63-105">This property is available on two classes:</span></span>  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> <span data-ttu-id="05a63-106">W przypadku bezpiecznej konwersacji zmiany wprowadzane we `MaxClockSkew` właściwości muszą zostać wprowadzone podczas ładowania usługi lub klienta.</span><span class="sxs-lookup"><span data-stu-id="05a63-106">For a secure conversation, changes to the `MaxClockSkew` property  must be made when the service or client is bootstrapped.</span></span> <span data-ttu-id="05a63-107">Aby to zrobić, należy ustawić właściwość <xref:System.ServiceModel.Channels.SecurityBindingElement> zwracaną przez <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="05a63-107">To do this, you must set the property on the <xref:System.ServiceModel.Channels.SecurityBindingElement> returned by the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="05a63-108">Aby zmienić właściwość jednego z powiązań dostarczonych przez system, należy znaleźć element powiązania zabezpieczeń w kolekcji powiązań i ustawić `MaxClockSkew` Właściwość na nową wartość.</span><span class="sxs-lookup"><span data-stu-id="05a63-108">To change the property on one of the system-provided bindings, you must find the security binding element in the collection of bindings and set the `MaxClockSkew` property to a new value.</span></span> <span data-ttu-id="05a63-109">Dwie klasy pochodzą z <xref:System.ServiceModel.Channels.SecurityBindingElement> : <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> i <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="05a63-109">Two classes derive from the <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="05a63-110">Podczas pobierania powiązania zabezpieczeń z kolekcji, należy rzutować na jeden z tych typów w celu poprawnego ustawienia `MaxClockSkew` właściwości.</span><span class="sxs-lookup"><span data-stu-id="05a63-110">When retrieving the security binding from the collection, you must cast to one of these types in order to correctly set the `MaxClockSkew` property.</span></span> <span data-ttu-id="05a63-111">W poniższym przykładzie używany jest element <xref:System.ServiceModel.WSHttpBinding> , który używa <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="05a63-111">The following example uses a <xref:System.ServiceModel.WSHttpBinding>, which uses the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="05a63-112">Aby uzyskać listę określającą typ powiązania zabezpieczeń, który ma być używany w każdym powiązaniu z systemem, zobacz [powiązania dostarczone](../system-provided-bindings.md)przez system.</span><span class="sxs-lookup"><span data-stu-id="05a63-112">For a list that specifies which type of security binding to use in each system-provided binding, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a><span data-ttu-id="05a63-113">Aby utworzyć niestandardowe powiązanie z nową wartością przesunięcia zegara w kodzie</span><span class="sxs-lookup"><span data-stu-id="05a63-113">To create a custom binding with a new clock skew value in code</span></span>  
  
> [!WARNING]
> <span data-ttu-id="05a63-114">Dodaj odwołania do następujących przestrzeni nazw w kodzie: <xref:System.ServiceModel.Channels> ,, <xref:System.ServiceModel.Description> <xref:System.Security.Permissions> , i <xref:System.ServiceModel.Security.Tokens> .</span><span class="sxs-lookup"><span data-stu-id="05a63-114">Add references to the following namespaces in your code: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, and <xref:System.ServiceModel.Security.Tokens>.</span></span>  
  
1. <span data-ttu-id="05a63-115">Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw dla niego tryb zabezpieczeń <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="05a63-115">Create an instance of a <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="05a63-116">Utwórz nowe wystąpienie <xref:System.ServiceModel.Channels.BindingElementCollection> klasy, wywołując <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="05a63-116">Create a new instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class by calling the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3. <span data-ttu-id="05a63-117">Użyj <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> metody <xref:System.ServiceModel.Channels.BindingElementCollection> klasy, aby znaleźć element powiązania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="05a63-117">Use the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method of the <xref:System.ServiceModel.Channels.BindingElementCollection> class to find the security binding element.</span></span>  
  
4. <span data-ttu-id="05a63-118">W przypadku korzystania z <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> metody rzutowanie na typ rzeczywisty.</span><span class="sxs-lookup"><span data-stu-id="05a63-118">When using the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method, cast to the actual type.</span></span> <span data-ttu-id="05a63-119">W poniższym przykładzie rzutowanie na <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> Typ.</span><span class="sxs-lookup"><span data-stu-id="05a63-119">The example below casts to the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> type.</span></span>  
  
5. <span data-ttu-id="05a63-120">Ustaw <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> Właściwość dla elementu powiązania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="05a63-120">Set the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> property on the security binding element.</span></span>  
  
6. <span data-ttu-id="05a63-121">Utwórz <xref:System.ServiceModel.ServiceHost> z odpowiednim typem usługi i adresem podstawowym.</span><span class="sxs-lookup"><span data-stu-id="05a63-121">Create a <xref:System.ServiceModel.ServiceHost> with an appropriate service type and base address.</span></span>  
  
7. <span data-ttu-id="05a63-122">Użyj <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody, aby dodać punkt końcowy i uwzględnić <xref:System.ServiceModel.Channels.CustomBinding> .</span><span class="sxs-lookup"><span data-stu-id="05a63-122">Use the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method to add an endpoint and include the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a><span data-ttu-id="05a63-123">Aby ustawić MaxClockSkew w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="05a63-123">To set the MaxClockSkew in configuration</span></span>  
  
1. <span data-ttu-id="05a63-124">Utwórz [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element w sekcji elementu.</span><span class="sxs-lookup"><span data-stu-id="05a63-124">Create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) in the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element section.</span></span>  
  
2. <span data-ttu-id="05a63-125">Utwórz [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element i ustaw `name` odpowiednią wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="05a63-125">Create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="05a63-126">W poniższym przykładzie jest ustawiana wartość `MaxClockSkewBinding` .</span><span class="sxs-lookup"><span data-stu-id="05a63-126">The following example sets it to `MaxClockSkewBinding`.</span></span>  
  
3. <span data-ttu-id="05a63-127">Dodaj element kodowania.</span><span class="sxs-lookup"><span data-stu-id="05a63-127">Add an encoding element.</span></span> <span data-ttu-id="05a63-128">Poniższy przykład dodaje [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) .</span><span class="sxs-lookup"><span data-stu-id="05a63-128">The example below adds a [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
4. <span data-ttu-id="05a63-129">Dodaj [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element i ustaw `authenticationMode` dla atrybutu odpowiednie ustawienie.</span><span class="sxs-lookup"><span data-stu-id="05a63-129">Add a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element and set the `authenticationMode` attribute to an appropriate setting.</span></span> <span data-ttu-id="05a63-130">Poniższy przykład ustawia atrybut na, aby `Kerberos` określić, że usługa używa uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="05a63-130">The following example set the attribute to `Kerberos` to specify that the service use Windows authentication.</span></span>  
  
5. <span data-ttu-id="05a63-131">Dodaj [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) i ustaw `maxClockSkew` atrybut na wartość w postaci `"##:##:##"` .</span><span class="sxs-lookup"><span data-stu-id="05a63-131">Add a [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to a value in the form of `"##:##:##"`.</span></span> <span data-ttu-id="05a63-132">Poniższy przykład ustawia go na 7 minut.</span><span class="sxs-lookup"><span data-stu-id="05a63-132">The following example sets it to 7 minutes.</span></span> <span data-ttu-id="05a63-133">Opcjonalnie Dodaj [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) i ustaw `maxClockSkew` atrybut na odpowiednie ustawienie.</span><span class="sxs-lookup"><span data-stu-id="05a63-133">Optionally, add a [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to an appropriate setting.</span></span>  
  
6. <span data-ttu-id="05a63-134">Dodaj element transportowy.</span><span class="sxs-lookup"><span data-stu-id="05a63-134">Add a transport element.</span></span> <span data-ttu-id="05a63-135">Poniższy przykład używa [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) .</span><span class="sxs-lookup"><span data-stu-id="05a63-135">The following example uses an [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
7. <span data-ttu-id="05a63-136">W przypadku bezpiecznej konwersacji ustawienia zabezpieczeń muszą wystąpić na Bootstrap w [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) elemencie.</span><span class="sxs-lookup"><span data-stu-id="05a63-136">For a secure conversation, the security settings must occur at the bootstrap in the [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="05a63-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05a63-137">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="05a63-138">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="05a63-138">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
