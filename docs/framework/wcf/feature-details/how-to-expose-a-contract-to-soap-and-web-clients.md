---
title: 'Instrukcje: Ujawnianie kontraktu klientom sieci Web i SOAP'
description: Dowiedz się, jak udostępnić punkt końcowy serwera WFC zarówno klientom protokołu SOAP, jak i innym niż SOAP. Domyślnie punkty końcowe są dostępne tylko dla klientów SOAP.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
ms.openlocfilehash: b1bdb7af51e0e2795c36865058fbeb34a716e3e2
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246977"
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a>Instrukcje: Ujawnianie kontraktu klientom sieci Web i SOAP

Domyślnie usługa Windows Communication Foundation (WCF) zapewnia punkty końcowe dostępne tylko dla klientów SOAP. [Instrukcje: Tworzenie podstawowej usługi HTTP sieci Web](how-to-create-a-basic-wcf-web-http-service.md)w programie WCF — punkt końcowy jest dostępny dla klientów innych niż SOAP. Mogą wystąpić sytuacje, w których ten sam kontrakt jest dostępny zarówno jako punkt końcowy sieci Web, jak i jako punkt końcowy protokołu SOAP. W tym temacie przedstawiono przykład sposobu wykonania tej czynności.

## <a name="to-define-the-service-contract"></a>Aby zdefiniować kontrakt usługi

1. Zdefiniuj kontrakt usługi przy użyciu interfejsu oznaczonego za pomocą <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> i <xref:System.ServiceModel.Web.WebGetAttribute> atrybutów, jak pokazano w poniższym kodzie:

    [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
    [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]

    > [!NOTE]
    > Domyślnie <xref:System.ServiceModel.Web.WebInvokeAttribute> mapuje wywołania do operacji. Można jednak określić metodę do mapowania do operacji przez określenie parametru "Metoda =". <xref:System.ServiceModel.Web.WebGetAttribute>nie ma parametru "Method =" i tylko mapuje wywołania GET do operacji usługi.

2. Zaimplementuj kontrakt usługi, jak pokazano w poniższym kodzie:

     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]

## <a name="to-host-the-service"></a>Aby hostować usługę

1. Utwórz <xref:System.ServiceModel.ServiceHost> obiekt, jak pokazano w poniższym kodzie:

     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]

2. Dodaj element <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.BasicHttpBinding> dla punktu końcowego protokołu SOAP, jak pokazano w poniższym kodzie:

     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]

3. Dodaj element <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.WebHttpBinding> dla punktu końcowego innego niż SOAP i dodaj go <xref:System.ServiceModel.Description.WebHttpBehavior> do punktu końcowego, jak pokazano w poniższym kodzie:

     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]

4. Zadzwoń `Open()` na <xref:System.ServiceModel.ServiceHost> wystąpienie, aby otworzyć hosta usługi, jak pokazano w poniższym kodzie:

     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a>Aby wywołać operacje usługi mapowane do pobrania w programie Internet Explorer

1. Otwórz program Internet Explorer i wpisz " `http://localhost:8000/Web/EchoWithGet?s=Hello, world!` " i naciśnij klawisz ENTER. Adres URL zawiera adres podstawowy usługi ( `http://localhost:8000/` ), adres względny punktu końcowego (""), operację usługi do wywołania ("EchoWithGet") i znak zapytania oraz listę nazwanych parametrów oddzielonych znakiem handlowego "i" (&).

## <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a>Aby wywołać operacje usługi w punkcie końcowym sieci Web w kodzie

1. Utwórz wystąpienie <xref:System.ServiceModel.Web.WebChannelFactory%601> w `using` bloku, jak pokazano w poniższym kodzie.

     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]

> [!NOTE]
> `Close()`jest automatycznie wywoływana na kanale na końcu `using` bloku.

1. Utwórz kanał i Wywołaj usługę, jak pokazano w poniższym kodzie.

     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]

## <a name="to-call-service-operations-on-the-soap-endpoint"></a>Aby wywołać operacje usługi w punkcie końcowym protokołu SOAP

1. Utwórz wystąpienie <xref:System.ServiceModel.ChannelFactory> w `using` bloku, jak pokazano w poniższym kodzie.

    [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
    [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]

2. Utwórz kanał i Wywołaj usługę, jak pokazano w poniższym kodzie.

    [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
    [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]

## <a name="to-close-the-service-host"></a>Aby zamknąć hosta usługi

1. Zamknij hosta usługi, jak pokazano w poniższym kodzie.

    [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
    [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]

## <a name="example"></a>Przykład

Oto pełna lista kodów dla tego tematu:

[!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
[!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

 Podczas kompilowania Service.cs należy odwołać się do System.ServiceModel.dll i System.ServiceModel.Web.dll.

## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.ChannelFactory>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [Model programowania protokołu HTTP sieci Web w programie WCF](wcf-web-http-programming-model.md)
