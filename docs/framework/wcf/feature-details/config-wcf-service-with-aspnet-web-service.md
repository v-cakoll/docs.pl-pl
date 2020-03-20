---
title: 'Instrukcje: Konfigurowanie usługi WCF na potrzeby współdziałania z klientami usługi ASP.NET w sieci Web'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
ms.openlocfilehash: 6a06e1983a54581cfb89f008e9f063a671e992c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185353"
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a>Instrukcje: Konfigurowanie usługi WCF na potrzeby współdziałania z klientami usługi ASP.NET w sieci Web
Aby skonfigurować punkt końcowy usługi Windows Communication Foundation (WCF) jako interoperacyjny z <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> ASP.NET klientami usługi sieci Web, należy użyć tego typu jako typu powiązania dla punktu końcowego usługi.  
  
 Opcjonalnie można włączyć obsługę https i uwierzytelniania klienta na poziomie transportu na powiązanie. ASP.NET klienci usługi sieci Web nie obsługują kodowania <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> komunikatów MTOM, więc właściwość <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>powinna być pozostawiona jako wartość domyślna, czyli . ASP.Net klienci usługi sieci Web nie obsługują usługi WS-Security, więc <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> należy ustawić na <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.  
  
 Aby udostępnić metadane usługi WCF ASP.NET narzędzi generowania serwera proxy usługi sieci Web (czyli [narzędzia języka opisu usług sieci Web (Wsdl.exe),](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v%3dvs.100)) [narzędzia do odnajdowania usług sieci Web (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100))i funkcji Dodaj odwołanie do sieci Web w programie Visual Studio), należy udostępnić punkt końcowy metadanych HTTP/GET.  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-code"></a>Aby dodać punkt końcowy WCF, który jest zgodny z ASP.NET klientami usługi sieci Web w kodzie  
  
1. Tworzenie nowego <xref:System.ServiceModel.BasicHttpBinding> wystąpienia  
  
2. Opcjonalnie włącz zabezpieczenia transportu dla tego powiązania punktu końcowego <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>usługi, ustawiając tryb zabezpieczeń dla powiązania na . Szczegółowe informacje można znaleźć w [bezpieczeństwie transportu](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3. Dodaj nowy punkt końcowy aplikacji do hosta usługi przy użyciu wystąpienia powiązania, które właśnie utworzono. Aby uzyskać szczegółowe informacje na temat dodawania punktu końcowego usługi w kodzie, zobacz [Jak: Tworzenie punktu końcowego usługi w kodzie](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
4. Włącz punkt końcowy metadanych HTTP/GET dla usługi. Aby uzyskać szczegółowe informacje, zobacz [Jak: Publikowanie metadanych dla usługi przy użyciu kodu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-a-configuration-file"></a>Aby dodać punkt końcowy WCF zgodny z ASP.NET klientami usługi sieci Web w pliku konfiguracyjnym  
  
1. Utwórz <xref:System.ServiceModel.BasicHttpBinding> nową konfigurację powiązania. Aby uzyskać szczegółowe informacje, zobacz [Jak: Określanie powiązania usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
2. Opcjonalnie włącz zabezpieczenia transportu dla tej konfiguracji powiązania punktu końcowego <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>usługi, ustawiając tryb zabezpieczeń dla powiązania na . Aby uzyskać szczegółowe informacje, zobacz [Bezpieczeństwo transportu](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3. Skonfiguruj nowy punkt końcowy aplikacji dla usługi przy użyciu konfiguracji powiązania, która została właśnie utworzona. Aby uzyskać szczegółowe informacje na temat dodawania punktu końcowego usługi do pliku konfiguracyjnego, zobacz [Sposób: Tworzenie punktu końcowego usługi w konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).  
  
4. Włącz punkt końcowy metadanych HTTP/GET dla usługi. Aby uzyskać szczegółowe informacje, zobacz [jak: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracyjnego](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod pokazuje, jak dodać punkt końcowy WCF, który jest zgodny z ASP.NET klientami usługi sieci Web w kodzie i alternatywnie w plikach konfiguracyjnych.  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: tworzenie punktu końcowego usługi w kodzie](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)
- [Instrukcje: publikowanie metadanych dla usługi przy użyciu kodu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
- [Instrukcje: określanie powiązania usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [Instrukcje: tworzenie punktu końcowego usługi w konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Zabezpieczenia transportu](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [Używanie metadanych](../../../../docs/framework/wcf/feature-details/using-metadata.md)
