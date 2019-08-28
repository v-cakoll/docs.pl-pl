---
title: Praca z danymi binarnymi (Usługi danych programu WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, binary data
- WCF Data Services, streams
ms.assetid: aeccc45c-d5c5-4671-ad63-a492ac8043ac
ms.openlocfilehash: 21501ec9d0af4c785dd86946fa34c1041bb34b9d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043895"
---
# <a name="working-with-binary-data-wcf-data-services"></a>Praca z danymi binarnymi (Usługi danych programu WCF)

Biblioteka klienta umożliwia pobieranie i aktualizowanie danych binarnych [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] z kanału informacyjnego w jeden z następujących sposobów: [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]

- Jako właściwość typu pierwotnego jednostki. Jest to zalecana metoda pracy z małymi obiektami danych binarnych, które można łatwo załadować do pamięci. W tym przypadku Właściwość Binary jest właściwością jednostki uwidocznioną przez model danych, a usługa danych serializować dane binarne jako plik binarny z kodowaniem Base-64 w komunikacie odpowiedzi.

- Jako oddzielny strumień zasobów binarnych. Jest to zalecana metoda do uzyskiwania dostępu do danych binarnych dużych obiektów (BLOB), które mogą reprezentować zdjęcia, wideo lub dowolnego innego typu binarne dane zakodowane.

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]implementuje przesyłanie strumieniowe danych binarnych przy użyciu protokołu HTTP, jak [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]zdefiniowano w. W tym mechanizmie dane binarne są traktowane jako zasób multimedialny, który jest oddzielony od, ale związany z jednostką, która jest nazywana wpisem multimediów. Aby uzyskać więcej informacji, zobacz [dostawca przesyłania strumieniowego](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).

