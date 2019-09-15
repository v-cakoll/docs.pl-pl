---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: f12fae48f1cee198aac22e6f09e616b407b4e9b5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990068"
---
# <a name="configurationcodegenerator"></a>ConfigurationCodeGenerator
ConfigurationCodeGenerator to narzędzie, za pomocą którego można uwidocznić niestandardowe implementacje kanałów w systemie konfiguracji. Umożliwia to użytkownikom niestandardowego kanału Konfigurowanie kanału przy użyciu pliku. config tak samo jak w przypadku konfigurowania powiązania dostarczonego przez system, takiego jak `NetTcpBinding` lub niestandardowego powiązania `TcpTransportBindingElement`przy użyciu.  
  
 Podczas pisania niestandardowego kanału i uwidocznienia go w modelu programowania przy użyciu `BindingElement` nowego lub `Binding`, należy utworzyć zestaw `Binding` klas, aby można było `BindingElement` użyć pliku. config. Możesz użyć narzędzia ConfigurationCodeGenerator do wygenerowania tych klas i zwiększenia środowiska klienta.  
  
### <a name="to-build-the-tool"></a>Aby skompilować narzędzie  
  
1. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Kompilowanie rozwiązania generuje jeden plik: ConfigurationCodeGenerator.exe. Plik SampleRun. cmd zawiera przykładowy wiersz polecenia, który pokazuje, jak używać tego narzędzia do generowania klas do [transportu: Przykład](../../../../docs/framework/wcf/samples/transport-udp.md) protokołu UDP.  
  
### <a name="to-run-the-tool"></a>Aby uruchomić narzędzie  
  
1. W wierszu polecenia wpisz następujące polecenie, jeśli istnieje zarówno typ niestandardowy `BindingElement` , jak i typ niestandardowy: `Binding`  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     Lub wpisz następujące, jeśli masz tylko typ niestandardowy `BindingElement` :  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     Lub wpisz następujące, jeśli masz tylko typ niestandardowy `Binding` :  
  
    ```console  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     Polecenie generuje trzy pliki. cs dla `BindingElement` (Jeśli określono/be: opcja), pięć plików CS dla standardowego `Binding` (Jeśli określono/SB: Option) i plik. XML.  
  
    1. Jeśli użyto opcji/BE, jeden z plików CS implementuje `BindingElementExtensionSection` dla elementu powiązania. Ten kod uwidacznia `BindingElement` systemowi konfiguracji, tak aby inne powiązania niestandardowe mogły korzystać z elementu powiązania. Inne pliki zawierają klasy, które reprezentują wartości domyślne i stałe. Pliki mają `//TODO` komentarze, aby przypominać o zaktualizowaniu wartości domyślnych.  
  
    2. W przypadku wybrania opcji/SB dwa z plików CS implementują `StandardBindingElement` `StandardBindingCollectionElement` i odpowiednio, które udostępniają standardowe powiązanie z systemem konfiguracji. Inne pliki zawierają klasy, które reprezentują wartości domyślne i stałe. Pliki mają `//TODO` komentarze, aby przypominać o zaktualizowaniu wartości domyślnych.  
  
         W przypadku określenia opcji/SB: CodeToAddTo\<*YourStdBinding*>. cs ma kod, który trzeba ręcznie dodać do klasy, która implementuje powiązanie standardowe.  
  
     Plik SampleConfig. xml zawiera kod konfiguracji, który należy dodać do pliku konfiguracji, który rejestruje programy obsługi zdefiniowane w poprzednim kroku 1 lub 2.  
