---
title: Przegląd zabezpieczeń transportu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00959326-aa9d-44d0-af61-54933d4adc7f
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 9a04b8aaf9c6263a8935099963aaa1dc8d9100fd
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195429"
---
# <a name="transport-security-overview"></a>Przegląd zabezpieczeń transportu
Mechanizmy zabezpieczeń transportu w Windows Communication Foundation (WCF) zależy od tego, powiązania i transport używane. Na przykład w przypadku korzystania z <xref:System.ServiceModel.WSHttpBinding> klasy, transport, jest protokół HTTP i zabezpieczanie transportu przy użyciu podstawowego mechanizmu jest Secure Sockets Layer (SSL) przy użyciu protokołu HTTP, często nazywane protokołu HTTPS. W tym temacie opisano mechanizmy zabezpieczeń transportu głównych używanych w WCF powiązania dostarczane przez system.  
  
> [!NOTE]
>  Stosowania zabezpieczeń SSL za pomocą programu .NET Framework 3.5 lub nowszy klient WCF używa certyfikatów pośrednich w magazynie certyfikatów i certyfikaty pośrednie odebranych podczas negocjacji w protokole SSL do przeprowadzania weryfikacji łańcucha certyfikatu usługi certyfikat. .NET framework 3.0 używa tylko certyfikaty pośrednie zainstalowany w lokalnym magazynie certyfikatów.  
  
> [!WARNING]
>  W przypadku zabezpieczeń transportu <!--zz <xref:System.Treading.Thread.CurrentPrincipal%2A> --> `CurrentPrincipal` właściwości mogą zostać nadpisane. Aby zapobiec tego zestawu występuje <!--zz <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermission%2A> --> `PrincipalPermission` None. <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> to zachowanie usługi, które mogą zostać ustawione na opisu usługi.  
  
## <a name="basichttpbinding"></a>BasicHttpBinding  
 Domyślnie <xref:System.ServiceModel.BasicHttpBinding> klasa nie zapewnia zabezpieczeń. To powiązanie jest współdziałania w ramach zaprojektowana pod kątem dostawcy usług sieci Web, które nie implementują zabezpieczeń. Jednakże, możesz włączyć zabezpieczeń przez ustawienie <xref:System.ServiceModel.BasicHttpSecurity.Mode%2A> właściwość do dowolnej wartości za wyjątkiem <xref:System.ServiceModel.BasicHttpSecurityMode.None>. Aby włączyć zabezpieczenia transportu, ustaw właściwość na <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.  
  
