---
title: "Przegląd zabezpieczeń transportu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 00959326-aa9d-44d0-af61-54933d4adc7f
caps.latest.revision: "23"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 8e35634f60ff68a07c199cf6f3893e741b631a08
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="transport-security-overview"></a>Przegląd zabezpieczeń transportu
Mechanizmy zabezpieczeń transportu [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] są zależne od powiązania i transportu są używane. Na przykład w przypadku korzystania z <xref:System.ServiceModel.WSHttpBinding> klasy, transport HTTP i podstawowego mechanizmu zabezpieczanie transportu Secure Sockets Layer (SSL) za pośrednictwem protokołu HTTP, często nazywane HTTPS. W tym temacie omówiono mechanizmy zabezpieczeń transportu główne używane w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] powiązania dostarczane przez system.  
  
> [!NOTE]
>  Stosowania zabezpieczeń SSL z programem .NET Framework 3.5 lub nowszym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klient używa zarówno certyfikaty pośrednie w magazynie certyfikatów i certyfikaty pośrednie otrzymał podczas negocjacji w protokole SSL podczas weryfikacji łańcucha certyfikatu certyfikat usługi. .NET framework 3.0 używa tylko certyfikaty pośrednie zainstalowane w lokalnym magazynie certyfikatów.  
  
> [!WARNING]
>  Gdy używane są zabezpieczenia transportu <!--zz <xref:System.Treading.Thread.CurrentPrincipal%2A> --> `CurrentPrincipal` właściwości mogą zostać nadpisane. Aby temu zapobiec występowaniu zestaw <!--zz <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermission%2A> --> `PrincipalPermission` None. <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>jest to zachowanie usługi, które można ustawić opisu usługi.  
  
## <a name="basichttpbinding"></a>BasicHttpBinding  
 Domyślnie <xref:System.ServiceModel.BasicHttpBinding> klasa nie zapewnia zabezpieczeń. To powiązanie jest przeznaczony do współdziałania z dostawców usług sieci Web, które nie implementują zabezpieczeń. Jednak można przełączyć na zabezpieczeń przez ustawienie <xref:System.ServiceModel.BasicHttpSecurity.Mode%2A> właściwości do każdej wartości z wyjątkiem <xref:System.ServiceModel.BasicHttpSecurityMode.None>. Aby włączyć zabezpieczeń transportu, ustaw właściwość <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.  
  
### <a name="interoperation-with-iis"></a>Współdziałanie z usługami IIS  
 <xref:System.ServiceModel.BasicHttpBinding> Klasa jest głównie używana na potrzeby współdziałania z istniejącymi usługami sieci Web i obsługiwanych wiele z tych usług Internet Information Services (IIS). W rezultacie zabezpieczeń transportu dla tego powiązania jest przeznaczona dla bezproblemowe współdziałanie z witryny usług IIS. Odbywa się przez ustawienie trybu zabezpieczeń <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> , a następnie ustawić typ poświadczeń klienta. Wartości typu poświadczeń odpowiadają mechanizmów zabezpieczeń katalogu usług IIS. Poniższy kod przedstawia sposób ustawiania i Ustaw typ poświadczeń systemu Windows. Jeśli zarówno klient, jak i serwera znajdują się w tej samej domenie systemu Windows, można użyć tej konfiguracji.  
  
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
  
 W poniższych sekcjach omówiono innego typu poświadczeń klienta.  
  
