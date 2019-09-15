---
title: 'Instrukcje: weryfikacja skompilowanego kodu usługi za pomocą programu Svcutil.exe'
ms.date: 03/30/2017
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
ms.openlocfilehash: be8755ab4281b40d23ea4c8674c8c4f33631e7b6
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991593"
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a>Instrukcje: weryfikacja skompilowanego kodu usługi za pomocą programu Svcutil.exe
Za pomocą narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) można wykrywać błędy w implementacjach i konfiguracjach usług bez konieczności obsługiwania usługi.  
  
### <a name="to-validate-a-service"></a>Aby sprawdzić poprawność usługi  
  
1. Skompiluj usługę do pliku wykonywalnego i jednego lub więcej zestawów zależnych.  
  
2. Otwórz wiersz polecenia zestawu SDK  
  
3. W wierszu polecenia Uruchom narzędzie Svcutil. exe, używając następującego formatu. Aby uzyskać więcej informacji na temat różnych parametrów, zobacz Validationsection usługi w temacie [Narzędzie metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) .  
  
    ```console
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     Musisz użyć `/serviceName` opcji, aby wskazać nazwę konfiguracji usługi, którą chcesz zweryfikować.  
  
     `assemblyPath` Argument określa ścieżkę do pliku wykonywalnego usługi i co najmniej jeden zestaw zawierający typy usługi do zweryfikowania. Zestaw wykonywalny musi mieć skojarzony plik konfiguracji, aby zapewnić konfigurację usługi. Możesz użyć standardowych symboli wieloznacznych wiersza polecenia, aby udostępnić wiele zestawów.  
  
## <a name="example"></a>Przykład  
 Następujące polecenie jest zaimplementowane w pliku wykonywalnym myServiceHost. exe.  Plik konfiguracji usługi (myServiceHost. exe. config) jest ładowany automatycznie.  
  
```console  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
