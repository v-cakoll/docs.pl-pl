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
ms.openlocfilehash: e088383adf2345f9a2698d0f8794765461cdbaad
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975022"
---
# <a name="working-with-binary-data-wcf-data-services"></a>Praca z danymi binarnymi (Usługi danych programu WCF)

Biblioteka klienta [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] umożliwia pobieranie i aktualizowanie danych binarnych za pomocą źródła danych Open Data Protocol (OData) w jeden z następujących sposobów:

- Jako właściwość typu pierwotnego jednostki. Jest to zalecana metoda pracy z małymi obiektami danych binarnych, które można łatwo załadować do pamięci. W tym przypadku Właściwość Binary jest właściwością jednostki uwidocznioną przez model danych, a usługa danych serializować dane binarne jako plik binarny z kodowaniem Base-64 w komunikacie odpowiedzi.

- Jako oddzielny strumień zasobów binarnych. Jest to zalecana metoda do uzyskiwania dostępu do danych binarnych dużych obiektów (BLOB), które mogą reprezentować zdjęcia, wideo lub dowolnego innego typu binarne dane zakodowane.

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] implementuje przesyłanie strumieniowe danych binarnych przy użyciu protokołu HTTP zgodnie z definicją w protokole OData. W tym mechanizmie dane binarne są traktowane jako zasób multimedialny, który jest oddzielony od, ale związany z jednostką, która jest nazywana wpisem multimediów. Aby uzyskać więcej informacji, zobacz [dostawca przesyłania strumieniowego](streaming-provider-wcf-data-services.md).

