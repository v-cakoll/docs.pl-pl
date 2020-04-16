---
title: Przegląd zabezpieczeń transportu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00959326-aa9d-44d0-af61-54933d4adc7f
ms.openlocfilehash: 6796ca0b16e65a07735aec075d63b0cdfe38d080
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464013"
---
# <a name="transport-security-overview"></a>Przegląd zabezpieczeń transportu
Mechanizmy zabezpieczeń transportu w Programie Komunikacji systemu Windows (WCF) zależą od używanego powiązania i transportu. Na przykład podczas <xref:System.ServiceModel.WSHttpBinding> korzystania z klasy transport jest HTTP, a podstawowym mechanizmem zabezpieczania transportu jest secure Sockets Layer (SSL) za pośrednictwem protokołu HTTP, powszechnie nazywany HTTPS. W tym temacie omówiono główne mechanizmy zabezpieczeń transportu używane w powiązaniach dostarczonych przez system WCF.  
  
> [!NOTE]
> Gdy zabezpieczenia SSL są używane z programem .NET Framework 3.5, a później klient WCF używa zarówno certyfikatów pośrednich w magazynie certyfikatów, jak i certyfikatów pośrednich otrzymanych podczas negocjacji SSL w celu przeprowadzenia sprawdzania poprawności łańcucha certyfikatów na certyfikacie usługi. Program .NET Framework 3.0 używa tylko certyfikatów pośrednich zainstalowanych w lokalnym magazynie certyfikatów.  
  
> [!WARNING]
> W przypadku użycia zabezpieczeń <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> transportu właściwość może zostać zastąpiona. Aby temu zapobiec, <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A?displayProperty=nameWithType> ustaw <xref:System.ServiceModel.Description.PrincipalPermissionMode.None?displayProperty=nameWithType>na . <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>jest zachowaniem usługi, które można ustawić w opisie usługi.  
  
## <a name="basichttpbinding"></a>PodstawowehttpBinding  
 Domyślnie <xref:System.ServiceModel.BasicHttpBinding> klasa nie zapewnia zabezpieczeń. To powiązanie jest przeznaczone do współdziałania z dostawcami usług sieci Web, którzy nie implementują zabezpieczeń. Można jednak włączyć zabezpieczenia, ustawiając <xref:System.ServiceModel.BasicHttpSecurity.Mode%2A> właściwość <xref:System.ServiceModel.BasicHttpSecurityMode.None>na dowolną wartość z wyjątkiem . Aby włączyć bezpieczeństwo transportu, <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>ustaw właściwość na .  
  
