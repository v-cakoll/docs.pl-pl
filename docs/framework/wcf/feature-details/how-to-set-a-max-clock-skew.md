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
ms.openlocfilehash: e487da6316ec381c2009ee33575848dd80df8ab2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076631"
---
# <a name="how-to-set-a-max-clock-skew"></a>Instrukcje: ustawianie maksymalnego przesunięcia czasowego zegara
Czas ma istotne znaczenie funkcje można derailed, jeśli różnią się ustawienia zegara na dwóch komputerach. Aby uniknąć tej możliwości, możesz ustawić `MaxClockSkew` właściwość <xref:System.TimeSpan>. Ta właściwość jest dostępna w dwóch klas:  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
>  Ważne dla bezpiecznej konwersacji zmieni się na `MaxClockSkew` właściwości muszą być wykonane, gdy jest załadować usługi lub klienta. Aby to zrobić, należy ustawić właściwość na <xref:System.ServiceModel.Channels.SecurityBindingElement> zwrócone przez <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A>.  
  
 Aby zmienić właściwość na jednym z powiązań dostarczanych przez system, możesz znaleźć elementu powiązania zabezpieczeń w kolekcji powiązania i ustawić `MaxClockSkew` właściwości na nową wartość. Dwoma klasami pochodnymi <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> i <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. Podczas pobierania powiązanie zabezpieczeń z kolekcji, należy rzutować do jednego z następujących typów Aby poprawnie ustawić `MaxClockSkew` właściwości. W poniższym przykładzie użyto <xref:System.ServiceModel.WSHttpBinding>, który używa <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>. Aby uzyskać listę, która określa typ zabezpieczeń powiązania do użycia w każdym powiązania dostarczane przez system, zobacz [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
### <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a>Aby utworzyć niestandardowego powiązania za pomocą nowego zegara pochylanie wartości w kodzie  
  
1.  > [!WARNING]
    >  Należy pamiętać, dodaj odwołania do następujących przestrzeni nazw w kodzie: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, i <xref:System.ServiceModel.Security.Tokens>.  
  
     Utwórz wystąpienie obiektu <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw jego tryb zabezpieczeń <xref:System.ServiceModel.SecurityMode.Message>.  
  
2.  Utwórz nowe wystąpienie klasy <xref:System.ServiceModel.Channels.BindingElementCollection> klasy przez wywołanie metody <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> metody.  
  
3.  Użyj <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> metody <xref:System.ServiceModel.Channels.BindingElementCollection> klasy można znaleźć elementu powiązania zabezpieczeń.  
  
4.  Korzystając z <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> metody rzutowany na typ rzeczywistego. W poniższym rzutowania na przykładzie <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> typu.  
  
5.  Ustaw <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> właściwość elementu powiązania zabezpieczeń.  
  
6.  Utwórz <xref:System.ServiceModel.ServiceHost> przy użyciu adresu typu i base odpowiednią usługę.  
  
7.  Użyj <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metodę, aby dodać punkt końcowy i zawierać <xref:System.ServiceModel.Channels.CustomBinding>.  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
### <a name="to-set-the-maxclockskew-in-configuration"></a>Aby ustawić konfigurację MaxClockSkew  
  
1.  Tworzenie [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) w [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) sekcji.  
  
2.  Tworzenie [ \<powiązania >](../../../../docs/framework/misc/binding.md) element i ustaw `name` atrybutu do odpowiedniej wartości. Poniższy przykład ustawia ją na `MaxClockSkewBinding`.  
  
3.  Dodawanie elementu kodowania. Poniższy przykład dodaje [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
4.  Dodaj [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element i ustaw `authenticationMode` atrybutu do odpowiedniego ustawienia. Poniższy przykład atrybut jest ustawiony na `Kerberos` do określenia, że usługa używa uwierzytelniania Windows.  
  
5.  Dodaj [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) i ustaw `maxClockSkew` atrybutu wartości w postaci `"##:##:##"`. Poniższy przykład ustawia ją na 7 minut. Opcjonalnie dodaj [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) i ustaw `maxClockSkew` atrybutu do odpowiedniego ustawienia.  
  
6.  Dodaj element transportu. W poniższym przykładzie użyto [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
7.  Do bezpiecznej konwersacji, ustawienia zabezpieczeń musi wystąpić na bootstrap w [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) elementu.  
  
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
- [Instrukcje: tworzenie niestandardowego wiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
