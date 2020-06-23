---
title: 'Instrukcje: Tworzenie podstawowej, opartej na protokole HTTP usługi sieci Web programu WCF'
description: Dowiedz się, jak utworzyć usługę, która uwidacznia punkt końcowy sieci Web w programie WCF. Punkty końcowe sieci Web wysyłają dane przy użyciu kodu XML lub JSON. Brak koperty protokołu SOAP.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
ms.openlocfilehash: 7481367f27d973ba809dff5ca1c4a4f168fbbb98
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247107"
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a>Instrukcje: Tworzenie podstawowej, opartej na protokole HTTP usługi sieci Web programu WCF

Windows Communication Foundation (WCF) umożliwia tworzenie usługi, która uwidacznia punkt końcowy sieci Web. Punkty końcowe sieci Web wysyłają dane w formacie XML lub JSON, ale nie ma koperty protokołu SOAP. W tym temacie pokazano, jak uwidocznić taki punkt końcowy.

> [!NOTE]
> Jedynym sposobem zabezpieczenia punktu końcowego sieci Web jest udostępnienie go za pośrednictwem protokołu HTTPS przy użyciu zabezpieczeń transportu. W przypadku korzystania z zabezpieczeń opartych na komunikatach informacje o zabezpieczeniach są zwykle umieszczane w nagłówkach protokołu SOAP, a ponieważ komunikaty wysyłane do punktów końcowych innych niż SOAP nie zawierają koperty protokołu SOAP, nie można umieścić informacji o zabezpieczeniach i należy polegać na zabezpieczeniach transportu.

## <a name="to-create-a-web-endpoint"></a>Aby utworzyć punkt końcowy sieci Web

1. Zdefiniuj kontrakt usługi przy użyciu interfejsu oznaczonego za pomocą <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> i <xref:System.ServiceModel.Web.WebGetAttribute> atrybutów.

     [!code-csharp[htBasicService#0](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]

    > [!NOTE]
    > Domyślnie <xref:System.ServiceModel.Web.WebInvokeAttribute> mapuje wywołania do operacji. Można jednak określić metodę HTTP (na przykład, nagłówek, PUT lub DELETE) do mapowania do operacji przez określenie parametru "Metoda =". <xref:System.ServiceModel.Web.WebGetAttribute>nie ma parametru "Method =" i tylko mapuje wywołania GET do operacji usługi.

2. Zaimplementuj kontrakt usługi.

     [!code-csharp[htBasicService#1](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]

## <a name="to-host-the-service"></a>Aby hostować usługę

1. Utwórz <xref:System.ServiceModel.Web.WebServiceHost> obiekt.

     [!code-csharp[htBasicService#2](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]

2. Dodaj <xref:System.ServiceModel.Description.ServiceEndpoint> przy użyciu <xref:System.ServiceModel.Description.WebHttpBehavior> .

     [!code-csharp[htBasicService#3](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]

    > [!NOTE]
    > Jeśli nie dodasz punktu końcowego, program <xref:System.ServiceModel.Web.WebServiceHost> automatycznie utworzy domyślny punkt końcowy. <xref:System.ServiceModel.Web.WebServiceHost>Ponadto dodaje <xref:System.ServiceModel.Description.WebHttpBehavior> i wyłącza stronę pomocy http i funkcję pobierania Web Services Description Language (WSDL), dzięki czemu punkt końcowy metadanych nie zakłóca domyślnego punktu końcowego http.
    >
    >  Dodanie punktu końcowego innego niż SOAP o adresie URL "" powoduje nieoczekiwane zachowanie, gdy podjęto próbę wywołania operacji w punkcie końcowym. Przyczyną tego jest identyfikator URI nasłuchiwania punktu końcowego, który jest taki sam jak identyfikator URI strony pomocy (strona wyświetlana po przejściu na adres podstawowy usługi WCF).

     Można wykonać jedną z następujących czynności, aby zapobiec takiej sytuacji:

    - Zawsze należy określić niepusty identyfikator URI dla punktu końcowego innego niż SOAP.

    - Wyłącz stronę pomocy. Można to zrobić przy użyciu następującego kodu:

     [!code-csharp[htBasicService#4](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]

3. Otwórz hosta usługi i poczekaj, aż użytkownik naciśnie klawisz ENTER.

     [!code-csharp[htBasicService#5](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]

     Ten przykład pokazuje, jak hostować usługę w stylu sieci Web za pomocą aplikacji konsolowej. Możesz również hostować taką usługę w ramach usług IIS. W tym celu należy określić <xref:System.ServiceModel.Activation.WebServiceHostFactory> klasę w pliku SVC, jak pokazano w poniższym kodzie.

    ```text
    <%ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Samples.Service"
        Factory=System.ServiceModel.Activation.WebServiceHostFactory%>
    ```

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a>Aby wywołać operacje usługi mapowane do pobrania w programie Internet Explorer

1. Otwórz program Internet Explorer i wpisz " `http://localhost:8000/EchoWithGet?s=Hello, world!` " i naciśnij klawisz ENTER. Adres URL zawiera adres podstawowy usługi ( `http://localhost:8000/` ), adres względny punktu końcowego (""), operację usługi do wywołania ("EchoWithGet") i znak zapytania oraz listę nazwanych parametrów oddzielonych znakiem handlowego "i" (&).

## <a name="to-call-service-operations-in-code"></a>Aby wywołać operacje usługi w kodzie

1. Utwórz wystąpienie <xref:System.ServiceModel.ChannelFactory%601> w `using` bloku.

     [!code-csharp[htBasicService#6](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]

2. Dodaj <xref:System.ServiceModel.Description.WebHttpBehavior> do punktu końcowego <xref:System.ServiceModel.ChannelFactory%601> wywołań.

     [!code-csharp[htBasicService#7](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]

3. Utwórz kanał i Wywołaj usługę.

     [!code-csharp[htBasicService#8](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]

4. Zamknij okno <xref:System.ServiceModel.Web.WebServiceHost> .

     [!code-csharp[htBasicService#9](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]

## <a name="example"></a>Przykład

Poniżej znajduje się pełna lista kodów dla tego przykładu.

[!code-csharp[htBasicService#10](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
[!code-vb[htBasicService#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Podczas kompilowania System.ServiceModel.dll odwołania do Service.cs i System.ServiceModel.Web.dll.

## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [Model programowania protokołu HTTP sieci Web w programie WCF](wcf-web-http-programming-model.md)
