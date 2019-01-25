---
title: 'Instrukcje: Weryfikacja skompilowanego kodu usługi za pomocą programu Svcutil.exe'
ms.date: 03/30/2017
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
ms.openlocfilehash: a06cf57fce883753af4686b294396d6d6da73a13
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531931"
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a>Instrukcje: Weryfikacja skompilowanego kodu usługi za pomocą programu Svcutil.exe
Możesz użyć [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do wykrywania błędów w implementacji usługi i konfiguracji bez obsługującego usługę.  
  
### <a name="to-validate-a-service"></a>Aby sprawdzić poprawność usługi  
  
1.  Kompiluj usługi do pliku wykonywalnego i jeden lub więcej zestawów zależnych.  
  
2.  Otwórz wiersz polecenia z zestawu SDK  
  
3.  W wierszu polecenia Uruchom narzędzia Svcutil.exe w następującym formacie. Aby uzyskać więcej informacji na temat różnych parametrów, zobacz Validationsection usługi z [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tematu.  
  
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
