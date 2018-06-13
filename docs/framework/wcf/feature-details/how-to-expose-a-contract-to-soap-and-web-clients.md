---
title: 'Instrukcje: Ujawnianie kontraktu klientom sieci Web i SOAP'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
ms.openlocfilehash: a9a730fe94d1df8c887a2eaf20c1e338bd056ed5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494153"
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a>Instrukcje: Ujawnianie kontraktu klientom sieci Web i SOAP
Domyślnie program Windows Communication Foundation (WCF) udostępnia punkty końcowe tylko do klientów protokołu SOAP. W [porady: Tworzenie podstawowej usługi HTTP sieci Web WCF](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md), punkt końcowy będą dostępne dla klientów z systemem innym niż SOAP. Może to być razy, jeśli chcesz udostępnić ten sam kontrakt obu kierunkach, jako punkt końcowy sieci Web, a punkt końcowy protokołu SOAP. W tym temacie przedstawiono przykład sposobu wykonania tego zadania.  
  
### <a name="to-define-the-service-contract"></a>Aby zdefiniować kontrakt usługi  
  
1.  Definiowanie kontraktu usługi przy użyciu interfejsu oznaczony atrybutem <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> i <xref:System.ServiceModel.Web.WebGetAttribute> atrybutów, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
     [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]  
  
    > [!NOTE]
    >  Domyślnie <xref:System.ServiceModel.Web.WebInvokeAttribute> mapuje wywołania operacji POST. Można jednak określić metodę do mapowania na operację, określając "metody =" parametru. <xref:System.ServiceModel.Web.WebGetAttribute> nie ma "metody =" parametru i map tylko GET wywołania do operacji usługi.  
  
2.  Implementowanie kontraktu usługi, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]  
  
### <a name="to-host-the-service"></a>Do obsługi usługi  
  
1.  Utwórz <xref:System.ServiceModel.ServiceHost> obiektów, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]  
  
2.  Dodaj <xref:System.ServiceModel.Description.ServiceEndpoint> z <xref:System.ServiceModel.BasicHttpBinding> dla punktu końcowego protokołu SOAP, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]  
  
3.  Dodaj <xref:System.ServiceModel.Description.ServiceEndpoint> z <xref:System.ServiceModel.WebHttpBinding> dla punktu końcowego z systemem innym niż SOAP i Dodaj <xref:System.ServiceModel.Description.WebHttpBehavior> do punktu końcowego, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]  
  
4.  Wywołanie `Open()` na <xref:System.ServiceModel.ServiceHost> wystąpienia można otworzyć hosta usługi, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]  
  
### <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a>Do wywołania operacji usługi mapowane na GET w programie Internet Explorer  
  
1.  Otwórz program Internet Explorer i wpisz "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`" i naciśnij klawisz ENTER. Adres URL zawiera adres podstawowy usługi ("http://localhost:8000/"), względny adres punktu końcowego (""), usługi operację wywołania ("EchoWithGet") i znak zapytania następuje lista parametrów nazwanych oddzielonymi znakiem handlowego "i" (&).  
  
### <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a>Do wywołania operacji usługi sieci Web w punkcie końcowym w kodzie  
  
1.  Utwórz wystąpienie <xref:System.ServiceModel.Web.WebChannelFactory%601> w `using` zablokować, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]  
  
> [!NOTE]
>  `Close()` automatycznie jest wywoływana w kanale na końcu `using` bloku.  
  
1.  Tworzenie kanału i wywołania tej usługi, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]  
  
### <a name="to-call-service-operations-on-the-soap-endpoint"></a>Do wywołania operacji usługi w punkcie końcowym protokołu SOAP  
  
1.  Utwórz wystąpienie <xref:System.ServiceModel.ChannelFactory> w `using` zablokować, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
     [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]  
  
2.  Tworzenie kanału i wywołania tej usługi, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
     [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]  
  
### <a name="to-close-the-service-host"></a>Aby zamknąć hosta usługi  
  
1.  Zamknij hosta usługi, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
     [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się pełny kod dla tego tematu.  
  
 [!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
 [!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W przypadku kompilowania kodu Service.cs, odwołanie System.ServiceModel.dll i System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Web.WebServiceHost>  
 <xref:System.ServiceModel.ChannelFactory>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
