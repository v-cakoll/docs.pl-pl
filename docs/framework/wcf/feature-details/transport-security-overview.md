---
title: Przegląd zabezpieczeń transportu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00959326-aa9d-44d0-af61-54933d4adc7f
ms.openlocfilehash: ba5f963ebb33da0aaf2c33c776fee7f226e52e85
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742708"
---
# <a name="transport-security-overview"></a>Przegląd zabezpieczeń transportu
Mechanizmy zabezpieczeń transportu w programie Windows Communication Foundation (WCF) zależą od powiązań i używanego transportu. Na przykład podczas korzystania z klasy <xref:System.ServiceModel.WSHttpBinding>, transport to HTTP, a podstawowy mechanizm zabezpieczania transportu jest SSL (SSL) przez protokół HTTP, powszechnie nazywany protokołem HTTPS. W tym temacie omówiono główne mechanizmy zabezpieczeń transportu używane w powiązaniach dostarczonych przez system w systemie WCF.  
  
> [!NOTE]
> Gdy zabezpieczenia SSL są używane z .NET Framework 3,5 i nowsze, klient WCF używa zarówno certyfikatów pośrednich w magazynie certyfikatów, jak i certyfikatów pośrednich odebranych podczas negocjowania protokołu SSL w celu przeprowadzenia walidacji łańcucha certyfikatów w usłudze certyfikatu. .NET Framework 3,0 używa tylko certyfikatów pośrednich zainstalowanych w lokalnym magazynie certyfikatów.  
  
> [!WARNING]
> W przypadku korzystania z zabezpieczeń transportu Właściwość <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> może zostać nadpisywana. Aby temu zapobiec, ustaw <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Description.PrincipalPermissionMode.None?displayProperty=nameWithType>. <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> to zachowanie usługi, które można ustawić w opisie usługi.  
  
## <a name="basichttpbinding"></a>BasicHttpBinding  
 Domyślnie Klasa <xref:System.ServiceModel.BasicHttpBinding> nie zapewnia zabezpieczeń. To powiązanie jest przeznaczone do współdziałania z dostawcami usług sieci Web, które nie implementują zabezpieczeń. Można jednak włączyć zabezpieczenia, ustawiając właściwość <xref:System.ServiceModel.BasicHttpSecurity.Mode%2A> na dowolną wartość z wyjątkiem <xref:System.ServiceModel.BasicHttpSecurityMode.None>. Aby włączyć zabezpieczenia transportu, ustaw właściwość na <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.  
  
