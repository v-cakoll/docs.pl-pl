---
title: 'Instrukcje: konfigurowanie usługi WCF na potrzeby współdziałania z klientami usługi ASP.NET w Internecie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
ms.openlocfilehash: 84762d8917609b84a049ea665b575acfa6e5fecf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59325192"
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a>Instrukcje: konfigurowanie usługi WCF na potrzeby współdziałania z klientami usługi ASP.NET w Internecie
Aby skonfigurować punkt końcowy usługi Windows Communication Foundation (WCF), aby współdziałać z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] obsługi klientów w sieci Web, należy użyć <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> typ jako typ powiązania punktu końcowego usługi.  
  
 Opcjonalnie można włączyć obsługę protokołu HTTPS i uwierzytelniania klienta na poziomie transportu w powiązaniu. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Klientami usługi sieci Web nie obsługują kodowanie MTOM wiadomości, więc <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> właściwość, należy pozostawić jako jego wartość domyślna, czyli <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>. Klienci usługi sieci Web programu ASP.Net nie obsługują WS-Security, więc <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> powinna być równa <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.  
  
 Aby udostępnić metadanych dla usługi WCF [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] narzędzia generowania serwera proxy usługi internetowej (oznacza to, [narzędzia języka opisu usługi sieci Web (Wsdl.exe)](https://go.microsoft.com/fwlink/?LinkId=73833), [narzędzia odnajdywania usług sieci Web (Disco.exe)](https://go.microsoft.com/fwlink/?LinkId=73834)oraz funkcji Dodaj odwołanie sieci Web w programie Visual Studio), należy udostępnić punkt końcowy metadanych HTTP/GET.  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-code"></a>Dodawanie punktu końcowego WCF, która jest zgodna z klientami usługi sieci Web platformy ASP.NET w kodzie  
  
1. Utwórz nową <xref:System.ServiceModel.BasicHttpBinding> wystąpienia  
  
2. Opcjonalnie włączyć zabezpieczenia transportu dla tego powiązania punktu końcowego usługi przez ustawianie trybu zabezpieczeń dla wiązania <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Aby uzyskać więcej informacji, zobacz [Transport Security](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3. Dodaj nowy punkt końcowy aplikacji do hosta usługi przy użyciu wystąpienia powiązania, który został utworzony. Aby uzyskać szczegółowe informacje dotyczące sposobu dodawania punktu końcowego usługi w kodzie, zobacz [jak: Tworzenie punktu końcowego usługi w kodzie](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
4. Włączanie punktu końcowego metadanych HTTP/GET dla Twojej usługi. Aby uzyskać szczegółowe informacje, zobacz [jak: Publikowanie metadanych dla usługi przy użyciu kodu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-a-configuration-file"></a>Dodawanie punktu końcowego WCF, która jest zgodna z klientami usługi sieci Web platformy ASP.NET w pliku konfiguracji  
  
1. Utwórz nową <xref:System.ServiceModel.BasicHttpBinding> Konfiguracja powiązania. Aby uzyskać więcej informacji, zobacz [jak: Określanie wiązań usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
2. Opcjonalnie włączyć zabezpieczenia transportu dla tej konfiguracji powiązania punktu końcowego usługi przez ustawianie trybu zabezpieczeń dla wiązania <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Aby uzyskać więcej informacji, zobacz [Transport Security](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3. Skonfiguruj nowy punkt końcowy aplikacji dla usługi przy użyciu konfiguracji powiązania, który został utworzony. Aby uzyskać szczegółowe informacje dotyczące sposobu dodawania punktu końcowego usługi w pliku konfiguracji, zobacz [jak: Tworzenie punktu końcowego usługi w konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).  
  
4. Włączanie punktu końcowego metadanych HTTP/GET dla Twojej usługi. Aby uzyskać szczegółowe informacje, zobacz [jak: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób dodawania punktu końcowego WCF, która jest zgodna z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] sieci Web obsługi klientów w kodzie i można również w plikach konfiguracji.  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)] 
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)] 
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]     
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie punktu końcowego usługi w kodzie](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)
- [Instrukcje: Publikowanie metadanych dla usługi przy użyciu kodu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
- [Instrukcje: Określanie wiązań usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [Instrukcje: Tworzenie punktu końcowego usługi w konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [Instrukcje: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Zabezpieczenia transportu](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [Używanie metadanych](../../../../docs/framework/wcf/feature-details/using-metadata.md)
