---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: 5575de8a9932777a5bda49a34a108b84593e013c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33500860"
---
# <a name="configurationcodegenerator"></a>ConfigurationCodeGenerator
ConfigurationCodeGenerator to narzędzie, które można użyć do udostępnienia implementacjach użytkownika niestandardowego kanału do konfiguracji systemu. Pozwala to użytkownikom niestandardowego kanału skonfigurować kanał przy użyciu pliku .config, zgodnie z ich skonfigurowania, dostarczane przez system powiązanie takich jak `NetTcpBinding` lub niestandardowego powiązania za pomocą `TcpTransportBindingElement`.  
  
 Podczas zapisu w niestandardowym kanale i je ujawnić w modelu programowania przy użyciu nowego `BindingElement` lub `Binding`, należy utworzyć zestaw klas, aby `BindingElement` lub `Binding` można skonfigurować za pomocą pliku .config. Narzędzie ConfigurationCodeGenerator do wygenerowania tych klas i udoskonalenie procesu klienta.  
  
### <a name="to-build-the-tool"></a>Aby utworzyć narzędzie  
  
1.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Tworzenie rozwiązania generuje jeden plik: ConfigurationCodeGenerator.exe. Plik SampleRun.cmd zawiera przykładowy wiersz polecenia, który przedstawia sposób użycia to narzędzie do generowania klasy dla [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.  
  
### <a name="to-run-the-tool"></a>Aby uruchomić narzędzie  
  
1.  W wierszu polecenia wpisz następujące, jeżeli masz zarówno niestandardowego `BindingElement` typu i niestandardowej `Binding` typu:  
  
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
  
     Polecenie generuje trzy pliki .cs dla `BindingElement` (Jeśli określono /: opcja), pięć plików .cs standardu `Binding` (Jeśli określono /sb: opcja) i pliku XML.  
  
    1.  Jeśli użyto opcji /be jedną .cs plików implementuje `BindingElementExtensionSection` Twojego elementu powiązania. Ten kod przedstawia Twojej `BindingElement` do konfiguracji systemu, aby powiązania niestandardowe można użyć z elementu powiązania. Inne pliki mają klasy reprezentujące domyślne i stałe. Pliki mają `//TODO` komentarze do odnotowania można zaktualizować wartości domyślne.  
  
    2.  Jeśli określono opcję /sb zaimplementować dwa pliki .cs `StandardBindingElement` i `StandardBindingCollectionElement` odpowiednio, który udostępnia standardowe wiązania do konfiguracji systemu. Inne pliki mają klasy reprezentujące domyślne i stałe. Pliki mają `//TODO` komentarze do odnotowania można zaktualizować wartości domyślne.  
  
         Jeśli określono /sb: opcja CodeToAddTo\<*YourStdBinding*> .cs zawiera kod, który należy ręcznie dodać do klasy, który implementuje standardowe wiązania.  
  
     Plik SampleConfig.xml zawiera kod konfiguracji, które należy dodać do pliku konfiguracji, który rejestruje programy obsługi zdefiniowane w poprzednim kroku, 1 lub 2.  
  
## <a name="see-also"></a>Zobacz też
