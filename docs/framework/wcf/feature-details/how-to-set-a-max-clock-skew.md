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
# <a name="how-to-set-a-max-clock-skew"></a>Instrukcje: ustawianie maksymalnego przesunięcia czasowego zegara
Funkcje o kluczowym znaczeniu można wykolejić, jeśli ustawienia zegara na dwóch komputerach są różne. Aby wyeliminować tę możliwość, można ustawić `MaxClockSkew` Właściwość <xref:System.TimeSpan>na. Ta właściwość jest dostępna w dwóch klasach:  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> W przypadku bezpiecznej konwersacji zmiany wprowadzane we `MaxClockSkew` właściwości muszą zostać wprowadzone podczas ładowania usługi lub klienta. Aby to zrobić, należy ustawić właściwość <xref:System.ServiceModel.Channels.SecurityBindingElement> zwracaną <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> przez właściwość.  
  
 Aby zmienić właściwość jednego z powiązań dostarczonych przez system, należy znaleźć element powiązania zabezpieczeń w kolekcji powiązań i ustawić `MaxClockSkew` właściwość na nową wartość. Dwie klasy pochodzą z <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> i <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. Podczas pobierania powiązania zabezpieczeń z kolekcji, należy rzutować na jeden z tych typów w celu poprawnego ustawienia `MaxClockSkew` właściwości. W poniższym przykładzie używany jest <xref:System.ServiceModel.WSHttpBinding>element, który <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>używa. Aby uzyskać listę określającą typ powiązania zabezpieczeń, który ma być używany w każdym powiązaniu z systemem, zobacz [powiązania dostarczone](../../../../docs/framework/wcf/system-provided-bindings.md)przez system.  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a>Aby utworzyć niestandardowe powiązanie z nową wartością przesunięcia zegara w kodzie  
  
> [!WARNING]
> Dodaj odwołania do następujących przestrzeni nazw w <xref:System.ServiceModel.Channels>kodzie: <xref:System.Security.Permissions>, <xref:System.ServiceModel.Description>,, i <xref:System.ServiceModel.Security.Tokens>.  
  
1. Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw dla <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>niego tryb zabezpieczeń.  
  
2. Utwórz nowe wystąpienie <xref:System.ServiceModel.Channels.BindingElementCollection> klasy, <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> wywołując metodę.  
  
3. <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> Użyj metody <xref:System.ServiceModel.Channels.BindingElementCollection> klasy, aby znaleźć element powiązania zabezpieczeń.  
  
4. W przypadku korzystania <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> z metody rzutowanie na typ rzeczywisty. W poniższym przykładzie rzutowanie na <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> typ.  
  
5. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> Ustaw właściwość dla elementu powiązania zabezpieczeń.  
  
6. <xref:System.ServiceModel.ServiceHost> Utwórz z odpowiednim typem usługi i adresem podstawowym.  
  
7. Użyj metody, aby dodać punkt końcowy i <xref:System.ServiceModel.Channels.CustomBinding>uwzględnić. <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a>Aby ustawić MaxClockSkew w konfiguracji  
  
1. Utwórz niestandardową [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) >Binding w sekcji powiązań > elementu. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
  
2. Utwórz powiązanie [ >elementuiustawodpowiedniąwartośćatrybutu.\<](../../../../docs/framework/misc/binding.md) `name` W poniższym przykładzie jest `MaxClockSkewBinding`ustawiana wartość.  
  
3. Dodaj element kodowania. Poniższy przykład dodaje [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
4. Dodaj element [> zabezpieczeń i ustaw dla atrybutu odpowiednie ustawienie. \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) `authenticationMode` Poniższy przykład ustawia atrybut na `Kerberos` , aby określić, że usługa używa uwierzytelniania systemu Windows.  
  
5. Dodaj > `maxClockSkew` `"##:##:##"`localServiceSettings i ustaw dla atrybutu wartość w postaci. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) Poniższy przykład ustawia go na 7 minut. Opcjonalnie Dodaj [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) i ustaw `maxClockSkew` dla atrybutu odpowiednie ustawienie.  
  
6. Dodaj element transportowy. Poniższy przykład używa [ \<> httpTransport](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
7. W przypadku bezpiecznej konwersacji ustawienia zabezpieczeń muszą następować po stronie Bootstrap [ \<elementu secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) .  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