### <a name="interoperation-with-iis"></a>Współpraca z iis  
 Klasa <xref:System.ServiceModel.BasicHttpBinding> jest używana głównie do współpracy z istniejącymi usługami sieci Web, a wiele z tych usług jest obsługiwanych przez internetowe usługi informacyjne (IIS). W związku z tym zabezpieczenia transportu dla tego powiązania jest przeznaczony do bezproblemowej współpracy z iis lokacji. Odbywa się to przez ustawienie <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> trybu zabezpieczeń, a następnie ustawienie typu poświadczeń klienta. Wartości typu poświadczeń odpowiadają mechanizmom zabezpieczeń katalogu IIS. Poniższy kod przedstawia ustawiony tryb i typ poświadczeń ustawiony na Windows. Tej konfiguracji można użyć, gdy zarówno klient, jak i serwer znajdują się w tej samej domenie systemu Windows.  
  
 [!code-csharp[c_ProgrammingSecurity#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#10)]
 [!code-vb[c_ProgrammingSecurity#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#10)]  
  
 Lub, w konfiguracji:  
  
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
 Odpowiada to metodzie uwierzytelniania podstawowego w uzywaczu IIS. W tym trybie serwer usług IIS musi być skonfigurowany z kontami użytkowników systemu Windows i odpowiednimi uprawnieniami systemu plików NTFS. Aby uzyskać więcej informacji na temat usługi IIS 6.0, zobacz [Włączanie uwierzytelniania podstawowego i konfigurowanie nazwy obszaru](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc785293(v=ws.10)). Aby uzyskać więcej informacji na temat usługi IIS 7.0, zobacz [Konfigurowanie uwierzytelniania podstawowego (IIS 7)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772009(v=ws.10)).  
  
#### <a name="certificate"></a>Certyfikat  
 Usługi IIS mają opcję wymagania od klientów logowania się za pomocą certyfikatu. Funkcja umożliwia również usługi IIS mapowanie certyfikatu klienta na konto systemu Windows. Aby uzyskać więcej informacji na temat usługi IIS 6.0, zobacz [Włączanie certyfikatów klientów w iis 6.0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc727994(v=ws.10)). Aby uzyskać więcej informacji na temat usług IIS 7.0, zobacz [Konfigurowanie certyfikatów serwera w usługach IIS 7](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).  
  
#### <a name="digest"></a>Szyfrowane  
 Uwierzytelnianie szyfrowane jest podobne do uwierzytelniania podstawowego, ale oferuje tę zaletę, że wysyłanie poświadczeń jako skrótu, a nie w postaci zwykłego tekstu. Aby uzyskać więcej informacji na temat usługi IIS 6.0, zobacz [Uwierzytelnianie szyfrowane w iis 6.0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)). Aby uzyskać więcej informacji na temat usługi IIS 7.0, zobacz [Konfigurowanie uwierzytelniania szyfrowanego (IIS 7)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754104(v=ws.10)).  
  
#### <a name="windows"></a>Windows  
 Odpowiada to zintegrowanemu uwierzytelnianiu systemu Windows w usłudze IIS. Po ustawieniu tej wartości oczekuje się, że serwer będzie również istniał w domenie systemu Windows, która używa protokołu Kerberos jako kontrolera domeny. Jeśli serwer nie znajduje się w domenie kopii zapasowej protokołu Kerberos lub system Kerberos ulegnie awarii, można użyć wartości Menedżera NT LAN (NTLM) opisanej w następnej sekcji. Aby uzyskać więcej informacji na temat usługi IIS 6.0, zobacz [Zintegrowane uwierzytelnianie systemu Windows w systemie IIS 6.0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc738016(v=ws.10)). Aby uzyskać więcej informacji na temat usług IIS 7.0, zobacz [Konfigurowanie certyfikatów serwera w usługach IIS 7](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).
  
#### <a name="ntlm"></a>NTLM  
 Dzięki temu serwer może używać NTLM do uwierzytelniania, jeśli protokół Kerberos nie powiedzie się. Aby uzyskać więcej informacji na temat konfigurowania usługi IIS w u.0 usługi IIS 6.0, zobacz [Wymuszanie uwierzytelniania NTLM](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc786486(v=ws.10)). W przypadku usługi IIS 7.0 uwierzytelnianie systemu Windows obejmuje uwierzytelnianie NTLM. Aby uzyskać więcej informacji, zobacz [Konfigurowanie certyfikatów serwera w usługach IIS 7](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).
  
## <a name="wshttpbinding"></a>WsHttpBinding  
 Klasa <xref:System.ServiceModel.WSHttpBinding> jest przeznaczona do współpracy z usługami, które implementują specyfikacje WS-*. Zabezpieczenia transportu dla tego powiązania jest Secure Sockets Layer (SSL) za pośrednictwem protokołu HTTP lub HTTPS. Aby utworzyć aplikację WCF, która używa SSL, użyj usług IIS do hosta aplikacji. Alternatywnie, jeśli tworzysz aplikację hostowane samodzielnie, użyj narzędzia HttpCfg.exe, aby powiązać certyfikat X.509 z określonym portem na komputerze. Numer portu jest określony jako część aplikacji WCF jako adres punktu końcowego. Podczas korzystania z trybu transportu, adres punktu końcowego musi zawierać protokół HTTPS lub wyjątek zostanie zgłoszony w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 W przypadku uwierzytelniania <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> klienta <xref:System.ServiceModel.HttpTransportSecurity> ustaw właściwość <xref:System.ServiceModel.HttpClientCredentialType> klasy na jedną z wartości wyliczenia. Wartości wyliczenia są identyczne z <xref:System.ServiceModel.BasicHttpBinding> typami poświadczeń klienta i są przeznaczone do obsługi z usługami IIS.  
  
 W poniższym przykładzie przedstawiono powiązanie używane z typem poświadczeń klienta systemu Windows.  
  
 [!code-csharp[c_ProgrammingSecurity#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#11)]
 [!code-vb[c_ProgrammingSecurity#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#11)]  
  
## <a name="wsdualhttpbinding"></a>WSDualHttpBinowanie  
 To powiązanie zapewnia tylko zabezpieczenia na poziomie wiadomości, a nie zabezpieczenia na poziomie transportu.  
  
## <a name="nettcpbinding"></a>Nettcpbinding  
 Klasa <xref:System.ServiceModel.NetTcpBinding> używa protokołu TCP do transportu wiadomości. Zabezpieczenia dla trybu transportu są zapewniane przez implementowanie zabezpieczeń warstwy transportu (TLS) za pomocą protokołu TCP. Implementacja TLS jest dostarczana przez system operacyjny.  
  
 Można również określić typ poświadczeń klienta, ustawiając <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> właściwość klasy na <xref:System.ServiceModel.TcpTransportSecurity> jedną z <xref:System.ServiceModel.TcpClientCredentialType> wartości, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[c_ProgrammingSecurity#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#12)]
 [!code-vb[c_ProgrammingSecurity#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#12)]  
  
#### <a name="client"></a>Klient  
 Na kliencie należy określić certyfikat <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> przy <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> użyciu metody klasy.  
  
> [!NOTE]
> Jeśli używasz zabezpieczeń systemu Windows, certyfikat nie jest wymagany.  
  
 Poniższy kod używa odcisku palca certyfikatu, który jednoznacznie identyfikuje go. Aby uzyskać więcej informacji o certyfikatach, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 [!code-csharp[c_ProgrammingSecurity#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#13)]
 [!code-vb[c_ProgrammingSecurity#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#13)]  
  
 Alternatywnie należy określić certyfikat w konfiguracji klienta przy użyciu [ \<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element w sekcji zachowania.  
  
```xml  
<behaviors>  
  <behavior>  
   <clientCredentials>  
     <clientCertificate findValue= "101010101010101010101010101010000000000"
      storeLocation="LocalMachine" storeName="My"
      X509FindType="FindByThumbPrint">  
     </clientCertificate>  
   </clientCredentials>  
 </behavior>  
</behaviors>
```  
  
## <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 Klasa <xref:System.ServiceModel.NetNamedPipeBinding> jest przeznaczona do wydajnej komunikacji wewnątrz komputera; oznacza to, że dla procesów uruchomionych na tym samym komputerze, chociaż nazwane kanały potoku mogą być tworzone między dwoma komputerami w tej samej sieci. To powiązanie zapewnia tylko zabezpieczenia na poziomie transportu. Podczas tworzenia aplikacji przy użyciu tego powiązania adresy punktów końcowych musi zawierać "net.pipe" jako protokół adresu punktu końcowego.  
  
## <a name="wsfederationhttpbinding"></a>WSFederacjaHttpBinowanie  
 Podczas korzystania z zabezpieczeń transportu to powiązanie używa protokołu SSL za<xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential>pośrednictwem protokołu HTTP, znanego jako HTTPS z wystawionym tokenem ( ). Aby uzyskać więcej informacji o aplikacjach federacyjnych, zobacz [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="netpeertcpbinding"></a>Netpeertcpbinding  
 Klasa <xref:System.ServiceModel.NetPeerTcpBinding> jest bezpieczny transport, który jest przeznaczony do wydajnej komunikacji przy użyciu funkcji sieci peer-to-peer. Jak wskazuje nazwa klasy i powiązania, TCP jest protokołem. Gdy tryb zabezpieczeń jest ustawiony na Transport, powiązanie implementuje protokół TLS za ok. Aby uzyskać więcej informacji na temat funkcji peer-to-peer, zobacz [Sieci równorzędne](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="msmqintegrationbinding-and-netmsmqbinding"></a>MsmqIntegrationBinding i NetMsmqBinding  
 Aby zapoznać się z pełną dyskusją na temat zabezpieczeń transportu za pomocą usługi kolejkowania wiadomości (wcześniej nazywanej usługę MSMQ), zobacz [Zabezpieczanie wiadomości przy użyciu zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
## <a name="see-also"></a>Zobacz też

- [Programowanie zabezpieczeń WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
