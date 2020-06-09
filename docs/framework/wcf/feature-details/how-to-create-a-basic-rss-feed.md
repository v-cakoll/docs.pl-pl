---
title: 'Instrukcje: Tworzenie podstawowego kanału informacyjnego RSS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 431879b8-a5f8-4947-ad1e-4768c726aca8
ms.openlocfilehash: 872fe325a6705e79d026cd7f6e1f7cfef5145307
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599025"
---
# <a name="how-to-create-a-basic-rss-feed"></a>Instrukcje: Tworzenie podstawowego kanału informacyjnego RSS
Windows Communication Foundation (WCF) umożliwia utworzenie usługi, która uwidacznia zespolone źródło danych. W tym temacie omówiono sposób tworzenia usługi zespolonej, która uwidacznia kanał informacyjny zespolonej RSS.  
  
### <a name="to-create-a-basic-syndication-service"></a>Aby utworzyć podstawową usługę zespalania  
  
1. Zdefiniuj kontrakt usługi przy użyciu interfejsu oznaczonego <xref:System.ServiceModel.Web.WebGetAttribute> atrybutem. Każda operacja, która jest udostępniana jako zespolone źródło danych, powinna zwracać <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> obiekt.  
  
     [!code-csharp[htRssBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#0)]
     [!code-vb[htRssBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#0)]  
  
    > [!NOTE]
    > Wszystkie operacje usługi, które stosują ten <xref:System.ServiceModel.Web.WebGetAttribute> atrybut są mapowane na żądania HTTP GET. Aby zmapować operację na inną metodę HTTP, użyj <xref:System.ServiceModel.Web.WebInvokeAttribute> zamiast niego. Aby uzyskać więcej informacji, zobacz [How to: Create a Basic Internet http Web Service](how-to-create-a-basic-wcf-web-http-service.md).  
  
2. Zaimplementuj kontrakt usługi.  
  
     [!code-csharp[htRssBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#1)]
     [!code-vb[htRssBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#1)]  
  
3. Utwórz <xref:System.ServiceModel.Syndication.SyndicationFeed> obiekt i Dodaj autora, kategorię i opis.  
  
     [!code-csharp[htRssBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#2)]
     [!code-vb[htRssBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#2)]  
  
4. Utwórz kilka <xref:System.ServiceModel.Syndication.SyndicationItem> obiektów.  
  
     [!code-csharp[htRssBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#3)]
     [!code-vb[htRssBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#3)]  
  
5. Dodaj <xref:System.ServiceModel.Syndication.SyndicationItem> do źródła danych.  
  
     [!code-csharp[htRssBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#4)]
     [!code-vb[htRssBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#4)]  
  
6. Zwróć źródło danych.  
  
     [!code-csharp[htRssBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#5)]
     [!code-vb[htRssBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#5)]  
  
### <a name="to-host-a-service"></a>Aby hostować usługę  
  
1. Utwórz <xref:System.ServiceModel.Web.WebServiceHost> obiekt.  
  
     [!code-csharp[htRssBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#6)]
     [!code-vb[htRssBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#6)]  
  
2. Otwórz hosta usługi i poczekaj, aż użytkownik naciśnie klawisz ENTER.  
  
     [!code-csharp[htRssBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#8)]
     [!code-vb[htRssBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>Aby wywołać metodę getblog () przy użyciu protokołu HTTP GET  
  
1. Otwórz program Internet Explorer, wpisz następujący adres URL, a następnie naciśnij klawisz ENTER: `http://localhost:8000/BlogService/GetBlog` . Adres URL zawiera adres podstawowy usługi ( `http://localhost:8000/BlogService` ), adres względny punktu końcowego i operację usługi do wywołania.  
  
### <a name="to-call-getblog-from-code"></a>Aby wywołać metodę getblog () z kodu  
  
1. Utwórz <xref:System.Xml.XmlReader> z adresem podstawowym i metodą, którą wywołujesz.  
  
     [!code-csharp[htRssBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#9)]
     [!code-vb[htRssBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#9)]  
  
2. Wywołaj metodę statyczną <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> , przekazując w <xref:System.Xml.XmlReader> właśnie utworzony sposób.  
  
     [!code-csharp[htRssBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#10)]
     [!code-vb[htRssBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#10)]  
  
     Spowoduje to wywołanie operacji usługi i wypełnienie nowej <xref:System.ServiceModel.Syndication.SyndicationFeed> z programem formatującego zwróconym przez operację usługi.  
  
3. Dostęp do obiektu źródła danych.  
  
     [!code-csharp[htRssBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#11)]
     [!code-vb[htRssBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#11)]  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się pełna lista kodów dla tego przykładu.  
  
 [!code-csharp[htRssBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#12)]
 [!code-vb[htRssBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Podczas kompilowania powyższego kodu odwołuje się do System. ServiceModel. dll i system. ServiceModel. Web. dll.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
