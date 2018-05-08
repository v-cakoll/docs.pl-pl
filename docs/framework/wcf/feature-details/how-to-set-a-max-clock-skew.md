---
title: 'Porady: zestaw Max niedokładność zegara'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
ms.openlocfilehash: dca675b8d5774948bffd936d146cb0e1dd9aa62d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-a-max-clock-skew"></a>Porady: zestaw Max niedokładność zegara
Funkcje o krytycznym znaczeniu czasu można derailed, jeśli są różne ustawienia zegara na dwóch komputerach. Aby ograniczyć to ryzyko, można ustawić `MaxClockSkew` właściwości <xref:System.TimeSpan>. Ta właściwość jest dostępna na dwie klasy:  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
>  Ważne dla bezpiecznej konwersacji, zmienia się na `MaxClockSkew` muszą być wprowadzane właściwości, gdy jest zainicjowano usługi lub klienta. Aby to zrobić, należy ustawić właściwość na <xref:System.ServiceModel.Channels.SecurityBindingElement> zwrócony przez <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A>.  
  
 Aby zmienić właściwości na jednym z powiązania dostarczane przez system, należy odnaleźć w kolekcji powiązania elementu powiązania zabezpieczeń i ustawić `MaxClockSkew` właściwości na nową wartość. Dwie klasy pochodzi od <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> i <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. Podczas pobierania powiązania zabezpieczeń z kolekcji, należy rzutowanie do jednego z następujących typów, aby poprawnie ustawić `MaxClockSkew` właściwości. W poniższym przykładzie użyto <xref:System.ServiceModel.WSHttpBinding>, który korzysta z <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>. Aby uzyskać listę, która określa typ powiązania zabezpieczeń do użycia w każdego powiązania dostarczane przez system, zobacz [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
### <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a>Aby utworzyć niestandardowego powiązania z zegarem nowe pochylanie wartości w kodzie  
  
1.  > [!WARNING]
    >  Należy pamiętać, dodaj odwołania do następujących przestrzeni nazw w kodzie: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, i <xref:System.ServiceModel.Security.Tokens>.  
  
     Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw jego tryb zabezpieczeń <xref:System.ServiceModel.SecurityMode.Message>.  
  
2.  Utwórz nowe wystąpienie klasy <xref:System.ServiceModel.Channels.BindingElementCollection> klasy przez wywołanie metody <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> metody.  
  
3.  Użyj <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> metody <xref:System.ServiceModel.Channels.BindingElementCollection> klasy można znaleźć elementu powiązania zabezpieczeń.  
  
4.  Korzystając z <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> metody rzutowany na typ rzeczywistego. Przykład poniżej rzutowania do <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> typu.  
  
5.  Ustaw <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> właściwość elementu powiązania zabezpieczeń.  
  
6.  Utwórz <xref:System.ServiceModel.ServiceHost> przy użyciu adresu typu i base odpowiednią usługę.  
  
7.  Użyj <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metodę, aby dodać punkt końcowy i obejmują <xref:System.ServiceModel.Channels.CustomBinding>.  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
### <a name="to-set-the-maxclockskew-in-configuration"></a>Aby ustawić MaxClockSkew w konfiguracji  
  
1.  Utwórz [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) w [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) sekcji.  
  
2.  Utwórz [ \<powiązania >](../../../../docs/framework/misc/binding.md) element i ustaw `name` atrybutu odpowiednią wartość. Poniższy przykład ustawia ją na `MaxClockSkewBinding`.  
  
3.  Dodaj element kodowania. W poniższym przykładzie dodaje [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
4.  Dodaj [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element i ustaw `authenticationMode` atrybutu odpowiednie ustawienia. Poniższy przykład ustaw dla atrybutu `Kerberos` do określenia, że usługa używa uwierzytelniania systemu Windows.  
  
5.  Dodaj [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) i ustaw `maxClockSkew` atrybut na wartość w formie `"##:##:##"`. Poniższy przykład ustawia ją na 7 minut. Opcjonalnie dodaj [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) i ustaw `maxClockSkew` atrybutu odpowiednie ustawienia.  
  
6.  Dodaj element transportu. W poniższym przykładzie użyto [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
7.  Dla bezpiecznej konwersacji, ustawienia zabezpieczeń musi być bootstrap w [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) elementu.  
  
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
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
