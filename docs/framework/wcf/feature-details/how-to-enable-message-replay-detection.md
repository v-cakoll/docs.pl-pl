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
ms.openlocfilehash: 450a99fc6604ccb3fa796e8a73e1ddc3e3adff9e
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964661"
---
# <a name="how-to-enable-message-replay-detection"></a>Instrukcje: Włączanie wykrywania powtarzania komunikatu
Ataku powtarzania występuje, gdy osoba atakująca kopiuje strumień komunikatów między dwiema stronami i odtwarza strumień do co najmniej jednej ze stron. O ile nie zostanie to skorygowane, komputery, które podlegają atakom, przetworzyją strumień jako wiarygodne komunikaty, co skutkuje zakresem nieprawidłowych skutków, takich jak nadmiarowe zamówienia elementu.  
  
 Aby uzyskać więcej informacji na temat wykrywania powtarzania wiadomości, zobacz [wykrywanie powtarzania komunikatów](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).  
  
 Poniższa procedura przedstawia różne właściwości, których można użyć do kontrolowania wykrywania powtarzania przy użyciu Windows Communication Foundation (WCF).  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a>Aby kontrolować wykrywanie powtarzania na kliencie przy użyciu kodu  
  
1. Utwórz <xref:System.ServiceModel.Channels.SecurityBindingElement> do użycia w <xref:System.ServiceModel.Channels.CustomBinding>. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). Poniższy przykład używa <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> utworzonego za pomocą <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> klasy <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
2. Użyj właściwości <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>, aby zwrócić odwołanie do klasy <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> i ustawić dowolne z następujących właściwości, zgodnie z potrzebami:  
  
    1. `DetectReplay`. Wartość logiczna. Reguluje to, czy klient powinien wykryć odtwarzanie z serwera. Wartość domyślna to `true`.  
  
    2. `MaxClockSkew`. Wartość <xref:System.TimeSpan>. Decyduje o tym, ile czasu może odchylać mechanizm powtarzania między klientem a serwerem. Mechanizm zabezpieczeń sprawdza, czy sygnatura czasowa jest wysyłana, i określa, czy wysłano ją zbyt długo w przeszłości. Wartość domyślna to 5 minut.  
  
    3. `ReplayWindow`. Wartość `TimeSpan`. Reguluje to, jak długo komunikat może być aktywny w sieci po wysłaniu go przez serwer (za pośrednictwem pośredników) przed osiągnięciem klienta. Klient śledzi sygnatury komunikatów wysyłanych w ciągu najnowszych `ReplayWindow` na potrzeby wykrywania powtarzania.  
  
    4. `ReplayCacheSize`. Wartość całkowita. Klient przechowuje podpisy wiadomości w pamięci podręcznej. To ustawienie określa, ile sygnatur może być przechowywanych w pamięci podręcznej. Jeśli liczba komunikatów wysłanych w ramach ostatniego okna powtarzania osiągnie limit pamięci podręcznej, nowe komunikaty są odrzucane do momentu osiągnięcia limitu czasu dla najstarszych podpisów w pamięci podręcznej. Wartość domyślna to 500000.  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a>Aby kontrolować wykrywanie powtarzania w usłudze przy użyciu kodu  
  
1. Utwórz <xref:System.ServiceModel.Channels.SecurityBindingElement> do użycia w <xref:System.ServiceModel.Channels.CustomBinding>.  
  
2. Użyj właściwości <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>, aby zwrócić odwołanie do klasy <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> i ustawić właściwości zgodnie z opisem wcześniej.  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a>Aby kontrolować wykrywanie powtarzania w konfiguracji dla klienta lub usługi  
  
1. Utwórz [\<niestandardowebinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
2. Utwórz element `<security>`.  
  
3. Utwórz [\<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) lub [\<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).  
  
4. Ustaw następujące wartości atrybutów, zgodnie z potrzebami: `detectReplays`, `maxClockSkew`, `replayWindow`i `replayCacheSize`. Poniższy przykład ustawia atrybuty elementu `<localServiceSettings>` i `<localClientSettings>`:  
  
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
 Poniższy przykład tworzy <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> przy użyciu metody <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> i ustawia właściwości powtarzania powiązania.  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a>Zakres powtarzania: tylko zabezpieczenia wiadomości  
 Należy zauważyć, że poniższe procedury dotyczą tylko trybu zabezpieczeń wiadomości. W przypadku transportu i transportu z trybami poświadczeń wiadomości mechanizmy transportu wykrywają odtwarzanie.  
  
## <a name="secure-conversation-notes"></a>Uwagi dotyczące bezpiecznej konwersacji  
 W przypadku powiązań umożliwiających bezpieczne konwersacje można dostosować te ustawienia zarówno dla kanału aplikacji, jak i dla powiązania inicjowania bezpiecznego konwersacji. Można na przykład wyłączyć odtwarzanie dla kanału aplikacji, ale włączyć je dla kanału ładowania początkowego, który nawiązuje bezpieczną konwersację.  
  
 Jeśli nie używasz sesji bezpiecznych konwersacji, wykrywanie powtarzania nie gwarantuje wykrywania operacji odtwarzania w scenariuszach farmy serwerów i podczas odtwarzania procesu. Dotyczy to następujących powiązań dostarczonych przez system:  
  
- <xref:System.ServiceModel.BasicHttpBinding>.  
  
- <xref:System.ServiceModel.WSHttpBinding> z właściwością <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> ustawioną na `false`.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Do skompilowania kodu wymagane są następujące przestrzenie nazw:  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [Bezpieczne konwersacje i bezpieczne sesje](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)
- [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)
- [Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
