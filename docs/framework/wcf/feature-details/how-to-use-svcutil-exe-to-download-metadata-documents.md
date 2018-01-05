---
title: "Instrukcje: Używanie programu Svcutil.exe do pobierania dokumentów metadanych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 571465ab483aef3e3e663b9f82974f35e100c73e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>Instrukcje: Używanie programu Svcutil.exe do pobierania dokumentów metadanych
Svcutil.exe służy do pobierania metadanych z uruchomionymi usługami i zapisać metadanych do plików lokalnych. Schematy HTTP i HTTPS URL, aby uzyskać Svcutil.exe próbuje pobrać metadanych za pomocą usługi WS-MetadataExchange i [odnajdowanie usługi XML sieci Web](http://go.microsoft.com/fwlink/?LinkId=94950). W przypadku innych Schematy adresów URL Svcutil.exe używa tylko WS-MetadataExchange.  
  
 Domyślnie korzysta z powiązań zdefiniowanych w Svcutil.exe <xref:System.ServiceModel.Description.MetadataExchangeBindings> klasy. Aby skonfigurować powiązanie użyte dla protokołu WS-MetadataExchange, należy zdefiniować punkt końcowy klienta w pliku konfiguracji dla Svcutil.exe (svcutil.exe.config) używa `IMetadataExchange` kontraktu i który ma taką samą nazwę jak jednolity identyfikator zasobów (URI) Schemat adres punktu końcowego metadanych.  
  
> [!CAUTION]
>  Gdy uruchomiony Svcutil.exe można pobrać metadanych dla usługi, która udostępnia dwa różne usługi umów, że każdy zawierać operacji o tej samej nazwie, Svcutil.exe jest wyświetlany błąd informujący o tym, "Nie można uzyskać metadanych z..." Na przykład jeśli masz usługę, która uwidacznia kontraktu usługi o nazwie ICarService zawierający operacji Get (samochód c) i tej samej usługi udostępnia kontraktu usługi o nazwie IBookService zawierający operacji Get (książka b). Aby obejść ten problem, wykonaj jedną z następujących czynności:  
>   
>  -   Zmień nazwę jednej z operacji  
> -   Ustaw <xref:System.ServiceModel.OperationContractAttribute.Name%2A> pod inną nazwą.  
> -   Wartość jednej z operacji w przestrzeni nazw przy użyciu różnych nazw <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> właściwości.  
  
### <a name="to-download-metadata-using-svcutilexe"></a>Do pobierania metadanych za pomocą Svcutil.exe  
  
1.  Zlokalizuj narzędzia Svcutil.exe w następującej lokalizacji:  
  
     C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin  
  
2.  W wierszu polecenia Uruchom narzędzie w następującym formacie.  
  
    ```  
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     Należy określić `/t:metadata` opcję, aby pobrać metadanych. W przeciwnym razie wygenerowany kod klienta i konfiguracji.  
  
3.  <`url`> Argument określa adres URL punktu końcowego usługi, która udostępnia metadane lub dokument metadanych, hostowana w trybie online. <`epr`> Argument określa ścieżkę do pliku XML, który zawiera WS-Addressing `EndpointAddress` punktu końcowego usługi, która obsługuje WS-MetadataExchange.  
  
 Aby wyświetlić więcej opcji dotyczących dla pobierania metadanych za pomocą tego narzędzia, zobacz [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="example"></a>Przykład  
 Polecenie pobiera dokumentów metadanych z uruchomioną usługę.  
  
```  
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
