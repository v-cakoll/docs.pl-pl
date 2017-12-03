---
title: "Instrukcje: Konfigurowanie usługi WCF na potrzeby współdziałania z klientami usługi ASP.NET w sieci Web"
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
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7ed4bf8e86e727505d48e85bb55a88452217c76b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a>Instrukcje: Konfigurowanie usługi WCF na potrzeby współdziałania z klientami usługi ASP.NET w sieci Web
Aby skonfigurować [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] punktu końcowego usługi do współdziałać z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] obsługi klientów w sieci Web, użyj <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> typu powiązanie dla punktu końcowego usługi.  
  
 Opcjonalnie można włączyć obsługę uwierzytelniania klienta na poziomie transportu dla powiązania i HTTPS. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Klienci usługi sieci Web nie obsługują kodowanie komunikatu MTOM więc <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> właściwości powinny pozostać jako jego wartość domyślna, czyli <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>. Klienci usługi sieci Web ASP.Net nie obsługują WS-Security, więc <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> powinien być ustawiony na <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.  
  
 Aby uzyskać metadanych [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dostępnych usług do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] sieci Web narzędzia Generowanie serwera proxy usługi (oznacza to, [narzędzia języka opisu usługi sieci Web (Wsdl.exe)](http://go.microsoft.com/fwlink/?LinkId=73833), [narzędzia odnajdywania usług sieci Web ( DISCO.exe)](http://go.microsoft.com/fwlink/?LinkId=73834)i Dodaj odwołanie sieci Web w Visual Studio), powinny ujawniać punkt końcowy metadanych HTTP/GET.  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-code"></a>Można dodać punktu końcowego WCF, która jest zgodna z klientami usługi sieci Web ASP.NET w kodzie  
  
1.  Utwórz nową <xref:System.ServiceModel.BasicHttpBinding> wystąpienia  
  
2.  Opcjonalnie włączyć zabezpieczeń transportu dla tego powiązania punktu końcowego usługi przez ustawienie trybu zabezpieczeń dla powiązania <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Aby uzyskać więcej informacji, zobacz [zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3.  Dodaj nowy punkt końcowy aplikacji do host usług przy użyciu wystąpienia powiązania, który został właśnie utworzony. Aby uzyskać więcej informacji o sposobie dodawania punktu końcowego usługi w kodzie, zobacz [porady: Tworzenie punktu końcowego usługi w kodzie](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
4.  Włącz HTTP/GET punktu końcowego metadanych usługi. Aby uzyskać więcej informacji, zobacz [porady: Publikowanie metadanych dla kodu przy użyciu usługi](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-a-configuration-file"></a>Można dodać punktu końcowego WCF, która jest zgodna z klientami usługi sieci Web ASP.NET w pliku konfiguracji  
  
1.  Utwórz nową <xref:System.ServiceModel.BasicHttpBinding> konfiguracji powiązania. Aby uzyskać więcej informacji, zobacz [porady: Określanie powiązania usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
2.  Opcjonalnie włączyć zabezpieczeń transportu dla tej konfiguracji powiązania punktu końcowego usługi przez ustawienie trybu zabezpieczeń dla powiązania <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Aby uzyskać więcej informacji, zobacz [zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3.  Skonfiguruj nowy punkt końcowy aplikacji dla usługi przy użyciu Konfiguracja powiązania, który został właśnie utworzony. Aby uzyskać więcej informacji o sposobie dodawania punktu końcowego usługi w pliku konfiguracji, zobacz [porady: Tworzenie punktu końcowego usługi w konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).  
  
4.  Włącz HTTP/GET punktu końcowego metadanych usługi. Aby uzyskać więcej informacji, zobacz [porady: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób dodawania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktu końcowego, który jest zgodny z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] sieci Web obsługi klientów w kodzie i również w plikach konfiguracji.  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)] 
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)] 
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]     
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Tworzenie punktu końcowego usługi w kodzie](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 [Porady: Publikowanie metadanych dla usługi przy użyciu kodu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 [Porady: Określanie wiązań usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [Porady: Tworzenie punktu końcowego usługi w konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 [Porady: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [Zabezpieczenia transportu](../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [Przy użyciu metadanych](../../../../docs/framework/wcf/feature-details/using-metadata.md)
