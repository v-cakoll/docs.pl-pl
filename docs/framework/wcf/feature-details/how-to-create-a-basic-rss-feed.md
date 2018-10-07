---
title: 'Instrukcje: Tworzenie podstawowego kanału informacyjnego RSS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 431879b8-a5f8-4947-ad1e-4768c726aca8
ms.openlocfilehash: bf8f719a47fda8b592165368234a2db0467c59ce
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48835800"
---
# <a name="how-to-create-a-basic-rss-feed"></a>Instrukcje: Tworzenie podstawowego kanału informacyjnego RSS
Windows Communication Foundation (WCF) pozwala utworzyć usługę, która udostępnia kanał. W tym temacie omówiono sposób tworzenia usługa syndykacji, która udostępnia źródło danych RSS, źródła danych.  
  
### <a name="to-create-a-basic-syndication-service"></a>Aby utworzyć usługę syndykacji podstawowe  
  
1.  Definiowanie kontraktu usługi przy użyciu interfejsu oznaczone <xref:System.ServiceModel.Web.WebGetAttribute> atrybutu. Każda operacja, która jest widoczna jako źródło danych ma zwracać <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> obiektu.  
  
     [!code-csharp[htRssBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#0)]
     [!code-vb[htRssBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#0)]  
  
    > [!NOTE]
    >  Wszystkie operacje usługi, które są stosowane <xref:System.ServiceModel.Web.WebGetAttribute> atrybutu są mapowane na żądania HTTP GET. Aby zamapować operację na innej metody HTTP, użyj <xref:System.ServiceModel.Web.WebInvokeAttribute> zamiast tego. Aby uzyskać więcej informacji, zobacz [porady: tworzenie podstawowa usługa HTTP w sieci Web WCF](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).  
  
2.  Implementowanie kontraktu usługi.  
  
     [!code-csharp[htRssBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#1)]
     [!code-vb[htRssBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#1)]  
  
3.  Utwórz <xref:System.ServiceModel.Syndication.SyndicationFeed> obiektu, a następnie dodaj autora, kategoria i opis.  
  
     [!code-csharp[htRssBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#2)]
     [!code-vb[htRssBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#2)]  
  
4.  Utwórz kilka <xref:System.ServiceModel.Syndication.SyndicationItem> obiektów.  
  
     [!code-csharp[htRssBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#3)]
     [!code-vb[htRssBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#3)]  
  
5.  Dodaj <xref:System.ServiceModel.Syndication.SyndicationItem> w strumieniowym źródle danych.  
  
     [!code-csharp[htRssBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#4)]
     [!code-vb[htRssBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#4)]  
  
6.  Zwróć źródła danych.  
  
     [!code-csharp[htRssBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#5)]
     [!code-vb[htRssBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#5)]  
  
### <a name="to-host-a-service"></a>Host usługi  
  
1.  Tworzy obiekt <xref:System.ServiceModel.Web.WebServiceHost>.  
  
     [!code-csharp[htRssBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#6)]
     [!code-vb[htRssBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#6)]  
  
2.  Otworzyć hosta usługi i zaczekaj, aż użytkownik naciśnie klawisz ENTER.  
  
     [!code-csharp[htRssBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#8)]
     [!code-vb[htRssBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>Aby wywołać GetBlog() za pomocą żądania HTTP GET  
  
1.  Otwórz program Internet Explorer, wpisz następujący adres URL i naciśnij klawisz ENTER: `http://localhost:8000/BlogService/GetBlog`. Adres URL zawiera adres podstawowy usługi (`http://localhost:8000/BlogService`), adres względny punktu końcowego, a operacja usługi do wywołania.  
  
### <a name="to-call-getblog-from-code"></a>Aby wywołać GetBlog() z kodu  
  
1.  Utwórz <xref:System.Xml.XmlReader> z adresu podstawowego i metody, którą wywołujesz.  
  
     [!code-csharp[htRssBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#9)]
     [!code-vb[htRssBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#9)]  
  
2.  Wywołaj statyczną <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> metody, przekazując <xref:System.Xml.XmlReader> właśnie utworzony.  
  
     [!code-csharp[htRssBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#10)]
     [!code-vb[htRssBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#10)]  
  
     To wywołanie operacji usługi i wypełnia nową <xref:System.ServiceModel.Syndication.SyndicationFeed> z elementem formatującym zwrócony przez operację usługi.  
  
3.  Dostęp do obiektu źródła danych.  
  
     [!code-csharp[htRssBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#11)]
     [!code-vb[htRssBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#11)]  
  
## <a name="example"></a>Przykład  
 Oto pełny kod dla tego przykładu.  
  
 [!code-csharp[htRssBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#12)]
 [!code-vb[htRssBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Podczas kompilowania w poprzednim kodzie, odwołać System.ServiceModel.dll i System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>