#### <a name="basic"></a>Podstawowy  
 Odpowiada to podstawowa metoda uwierzytelniania w usługach IIS. W tym trybie serwer usług IIS musi mieć skonfigurowaną konta użytkownika systemu Windows i odpowiednie uprawnienia systemu plików NTFS. [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iis601](../../../../includes/iis601-md.md)], zobacz [włączania uwierzytelniania podstawowego i konfigurowanie nazwy obszaru](http://go.microsoft.com/fwlink/?LinkId=88592). [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iisver](../../../../includes/iisver-md.md)], zobacz [usług IIS 7.0 Beta: Konfigurowanie uwierzytelniania podstawowego](http://go.microsoft.com/fwlink/?LinkId=88593).  
  
#### <a name="certificate"></a>certyfikat  
 Usługi IIS jest dostępna opcja wymaga przez klientów do logowania się przy użyciu certyfikatu. Funkcja umożliwia także usług IIS w celu zmapowania certyfikatu klienta na konto systemu Windows. [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iis601](../../../../includes/iis601-md.md)], zobacz [Włączanie certyfikatów klientów w usługach IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=88594). [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iisver](../../../../includes/iisver-md.md)], zobacz [usług IIS 7.0 Beta: Konfigurowanie certyfikatów serwerów w usługach IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=88595).  
  
#### <a name="digest"></a>Skrót  
 Uwierzytelnianie szyfrowane jest podobny do podstawowego uwierzytelniania, ale daje możliwość wysyłania poświadczeń jako skrót, a nie w postaci zwykłego tekstu. [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iis601](../../../../includes/iis601-md.md)], zobacz [uwierzytelnianie szyfrowane w usługach IIS 6.0](http://go.microsoft.com/fwlink/?LinkID=88443). [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iisver](../../../../includes/iisver-md.md)], zobacz [usług IIS 7.0 Beta: Konfigurowanie uwierzytelniania szyfrowanego](http://go.microsoft.com/fwlink/?LinkId=88596).  
  
#### <a name="windows"></a>Windows  
 Odpowiada to zintegrowane uwierzytelnianie systemu Windows w usługach IIS. Po ustawieniu tej wartości serwer również powinien istnieć w domenie systemu Windows, który korzysta z protokołu Kerberos jako kontrolera domeny. Jeśli serwer nie jest w domenie kopii protokołu Kerberos lub system protokołu Kerberos nie powiedzie się, możesz użyć wartości NT LAN Manager (NTLM), opisane w następnej sekcji. [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iis601](../../../../includes/iis601-md.md)], zobacz [zintegrowane uwierzytelnianie systemu Windows w usługach IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=88597). [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iisver](../../../../includes/iisver-md.md)], zobacz [usług IIS 7.0 Beta: Konfigurowanie certyfikatów serwerów w usługach IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=88595).  
  