> [!TIP]
> Aby zapoznać się z przykładem krok po kroku, jak utworzyć aplikację kliencką Windows Presentation Foundation (WPF), która pobiera pliki obrazów binarnych [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] z usługi, w której są przechowywane Zdjęcia [, zobacz Data Services seria dostawcy przesyłania strumieniowego 2: Uzyskiwanie dostępu do strumienia zasobów multimediów z](https://go.microsoft.com/fwlink/?LinkId=201637)klienta programu. Aby pobrać przykładowy kod dla oferty usługi przesyłania strumieniowego strumienia w blogu, zobacz [przykład przesyłania strumieniowego usługi danych zdjęć](https://go.microsoft.com/fwlink/?LinkId=198988) w witrynie MSDN Gallery.

## <a name="entity-metadata"></a>Metadane jednostki

Jednostka, która ma powiązany strumień zasobów multimediów, jest wskazywany w metadanych usługi danych przez `HasStream` atrybut zastosowany do typu jednostki, który jest wpisem linku do nośnika. W poniższym przykładzie `PhotoInfo` jednostką jest wpis linku do nośnika z powiązanym zasobem multimedialnym wskazywanym `HasStream` przez atrybut.

[!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_photo_streaming_service/xml/photodata.edmx#hasstream)]

Pozostałe przykłady w tym temacie pokazują, jak uzyskać dostęp do strumienia zasobów multimediów i zmienić go. Aby zapoznać się z kompletnym przykładem użycia strumienia zasobów multimediów w .NET Framework aplikacji klienckiej przy użyciu [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteki klienta, zobacz temat Wysyłanie dostępu do [strumienia zasobów multimediów z klienta](https://go.microsoft.com/fwlink/?LinkID=201637).

## <a name="accessing-the-binary-resource-stream"></a>Uzyskiwanie dostępu do strumienia zasobów binarnych

Biblioteka kliencka zawiera metody uzyskiwania dostępu do strumieni zasobów binarnych [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]z usługi danych opartych na usłudze. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Podczas pobierania zasobu multimedialnego można użyć identyfikatora URI zasobu multimedialnego lub uzyskać strumień binarny, który zawiera same dane zasobów multimedialnych. Możesz również przekazać dane zasobów multimedialnych jako strumień binarny.

> [!TIP]
> Aby zapoznać się z przykładem krok po kroku, jak utworzyć aplikację kliencką Windows Presentation Foundation (WPF), która pobiera pliki obrazów binarnych [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] z usługi, w której są przechowywane Zdjęcia [, zobacz Data Services seria dostawcy przesyłania strumieniowego 2: Uzyskiwanie dostępu do strumienia zasobów multimediów z](https://go.microsoft.com/fwlink/?LinkId=201637)klienta programu. Aby pobrać przykładowy kod dla oferty usługi przesyłania strumieniowego strumienia w blogu, zobacz [przykład przesyłania strumieniowego usługi danych zdjęć](https://go.microsoft.com/fwlink/?LinkId=198988) w witrynie MSDN Gallery.

### <a name="getting-the-uri-of-the-binary-stream"></a>Pobieranie identyfikatora URI strumienia binarnego

Podczas pobierania niektórych typów zasobów multimedialnych, takich jak obrazy i inne pliki multimedialne, często łatwiej jest używać identyfikatora URI zasobu multimedialnego w aplikacji niż obsługa samego strumienia danych binarnych. Aby uzyskać identyfikator URI strumienia zasobów skojarzonego z wpisem "Udostępnij multimedia link", należy wywołać <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> metodę <xref:System.Data.Services.Client.DataServiceContext> w wystąpieniu, które śledzi jednostkę. Poniższy przykład pokazuje, jak wywołać metodę, <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> Aby uzyskać identyfikator URI strumienia zasobów multimediów używanego do tworzenia nowego obrazu na kliencie:

[!code-csharp[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_client/cs/photowindow.xaml.cs#getreadstreamuri)]
[!code-vb[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_client/vb/photowindow.xaml.vb#getreadstreamuri)]

### <a name="downloading-the-binary-resource-stream"></a>Pobieranie strumienia zasobów binarnych

Podczas pobierania strumienia zasobów binarnych należy wywołać <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> metodę <xref:System.Data.Services.Client.DataServiceContext> w wystąpieniu, które śledzi wpis linku do nośnika. Ta metoda wysyła żądanie do usługi danych, która zwraca <xref:System.Data.Services.Client.DataServiceStreamResponse> obiekt, który zawiera odwołanie do strumienia zawierającego zasób. Tej metody należy użyć, gdy aplikacja wymaga zasobu binarnego jako <xref:System.IO.Stream>. Poniższy przykład pokazuje, <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> jak wywołać metodę, aby pobrać strumień, który jest używany do tworzenia nowego obrazu na kliencie:

[!code-csharp[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_streaming_client/cs/customerphotowindow.xaml.cs#getreadstreamclient)]
[!code-vb[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_streaming_client/vb/customerphotowindow.xaml.vb#getreadstreamclient)]

> [!NOTE]
> Nagłówek Content-Length w komunikacie odpowiedzi zawierającym parę binarną nie jest ustawiony przez usługę danych. Ta wartość nie może odzwierciedlać rzeczywistej długości strumienia danych binarnych.

### <a name="uploading-a-media-resource-as-a-stream"></a>Przekazywanie zasobu multimedialnego jako strumienia

Aby wstawić lub zaktualizować zasób multimedialny, wywołaj <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> metodę <xref:System.Data.Services.Client.DataServiceContext> w wystąpieniu, które śledzi jednostkę. Ta metoda wysyła żądanie do usługi danych zawierającej zasób nośnika odczytany z podanego strumienia. Poniższy przykład pokazuje, <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> jak wywołać metodę w celu wysłania obrazu do usługi danych:

[!code-csharp[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_client/cs/photodetailswindow.xaml.cs#setsavestream)]
[!code-vb[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_client/vb/photodetailswindow.xaml.vb#setsavestream)]

W tym przykładzie <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> Metoda jest wywoływana przez dostarczenie `true` wartości `closeStream` parametru. Gwarantuje to, że <xref:System.Data.Services.Client.DataServiceContext> zamknięcie strumienia po danych binarnych zostanie przekazane do usługi danych.

> [!NOTE]
> Po wywołaniu <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A>, strumień nie jest wysyłany do usługi danych do momentu <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> wywołania.

## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Wiązanie danych do kontrolki](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)
