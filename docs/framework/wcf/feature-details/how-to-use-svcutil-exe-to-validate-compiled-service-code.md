---
title: 'Instrukcje: weryfikacja skompilowanego kodu usługi za pomocą programu Svcutil.exe'
ms.date: 03/30/2017
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
ms.openlocfilehash: 599f5624b7eb0c32cbcc0a78e6c7f989ce470b58
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312426"
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a>Instrukcje: weryfikacja skompilowanego kodu usługi za pomocą programu Svcutil.exe
Możesz użyć [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do wykrywania błędów w implementacji usługi i konfiguracji bez obsługującego usługę.  
  
### <a name="to-validate-a-service"></a>Aby sprawdzić poprawność usługi  
  
1. Kompiluj usługi do pliku wykonywalnego i jeden lub więcej zestawów zależnych.  
  
2. Otwórz wiersz polecenia z zestawu SDK  
  
3. W wierszu polecenia Uruchom narzędzia Svcutil.exe w następującym formacie. Aby uzyskać więcej informacji na temat różnych parametrów, zobacz Validationsection usługi z [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tematu.  
  
    ```  
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     Należy użyć `/serviceName` opcję, aby wskazać nazwę konfiguracji usługi, którą chcesz zweryfikować.  
  
     `assemblyPath` Argument określa ścieżkę do pliku wykonywalnego dla usługi i jeden lub więcej zestawów zawierających typy usług, które ma zostać zweryfikowana. Zestawu pliku wykonywalnego musi mieć skojarzony plik konfiguracji do zapewnienia konfiguracji usługi. Zapewnienie wiele zestawów, można użyć standardowych symboli wieloznacznych wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 Polecenie myServiceName usługę, zaimplementowane w pliku wykonywalnym myServiceHost.exe.  Plik konfiguracji usługi (myServiceHost.exe.config) jest automatycznie ładowany.  
  
```  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
