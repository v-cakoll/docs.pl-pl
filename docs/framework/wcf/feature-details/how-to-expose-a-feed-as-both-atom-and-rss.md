---
title: "Porady: udostępnianie źródło danych jako Atom i RSS"
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
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2dad8fe137cfc495d1edc6936d13830861e1654e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a>Porady: udostępnianie źródło danych jako Atom i RSS
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Służy do tworzenia usługi, który ujawnia zespolonego źródła danych. W tym temacie omówiono sposób tworzenia usługa syndykacji ujawniający zespolonego źródła danych przy użyciu zarówno Atom 1.0 i RSS 2.0. Ta usługa udostępnia jeden punkt końcowy, który może zwrócić albo formacie zespolonego. Dla uproszczenia usługę używaną w tym przykładzie jest samodzielnie hostowana. W środowisku produkcyjnym usługi tego typu może być hostowana w ramach usług IIS lub WAS. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]różnych [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hosting opcji, zobacz [hostingu](../../../../docs/framework/wcf/feature-details/hosting.md).  
  
### <a name="to-create-a-basic-syndication-service"></a>Aby utworzyć usługę zespolonego podstawowe  
  
1.  Definiowanie kontraktu usługi przy użyciu interfejsu oznaczony atrybutem <xref:System.ServiceModel.Web.WebGetAttribute> atrybutu. Każda operacja uwidocznioną jak zespolonego źródła danych zwraca <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> obiektu. Należy pamiętać, parametry <xref:System.ServiceModel.Web.WebGetAttribute>. `UriTemplate`Określa adres URL używany do wywołania tej operacji usługi. Ciąg dla tego parametru zawiera literały i zmiennej w nawiasach klamrowych ({*format*}). Ta zmienna odnosi się do operacji usługi `format` parametru. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.UriTemplate>. `BodyStyle`wpływa na sposób tej operacji usługi wysyła i odbiera komunikaty są zapisywane. <xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare>Określa, że dane wysyłane do i z tej operacji usługi nie są opakowane w usłudze zdefiniowane infrastruktury elementów XML. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.Web.WebMessageBodyStyle>.  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    >  Użyj <xref:System.ServiceModel.ServiceKnownTypeAttribute> Aby określić typy, które są zwracane przez operacje usług w tym interfejsie.  
  
2.  Implementowanie kontraktu usługi.  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3.  Utwórz <xref:System.ServiceModel.Syndication.SyndicationFeed> obiektu i dodać autora, kategoria i opis.  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4.  Utwórz kilka <xref:System.ServiceModel.Syndication.SyndicationItem> obiektów.  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5.  Dodaj <xref:System.ServiceModel.Syndication.SyndicationItem> obiektów do źródła danych.  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6.  Użyj parametru formatu, aby zwrócić żądany format.  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a>Do obsługi usługi  
  
1.  Utwórz <xref:System.ServiceModel.Web.WebServiceHost> obiektu. <xref:System.ServiceModel.Web.WebServiceHost> Klasy automatycznie dodaje punkt końcowy na adres podstawowy usługi, chyba że został określony w konfiguracji lub kodu. W tym przykładzie punkty końcowe nie są określone, domyślny punkt końcowy jest widoczna.  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2.  Otworzyć hosta usługi, załadować źródła strumieniowego z usługi, Wyświetl źródło i poczekaj, aż użytkownikowi naciśnij klawisz ENTER.  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>Aby wywołać GetBlog z HTTP GET  
  
1.  Otwórz program Internet Explorer, wpisz następujący adres URL, a następnie naciśnij klawisz ENTER. http://localhost: 8000/BlogService/GetBlog  
  
     Adres URL zawiera adres podstawowy usługi (http://localhost: 8000/BlogService), względny adres punktu końcowego i do wywołania operacji usługi.  
  
### <a name="to-call-getblog-from-code"></a>Aby wywołać GetBlog() z kodu  
  
1.  Utwórz <xref:System.Xml.XmlReader> z adresu podstawowego i wywoływania metody.  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2.  Wywołaj statycznych <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> metody, przekazując <xref:System.Xml.XmlReader> właśnie utworzony.  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     To wywołanie operacji usługi i wypełnia nowy <xref:System.ServiceModel.Syndication.SyndicationFeed> z elementem formatującym zwrócony przez operację usługi.  
  
3.  Dostęp do źródła strumieniowego obiektu.  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się pełna listy w tym przykładzie kodu.  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W przypadku kompilowania kodu poprzedni kod, odniesienia System.ServiceModel.dll i System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>
