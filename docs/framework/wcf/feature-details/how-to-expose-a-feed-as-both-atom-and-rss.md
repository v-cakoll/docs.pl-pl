---
title: 'Instrukcje: udostępnianie kanału informacyjnego w formatach Atom i RSS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
ms.openlocfilehash: f31f24cfc18f2c56539fe2b4623d54fe77a27797
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950594"
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a>Instrukcje: udostępnianie kanału informacyjnego w formatach Atom i RSS
Windows Communication Foundation (WCF) umożliwia utworzenie usługi, która uwidacznia zespolone źródło danych. W tym temacie omówiono sposób tworzenia usługi zespolonej, która uwidacznia zespolone źródło danych za pomocą Atom 1,0 i RSS 2,0. Ta usługa ujawnia jeden punkt końcowy, który może zwracać format zespolony. Dla uproszczenia Usługa używana w tym przykładzie jest samodzielna. W środowisku produkcyjnym usługi tego typu byłyby hostowane w usługach IIS lub WAS. Aby uzyskać więcej informacji na temat różnych opcji hostingu WCF, zobacz [hosting](../../../../docs/framework/wcf/feature-details/hosting.md).  
  
### <a name="to-create-a-basic-syndication-service"></a>Aby utworzyć podstawową usługę zespalania  
  
1. Zdefiniuj kontrakt usługi przy użyciu interfejsu oznaczonego <xref:System.ServiceModel.Web.WebGetAttribute> atrybutem. Każda operacja, która jest udostępniana jako zespolone źródło <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> danych, zwraca obiekt. Zwróć uwagę na parametry <xref:System.ServiceModel.Web.WebGetAttribute>. `UriTemplate`Określa adres URL służący do wywoływania tej operacji usługi. Ciąg dla tego parametru zawiera literały i zmienną w nawiasach klamrowych ({*Format*}). Ta zmienna odpowiada `format` parametrowi operacji usługi. Aby uzyskać więcej informacji, zobacz <xref:System.UriTemplate>. `BodyStyle`wpływa na to, w jaki sposób wiadomości wysyłane i odbierane przez tę operację usługi są zapisywane. <xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare>Określa, że dane wysyłane do i z tej operacji usługi nie są opakowane przez zdefiniowane przez infrastrukturę elementy XML. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Web.WebMessageBodyStyle>.  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    > Użyj, <xref:System.ServiceModel.ServiceKnownTypeAttribute> aby określić typy, które są zwracane przez operacje usługi w tym interfejsie.  
  
2. Zaimplementuj kontrakt usługi.  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3. <xref:System.ServiceModel.Syndication.SyndicationFeed> Utwórz obiekt i Dodaj autora, kategorię i opis.  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4. Utwórz kilka <xref:System.ServiceModel.Syndication.SyndicationItem> obiektów.  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5. <xref:System.ServiceModel.Syndication.SyndicationItem> Dodaj obiekty do źródła danych.  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6. Użyj parametru format, aby zwrócić żądany format.  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a>Aby hostować usługę  
  
1. Tworzy obiekt <xref:System.ServiceModel.Web.WebServiceHost>. <xref:System.ServiceModel.Web.WebServiceHost> Klasa automatycznie dodaje punkt końcowy pod adresem podstawowym usługi, chyba że jest określony w kodzie lub konfiguracji. W tym przykładzie nie określono żadnych punktów końcowych, więc domyślny punkt końcowy jest ujawniany.  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2. Otwórz hosta usługi, Załaduj źródło danych z usługi, Wyświetl źródło i poczekaj na naciśnięcie klawisza ENTER przez użytkownika.  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>Aby wywołać metodę getblog przy użyciu protokołu HTTP GET  
  
1. Otwórz program Internet Explorer, wpisz następujący adres URL, a następnie naciśnij `http://localhost:8000/BlogService/GetBlog`klawisz ENTER:.
  
     Adres URL zawiera adres podstawowy usługi (`http://localhost:8000/BlogService`), adres względny punktu końcowego i operację usługi do wywołania.  
  
### <a name="to-call-getblog-from-code"></a>Aby wywołać metodę getblog () z kodu  
  
1. <xref:System.Xml.XmlReader> Utwórz z adresem podstawowym i metodą, którą wywołujesz.  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2. Wywołaj metodę <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> statyczną, przekazując <xref:System.Xml.XmlReader> w właśnie utworzony sposób.  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     Spowoduje to wywołanie operacji usługi i wypełnienie nowej <xref:System.ServiceModel.Syndication.SyndicationFeed> z programem formatującego zwróconym przez operację usługi.  
  
3. Dostęp do obiektu źródła danych.  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się pełna lista kodów dla tego przykładu.  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Podczas kompilowania powyższego kodu odwołuje się do System. ServiceModel. dll i system. ServiceModel. Web. dll.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
