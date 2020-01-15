---
title: 'Instrukcje: Konfigurowanie usługi WCF na potrzeby współdziałania z klientami usługi ASP.NET w sieci Web'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
ms.openlocfilehash: 7e07e8d8781040d4ddc1d5643446f5a42354a557
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963549"
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a>Instrukcje: Konfigurowanie usługi WCF na potrzeby współdziałania z klientami usługi ASP.NET w sieci Web
Aby skonfigurować punkt końcowy usługi Windows Communication Foundation (WCF) do współdziałania z klientami usługi sieci Web ASP.NET, użyj typu <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> jako typu powiązania dla punktu końcowego usługi.  
  
 Opcjonalnie można włączyć obsługę uwierzytelniania przy użyciu protokołu HTTPS i klienta na poziomie transportu. Klienci usługi sieci Web ASP.NET nie obsługują kodowania komunikatów MTOM, więc Właściwość <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> powinna pozostać jako wartość domyślna, która jest <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>. Klienci usługi sieci Web ASP.Net nie obsługują protokołu WS-Security, więc <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> powinna być ustawiona na <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.  
  
 Aby udostępnić metadane usługi WCF ASP.NET narzędzia do generowania serwera proxy usługi sieci Web (czyli [narzędzie Web Services Description Language (WSDL. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v%3dvs.100)), [narzędzie odnajdywania usług sieci Web (Disco. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100))i funkcję Dodaj odwołanie sieci Web w programie Visual Studio, należy uwidocznić punkt końcowy metadanych HTTP/GET.  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-code"></a>Aby dodać punkt końcowy WCF, który jest zgodny z klientami usługi sieci Web ASP.NET w kodzie  
  
1. Utwórz nowe wystąpienie <xref:System.ServiceModel.BasicHttpBinding>  
  
2. Opcjonalnie Włącz zabezpieczenia transportu dla tego powiązania punktu końcowego usługi przez ustawienie trybu zabezpieczeń dla powiązania do <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Aby uzyskać szczegółowe informacje, zobacz [zabezpieczenia transportu](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3. Dodaj nowy punkt końcowy aplikacji do hosta usługi przy użyciu utworzonego wystąpienia powiązania. Aby uzyskać szczegółowe informacje na temat dodawania punktu końcowego usługi w kodzie, zobacz [instrukcje: Tworzenie punktu końcowego usługi w kodzie](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
4. Włącz punkt końcowy metadanych HTTP/GET dla usługi. Aby uzyskać szczegółowe informacje [, zobacz jak: Publikowanie metadanych dla usługi przy użyciu kodu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-a-configuration-file"></a>Aby dodać punkt końcowy WCF, który jest zgodny z klientami usługi sieci Web ASP.NET w pliku konfiguracji  
  
1. Utwórz nową konfigurację powiązania <xref:System.ServiceModel.BasicHttpBinding>. Aby uzyskać szczegółowe informacje, zobacz [instrukcje: Określanie powiązania usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
2. Opcjonalnie Włącz zabezpieczenia transportu dla tej konfiguracji powiązania punktu końcowego usługi, ustawiając tryb zabezpieczeń dla powiązania na <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Aby uzyskać szczegółowe informacje, zobacz [Transport Security](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3. Skonfiguruj nowy punkt końcowy aplikacji dla usługi przy użyciu konfiguracji powiązania, która została właśnie utworzona. Aby uzyskać szczegółowe informacje na temat dodawania punktu końcowego usługi w pliku konfiguracji, zobacz [temat jak: Tworzenie punktu końcowego usługi w konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).  
  
4. Włącz punkt końcowy metadanych HTTP/GET dla usługi. Aby uzyskać szczegółowe informacje, zobacz [instrukcje: Publikowanie metadanych dla usługi za pomocą pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod demonstruje sposób dodawania punktu końcowego WCF, który jest zgodny z klientami usługi sieci Web ASP.NET w kodzie i Alternatywnie w plikach konfiguracji.  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)] 
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)] 
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]     
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: tworzenie punktu końcowego usługi w kodzie](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)
- [Instrukcje: publikowanie metadanych dla usługi przy użyciu kodu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
- [Instrukcje: określanie powiązania usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [Instrukcje: tworzenie punktu końcowego usługi w konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Zabezpieczenia transportu](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [Używanie metadanych](../../../../docs/framework/wcf/feature-details/using-metadata.md)
