---
title: 'Instrukcje: włączanie wykrywania powtarzania komunikatu'
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
ms.openlocfilehash: 3fe43e3f815e0f918e22a1ec0fd485079afadde8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156029"
---
# <a name="how-to-enable-message-replay-detection"></a>Instrukcje: włączanie wykrywania powtarzania komunikatu
Atak przez powtarzanie występuje, gdy osoba atakująca kopiuje strumienia komunikatów między dwiema stronami i odtwarza strumienia do jednego lub więcej stron. Chyba że skorygowane, komputery, które podlegają ataku przetworzy strumienia jako wiarygodnego wiadomości, co w zakresie zły konsekwencje, takie jak nadmiarowe zamówienia elementu.  
  
 Aby uzyskać więcej informacji na temat wykrywania powtarzania komunikatu zobacz [wykrywania powtarzania komunikatu](https://go.microsoft.com/fwlink/?LinkId=88536).  
  
 Poniższa procedura demonstruje różne właściwości, które służą do kontrolowania wykrywania powtarzania przy użyciu usługi Windows Communication Foundation (WCF).  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a>Aby kontrolować wykrywania powtarzania na kliencie przy użyciu kodu  
  
1.  Tworzenie <xref:System.ServiceModel.Channels.SecurityBindingElement> do użycia w <xref:System.ServiceModel.Channels.CustomBinding>. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). W poniższym przykładzie użyto <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> utworzone za pomocą <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> z <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy.  
  
2.  Użyj <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> właściwość, aby zwrócić odwołanie do <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> klasy i skonfiguruj następujące właściwości zgodnie z potrzebami:  
  
    1.  `DetectReplay`. Wartość logiczna. To decyduje, czy klient powinien wykryć odtworzenie z serwera. Wartość domyślna to `true`.  
  
    2.  `MaxClockSkew`. A <xref:System.TimeSpan> wartość. Określa, ile czasu przesunięcia czasowego, mechanizm powtórzeń może tolerować między klientem a serwerem. Mechanizm zabezpieczeń sprawdza, czy czas sygnaturę wysyłane i określa, czy wysłano zbyt daleko w przeszłości. Wartość domyślna to 5 minut.  
  
    3.  `ReplayWindow`. A `TimeSpan` wartość. To decyduje, jak długo komunikat może na żywo w sieci po serwer wysyła on (za pośrednictwem pośredników) przed dotarciem do klienta. Klient śledzi podpisy komunikaty wysyłane w ramach najnowsze `ReplayWindow` na potrzeby wykrywania powtarzania.  
  
    4.  `ReplayCacheSize`. Wartość całkowitą. Klient przechowuje podpisów wiadomości w pamięci podręcznej. To ustawienie określa, ile podpisów, które mogą być przechowywane w pamięci podręcznej. Jeśli liczba wiadomości wysyłanych w ramach ostatniego okna powtarzania osiągnie limit pamięci podręcznej, nowe wiadomości są odrzucane, najstarsze podpisów pamięci podręcznej aż limitu czasu. Wartość domyślna wynosi 500 000.  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a>Aby kontrolować wykrywania powtarzania w usłudze przy użyciu kodu  
  
1.  Tworzenie <xref:System.ServiceModel.Channels.SecurityBindingElement> do użycia w <xref:System.ServiceModel.Channels.CustomBinding>.  
  
2.  Użyj <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> właściwość, aby zwrócić odwołanie do <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> klasy, a następnie ustaw właściwości, zgodnie z wcześniejszym opisem.  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a>Aby kontrolować wykrywania powtarzania w konfiguracji dla klienta lub usługę  
  
1.  Tworzenie [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
2.  Utwórz `<security>` elementu.  
  
3.  Tworzenie [ \<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) lub [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).  
  
4.  Ustaw następujące wartości atrybutów zgodnie z potrzebami: `detectReplays`, `maxClockSkew`, `replayWindow`, i `replayCacheSize`. W poniższym przykładzie ustawiono oba atrybuty `<localServiceSettings>` i `<localClientSettings>` elementu:  
  
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
 Poniższy przykład tworzy <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> przy użyciu <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> metody i zestawy właściwości powtarzania wiązania.  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a>Zakres powtarzania: Tylko zabezpieczeń komunikatów  
 Należy pamiętać, że poniższe procedury dotyczą tylko trybu zabezpieczenia wiadomości. Transport i Transport z poświadczeniami komunikatu tryby mechanizmy transportu wykryć odtworzenie.  
  
## <a name="secure-conversation-notes"></a>Zabezpieczanie uwagi konwersacji  
 Dla powiązania, które umożliwiają bezpieczne konwersacje można dostosować te ustawienia, zarówno dla kanału aplikacji, a także dla powiązania uruchamiania bezpiecznej konwersacji. Na przykład możesz wyłączyć odtworzenie dla kanału aplikacji, ale włączyć je do ładowania początkowego kanału, który ustanawia bezpiecznej konwersacji.  
  
 Jeśli nie używasz sesji bezpiecznej konwersacji, wykrywania powtarzania nie gwarantuje wykrywania odtworzenie w scenariuszach z farmami serwera i po ten proces zostanie odtworzony. Dotyczy to następujących powiązania dostarczane przez system:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>.  
  
-   <xref:System.ServiceModel.WSHttpBinding> za pomocą <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> właściwością `false`.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Następujące przestrzenie nazw są wymagane, aby skompilować kod:  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [Bezpieczne konwersacje i bezpieczne sesje](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)
- [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)
- [Instrukcje: tworzenie niestandardowego wiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
