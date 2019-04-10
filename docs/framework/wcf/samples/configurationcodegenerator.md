---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: 97197926db0b44f1ad36e2eba6ab6bec42eced33
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342014"
---
# <a name="configurationcodegenerator"></a>ConfigurationCodeGenerator
ConfigurationCodeGenerator jest narzędziem, które można użyć do udostępnienia implementacji usługi niestandardowym kanale w celu system konfiguracji. Dzięki temu użytkownicy niestandardowy kanał skonfigurować kanał przy użyciu pliku config, zgodnie z ich konfigurowania, dostarczane przez system powiązań takich jak `NetTcpBinding` lub niestandardowego powiązania za pomocą `TcpTransportBindingElement`.  
  
 Podczas zapisu w niestandardowym kanale i udostępnić ją modelu programowania przy użyciu nowego `BindingElement` lub `Binding`, należy utworzyć zestaw klas, które umożliwiają `BindingElement` lub `Binding` można konfigurować przy użyciu pliku Config. Narzędzie ConfigurationCodeGenerator do wygenerowania tych klas i poprawić funkcjonalność z perspektywy klienta.  
  
### <a name="to-build-the-tool"></a>Aby utworzyć narzędzie  
  
1. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Skompilować rozwiązanie generuje jeden plik: ConfigurationCodeGenerator.exe. Plik SampleRun.cmd zawiera przykładowy wiersz polecenia, który pokazuje, jak używać tego narzędzia do generowania klasy dla [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.  
  
### <a name="to-run-the-tool"></a>Aby uruchomić narzędzie  
  
1. W wierszu polecenia wpisz następujące polecenie, w przypadku obu niestandardowe `BindingElement` typu i niestandardowego `Binding` typu:  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     Lub wpisz następujące polecenie, jeśli masz tylko niestandardowego `BindingElement` typu:  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     Lub wpisz następujące polecenie, jeśli masz tylko niestandardowego `Binding` typu:  
  
    ```  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     Polecenie spowoduje wygenerowanie trzy pliki CS `BindingElement` (Jeśli określono / to: opcja), pięć plików .cs standardu `Binding` (Jeśli określono /sb: opcja) i pliku XML.  
  
    1.  Jeśli użyto opcji /be jeden .cs pliki implementuje `BindingElementExtensionSection` dla danego elementu powiązania. Ten kod przedstawia swoje `BindingElement` do konfiguracji systemu, aby powiązań niestandardowych można użyć usługi elementu powiązania. Inne pliki mają klas, które reprezentują stałe i wartości domyślne. Pliki mają `//TODO` komentarze, aby przypomnieć Ci można zaktualizować wartości domyślne.  
  
    2.  Jeśli określono opcję /sb dwa pliki CS zaimplementować `StandardBindingElement` i `StandardBindingCollectionElement` odpowiednio, który udostępnia standardowy wiązania do systemu konfiguracji. Inne pliki mają klas, które reprezentują stałe i wartości domyślne. Pliki mają `//TODO` komentarze, aby przypomnieć Ci można zaktualizować wartości domyślne.  
  
         Jeśli określono /sb: opcja CodeToAddTo\<*YourStdBinding*> .cs zawiera kod, należy ręcznie dodać do klasy, która implementuje standardowe wiązania.  
  
     Plik SampleConfig.xml zawiera kod konfiguracji, które należy dodać do pliku konfiguracji, który rejestruje programy obsługi zdefiniowane w poprzednim kroku, 1 lub 2.  
