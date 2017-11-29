---
title: "Instrukcje: Tworzenie podstawowej, opartej na protokole HTTP usługi sieci Web programu WCF"
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
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8352c7761447322d1ddf8381be145e38d6b7df8d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a>Instrukcje: Tworzenie podstawowej, opartej na protokole HTTP usługi sieci Web programu WCF
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Służy do tworzenia usługi, która udostępnia punkt końcowy sieci Web. Punktów końcowych sieci Web wysyłać dane XML lub JSON, nie istnieje żadne koperty protokołu SOAP. W tym temacie przedstawiono sposób ujawniać punkt końcowy.  
  
> [!NOTE]
>  Jedynym sposobem, aby zabezpieczyć punkt końcowy sieci Web jest je ujawnić za pośrednictwem protokołu HTTPS, za pomocą zabezpieczeń transportu. Podczas korzystania z zabezpieczeń wiadomości, informacje o zabezpieczeniach zazwyczaj znajduje się w nagłówkach protokołu SOAP i dlatego komunikaty wysyłane do punktów końcowych SOAP nie zawiera żadnych koperty protokołu SOAP, nie nigdzie nie można umieścić informacji o zabezpieczeniach i konieczne jest zastosowanie zabezpieczeń transportu.  
  
### <a name="to-create-a-web-endpoint"></a>Aby utworzyć punkt końcowy sieci Web  
  
1.  Definiowanie kontraktu usługi przy użyciu interfejsu oznaczony atrybutem <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> i <xref:System.ServiceModel.Web.WebGetAttribute> atrybutów.  
  
     [!code-csharp[htBasicService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]  
  
    > [!NOTE]
    >  Domyślnie <xref:System.ServiceModel.Web.WebInvokeAttribute> mapuje wywołania operacji POST. Można jednak określić metodę HTTP (na przykład HEAD, PUT lub usuń) do mapowania na operację, określając "metody =" parametru. <xref:System.ServiceModel.Web.WebGetAttribute>nie ma "metody =" parametru i map tylko GET wywołania do operacji usługi.  
  
2.  Implementowanie kontraktu usługi.  
  
     [!code-csharp[htBasicService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]  
  
### <a name="to-host-the-service"></a>Do obsługi usługi  
  
1.  Utwórz <xref:System.ServiceModel.Web.WebServiceHost> obiektu.  
  
     [!code-csharp[htBasicService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]  
  
2.  Dodaj <xref:System.ServiceModel.Description.ServiceEndpoint> z <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
     [!code-csharp[htBasicService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]  
  
    > [!NOTE]
    >  Jeśli nie zostanie dodany punkt końcowy <xref:System.ServiceModel.Web.WebServiceHost> automatycznie tworzy domyślny punkt końcowy. <xref:System.ServiceModel.Web.WebServiceHost>dodaje również <xref:System.ServiceModel.Description.WebHttpBehavior> i wyłącza strona pomocy HTTP oraz funkcje GET Web Services Description Language (WSDL), aby punkt końcowy metadanych nie zakłóca domyślny punkt końcowy HTTP.  
    >   
    >  Dodawanie punktu końcowego z systemem innym niż SOAP z adresu URL "" powoduje, że nieoczekiwanego zachowania podczas próby wywołania operacji w punkcie końcowym. Przyczyną tego jest nasłuchiwania URI punktu końcowego jest taki sam jak identyfikator URI strony pomocy (strona, która jest wyświetlana podczas przeglądania adres bazowy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi).  
  
     Możesz wybrać jedną z następujących czynności, aby zapobiec to:  
  
    -   Zawsze należy określić niepustą identyfikatora URI dla punktu końcowego z systemem innym niż SOAP.  
  
    -   Wyłącz strony pomocy. Można to zrobić z następującym kodem.  
  
     [!code-csharp[htBasicService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]  
  
3.  Otworzyć hosta usługi i poczekaj, aż użytkownik naciśnie klawisz ENTER.  
  
     [!code-csharp[htBasicService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]  
  
     W tym przykładzie pokazano, jak udostępniać usługi stylu sieci Web za pomocą aplikacji konsoli. Może również obsługiwać usługi IIS. Aby to zrobić, należy określić <xref:System.ServiceModel.Activation.WebServiceHostFactory> klasy w pliku SVC, jak pokazano w następującym kodem.  
  
    ```  
          <%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Samples.Service"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory%>  
    ```  
  
### <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a>Do wywołania operacji usługi mapowane na GET w programie Internet Explorer  
  
1.  Otwórz program Internet Explorer i wpisz "`http://localhost:8000/EchoWithGet?s=Hello, world!`" i naciśnij klawisz ENTER. Adres URL zawiera adres podstawowy usługi ("http://localhost: 8000 /"), względny adres punktu końcowego (""), usługi operację wywołania ("EchoWithGet") i znak zapytania następuje lista parametrów nazwanych oddzielonymi znakiem handlowego "i" (&).  
  
### <a name="to-call-service-operations-in-code"></a>Do wywołania operacji usługi w kodzie  
  
1.  Utwórz wystąpienie <!--zz <xref:System.ServiceModel.Web.WebChannelFactory>--> `System.ServiceModel.Web.WebChannelFactory` w `using` bloku.  
  
     [!code-csharp[htBasicService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]  
  
2.  Dodaj <xref:System.ServiceModel.Description.WebHttpBehavior> do punktu końcowego <xref:System.ServiceModel.ChannelFactory> wywołania.  
  
     [!code-csharp[htBasicService#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]  
  
3.  Tworzenie kanału i wywołania tej usługi.  
  
     [!code-csharp[htBasicService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]  
  
4.  Zamknij <xref:System.ServiceModel.Web.WebServiceHost>.  
  
     [!code-csharp[htBasicService#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się pełna listy w tym przykładzie kodu.  
  
 [!code-csharp[htBasicService#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
 [!code-vb[htBasicService#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W przypadku kompilowania kodu odwołanie Service.cs System.ServiceModel.dll i System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Web.WebServiceHost>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [Model programowania protokołu HTTP sieci Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
