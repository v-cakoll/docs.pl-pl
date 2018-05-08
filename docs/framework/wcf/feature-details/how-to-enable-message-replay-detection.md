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
ms.openlocfilehash: 5c761a23d2560f40a0121d684dcb411a716de5a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-message-replay-detection"></a>Instrukcje: Włączanie wykrywania powtarzania komunikatu
Atak powtarzania występuje, gdy osoba atakująca kopiuje strumienia komunikatów między dwiema stronami i odtwarzaniem strumienia do jednego lub więcej stron. O ile skorygowane, komputery mogą ulec ataku zostaną przetworzone strumienia jako istotnych wiadomości, co w zakresie zły konsekwencje, takie jak nadmiarowe zamówień elementu.  
  
 Aby uzyskać więcej informacji na temat wykrywania powtarzania komunikatu, zobacz [wykrywania powtarzania komunikatu](http://go.microsoft.com/fwlink/?LinkId=88536).  
  
 W poniższej procedurze przedstawiono różne właściwości, których można kontrolować za pomocą usługi Windows Communication Foundation (WCF) wykrywania powtarzania.  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a>Aby kontrolować wykrywania powtórzeń na kliencie przy użyciu kodu  
  
1.  Utwórz <xref:System.ServiceModel.Channels.SecurityBindingElement> do użycia w <xref:System.ServiceModel.Channels.CustomBinding>. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). W poniższym przykładzie użyto <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> utworzone za pomocą <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> z <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy.  
  
2.  Użyj <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> zwraca odwołanie do właściwości <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> klasy i ustaw dowolne z poniższych właściwości, zależnie od potrzeb:  
  
    1.  `DetectReplay`. Wartość logiczna. Decyduje to, czy klient powinien wykryć odtworzenie z serwera. Wartość domyślna to `true`.  
  
    2.  `MaxClockSkew`. A <xref:System.TimeSpan> wartość. Kontroluje ilość czasu zegara, mechanizmu powtarzania może tolerować między klientem a serwerem. Mechanizm zabezpieczeń sprawdza, czy czas sygnatury wysyłane i określa, czy została ona wysłana zbyt daleko w przeszłości. Wartość domyślna to 5 minut.  
  
    3.  `ReplayWindow`. A `TimeSpan` wartość. Kontroluje to czas przechowywania wiadomości może współdziałać w sieci po serwer wysyła on (za pośrednictwem pośredników) przed osiągnięciem klienta. Klient śledzi podpisy wiadomości wysłane w najnowszej `ReplayWindow` na potrzeby wykrywania powtarzania.  
  
    4.  `ReplayCacheSize`. Wartość całkowita. Klient przechowuje podpisy wiadomości w pamięci podręcznej. To ustawienie określa, ile podpisów mogą być przechowywane w pamięci podręcznej. Jeśli liczbę komunikatów wysłanych w oknie powtarzania ostatniego osiągnie limit pamięci podręcznej, nowe komunikaty są odrzucane, dopóki najstarsze podpisów buforowane osiągnięcia limitu czasu. Wartość domyślna wynosi 500 000.  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a>Aby kontrolować wykrywania powtórzeń w usłudze przy użyciu kodu  
  
1.  Utwórz <xref:System.ServiceModel.Channels.SecurityBindingElement> do użycia w <xref:System.ServiceModel.Channels.CustomBinding>.  
  
2.  Użyj <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> zwraca odwołanie do właściwości <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> klasy, a następnie ustaw właściwości opisanych powyżej.  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a>Aby kontrolować wykrywania powtórzeń w konfiguracji dla klienta lub usługi  
  
1.  Utwórz [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
2.  Utwórz `<security>` elementu.  
  
3.  Utwórz [ \<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) lub [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).  
  
4.  Ustaw następujące wartości atrybutów odpowiednio: `detectReplays`, `maxClockSkew`, `replayWindow`, i `replayCacheSize`. W poniższym przykładzie ustawiono oba atrybuty `<localServiceSettings>` i `<localClientSettings>` elementu:  
  
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
 Poniższy przykład tworzy <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> przy użyciu <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> — metoda i ustawia właściwości powtarzania powiązania.  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a>Zakres powtarzania: zabezpieczenia wiadomości tylko  
 Należy pamiętać, że poniższe procedury dotyczą tylko tryb zabezpieczeń wiadomości. Dla transportu i transportu z poświadczeniami komunikatu trybami mechanizmów transportu wykryć odtworzenie.  
  
## <a name="secure-conversation-notes"></a>Zabezpieczanie konwersacji uwagi  
 Dla powiązania, które umożliwiają bezpiecznych konwersacji można dostosować te ustawienia, zarówno dla kanału aplikacji, a także ładowania początkowego powiązania bezpiecznej konwersacji. Na przykład można wyłączyć odtworzenie dla kanału aplikacji, ale włączyć je do ładowania początkowego kanału, który określa bezpiecznej konwersacji.  
  
 Jeśli nie używasz sesji bezpiecznej konwersacji, wykrywania powtórzeń nie gwarantuje wykrywania odtworzenie w scenariusze farmy serwera i gdy proces zostanie odtworzony. Dotyczy to następujących powiązania dostarczane przez system:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>.  
  
-   <xref:System.ServiceModel.WSHttpBinding> z <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> ustawioną właściwość `false`.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Następujących przestrzeni nazw są wymagane, aby skompilować kod:  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [Bezpieczne konwersacje i bezpieczne sesje](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)  
 [\<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)  
 [Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
