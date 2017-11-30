---
title: "Instrukcje: Używanie elementu MetadataExchangeClient do pobierania metadanych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0754e9dc-13c5-45c2-81b5-f3da466e5a87
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6a675c42c597928c0ea2cc60be6de0cea6111499
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-metadataexchangeclient-to-retrieve-metadata"></a>Instrukcje: Używanie elementu MetadataExchangeClient do pobierania metadanych
Użyj <xref:System.ServiceModel.Description.MetadataExchangeClient> klasy do pobierania metadanych za pomocą protokołu WS-MetadataExchange (MEX). Pliki pobierane metadane są zwracane jako <xref:System.ServiceModel.Description.MetadataSet> obiektu. Zwrócona <xref:System.ServiceModel.Description.MetadataSet> obiektu zawiera kolekcję <xref:System.ServiceModel.Description.MetadataSection> obiektów, z których każdy zawiera dialekt określonych metadanych i identyfikator. Metadane zwrócony może zapisywać do plików lub, jeśli metadane zwrócony zawiera dokumenty Web Services Description Language (WSDL), można importować przy użyciu metadanych <xref:System.ServiceModel.Description.WsdlImporter>.  
  
 <xref:System.ServiceModel.Description.MetadataExchangeClient> Konstruktorów przyjmujących adresu w systemie powiązania <xref:System.ServiceModel.Description.MetadataExchangeBindings> zgodny schemat identyfikatora URI (Uniform Resource) adres klasy statycznej. Możesz także użyć <xref:System.ServiceModel.Description.MetadataExchangeClient> Konstruktor, który można jawnie określić powiązania w celu użycia. Określone powiązanie jest używany do rozpoznawania wszystkie odwołania do metadanych.  
  
 Podobnie jak każdy inny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta, <xref:System.ServiceModel.Description.MetadataExchangeClient> typu zawiera konstruktora ładowania konfiguracji punktów końcowych klienta przy użyciu nazwy konfiguracji punktu końcowego. Określony punkt końcowy konfiguracji należy określić <xref:System.ServiceModel.Description.IMetadataExchange> kontraktu. Adres w konfiguracji punktu końcowego nie jest załadowany, więc należy użyć jednego z <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> przeciążeń, które przyjmują adres. Po określeniu przy użyciu adresu metadanych <xref:System.ServiceModel.EndpointAddress> wystąpienia, <xref:System.ServiceModel.Description.MetadataExchangeClient> przyjęto założenie, że adres wskazuje punkt końcowy MEX. Jeśli jako adres URL należy określić adres metadanych, należy również określić, które <xref:System.ServiceModel.Description.MetadataExchangeClientMode> do użycia w punkcie końcowym MEX lub HTTP GET.  
  
> [!IMPORTANT]
>  Domyślnie <xref:System.ServiceModel.Description.MetadataExchangeClient> rozpoznaje wszystkie odwołania, w tym WSDL i schematu XML importuje i zawiera. Tę funkcję można wyłączyć, ustawiając <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> właściwości `false`. Maksymalna liczba odwołań do rozwiązania przy użyciu można kontrolować <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> właściwości. Tej właściwości można użyć w połączeniu z `MaxReceivedMessageSize` właściwości w powiązaniu do kontroli, ile metadane są pobierane.  
  
### <a name="to-use-metadataexchangeclient-to-obtain-metadata"></a>Aby używanie elementu MetadataExchangeClient do uzyskania metadanych  
  
1.  Utwórz nową <xref:System.ServiceModel.Description.MetadataExchangeClient> obiektu, jawnie określając powiązanie, nazwa konfiguracji punktu końcowego lub adres metadanych.  
  
2.  Skonfiguruj <xref:System.ServiceModel.Description.MetadataExchangeClient> w zależności od potrzeb. Na przykład możesz określić poświadczenia do użycia podczas żądania metadanych, kontrolować sposób odwołania do metadanych są rozwiązane, a następnie ustaw <xref:System.ServiceModel.Description.MetadataExchangeClient.OperationTimeout%2A> właściwości do kontrolowania, jak długo ma zwracać zanim upłynie limit czasu żądania metadanych.  
  
3.  Uzyskaj <xref:System.ServiceModel.Description.MetadataSet> obiekt, który zawiera pobrane metadanych przez wywoływanie jednej z <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> metody. Należy pamiętać, że można używać tylko <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> przeciążenia, które nie przyjmuje żadnych argumentów Jeśli jawnie określony adres podczas konstruowania <xref:System.ServiceModel.Description.MetadataExchangeClient>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób użycia <xref:System.ServiceModel.Description.MetadataExchangeClient> do pobrania i wyliczania plików metadanych.  

 [!code-csharp[MetadataResolver#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/metadataresolver/cs/client.cs#3)]  

## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować ten przykładowy kod, musi odwoływać się do zestawu System.ServiceModel.dll i zaimportować <xref:System.ServiceModel.Description> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.MetadataResolver>  
 <xref:System.ServiceModel.Description.MetadataExchangeClient>  
 <xref:System.ServiceModel.Description.WsdlImporter>