> [!TIP]
> Aby zapoznać się z przykładem krok po kroku, jak utworzyć aplikację kliencką Windows Presentation Foundation (WPF), która pobiera pliki obrazów binarnych z usługi OData, która przechowuje zdjęcia, zobacz wpis [Data Services dostawcy przesyłania strumieniowego — część 2: uzyskiwanie dostępu do strumienia zasobów multimediów z klienta](https://go.microsoft.com/fwlink/?LinkId=201637)programu. Aby pobrać przykładowy kod dla oferty usługi przesyłania strumieniowego strumienia w blogu, zobacz [przykład przesyłania strumieniowego usługi danych zdjęć](https://go.microsoft.com/fwlink/?LinkId=198988) w witrynie MSDN Gallery.

## <a name="entity-metadata"></a>Metadane jednostki

Jednostka, która ma powiązany strumień zasobów multimediów, jest wskazywany w metadanych usługi danych przez atrybut `HasStream` stosowany do typu jednostki, który jest wpisem linku do nośnika. W poniższym przykładzie jednostką `PhotoInfo` jest wpis łącza do nośnika z powiązanym zasobem multimedialnym wskazywanym przez atrybut `HasStream`.

[!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_photo_streaming_service/xml/photodata.edmx#hasstream)]

Pozostałe przykłady w tym temacie pokazują, jak uzyskać dostęp do strumienia zasobów multimediów i zmienić go. Aby zapoznać się z kompletnym przykładem użycia strumienia zasobów multimediów w .NET Framework aplikacji klienckiej przy użyciu biblioteki klienta [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], zobacz temat Wysyłanie [dostępu do strumienia zasobów multimediów z klienta](https://go.microsoft.com/fwlink/?LinkID=201637).

## <a name="accessing-the-binary-resource-stream"></a>Uzyskiwanie dostępu do strumienia zasobów binarnych

Biblioteka klienta [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zapewnia metody uzyskiwania dostępu do strumieni zasobów binarnych z usługi danych opartych na protokole OData. Podczas pobierania zasobu multimedialnego można użyć identyfikatora URI zasobu multimedialnego lub uzyskać strumień binarny, który zawiera same dane zasobów multimedialnych. Możesz również przekazać dane zasobów multimedialnych jako strumień binarny.

> [!TIP]
> Aby zapoznać się z przykładem krok po kroku, jak utworzyć aplikację kliencką Windows Presentation Foundation (WPF), która pobiera pliki obrazów binarnych z usługi OData, która przechowuje zdjęcia, zobacz wpis [Data Services dostawcy przesyłania strumieniowego — część 2: uzyskiwanie dostępu do strumienia zasobów multimediów z klienta](https://go.microsoft.com/fwlink/?LinkId=201637)programu. Aby pobrać przykładowy kod dla oferty usługi przesyłania strumieniowego strumienia w blogu, zobacz [przykład przesyłania strumieniowego usługi danych zdjęć](https://go.microsoft.com/fwlink/?LinkId=198988) w witrynie MSDN Gallery.

### <a name="getting-the-uri-of-the-binary-stream"></a>Pobieranie identyfikatora URI strumienia binarnego

Podczas pobierania niektórych typów zasobów multimedialnych, takich jak obrazy i inne pliki multimedialne, często łatwiej jest używać identyfikatora URI zasobu multimedialnego w aplikacji niż obsługa samego strumienia danych binarnych. Aby uzyskać identyfikator URI strumienia zasobów skojarzonego z wpisem "Udostępnij multimedia link", należy wywołać metodę <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> w wystąpieniu <xref:System.Data.Services.Client.DataServiceContext>, które śledzi jednostkę. Poniższy przykład pokazuje, jak wywołać metodę <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A>, aby uzyskać identyfikator URI strumienia zasobów multimediów używanego do tworzenia nowego obrazu na kliencie:

[!code-csharp[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_client/cs/photowindow.xaml.cs#getreadstreamuri)]
[!code-vb[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_client/vb/photowindow.xaml.vb#getreadstreamuri)]

### <a name="downloading-the-binary-resource-stream"></a>Pobieranie strumienia zasobów binarnych

Podczas pobierania binarnego strumienia zasobów należy wywołać metodę <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> w wystąpieniu <xref:System.Data.Services.Client.DataServiceContext>, które śledzi wpis linku do nośnika. Ta metoda wysyła żądanie do usługi danych, która zwraca obiekt <xref:System.Data.Services.Client.DataServiceStreamResponse>, który zawiera odwołanie do strumienia zawierającego zasób. Tej metody należy użyć, gdy aplikacja wymaga zasobu binarnego jako <xref:System.IO.Stream>. Poniższy przykład pokazuje, jak wywołać metodę <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A>, aby pobrać strumień, który jest używany do tworzenia nowego obrazu na kliencie:

[!code-csharp[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_streaming_client/cs/customerphotowindow.xaml.cs#getreadstreamclient)]
[!code-vb[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_streaming_client/vb/customerphotowindow.xaml.vb#getreadstreamclient)]

> [!NOTE]
> Nagłówek Content-Length w komunikacie odpowiedzi zawierającym parę binarną nie jest ustawiony przez usługę danych. Ta wartość nie może odzwierciedlać rzeczywistej długości strumienia danych binarnych.

### <a name="uploading-a-media-resource-as-a-stream"></a>Przekazywanie zasobu multimedialnego jako strumienia

Aby wstawić lub zaktualizować zasób multimedialny, wywołaj metodę <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> w wystąpieniu <xref:System.Data.Services.Client.DataServiceContext>, które śledzi jednostkę. Ta metoda wysyła żądanie do usługi danych zawierającej zasób nośnika odczytany z podanego strumienia. Poniższy przykład pokazuje, jak wywołać metodę <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A>, aby wysłać obraz do usługi danych:

[!code-csharp[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_client/cs/photodetailswindow.xaml.cs#setsavestream)]
[!code-vb[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_client/vb/photodetailswindow.xaml.vb#setsavestream)]

W tym przykładzie metoda <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> jest wywoływana poprzez dostarczenie wartości `true` parametru `closeStream`. Gwarantuje to, że <xref:System.Data.Services.Client.DataServiceContext> zamyka strumień po przekazaniu danych binarnych do usługi danych.

> [!NOTE]
> Gdy wywołasz <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A>, strumień nie zostanie wysłany do usługi danych, dopóki nie zostanie wywołane <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>.

## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
- [Wiązanie danych do kontrolki](binding-data-to-controls-wcf-data-services.md)
