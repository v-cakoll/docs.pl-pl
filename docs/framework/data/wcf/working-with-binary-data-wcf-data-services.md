---
title: Praca z danymi binarnymi (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, binary data
- WCF Data Services, streams
ms.assetid: aeccc45c-d5c5-4671-ad63-a492ac8043ac
ms.openlocfilehash: 428f12c90d646b1c08cdeaf48467efc2ce53859a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64660258"
---
# <a name="working-with-binary-data-wcf-data-services"></a>Praca z danymi binarnymi (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Biblioteka klienta umożliwia pobieranie i aktualizację danych binarnych pochodzących ze [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych w jednym z następujących sposobów:  
  
- Jako typ pierwotny właściwość jednostki. Jest to zalecana metoda do pracy z danymi binarnymi małych obiektów, które można łatwo załadować do pamięci. W tym przypadku właściwość binarna jest właściwość jednostki udostępnianych przez model danych i usługi danych serializuje dane binarne jako binarne XML zakodowany base-64 w komunikacie odpowiedzi.  
  
- Jako strumień osobny zasób binarny. Jest to zalecana metoda uzyskiwania dostępu do oraz zmiana dane dużych obiektów binarnych (BLOB), który może reprezentować fotografii, wideo lub dowolnego typu dane binarne zakodowane.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] implementuje, przesyłanie strumieniowe danych binarnych przy użyciu protokołu HTTP, zgodnie z definicją w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Dane binarne ten mechanizm jest traktowany jako zasób nośnika, który jest oddzielony od ale powiązanych z jednostką, która nosi nazwę wpisu łącza nośnika. Aby uzyskać więcej informacji, zobacz [dostawca przesyłania strumieniowego](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).  
  
