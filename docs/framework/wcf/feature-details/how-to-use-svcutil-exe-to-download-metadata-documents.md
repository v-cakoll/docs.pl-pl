---
title: 'Instrukcje: Używanie programu Svcutil.exe do pobierania dokumentów metadanych'
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 359cdb58ef65c9fb69c0ecfc759f70164a369cce
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212112"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>Instrukcje: Używanie programu Svcutil.exe do pobierania dokumentów metadanych
Programu Svcutil. exe można użyć do pobierania metadanych z uruchomionych usług i zapisywania metadanych w plikach lokalnych. W przypadku schematów adresów URL protokołu HTTP i HTTPS Svcutil. exe próbuje pobrać metadane za pomocą usługi WS-MetadataExchange i [odnajdowania usług sieci Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)). W przypadku wszystkich innych schematów adresów URL Svcutil. exe używa tylko protokołu WS-MetadataExchange.  
  
 Domyślnie Svcutil. exe używa powiązań zdefiniowanych w klasie <xref:System.ServiceModel.Description.MetadataExchangeBindings>. Aby skonfigurować powiązanie używane dla protokołu WS-MetadataExchange, należy zdefiniować punkt końcowy klienta w pliku konfiguracyjnym programu Svcutil. exe (Svcutil. exe. config), który używa kontraktu `IMetadataExchange` i który ma taką samą nazwę jak schemat Uniform Resource Identifier (URI) adresu punktu końcowego metadanych.  
  
> [!CAUTION]
> Podczas uruchamiania programu Svcutil. exe w celu uzyskania metadanych dla usługi, która ujawnia dwie różne kontrakty usługi, które zawierają operacje o tej samej nazwie, Svcutil. exe wyświetla błąd mówiący "nie można uzyskać metadanych z..." Na przykład jeśli masz usługę, która ujawnia kontrakt usługi o nazwie `ICarService`, która ma `Get(Car c)` operacji, a ta sama usługa ujawnia kontrakt usługi o nazwie `IBookService`, która ma `Get(Book b)`operacji. Aby obejść ten problem, wykonaj jedną z następujących czynności:
>
> - Zmień nazwę jednej z operacji.
> - Ustaw <xref:System.ServiceModel.OperationContractAttribute.Name%2A> na inną nazwę.
> - Ustaw jedną z przestrzeni nazw operacji na inną przestrzeń nazw przy użyciu właściwości <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A>.
  
## <a name="to-download-metadata-using-svcutilexe"></a>Aby pobrać metadane przy użyciu programu Svcutil. exe  
  
1. Znajdź narzędzie Svcutil. exe w następującej lokalizacji:  
  
     C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin  
  
2. W wierszu polecenia Uruchom narzędzie przy użyciu następującego formatu.  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     Należy określić opcję `/t:metadata`, aby pobrać metadane. W przeciwnym razie jest generowany kod i konfiguracja klienta.  
  
3. <`url`> argument określa adres URL punktu końcowego usługi, który udostępnia metadane lub dokument metadanych hostowany w trybie online. `epr`> argument określa ścieżkę do pliku XML, który zawiera `EndpointAddress` adresu WS-Addressing dla punktu końcowego usługi, który obsługuje protokół WS-MetadataExchange.  
  
 Aby uzyskać więcej opcji dotyczących używania tego narzędzia do pobierania metadanych, zobacz [Narzędzie do przesyłania metadanych programu ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="example"></a>Przykład  
 Następujące polecenie pobiera dokumenty metadanych z uruchomionej usługi.  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
