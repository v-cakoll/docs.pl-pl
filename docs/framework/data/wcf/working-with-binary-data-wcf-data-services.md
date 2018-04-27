---
title: Praca z danych binarnych (usługi danych WCF)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, binary data
- WCF Data Services, streams
ms.assetid: aeccc45c-d5c5-4671-ad63-a492ac8043ac
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 99143200b8135d5737454de325a95399c62fd506
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="working-with-binary-data-wcf-data-services"></a>Praca z danych binarnych (usługi danych WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Biblioteki klienta umożliwia pobieranie i aktualizowanie danych binarnych z [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych w jednym z następujących sposobów:  
  
-   Jako właściwość typu pierwotnego jednostki. Jest to zalecana metoda pracy z danych binarnych małych obiektów, które mogą być łatwo załadowanych do pamięci. W takim przypadku właściwości binarnej jest właściwością jednostki udostępnianych przez model danych i usługi data serializuje dane binarne w formacie base-64 Binarny XML zakodowany w komunikacie odpowiedzi.  
  
-   Jako strumień oddzielne zasobu binarnego. Jest to zalecana metoda uzyskiwania dostępu do oraz zmienianie danych dużego obiektu binarnego (BLOB), może reprezentować fotografii, wideo lub innego typu danych binarnych zakodowany.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] implementuje przesyłanie strumieniowe danych binarnych przy użyciu protokołu HTTP, zgodnie z definicją w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. W ten mechanizm danych binarnych jest traktowane jako zasób nośnika, który różni się od, ale związane z jednostki, która jest wywoływana wpisu media link entry. Aby uzyskać więcej informacji, zobacz [przesyłania strumieniowego dostawcy](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).  
  
> [!TIP]
>  Krok po kroku przykład sposobu tworzenia aplikacji klienckiej Windows Presentation Foundation (WPF), która pobiera pliki binarny z [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi, która przechowuje zdjęć, zobacz wpis [danych usługi przesyłania strumieniowego dostawcy serii części 2: uzyskiwanie dostępu do zasobu multimediów strumieniowych z klienta](http://go.microsoft.com/fwlink/?LinkId=201637). Aby pobrać przykładowy kod umieszczony w blogu usługi danych strumienia zdjęć, zobacz [przesyłanie strumieniowe zdjęć danych usługi próbki](http://go.microsoft.com/fwlink/?LinkId=198988) w galerii kodu MSDN.  
  
## <a name="entity-metadata"></a>Metadane jednostki  
 Określonej jednostki, która ma powiązanych multimediów strumieniowych zasobów w metadanych usługi danych przez `HasStream` atrybut zastosowany do typu jednostki, który jest wpisu łącza nośnika. W poniższym przykładzie `PhotoInfo` jednostka jest wpisem media link entry z zasobem multimediów powiązane, wskazane przez `HasStream` atrybutu.  
  
 [!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria photo streaming service/xml/photodata.edmx#hasstream)]  
  
 Pozostałe przykłady w tym temacie przedstawiają sposób dostępu i zmiany strumienia zasobu multimediów. Pełny przykład można korzystać z multimediów strumieniowych zasobów w aplikacji klienta .NET Framework za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteki klienta, zobacz wpis [podczas uzyskiwania dostępu do zasobu multimediów strumieniowych z klienta](http://go.microsoft.com/fwlink/?LinkID=201637).  
  
## <a name="accessing-the-binary-resource-stream"></a>Uzyskiwanie dostępu do strumienia zasobów binarnych  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Biblioteki klienta dostarcza metod dostępu do zasobów binarnych strumieni z [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]— na podstawie danych usługi. Podczas pobierania zasobów nośnika, możesz użyć identyfikatora URI zasobu multimediów lub można uzyskać strumienia binarnego zawiera samych danych zasobu multimediów. Możesz również przekazywać dane zasobów nośnika jako strumienia binarnego.  
  
> [!TIP]
>  Krok po kroku przykład sposobu tworzenia aplikacji klienckiej Windows Presentation Foundation (WPF), która pobiera pliki binarny z [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi, która przechowuje zdjęć, zobacz wpis [danych usługi przesyłania strumieniowego dostawcy serii części 2: uzyskiwanie dostępu do zasobu multimediów strumieniowych z klienta](http://go.microsoft.com/fwlink/?LinkId=201637). Aby pobrać przykładowy kod umieszczony w blogu usługi danych strumienia zdjęć, zobacz [przesyłanie strumieniowe zdjęć danych usługi próbki](http://go.microsoft.com/fwlink/?LinkId=198988) w galerii kodu MSDN.  
  
### <a name="getting-the-uri-of-the-binary-stream"></a>Pobieranie identyfikatora URI strumienia danych binarnych  
 Podczas pobierania niektórych typów zasobów nośników, takich jak obrazy i inne pliki multimedialne często jest łatwiejsze do użycia w aplikacji niż Obsługa sam strumień danych binarnych identyfikator URI zasobu multimediów. Aby uzyskać identyfikator URI skojarzony z wpisu łącza nośnika zapewnia strumienia zasobów, należy wywołać <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> metoda <xref:System.Data.Services.Client.DataServiceContext> wystąpienia, który służy do śledzenia jednostki. Poniższy przykład przedstawia sposób wywołania <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> metody, aby uzyskać identyfikator URI strumień zasobów nośnika, który służy do tworzenia nowego obrazu na komputerze klienckim:  
  
 [!code-csharp[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria photo streaming client/cs/photowindow.xaml.cs#getreadstreamuri)]
 [!code-vb[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria photo streaming client/vb/photowindow.xaml.vb#getreadstreamuri)]  
  
### <a name="downloading-the-binary-resource-stream"></a>Pobieranie zasobu binarnego strumienia  
 Podczas pobierania strumienia zasobu binarnego, należy wywołać <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> metoda <xref:System.Data.Services.Client.DataServiceContext> wystąpienia, który służy do śledzenia wpisu media link entry. Ta metoda wysyła żądanie do usługi danych, która zwraca <xref:System.Data.Services.Client.DataServiceStreamResponse> obiektu, który odwołuje się do strumienia, który zawiera zasób. Użyj tej metody, gdy aplikacja wymaga zasobów binarnych jako <xref:System.IO.Stream>. Poniższy przykład przedstawia sposób wywołania <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> metoda pobierania strumienia, który służy do tworzenia nowego obrazu na komputerze klienckim:  
  
 [!code-csharp[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria streaming client/cs/customerphotowindow.xaml.cs#getreadstreamclient)]
 [!code-vb[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria streaming client/vb/customerphotowindow.xaml.vb#getreadstreamclient)]  
  
> [!NOTE]
>  Nagłówek Content-Length w komunikacie odpowiedzi, który zawiera pary binarny nie jest ustawiany przez usługę danych. Ta wartość może nie odzwierciedlać rzeczywista długość strumienia danych binarnych.  
  
### <a name="uploading-a-media-resource-as-a-stream"></a>Przekazywanie jako strumień zasobem multimediów  
 Aby wstawić lub zaktualizować zasobu multimedialnego, należy wywołać <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> metoda <xref:System.Data.Services.Client.DataServiceContext> wystąpienia, który służy do śledzenia jednostki. Ta metoda wysyła żądanie do usługi danych zawierający czytać ze strumienia dostarczonego zasobu multimediów. Poniższy przykład przedstawia sposób wywołania <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> do wysyłania obrazu z usługą danych:  
  
 [!code-csharp[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria photo streaming client/cs/photodetailswindow.xaml.cs#setsavestream)]
 [!code-vb[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria photo streaming client/vb/photodetailswindow.xaml.vb#setsavestream)]  
  
 W tym przykładzie <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> metoda jest wywoływana przez podanie wartości `true` dla `closeStream` parametru. Gwarantuje to, że <xref:System.Data.Services.Client.DataServiceContext> zamyka strumień po danych binarnych jest przekazywany do usługi danych.  
  
> [!NOTE]
>  Podczas wywoływania <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A>, strumienia nie są wysyłane do usługi danych do <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> jest wywoływana.  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Wiązanie danych do kontrolki](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)
