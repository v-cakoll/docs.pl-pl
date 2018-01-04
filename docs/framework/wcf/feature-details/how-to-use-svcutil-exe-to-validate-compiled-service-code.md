---
title: "Instrukcje: Weryfikacja skompilowanego kodu usługi za pomocą programu Svcutil.exe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b60356bd66a49c9599a8e0a9138d3b92dbe0b23c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a>Instrukcje: Weryfikacja skompilowanego kodu usługi za pomocą programu Svcutil.exe
Można użyć [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do wykrywania błędów w implementacji usługi i konfiguracji bez obsługującego usługę.  
  
### <a name="to-validate-a-service"></a>Aby sprawdzić poprawność usługi  
  
1.  Kompilacji usługi do pliku wykonywalnego i jeden lub więcej zestawów zależnych.  
  
2.  Otwórz wiersz polecenia z zestawu SDK  
  
3.  W wierszu polecenia Uruchom narzędzie Svcutil.exe w następującym formacie. Aby uzyskać więcej informacji o różnych parametrów, zobacz Validationsection usługi z [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tematu.  
  
    ```  
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     Należy użyć `/serviceName` możliwość wskazania nazwy konfiguracji usługi, który chcesz zweryfikować.  
  
     `assemblyPath` Argument określa ścieżkę do pliku wykonywalnego dla usług i jeden lub więcej zestawów zawierających typów usług do sprawdzenia poprawności. Wykonywalny zestaw musi mieć skojarzony plik konfiguracji zapewnienie konfiguracji usługi. Standardowa wiersza polecenia symboli wieloznacznych służy do nadania wiele zestawów.  
  
## <a name="example"></a>Przykład  
 Polecenie myServiceName usługi zaimplementowana w pliku wykonywalnym myServiceHost.exe.  Plik konfiguracji usługi (myServiceHost.exe.config) są ładowane automatycznie.  
  
```  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
