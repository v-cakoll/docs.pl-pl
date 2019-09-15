---
title: 'Instrukcje: używanie programu Svcutil.exe do pobierania dokumentów metadanych'
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 25840247e59b9dd61cadaa2ee94713240d135f88
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991615"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>Instrukcje: używanie programu Svcutil.exe do pobierania dokumentów metadanych
Programu Svcutil. exe można użyć do pobierania metadanych z uruchomionych usług i zapisywania metadanych w plikach lokalnych. W przypadku schematów adresów URL protokołu HTTP i HTTPS Svcutil. exe próbuje pobrać metadane za pomocą usługi WS-MetadataExchange i [odnajdowania usług sieci Web XML](https://go.microsoft.com/fwlink/?LinkId=94950). W przypadku wszystkich innych schematów adresów URL Svcutil. exe używa tylko protokołu WS-MetadataExchange.  
  
 Domyślnie Svcutil. exe używa powiązań zdefiniowanych w <xref:System.ServiceModel.Description.MetadataExchangeBindings> klasie. Aby skonfigurować powiązanie używane dla protokołu WS-MetadataExchange, należy zdefiniować punkt końcowy klienta w pliku konfiguracji dla Svcutil. exe (Svcutil. exe. config), który używa `IMetadataExchange` kontraktu i ma taką samą nazwę jak Uniform Resource Identifier (URI) schemat adresu punktu końcowego metadanych.  
  
> [!CAUTION]
> Podczas uruchamiania programu Svcutil. exe w celu uzyskania metadanych dla usługi, która ujawnia dwie różne kontrakty usługi, które zawierają operacje o tej samej nazwie, Svcutil. exe wyświetla błąd mówiący "nie można uzyskać metadanych z..." Na przykład jeśli masz usługę, która ujawnia kontrakt usługi o `ICarService` nazwie, który ma operację `Get(Car c)` , a ta sama usługa ujawnia kontrakt usługi o nazwie `IBookService` , który ma operację `Get(Book b)`. Aby obejść ten problem, wykonaj jedną z następujących czynności:
>
> - Zmień nazwę jednej z operacji.
> - <xref:System.ServiceModel.OperationContractAttribute.Name%2A> Ustaw inną nazwę.
> - Ustaw jedną z przestrzeni nazw operacji na inną przestrzeń nazw przy użyciu <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> właściwości.
  
## <a name="to-download-metadata-using-svcutilexe"></a>Aby pobrać metadane przy użyciu programu Svcutil. exe  
  
1. Znajdź narzędzie Svcutil. exe w następującej lokalizacji:  
  
     C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin  
  
2. W wierszu polecenia Uruchom narzędzie przy użyciu następującego formatu.  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     Należy określić `/t:metadata` opcję pobierania metadanych. W przeciwnym razie jest generowany kod i konfiguracja klienta.  
  
3. <`url`Argument > określa adres URL punktu końcowego usługi, który udostępnia metadane lub dokument metadanych hostowany w trybie online. <`epr`Argument > określa ścieżkę do pliku XML, który zawiera WS-Addressing `EndpointAddress` dla punktu końcowego usługi, który obsługuje protokół WS-MetadataExchange.  
  
 Aby uzyskać więcej opcji dotyczących używania tego narzędzia do pobierania metadanych, zobacz [Narzędzie do przesyłania metadanych programu ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="example"></a>Przykład  
 Następujące polecenie pobiera dokumenty metadanych z uruchomionej usługi.  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
