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
# <a name="how-to-set-a-max-clock-skew"></a>Instrukcje: ustawianie maksymalnego przesunięcia czasowego zegara
Funkcje o kluczowym znaczeniu można wykolejić, jeśli ustawienia zegara na dwóch komputerach są różne. Aby wyeliminować tę możliwość, można ustawić `MaxClockSkew` Właściwość na <xref:System.TimeSpan> . Ta właściwość jest dostępna w dwóch klasach:  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> W przypadku bezpiecznej konwersacji zmiany wprowadzane we `MaxClockSkew` właściwości muszą zostać wprowadzone podczas ładowania usługi lub klienta. Aby to zrobić, należy ustawić właściwość <xref:System.ServiceModel.Channels.SecurityBindingElement> zwracaną przez <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> Właściwość.  
  
 Aby zmienić właściwość jednego z powiązań dostarczonych przez system, należy znaleźć element powiązania zabezpieczeń w kolekcji powiązań i ustawić `MaxClockSkew` Właściwość na nową wartość. Dwie klasy pochodzą z <xref:System.ServiceModel.Channels.SecurityBindingElement> : <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> i <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> . Podczas pobierania powiązania zabezpieczeń z kolekcji, należy rzutować na jeden z tych typów w celu poprawnego ustawienia `MaxClockSkew` właściwości. W poniższym przykładzie używany jest element <xref:System.ServiceModel.WSHttpBinding> , który używa <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> . Aby uzyskać listę określającą typ powiązania zabezpieczeń, który ma być używany w każdym powiązaniu z systemem, zobacz [powiązania dostarczone](../system-provided-bindings.md)przez system.  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a>Aby utworzyć niestandardowe powiązanie z nową wartością przesunięcia zegara w kodzie  
  
> [!WARNING]
> Dodaj odwołania do następujących przestrzeni nazw w kodzie: <xref:System.ServiceModel.Channels> ,, <xref:System.ServiceModel.Description> <xref:System.Security.Permissions> , i <xref:System.ServiceModel.Security.Tokens> .  
  
1. Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw dla niego tryb zabezpieczeń <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType> .  
  
2. Utwórz nowe wystąpienie <xref:System.ServiceModel.Channels.BindingElementCollection> klasy, wywołując <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> metodę.  
  
3. Użyj <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> metody <xref:System.ServiceModel.Channels.BindingElementCollection> klasy, aby znaleźć element powiązania zabezpieczeń.  
  
4. W przypadku korzystania z <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> metody rzutowanie na typ rzeczywisty. W poniższym przykładzie rzutowanie na <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> Typ.  
  
5. Ustaw <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> Właściwość dla elementu powiązania zabezpieczeń.  
  
6. Utwórz <xref:System.ServiceModel.ServiceHost> z odpowiednim typem usługi i adresem podstawowym.  
  
7. Użyj <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody, aby dodać punkt końcowy i uwzględnić <xref:System.ServiceModel.Channels.CustomBinding> .  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a>Aby ustawić MaxClockSkew w konfiguracji  
  
1. Utwórz [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element w sekcji elementu.  
  
2. Utwórz [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element i ustaw `name` odpowiednią wartość atrybutu. W poniższym przykładzie jest ustawiana wartość `MaxClockSkewBinding` .  
  
3. Dodaj element kodowania. Poniższy przykład dodaje [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) .  
  
4. Dodaj [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element i ustaw `authenticationMode` dla atrybutu odpowiednie ustawienie. Poniższy przykład ustawia atrybut na, aby `Kerberos` określić, że usługa używa uwierzytelniania systemu Windows.  
  
5. Dodaj [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) i ustaw `maxClockSkew` atrybut na wartość w postaci `"##:##:##"` . Poniższy przykład ustawia go na 7 minut. Opcjonalnie Dodaj [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) i ustaw `maxClockSkew` atrybut na odpowiednie ustawienie.  
  
6. Dodaj element transportowy. Poniższy przykład używa [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) .  
  
7. W przypadku bezpiecznej konwersacji ustawienia zabezpieczeń muszą wystąpić na Bootstrap w [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) elemencie.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
