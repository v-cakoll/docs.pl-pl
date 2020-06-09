---
title: 'Instrukcje: Weryfikacja skompilowanego kodu usługi za pomocą programu Svcutil.exe'
ms.date: 03/30/2017
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
ms.openlocfilehash: 6f2064c696e3186c3208a7e57dc51655056d23ea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595352"
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a>Instrukcje: Weryfikacja skompilowanego kodu usługi za pomocą programu Svcutil.exe
Za pomocą narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) można wykrywać błędy w implementacjach i konfiguracjach usług bez konieczności obsługiwania usługi.  
  
### <a name="to-validate-a-service"></a>Aby sprawdzić poprawność usługi  
  
1. Skompiluj usługę do pliku wykonywalnego i jednego lub więcej zestawów zależnych.  
  
2. Otwórz wiersz polecenia zestawu SDK  
  
3. W wierszu polecenia Uruchom narzędzie Svcutil. exe, używając następującego formatu. Aby uzyskać więcej informacji na temat różnych parametrów, zobacz Validationsection usługi w temacie [Narzędzie metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) .  
  
    ```console
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     Musisz użyć opcji, `/serviceName` Aby wskazać nazwę konfiguracji usługi, którą chcesz zweryfikować.  
  
     `assemblyPath`Argument określa ścieżkę do pliku wykonywalnego usługi i co najmniej jeden zestaw zawierający typy usługi do zweryfikowania. Zestaw wykonywalny musi mieć skojarzony plik konfiguracji, aby zapewnić konfigurację usługi. Możesz użyć standardowych symboli wieloznacznych wiersza polecenia, aby udostępnić wiele zestawów.  
  
## <a name="example"></a>Przykład  
 Następujące polecenie jest zaimplementowane w pliku wykonywalnym myServiceHost. exe.  Plik konfiguracji usługi (myServiceHost. exe. config) jest ładowany automatycznie.  
  
```console  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a>Zobacz też

- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
