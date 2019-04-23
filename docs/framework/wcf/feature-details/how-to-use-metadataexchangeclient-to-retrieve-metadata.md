---
title: 'Instrukcje: używanie elementu MetadataExchangeClient do pobierania metadanych'
ms.date: 03/30/2017
ms.assetid: 0754e9dc-13c5-45c2-81b5-f3da466e5a87
ms.openlocfilehash: 32acef65ee30d7b80b37c11bdd024e3c09a935ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977674"
---
# <a name="how-to-use-metadataexchangeclient-to-retrieve-metadata"></a>Instrukcje: używanie elementu MetadataExchangeClient do pobierania metadanych
Użyj <xref:System.ServiceModel.Description.MetadataExchangeClient> klasy można pobrać metadanych przy użyciu protokołu WS-MetadataExchange (MEX). Pliki pobrane metadanych są zwracane jako <xref:System.ServiceModel.Description.MetadataSet> obiektu. Zwrócony <xref:System.ServiceModel.Description.MetadataSet> obiekt zawiera zbiór <xref:System.ServiceModel.Description.MetadataSection> obiektów, z których każdy zawiera dialekt określonych metadanych i identyfikator. Możesz zapisywać zwróconych metadanych plików, lub jeśli zwróconych metadanych zawiera dokumentów sieci Web Services Description Language (WSDL), możesz zaimportować przy użyciu metadanych <xref:System.ServiceModel.Description.WsdlImporter>.  
  
 <xref:System.ServiceModel.Description.MetadataExchangeClient> Konstruktorów, które przyjmują adres stosować powiązanie na <xref:System.ServiceModel.Description.MetadataExchangeBindings> statyczne klasy, która pasuje do schematu identyfikatora URI (Uniform Resource) adresu. Możesz też użyć <xref:System.ServiceModel.Description.MetadataExchangeClient> Konstruktor, który umożliwia jawnie określić powiązania do użycia. Określone powiązanie jest używany do rozpoznawania wszystkie odwołania do metadanych.  
  
 Podobnie jak w przypadku innych klientów usługi Windows Communication Foundation (WCF), <xref:System.ServiceModel.Description.MetadataExchangeClient> typ dostarcza Konstruktor do ładowania konfiguracji punktu końcowego klientów przy użyciu nazwy konfiguracji punktu końcowego. Należy określić konfigurację określonego punktu końcowego <xref:System.ServiceModel.Description.IMetadataExchange> kontraktu. Adres w konfiguracji punktu końcowego nie został załadowany, więc należy użyć jednej z <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> przeciążeń, które przyjmują adresu. Po określeniu przy użyciu adresu metadanych <xref:System.ServiceModel.EndpointAddress> wypadku <xref:System.ServiceModel.Description.MetadataExchangeClient> przyjęto założenie, że adres wskazuje punkt końcowy wymiany Metadanych. Jeśli określisz adres metadanych jako adres URL, a następnie należy również określić, które <xref:System.ServiceModel.Description.MetadataExchangeClientMode> do użycia w punkcie końcowym MEX lub HTTP GET.  
  
> [!IMPORTANT]
>  Domyślnie <xref:System.ServiceModel.Description.MetadataExchangeClient> rozpoznaje wszystkie odwołania, w tym WSDL i schematu XML importuje i zawiera. Tę funkcję można wyłączyć, ustawiając <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> właściwość `false`. Można kontrolować, maksymalna liczba odwołań do rozwiązania przy użyciu <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> właściwości. Można użyć tej właściwości w połączeniu z `MaxReceivedMessageSize` właściwości powiązania do kontrolowania ilości metadane są pobierane.  
  
### <a name="to-use-metadataexchangeclient-to-obtain-metadata"></a>Aby używanie elementu MetadataExchangeClient do uzyskania metadanych  
  
1. Utwórz nową <xref:System.ServiceModel.Description.MetadataExchangeClient> obiektu przez jawne określenie powiązanie, nazwę konfiguracji punktu końcowego lub adres metadanych.  
  
2. Konfigurowanie <xref:System.ServiceModel.Description.MetadataExchangeClient> do własnych potrzeb. Na przykład można określić poświadczenia do użycia podczas żądania metadanych, kontrolować sposób odwołania do metadanych są rozwiązane i ustawić <xref:System.ServiceModel.Description.MetadataExchangeClient.OperationTimeout%2A> właściwości do kontrolowania, jak długo żądanie metadanych musi zwrócić przed upływem limitu czasu.  
  
3. Uzyskaj <xref:System.ServiceModel.Description.MetadataSet> obiekt, który zawiera metadane pobrane, wywołując jedną z <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> metody. Należy zauważyć, że można używać tylko <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> przeciążenia, które nie przyjmuje żadnych argumentów Jeśli jawnie określony adres przy konstruowaniu <xref:System.ServiceModel.Description.MetadataExchangeClient>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób użycia <xref:System.ServiceModel.Description.MetadataExchangeClient> do pobrania i wyliczanie metadanych plików.  

 [!code-csharp[MetadataResolver#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/metadataresolver/cs/client.cs#3)]  

## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować ten przykład kodu, możesz odwoływać się do zestawu System.ServiceModel.dll i zaimportować <xref:System.ServiceModel.Description> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.MetadataResolver>
- <xref:System.ServiceModel.Description.MetadataExchangeClient>
- <xref:System.ServiceModel.Description.WsdlImporter>