#### <a name="ntlm"></a>UWIERZYTELNIANIE NTLM  
 Dzięki temu serwer służącego do uwierzytelniania NTLM, jeżeli protokół Kerberos nie powiedzie się. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Konfigurowanie usług IIS w [!INCLUDE[iis601](../../../../includes/iis601-md.md)], zobacz [wymuszania uwierzytelnianie NTLM](http://go.microsoft.com/fwlink/?LinkId=88598). Aby uzyskać [!INCLUDE[iisver](../../../../includes/iisver-md.md)], uwierzytelnianie systemu Windows zawiera uwierzytelniania NTLM. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Usług IIS 7.0 Beta: Konfigurowanie certyfikatów serwera w usługach IIS 7.0](http://go.microsoft.com/fwlink/?LinkID=88595).  
  
## <a name="wshttpbinding"></a>WsHttpBinding  
 <xref:System.ServiceModel.WSHttpBinding> Klasy zaprojektowano pod kątem współpracy z usługami, które implementują WS-* specyfikacji. Zabezpieczenia transportu dla tego powiązania jest Secure Sockets Layer (SSL) za pośrednictwem protokołu HTTP lub HTTPS. Aby utworzyć [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji, która używa protokołu SSL, używać usług IIS do hostowania aplikacji. Alternatywnie Jeśli tworzysz aplikację hostowanie Samoobsługowe narzędzie HttpCfg.exe powiązać certyfikat X.509 do określonego portu na komputerze. Numer portu jest określony jako część [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji jako adresu punktu końcowego. W trybie transportu adres punktu końcowego musi zawierać nazwę protokołu HTTPS lub zostanie wygenerowany wyjątek w czasie wykonywania. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Zabezpieczenia transportu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Uwierzytelnianie klienta, można ustawić <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> właściwość <xref:System.ServiceModel.HttpTransportSecurity> klasy do jednego z <xref:System.ServiceModel.HttpClientCredentialType> wartości wyliczenia. Wartości wyliczenia są takie same jak typy poświadczeń klienta dla <xref:System.ServiceModel.BasicHttpBinding> i mają być obsługiwane z usługami IIS.  
  
 W poniższym przykładzie przedstawiono powiązania, używany z typu poświadczeń klienta systemu Windows.  
  
 [!code-csharp[c_ProgrammingSecurity#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#11)]
 [!code-vb[c_ProgrammingSecurity#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#11)]  
  
## <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 To powiązanie zawiera tylko poziom komunikatu zabezpieczenia, zabezpieczenia nie poziomu transportu.  
  
## <a name="nettcpbinding"></a>NetTcpBinding  
 <xref:System.ServiceModel.NetTcpBinding> Klasy używa protokołu TCP dla transportu wiadomości. Dla trybu transportu zabezpieczenia dzięki implementacji zabezpieczeń TLS (Transport Layer) za pośrednictwem protokołu TCP. Implementacja protokołu TLS są udostępniane przez system operacyjny.  
  
 Typ poświadczeń klienta można także określić przez ustawienie <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> właściwość <xref:System.ServiceModel.TcpTransportSecurity> klasy do jednego z <xref:System.ServiceModel.TcpClientCredentialType> wartości, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[c_ProgrammingSecurity#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#12)]
 [!code-vb[c_ProgrammingSecurity#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#12)]  
  
#### <a name="client"></a>Klient  
 Na komputerze klienckim, należy określić przy użyciu certyfikatu <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> klasy.  
  
> [!NOTE]
>  Jeśli używane są zabezpieczenia systemu Windows, certyfikat nie jest wymagane.  
  
 W poniższym kodzie użyto odcisk palca certyfikatu, który unikatowo identyfikuje ją. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]certyfikaty, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 [!code-csharp[c_ProgrammingSecurity#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#13)]
 [!code-vb[c_ProgrammingSecurity#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#13)]  
  
 Można również określić certyfikat w konfiguracji klienta przy użyciu [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element w sekcji zachowania.  
  
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
 <xref:System.ServiceModel.NetNamedPipeBinding> Klasy zaprojektowano pod kątem sprawną komunikację w obrębie maszyny oznacza to, procesów uruchomiona na tym samym komputerze, mimo że o nazwie kanały potoku można można utworzyć; między dwoma komputerami w tej samej sieci. To powiązanie zawiera tylko zabezpieczeń na poziomie transportu. Podczas tworzenia aplikacji za pomocą tego powiązania, adresy punktów końcowych musi zawierać "net.pipe" jako protokół adres punktu końcowego.  
  
## <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 Podczas korzystania z zabezpieczeń transportu, tego wiązania używa protokołu SSL za pośrednictwem protokołu HTTP, znany jako HTTPS z wystawionego tokenu (<xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential>). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]aplikacje federacyjne, zobacz [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="netpeertcpbinding"></a>NetPeerTcpBinding  
 <xref:System.ServiceModel.NetPeerTcpBinding> Klasa jest bezpiecznego transportu, które jest przeznaczone do sprawną komunikację za pomocą funkcji sieci peer-to-peer. Wskazywany przez nazwę klasy i powiązania protokołu TCP jest protokołem. Gdy tryb zabezpieczeń Transport powiązania implementuje TLS za pośrednictwem protokołu TCP. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Funkcja peer-to-peer, zobacz [sieci Peer-to-Peer](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="msmqintegrationbinding-and-netmsmqbinding"></a>MsmqIntegrationBinding i NetMsmqBinding  
 Pełne omówienie transportu zabezpieczeń z usługi kolejkowania komunikatów (wcześniej nazywane MSMQ), można znaleźć [Zabezpieczanie komunikatów za pomocą zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie zabezpieczeń WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
