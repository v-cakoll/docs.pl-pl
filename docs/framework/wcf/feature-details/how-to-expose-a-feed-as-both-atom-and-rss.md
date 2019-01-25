---
title: 'Instrukcje: Udostępnianie kanału informacyjnego w formatach Atom i RSS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
ms.openlocfilehash: 43ad8ae0b12b07e2d0abe3e208f6d1ccdb2ec77d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681173"
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a>Instrukcje: Udostępnianie kanału informacyjnego w formatach Atom i RSS
Windows Communication Foundation (WCF) pozwala utworzyć usługę, która udostępnia kanał. W tym temacie omówiono sposób tworzenia usługi syndykacji, który udostępnia kanał, za pomocą RSS 2.0 i Atom 1.0. Ta usługa udostępnia jeden punkt końcowy, który może zwracać albo formacie syndykacji. Dla uproszczenia usługi używane w tym przykładzie jest samodzielnie hostowana. W środowisku produkcyjnym usługi tego typu może być hostowana w ramach usług IIS i WAS. Aby uzyskać więcej informacji o różnych technologii WCF opcji hostingu, zobacz [hostingu](../../../../docs/framework/wcf/feature-details/hosting.md).  
  
### <a name="to-create-a-basic-syndication-service"></a>Aby utworzyć usługę syndykacji podstawowe  
  
1.  Definiowanie kontraktu usługi przy użyciu interfejsu oznaczone <xref:System.ServiceModel.Web.WebGetAttribute> atrybutu. Każda operacja, która jest widoczna jako zespolonego źródła danych zwraca <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> obiektu. Należy pamiętać, parametry <xref:System.ServiceModel.Web.WebGetAttribute>. `UriTemplate` Określa adres URL używany do wywoływania operacji tej usługi. Ciąg dla tego parametru zawiera literały i zmiennej w nawiasy klamrowe ({*format*}). Ta zmienna odnosi się do operacji usługi `format` parametru. Aby uzyskać więcej informacji, zobacz <xref:System.UriTemplate>. `BodyStyle` wpływa na sposób, które tej operacji usługa wysyła i odbiera komunikaty są zapisywane. <xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> Określa, czy dane wysyłane do i z tej operacji usługi nie są opakowane przez elementy XML zdefiniowane przez infrastrukturę. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Web.WebMessageBodyStyle>.  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    >  Użyj <xref:System.ServiceModel.ServiceKnownTypeAttribute> Aby określić typy, które są zwracane przez operacje usług, w tym interfejsie.  
  
2.  Implementowanie kontraktu usługi.  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3.  Utwórz <xref:System.ServiceModel.Syndication.SyndicationFeed> obiektu, a następnie dodaj autora, kategoria i opis.  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4.  Utwórz kilka <xref:System.ServiceModel.Syndication.SyndicationItem> obiektów.  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5.  Dodaj <xref:System.ServiceModel.Syndication.SyndicationItem> obiektów w strumieniowym źródle danych.  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6.  Użyj parametru formatu, aby zwrócić żądany format.  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a>Do obsługi usługi  
  
1.  Tworzy obiekt <xref:System.ServiceModel.Web.WebServiceHost>. <xref:System.ServiceModel.Web.WebServiceHost> Klasy automatycznie dodaje punkt końcowy na adres podstawowy usługi, chyba że został określony w kodzie lub konfiguracji. W tym przykładzie Brak punktów końcowych są określane tak domyślny punkt końcowy jest uwidaczniany.  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2.  Otworzyć hosta usługi, załadować źródła danych z usługi, Wyświetl źródło i czekać, aż użytkownik na naciśnięcie klawisza ENTER.  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>Aby wywołać GetBlog za pomocą żądania HTTP GET  
  
1.  Otwórz program Internet Explorer, wpisz następujący adres URL i naciśnij klawisz ENTER: `http://localhost:8000/BlogService/GetBlog`.
  
     Adres URL zawiera adres podstawowy usługi (`http://localhost:8000/BlogService`), adres względny punktu końcowego, a operacja usługi do wywołania.  
  
### <a name="to-call-getblog-from-code"></a>Aby wywołać GetBlog() z kodu  
  
1.  Utwórz <xref:System.Xml.XmlReader> z adresu podstawowego i metody, którą wywołujesz.  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2.  Wywołaj statyczną <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> metody, przekazując <xref:System.Xml.XmlReader> właśnie utworzony.  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     To wywołanie operacji usługi i wypełnia nową <xref:System.ServiceModel.Syndication.SyndicationFeed> z elementem formatującym zwrócony przez operację usługi.  
  
3.  Dostęp do obiektu źródła danych.  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a>Przykład  
 Oto pełny kod dla tego przykładu.  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Podczas kompilowania w poprzednim kodzie, odwołać System.ServiceModel.dll i System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