> [!TIP]
>  Aby uzyskać przykład krok po kroku dotyczące tworzenia aplikacji klienckiej Windows Presentation Foundation (WPF), która pobiera pliki obrazów binarnych z [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługa, która przechowuje zdjęcia, zobacz wpis [danych przesyłania strumieniowego dostawcy serii-Part usług 2: Uzyskiwanie dostępu do Stream zasobu multimediów od klienta](https://go.microsoft.com/fwlink/?LinkId=201637). Aby pobrać przykładowy kod dla usługi danych strumienia zdjęć polecane wpis w blogu, zobacz [przesyłanie strumieniowe zdjęć dane usług — przykład](https://go.microsoft.com/fwlink/?LinkId=198988) w galerii kodu MSDN.  
  
## <a name="entity-metadata"></a>Metadane jednostki  
 Jednostki, która ma powiązane multimediów strumieniowych zasobu jest wskazywane WE metadanych usługi danych przez `HasStream` zastosowany do typu jednostki, która jest nośnika wpisu łącza nośnika. W poniższym przykładzie `PhotoInfo` jednostka jest wpisu łącza nośnika, zawierającej powiązanych zasobów nośników, wskazywanym przez `HasStream` atrybutu.  
  
 [!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_photo_streaming_service/xml/photodata.edmx#hasstream)]  
  
 Pozostałe przykłady w tym temacie pokazano, jak dostępu i zmiany strumień zasobu multimediów. Pełny przykład sposobu korzystania z multimediów strumieniowych zasobów w aplikacji klienckiej .NET Framework za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteki klienta, zobacz wpis [uzyskiwania dostępu do Stream zasobu multimediów od klienta](https://go.microsoft.com/fwlink/?LinkID=201637).  
  
## <a name="accessing-the-binary-resource-stream"></a>Uzyskiwanie dostępu do Stream zasób binarny  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Biblioteki klienta dostarcza metod dostępu do strumieni zasób binarny z [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]— na podstawie danych usługi. Podczas pobierania zasobu multimediów, możesz użyć identyfikatora URI zasobu multimediów, lub można uzyskać strumień binarny zawiera same dane zasobu multimediów. Możesz również przekazać dane do zasobu multimediów jako strumień binarny.  
  
> [!TIP]
>  Aby uzyskać przykład krok po kroku dotyczące tworzenia aplikacji klienckiej Windows Presentation Foundation (WPF), która pobiera pliki obrazów binarnych z [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługa, która przechowuje zdjęcia, zobacz wpis [danych przesyłania strumieniowego dostawcy serii-Part usług 2: Uzyskiwanie dostępu do Stream zasobu multimediów od klienta](https://go.microsoft.com/fwlink/?LinkId=201637). Aby pobrać przykładowy kod dla usługi danych strumienia zdjęć polecane wpis w blogu, zobacz [przesyłanie strumieniowe zdjęć dane usług — przykład](https://go.microsoft.com/fwlink/?LinkId=198988) w galerii kodu MSDN.  
  
### <a name="getting-the-uri-of-the-binary-stream"></a>Uzyskiwanie identyfikatora URI binarne Stream  
 Podczas pobierania niektórych rodzajów zasobów nośników, takich jak obrazy i inne pliki multimedialne, często jest łatwiejszy w użyciu identyfikator URI zasobu multimediów w Twojej aplikacji, niż Obsługa sam strumień danych binarnych. Aby uzyskać identyfikator URI skojarzony z danym wpisu łącza nośnika strumienia zasobu, należy wywołać <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> metody <xref:System.Data.Services.Client.DataServiceContext> wystąpienie, które służy do śledzenia jednostki. Poniższy przykład pokazuje sposób wywoływania <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> metodę, aby uzyskać identyfikator URI multimediów strumieniowych zasobu, który jest używany do tworzenia nowego obrazu na komputerze klienckim:  
  
 [!code-csharp[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_client/cs/photowindow.xaml.cs#getreadstreamuri)]
 [!code-vb[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_client/vb/photowindow.xaml.vb#getreadstreamuri)]  
  
### <a name="downloading-the-binary-resource-stream"></a>Pobieranie Stream zasób binarny  
 Podczas pobierania strumienia binarnego, należy wywołać <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> metody <xref:System.Data.Services.Client.DataServiceContext> wystąpienie, które służy do śledzenia wpisu łącza nośnika. Ta metoda wysyła żądanie do usługi danych, która zwraca <xref:System.Data.Services.Client.DataServiceStreamResponse> obiektu, który zawiera odwołanie do strumienia, który zawiera zasób. Użyj tej metody, gdy aplikacja wymaga zasób binarny jako <xref:System.IO.Stream>. Poniższy przykład pokazuje sposób wywoływania <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> metodę, która pobierze strumień, który jest używany do tworzenia nowego obrazu na komputerze klienckim:  
  
 [!code-csharp[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_streaming_client/cs/customerphotowindow.xaml.cs#getreadstreamclient)]
 [!code-vb[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_streaming_client/vb/customerphotowindow.xaml.vb#getreadstreamclient)]  
  
> [!NOTE]
>  Nagłówek Content-Length w komunikacie odpowiedzi, który zawiera pary binarne nie jest ustawiony przez usługę danych. Ta wartość może nie odzwierciedlać rzeczywiste długość strumienia danych binarnych.  
  
### <a name="uploading-a-media-resource-as-a-stream"></a>Przekazywania zasobu multimediów jako Stream  
 Aby wstawić lub zaktualizować zasobu multimediów, należy wywołać <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> metody <xref:System.Data.Services.Client.DataServiceContext> wystąpienie, które służy do śledzenia jednostki. Ta metoda wysyła żądanie do usługi danych, która zawiera zasób nośnika odczytany ze strumienia podane. Poniższy przykład pokazuje sposób wywoływania <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> metodę, aby wysłać obrazu do usługi danych:  
  
 [!code-csharp[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_client/cs/photodetailswindow.xaml.cs#setsavestream)]
 [!code-vb[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_client/vb/photodetailswindow.xaml.vb#setsavestream)]  
  
 W tym przykładzie <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> metoda jest wywoływana przez podanie wartości `true` dla `closeStream` parametru. Gwarantuje to, że <xref:System.Data.Services.Client.DataServiceContext> zamyka strumień przekazane dane binarne do usługi danych.  
  
> [!NOTE]
>  Gdy wywołujesz <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A>, strumienia nie są wysyłane do usługi danych, dopóki <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> jest wywoływana.  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Wiązanie danych do kontrolki](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)