### <a name="interoperation-with-iis"></a>Współdziałanie z usługami IIS  
 Klasa <xref:System.ServiceModel.BasicHttpBinding> jest używana głównie do współpracy z istniejącymi usługami sieci Web, a wiele z tych usług jest hostowanych przez Internet Information Services (IIS). W związku z tym zabezpieczenia transportu dla tego powiązania są przeznaczone do bezproblemowego współdziałania z witrynami usług IIS. W tym celu należy ustawić tryb zabezpieczeń na <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> a następnie ustawić typ poświadczeń klienta. Wartości typu poświadczeń odpowiadają funkcjom zabezpieczeń katalogu usług IIS. Poniższy kod przedstawia ustawiony tryb i typ poświadczeń ustawiony na Windows. Tej konfiguracji można użyć, gdy zarówno klient, jak i serwer znajdują się w tej samej domenie systemu Windows.  
  
 [!code-csharp[c_ProgrammingSecurity#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#10)] 
 [!code-vb[c_ProgrammingSecurity#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#10)]  
  
 Lub w obszarze Konfiguracja:  
  
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
  
 W poniższych sekcjach omówiono inne typy poświadczeń klienta.  
  
#### <a name="basic"></a>Podstawowy  
 Odnosi się to do metody uwierzytelniania podstawowego w usługach IIS. W przypadku korzystania z tego trybu serwer IIS musi być skonfigurowany przy użyciu kont użytkowników systemu Windows i odpowiednich uprawnień systemu plików NTFS. Aby uzyskać więcej informacji na temat usług IIS 6,0, zobacz [Włączanie uwierzytelniania podstawowego i Konfigurowanie nazwy obszaru](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc785293(v=ws.10)). Aby uzyskać więcej informacji na temat usług IIS 7,0, zobacz [Konfigurowanie uwierzytelniania podstawowego (IIS 7)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772009(v=ws.10)).  
  
#### <a name="certificate"></a>Certyfikat  
 Usługi IIS mają opcję, aby wymagać od klientów zalogowania się przy użyciu certyfikatu. Ta funkcja umożliwia także programowi IIS Zamapowanie certyfikatu klienta na konto systemu Windows. Aby uzyskać więcej informacji na temat usług IIS 6,0, zobacz [Włączanie certyfikatów klienta w usługach IIS 6,0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc727994(v=ws.10)). Aby uzyskać więcej informacji na temat usług IIS 7,0, zobacz [Konfigurowanie certyfikatów serwera w usługach IIS 7](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).  
  
#### <a name="digest"></a>Szyfrowane  
 Uwierzytelnianie szyfrowane jest podobne do uwierzytelniania podstawowego, ale oferuje zalety wysyłania poświadczeń jako skrótu, a nie zwykłego tekstu. Aby uzyskać więcej informacji na temat usług IIS 6,0, zobacz [uwierzytelnianie szyfrowane w usługach iis 6,0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)). Aby uzyskać więcej informacji na temat usług IIS 7,0, zobacz [Konfigurowanie uwierzytelniania szyfrowanego (IIS 7)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754104(v=ws.10)).  
  
#### <a name="windows"></a>Windows  
 Odnosi się to do zintegrowanego uwierzytelniania systemu Windows w usługach IIS. W przypadku ustawienia tej wartości serwer powinien również istnieć w domenie systemu Windows, która używa protokołu Kerberos jako kontrolera domeny. Jeśli serwer nie znajduje się w domenie z zabezpieczeniami opartymi na protokole Kerberos lub w przypadku awarii systemu Kerberos, można użyć wartości z programu NT LAN Manager (NTLM) opisanej w następnej sekcji. Aby uzyskać więcej informacji na temat usług IIS 6,0, zobacz [zintegrowane uwierzytelnianie systemu Windows w usługach iis 6,0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc738016(v=ws.10)). Aby uzyskać więcej informacji na temat usług IIS 7,0, zobacz [Konfigurowanie certyfikatów serwera w usługach IIS 7](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).
  
#### <a name="ntlm"></a>NTLM  
 Pozwala to serwerowi na uwierzytelnianie przy użyciu protokołu NTLM w przypadku niepowodzenia. Aby uzyskać więcej informacji na temat konfigurowania usług IIS w usługach IIS 6,0, zobacz [Wymuszanie uwierzytelniania NTLM](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc786486(v=ws.10)). W przypadku usług IIS 7,0 uwierzytelnianie systemu Windows obejmuje uwierzytelnianie NTLM. Aby uzyskać więcej informacji, zobacz [Konfigurowanie certyfikatów serwera w usługach IIS 7](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).
  
## <a name="wshttpbinding"></a>WsHttpBinding  
 Klasa <xref:System.ServiceModel.WSHttpBinding> została zaprojektowana na potrzeby współdziałania z usługami, które implementują specyfikacje WS-*. Zabezpieczenia transportu dla tego powiązania są SSL (SSL) za pośrednictwem protokołu HTTP lub HTTPS. Aby utworzyć aplikację WCF, która używa protokołu SSL, Użyj usług IIS do hostowania aplikacji. Alternatywnie, jeśli tworzysz aplikację samoobsługową, użyj narzędzia HttpCfg. exe, aby powiązać certyfikat X. 509 z określonym portem na komputerze. Numer portu jest określony jako część aplikacji WCF jako adres punktu końcowego. W przypadku korzystania z trybu transportu adres punktu końcowego musi zawierać protokół HTTPS lub wyjątek w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [zabezpieczenia transportu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Dla opcji uwierzytelnianie klienta ustaw właściwość <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> klasy <xref:System.ServiceModel.HttpTransportSecurity> na jedną z wartości wyliczenia <xref:System.ServiceModel.HttpClientCredentialType>. Wartości wyliczenia są identyczne z typami poświadczeń klienta dla <xref:System.ServiceModel.BasicHttpBinding> i są przeznaczone do obsługi usług IIS.  
  
 Poniższy przykład pokazuje powiązanie używane z typem poświadczeń klienta systemu Windows.  
  
 [!code-csharp[c_ProgrammingSecurity#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#11)]
 [!code-vb[c_ProgrammingSecurity#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#11)]  
  
## <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 To powiązanie zapewnia tylko zabezpieczenia na poziomie komunikatów, a nie zabezpieczenia na poziomie transportu.  
  
## <a name="nettcpbinding"></a>NetTcpBinding  
 Klasa <xref:System.ServiceModel.NetTcpBinding> używa protokołu TCP do transportu komunikatów. Zabezpieczenia związane z trybem transportu są udostępniane przez implementację Transport Layer Security (TLS) przez TCP. Implementacja protokołu TLS jest dostarczana przez system operacyjny.  
  
 Możesz również określić typ poświadczeń klienta, ustawiając właściwość <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> klasy <xref:System.ServiceModel.TcpTransportSecurity> na jedną z wartości <xref:System.ServiceModel.TcpClientCredentialType>, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[c_ProgrammingSecurity#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#12)]
 [!code-vb[c_ProgrammingSecurity#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#12)]  
  
#### <a name="client"></a>Klient  
 Na kliencie należy określić certyfikat przy użyciu metody <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> klasy <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>.  
  
> [!NOTE]
> Jeśli używasz zabezpieczeń systemu Windows, certyfikat nie jest wymagany.  
  
 Poniższy kod używa odcisku palca certyfikatu, który jednoznacznie identyfikuje go. Aby uzyskać więcej informacji o certyfikatach, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 [!code-csharp[c_ProgrammingSecurity#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#13)]
 [!code-vb[c_ProgrammingSecurity#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#13)]  
  
 Alternatywnie można określić certyfikat w konfiguracji klienta przy użyciu [\<clientcredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu w sekcji Behaviors.  
  
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
 Klasa <xref:System.ServiceModel.NetNamedPipeBinding> została zaprojektowana w celu wydajnej komunikacji między maszynami; oznacza to, że w przypadku procesów uruchomionych na tym samym komputerze, chociaż kanały nazwanego potoku można utworzyć między dwoma komputerami w tej samej sieci. To powiązanie zapewnia tylko zabezpieczenia na poziomie transportu. Podczas tworzenia aplikacji korzystających z tego powiązania adresy punktów końcowych muszą zawierać wartość "net. Pipe" jako protokół adresu punktu końcowego.  
  
## <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 W przypadku korzystania z zabezpieczeń transportu to powiązanie używa protokołu SSL przez protokół HTTP, znanego jako HTTPS z wystawionym tokenem (<xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential>). Aby uzyskać więcej informacji na temat aplikacji federacyjnych, zobacz [federacyjne i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="netpeertcpbinding"></a>NetPeerTcpBinding  
 Klasa <xref:System.ServiceModel.NetPeerTcpBinding> jest bezpiecznym transportem zaprojektowanym do wydajnej komunikacji przy użyciu funkcji sieci równorzędnej. Jak wskazano nazwa klasy i powiązania, TCP to protokół. Gdy tryb zabezpieczeń jest ustawiony na transport, powiązanie implementuje protokół TLS przez TCP. Aby uzyskać więcej informacji na temat funkcji peer-to-peer, zobacz [sieci peer-to-](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)peer.  
  
## <a name="msmqintegrationbinding-and-netmsmqbinding"></a>MsmqIntegrationBinding i Msmqbinding  
 Aby zapoznać się ze wszystkimi zabezpieczeniami transportu za pomocą usługi kolejkowania komunikatów (wcześniej nazywanej MSMQ), zobacz [Zabezpieczanie komunikatów za pomocą zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie zabezpieczeń WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