### <a name="interoperation-with-iis"></a>Współdziałanie z usługami IIS  
 <xref:System.ServiceModel.BasicHttpBinding> Klasy jest używany głównie pod kątem współdziałania z istniejących usług sieci Web i znajdują się wiele z tych usług Internet Information Services (IIS). W związku z tym zabezpieczenia transportu dla tego powiązania jest przeznaczona dla bezproblemowe współdziałanie z witryny usług IIS. Jest to realizowane przez ustawianie trybu zabezpieczeń <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> , a następnie ustawiając typu poświadczeń klienta. Wartości typu poświadczeń odpowiadają mechanizmów zabezpieczeń katalogu usług IIS. Poniższy kod przedstawia sposób ustawiania, i Ustaw typ poświadczeń Windows. Jeśli klienta i serwera znajdują się w tej samej domenie Windows, można użyć tej konfiguracji.  
  
 [!code-csharp[c_ProgrammingSecurity#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#10)] 
 [!code-vb[c_ProgrammingSecurity#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#10)]  
  
 Lub w konfiguracji:  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <binding name="SecurityByTransport">  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" />  
       </security>  
     </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 W poniższych sekcjach omówiono innego typu poświadczeń klienta.  
  
#### <a name="basic"></a>Podstawowy  
 Odpowiada to podstawowa metoda uwierzytelniania w usługach IIS. Podczas korzystania z tego trybu serwera IIS muszą być skonfigurowane przy użyciu Windows kont użytkowników i odpowiednie uprawnienia systemu plików NTFS. Aby uzyskać więcej informacji na temat [!INCLUDE[iis601](../../../../includes/iis601-md.md)], zobacz [umożliwiające uwierzytelnianie podstawowe i konfigurowanie nazwy obszaru](https://go.microsoft.com/fwlink/?LinkId=88592). Aby uzyskać więcej informacji na temat [!INCLUDE[iisver](../../../../includes/iisver-md.md)], zobacz [IIS 7.0 Beta: Konfigurowanie uwierzytelniania podstawowego](https://go.microsoft.com/fwlink/?LinkId=88593).  
  
#### <a name="certificate"></a>Certyfikat  
 Usługi IIS zawiera opcję, aby wymagać od klientów, zaloguj się przy użyciu certyfikatu. Ta funkcja umożliwia także usługi IIS do mapowania certyfikatu klienta na konto Windows. Aby uzyskać więcej informacji na temat [!INCLUDE[iis601](../../../../includes/iis601-md.md)], zobacz [Włączanie certyfikatów klientów w usługach IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88594). Aby uzyskać więcej informacji na temat [!INCLUDE[iisver](../../../../includes/iisver-md.md)], zobacz [IIS 7.0 Beta: Konfigurowanie certyfikatów serwera w usługach IIS 7.0](https://go.microsoft.com/fwlink/?LinkId=88595).  
  
#### <a name="digest"></a>Podsumowanie  
 Uwierzytelnianie szyfrowane jest podobny do uwierzytelniania podstawowego, ale daje możliwość wysyłania poświadczeń jako skrót, a nie w postaci zwykłego tekstu. Aby uzyskać więcej informacji na temat [!INCLUDE[iis601](../../../../includes/iis601-md.md)], zobacz [uwierzytelnianie szyfrowane w usługach IIS 6.0](https://go.microsoft.com/fwlink/?LinkID=88443). Aby uzyskać więcej informacji na temat [!INCLUDE[iisver](../../../../includes/iisver-md.md)], zobacz [IIS 7.0 Beta: Konfigurowanie uwierzytelniania szyfrowanego](https://go.microsoft.com/fwlink/?LinkId=88596).  
  
#### <a name="windows"></a>Windows  
 Odpowiada to zintegrowane uwierzytelnianie Windows w usługach IIS. Po ustawieniu tej wartości, serwer również powinien istnieć w domenie Windows, która używa protokołu Kerberos w jako kontrolera domeny. Jeśli serwer nie znajduje się w domenie z kopią zapasową protokołu Kerberos, czy system protokołu Kerberos nie powiedzie się, można użyć wartości NT LAN Manager (NTLM) opisano w następnej sekcji. Aby uzyskać więcej informacji na temat [!INCLUDE[iis601](../../../../includes/iis601-md.md)], zobacz [zintegrowane uwierzytelnianie Windows w usługach IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88597). Aby uzyskać więcej informacji na temat [!INCLUDE[iisver](../../../../includes/iisver-md.md)], zobacz [IIS 7.0 Beta: Konfigurowanie certyfikatów serwera w usługach IIS 7.0](https://go.microsoft.com/fwlink/?LinkId=88595).  
  
#### <a name="ntlm"></a>NTLM  
 Dzięki temu serwerowi używany do uwierzytelniania NTLM, jeśli protokół Kerberos nie powiedzie się. Aby uzyskać więcej informacji na temat konfigurowania programu IIS w [!INCLUDE[iis601](../../../../includes/iis601-md.md)], zobacz [wymuszenie uwierzytelniania NTLM](https://go.microsoft.com/fwlink/?LinkId=88598). Aby uzyskać [!INCLUDE[iisver](../../../../includes/iisver-md.md)], uwierzytelnianie Windows obejmuje uwierzytelniania NTLM. Aby uzyskać więcej informacji, zobacz [IIS 7.0 Beta: Konfigurowanie certyfikatów serwera w usługach IIS 7.0](https://go.microsoft.com/fwlink/?LinkID=88595).  
  
## <a name="wshttpbinding"></a>WsHttpBinding  
 <xref:System.ServiceModel.WSHttpBinding> Klasa jest przeznaczona dla współdziałanie z usługami, które implementują WS-* specyfikacji. Zabezpieczenia transportu dla tego powiązania jest Secure Sockets Layer (SSL) za pośrednictwem protokołu HTTP lub HTTPS. Aby utworzyć aplikację WCF, która używa protokołu SSL, należy użyć usług IIS do hostowania aplikacji. Można również w przypadku tworzenia własnego aplikacji, należy użyć narzędzia HttpCfg.exe powiązać certyfikat X.509 z określonego portu, na komputerze. Numer portu jest określony jako część aplikacji WCF jako adresu punktu końcowego. Podczas korzystania z trybu transportu adres punktu końcowego musi zawierać nazwę protokołu HTTPS lub zostanie zgłoszony wyjątek w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [zabezpieczenia transportu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Uwierzytelnianie klienta, można ustawić <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> właściwość <xref:System.ServiceModel.HttpTransportSecurity> klasy do jednego z <xref:System.ServiceModel.HttpClientCredentialType> wartości wyliczenia. Wartości wyliczenia są takie same jak typy poświadczeń klienta dla <xref:System.ServiceModel.BasicHttpBinding> i mają być obsługiwana za pomocą usług IIS.  
  
 Wiązanie używane z typu poświadczeń klienta systemu Windows można znaleźć w poniższym przykładzie.  
  
 [!code-csharp[c_ProgrammingSecurity#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#11)]
 [!code-vb[c_ProgrammingSecurity#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#11)]  
  
## <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 To powiązanie zapewnia tylko wiadomości na poziomie zabezpieczeń, nie transportu do poziomu zabezpieczeń.  
  
## <a name="nettcpbinding"></a>NetTcpBinding  
 <xref:System.ServiceModel.NetTcpBinding> Klasa używa protokołu TCP dla transportu wiadomości. Dla trybu transportu zabezpieczenia dzięki wdrożeniu zabezpieczeń TLS (Transport Layer) za pośrednictwem protokołu TCP. Implementacja protokołu TLS są udostępniane przez system operacyjny.  
  
 Typ poświadczeń klienta można również określić, ustawiając <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> właściwość <xref:System.ServiceModel.TcpTransportSecurity> klasy do jednego z <xref:System.ServiceModel.TcpClientCredentialType> wartości, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[c_ProgrammingSecurity#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#12)]
 [!code-vb[c_ProgrammingSecurity#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#12)]  
  
#### <a name="client"></a>Klient  
 Na komputerze klienckim, należy określić certyfikatu za pomocą <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> klasy.  
  
> [!NOTE]
>  Jeśli używasz zabezpieczeń Windows certyfikat nie jest wymagane.  
  
 W poniższym kodzie użyto odcisk palca certyfikatu, który unikatowo identyfikuje go. Aby uzyskać więcej informacji na temat certyfikatów, zobacz [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 [!code-csharp[c_ProgrammingSecurity#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#13)]
 [!code-vb[c_ProgrammingSecurity#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#13)]  
  
 Alternatywnie, Określ certyfikat w konfiguracji klienta przy użyciu [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element w sekcji zachowania.  
  
```xml  
<behaviors>  
  <behavior>  
   <clientCredentials>  
     <clientCertificate findValue= "101010101010101010101010101010000000000"   
      storeLocation="LocalMachine" storeName="My"   
      X509FindType="FindByThumbPrint"/>  
     </clientCertificate>  
   </clientCredentials>  
 </behavior>  
</behaviors>    
```  
  
## <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 <xref:System.ServiceModel.NetNamedPipeBinding> Klasa jest przeznaczona dla efektywnego należącymi do tej komunikacji; oznacza to, że dla procesy uruchomione na tym samym komputerze, mimo że kanały nazwanego potoku można tworzyć między dwoma komputerami w tej samej sieci. To powiązanie zawiera tylko zabezpieczenia na poziomie transportu. Podczas tworzenia aplikacji za pomocą tego powiązania, adresy punktów końcowych musi zawierać "net.pipe" jako protokół adresu punktu końcowego.  
  
## <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 Korzystając z zabezpieczeń transportu, używa tego powiązania SSL za pośrednictwem protokołu HTTP, znane jako protokołu HTTPS z wystawiony token (<xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential>). Aby uzyskać więcej informacji na temat aplikacji federacyjnych zobacz [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="netpeertcpbinding"></a>NetPeerTcpBinding  
 <xref:System.ServiceModel.NetPeerTcpBinding> Klasa jest bezpiecznym transportem, który jest przeznaczony dla skutecznej komunikacji przy użyciu funkcji sieci peer-to-peer. Wskazane przez nazwę klasy i powiązanie TCP jest protokół. Gdy tryb zabezpieczeń Transport powiązanie implementuje protokołu TLS za pośrednictwem protokołu TCP. Aby uzyskać więcej informacji na temat funkcji peer-to-peer, zobacz [sieci Peer-to-Peer](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="msmqintegrationbinding-and-netmsmqbinding"></a>MsmqIntegrationBinding i NetMsmqBinding  
 Wyczerpujące omówienie transportu zabezpieczeń za pomocą usługi kolejkowania komunikatów (nazywanymi wcześniej MSMQ), zobacz [Zabezpieczanie komunikatów za pomocą zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie zabezpieczeń WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
