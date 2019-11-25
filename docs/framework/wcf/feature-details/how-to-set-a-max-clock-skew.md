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
# <a name="how-to-set-a-max-clock-skew"></a>Instrukcje: Ustawianie maksymalnego przesunięcia zegara
Funkcje o kluczowym znaczeniu można wykolejić, jeśli ustawienia zegara na dwóch komputerach są różne. Aby wyeliminować tę możliwość, można ustawić właściwość `MaxClockSkew` na <xref:System.TimeSpan>. Ta właściwość jest dostępna w dwóch klasach:  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> W przypadku bezpiecznej konwersacji należy wprowadzić zmiany właściwości `MaxClockSkew` podczas uruchamiania usługi lub klienta. Aby to zrobić, należy ustawić właściwość na <xref:System.ServiceModel.Channels.SecurityBindingElement> zwracanej przez właściwość <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType>.  
  
 Aby zmienić właściwość jednego z powiązań dostarczonych przez system, należy znaleźć element powiązania zabezpieczeń w kolekcji powiązań i ustawić dla właściwości `MaxClockSkew` nową wartość. Dwie klasy pochodzą z <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> i <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. Podczas pobierania powiązania zabezpieczeń z kolekcji, należy rzutować na jeden z tych typów, aby prawidłowo ustawić właściwość `MaxClockSkew`. Poniższy przykład używa <xref:System.ServiceModel.WSHttpBinding>, który używa <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>. Aby uzyskać listę określającą typ powiązania zabezpieczeń, który ma być używany w każdym powiązaniu z systemem, zobacz [powiązania dostarczone](../../../../docs/framework/wcf/system-provided-bindings.md)przez system.  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a>Aby utworzyć niestandardowe powiązanie z nową wartością przesunięcia zegara w kodzie  
  
> [!WARNING]
> Dodaj odwołania do następujących przestrzeni nazw w kodzie: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>i <xref:System.ServiceModel.Security.Tokens>.  
  
1. Utwórz wystąpienie klasy <xref:System.ServiceModel.WSHttpBinding> i ustaw jej tryb zabezpieczeń na <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>.  
  
2. Utwórz nowe wystąpienie klasy <xref:System.ServiceModel.Channels.BindingElementCollection>, wywołując metodę <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A>.  
  
3. Użyj metody <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> klasy <xref:System.ServiceModel.Channels.BindingElementCollection>, aby znaleźć element powiązania zabezpieczeń.  
  
4. Przy użyciu metody <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> rzutowanie na typ rzeczywisty. W poniższym przykładzie rzutowanie na typ <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
5. Ustaw właściwość <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> w elemencie powiązania zabezpieczeń.  
  
6. Utwórz <xref:System.ServiceModel.ServiceHost> z odpowiednim typem usługi i adresem podstawowym.  
  
7. Użyj metody <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>, aby dodać punkt końcowy i uwzględnić <xref:System.ServiceModel.Channels.CustomBinding>.  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a>Aby ustawić MaxClockSkew w konfiguracji  
  
1. Utwórz [\<niestandardowebinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) w sekcji [\<powiązań >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu.  
  
2. Utwórz element [> powiązań\<](../../configure-apps/file-schema/wcf/bindings.md) i ustaw odpowiednią wartość atrybutu `name`. Poniższy przykład ustawia go na `MaxClockSkewBinding`.  
  
3. Dodaj element kodowania. Poniższy przykład dodaje [\<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
4. Dodaj element [> zabezpieczeń\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) i ustaw dla atrybutu `authenticationMode` odpowiednie ustawienie. W poniższym przykładzie ustawiono atrybut `Kerberos`, aby określić, że usługa używa uwierzytelniania systemu Windows.  
  
5. Dodaj [\<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) i ustaw atrybut `maxClockSkew` na wartość w postaci `"##:##:##"`. Poniższy przykład ustawia go na 7 minut. Opcjonalnie można dodać [\<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) i ustawić atrybut `maxClockSkew` na odpowiednie ustawienie.  
  
6. Dodaj element transportowy. Poniższy przykład używa [\<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
7. W przypadku bezpiecznej konwersacji ustawienia zabezpieczeń muszą następować po stronie Bootstrap w\<elementu [> secureConversationBootstrap](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) .  
  
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
- [Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
