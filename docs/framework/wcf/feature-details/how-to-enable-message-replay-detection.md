---
title: 'Instrukcje: Włączanie wykrywania powtarzania komunikatu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF security
- replay detection [WCF]
- WCF, custom bindings
- WCF, security
ms.assetid: 8b847e91-69a3-49e1-9e5f-0c455e50d804
ms.openlocfilehash: 05bcddabf625e478616cce39f08b0ff8af282716
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184951"
---
# <a name="how-to-enable-message-replay-detection"></a>Instrukcje: Włączanie wykrywania powtarzania komunikatu
Atak powtarzania występuje, gdy osoba atakująca kopiuje strumień wiadomości między dwiema stronami i odtwarza strumień do jednej lub więcej stron. O ile nie zostanie złagodzone, komputery podlegające atakowi będą przetwarzać strumień jako prawidłowe wiadomości, co spowoduje szereg złych konsekwencji, takich jak zbędne zamówienia elementu.  
  
 Aby uzyskać więcej informacji na temat wykrywania powtarzania [komunikatów, zobacz Wykrywanie odtwolień komunikatów](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).  
  
 Poniższa procedura pokazuje różne właściwości, których można użyć do kontrolowania wykrywania powtarzania przy użyciu programu Windows Communication Foundation (WCF).  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a>Aby kontrolować wykrywanie powtórzeń na kliencie przy użyciu kodu  
  
1. Utwórz <xref:System.ServiceModel.Channels.SecurityBindingElement> a do <xref:System.ServiceModel.Channels.CustomBinding>użycia w pliku . Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). W poniższym przykładzie <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> użyto utworzonego <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> z <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy.  
  
2. Użyj <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> właściwości, aby zwrócić <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> odwołanie do klasy i ustawić dowolną z następujących właściwości, odpowiednio:  
  
    1. `DetectReplay`. Wartość logiczna. Określa, czy klient powinien wykryć powtórki z serwera. Wartość domyślna to `true`.  
  
    2. `MaxClockSkew`. Wartość. <xref:System.TimeSpan> Określa, ile czasu pochylić mechanizm powtarzania może tolerować między klientem a serwerem. Mechanizm zabezpieczeń sprawdza sygnaturę czasową wysłano i określa, czy został wysłany zbyt daleko wstecz w przeszłości. Wartość domyślna to 5 minut.  
  
    3. `ReplayWindow`. Wartość. `TimeSpan` Określa to, jak długo wiadomość może być owakowany w sieci po wysłaniu jej przez serwer (za pośrednictwem pośredników) przed dotarciem do klienta. Klient śledzi podpisy wiadomości wysłanych w `ReplayWindow` ciągu najnowszych do celów wykrywania powtórzeń.  
  
    4. `ReplayCacheSize`. Wartość całkowita. Klient przechowuje podpisy wiadomości w pamięci podręcznej. To ustawienie określa, ile podpisów może przechowywać pamięć podręczna. Jeśli liczba wiadomości wysłanych w ostatnim oknie powtarzania osiągnie limit pamięci podręcznej, nowe wiadomości są odrzucane, dopóki najstarsze buforowane podpisy nie osiągną limitu czasu. Wartość domyślna to 500000.  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a>Aby kontrolować wykrywanie powtórzeń w usłudze przy użyciu kodu  
  
1. Utwórz <xref:System.ServiceModel.Channels.SecurityBindingElement> a do <xref:System.ServiceModel.Channels.CustomBinding>użycia w pliku .  
  
2. Użyj <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> właściwości, aby zwrócić <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> odwołanie do klasy i ustawić właściwości, jak opisano wcześniej.  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a>Aby kontrolować wykrywanie powtarzania w konfiguracji dla klienta lub usługi  
  
1. Utwórz [ \<>niestandardowego. ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
  
2. Utwórz `<security>` element.  
  
3. Utwórz [ \<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) lub [ \<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).  
  
4. Ustaw następujące wartości atrybutów, `detectReplays`odpowiednio: `replayWindow`, `replayCacheSize` `maxClockSkew`, , i . Poniższy przykład ustawia atrybuty `<localServiceSettings>` zarówno `<localClientSettings>` a, jak i elementu:  
  
    ```xml  
    <customBinding>  
      <binding name="NewBinding0">  
       <textMessageEncoding />  
        <security>  
         <localClientSettings
          replayCacheSize="800000"
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
         <localServiceSettings
          replayCacheSize="800000"
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
        <secureConversationBootstrap />  
       </security>  
      <httpTransport />  
     </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> tworzy <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> przy użyciu metody i ustawia właściwości powtarzania powiązania.  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a>Zakres powtórki: tylko zabezpieczenia wiadomości  
 Należy zauważyć, że poniższe procedury dotyczą tylko trybu zabezpieczeń wiadomości. W przypadku transportu i transportu z trybami poświadczeń wiadomości mechanizmy transportu wykrywają powtórki.  
  
## <a name="secure-conversation-notes"></a>Bezpieczne notatki do konwersacji  
 W przypadku powiązań, które umożliwiają bezpieczne konwersacje, można dostosować te ustawienia zarówno dla kanału aplikacji, jak i dla powiązania boottrap bezpiecznej konwersacji. Na przykład można wyłączyć powtórki dla kanału aplikacji, ale włączyć je dla kanału bootstrap, który ustanawia bezpieczną konwersację.  
  
 Jeśli nie używasz bezpiecznych sesji konwersacji, wykrywanie powtarzania nie gwarantuje wykrywania powtórek w scenariuszach farmy serwerów i po odtwoniu procesu. Dotyczy to następujących powiązań dostarczonych przez system:  
  
- <xref:System.ServiceModel.BasicHttpBinding>.  
  
- <xref:System.ServiceModel.WSHttpBinding>z <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> właściwością `false`ustawioną na .  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Następujące obszary nazw są wymagane do skompilowania kodu:  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [Bezpieczne konwersacje i bezpieczne sesje](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)
- [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)
- [Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
