---
title: Obsługa zapytań
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: e281b5ae7a41bd282f8e7c7eb9db6f99ef5487f3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948937"
---
# <a name="support-for-queries"></a>Obsługa zapytań
Magazyn wystąpień przepływu pracy SQL rejestruje zestaw dobrze znanych właściwości w sklepie. Użytkownicy mogą wykonywać zapytania o wystąpienia na podstawie tych właściwości. Poniższa lista zawiera niektóre z tych dobrze znanych właściwości:  
  
- **Nazwa witryny.** Nazwa witryny sieci Web zawierającej usługę.  
  
- **Względna ścieżka aplikacji.** Ścieżka aplikacji względem witryny sieci Web.  
  
- **Względna ścieżka do usługi.** Ścieżka usługi względem aplikacji.  
  
- **Nazwa usługi.** Nazwa usługi.  
  
- **Przestrzeń nazw usługi.** Nazwa przestrzeni nazw używanej przez usługę.  
  
- **Bieżąca maszyna.**  
  
- **Ostatnia maszyna**. Komputer, na którym uruchomiono wystąpienie usługi przepływu pracy po raz ostatni.  
  
> [!NOTE]
> W przypadku scenariuszy samodzielnych przy użyciu hosta usługi przepływu pracy są wypełniane tylko ostatnie cztery właściwości. W przypadku scenariuszy aplikacji przepływu pracy tylko Ostatnia właściwość jest wypełniana.  
  
 Środowisko uruchomieniowe przepływu pracy dostarcza wartości dla pierwszych trzech właściwości. Host usługi przepływu pracy dostarcza wartość właściwości **Przyczyna wstrzymania** . W przypadku wystąpienia przepływu pracy SQL są przechowywane wartości dla **ostatniej zaktualizowanej właściwości maszyny** .  
  
 Funkcja magazynu wystąpień przepływu pracy SQL umożliwia również określenie właściwości niestandardowych, dla których mają być przechowywane wartości w bazie danych trwałości i które mają być używane w zapytaniach. Aby uzyskać więcej informacji na temat promocji niestandardowych, zobacz [rozszerzanie magazynu](store-extensibility.md).  
  
## <a name="views"></a>Widoki  
 Magazyn wystąpień zawiera następujące widoki: Aby uzyskać więcej informacji, zobacz [schemat bazy danych trwałości](persistence-database-schema.md) .  
  
### <a name="the-instances-view"></a>Widok wystąpień  
 Widok wystąpienia zawiera następujące pola:  
  
1. **Identyfikator**  
  
2. **PendingTimer**  
  
3. **CreationTime**  
  
4. **LastUpdatedTime**  
  
5. **ServiceDeploymentId**  
  
6. **SuspensionExceptionName**  
  
7. **SuspensionReason**  
  
8. **ActiveBookmarks**  
  
9. **CurrentMachine**  
  
10. **LastMachine**  
  
11. **ExecutionStatus**  
  
12. **IsInitialized**  
  
13. **Issuspended**  
  
14. **IsCompleted**  
  
15. **EncodingOption**  
  
16. **ReadWritePrimitiveDataProperties**  
  
17. **WriteOnlyPrimitiveDataProperties**  
  
18. **ReadWriteComplexDataProperties**  
  
19. **WriteOnlyComplexDataProperties**  
  
### <a name="the-servicedeployments-view"></a>Widok ServiceDeployments  
 Widok ServiceDeployments zawiera następujące pola:  
  
1. **SiteName**  
  
2. **RelativeServicePath**  
  
3. **RelativeApplicationPath**  
  
4. **ServiceName**  
  
5. **Przestrzeń nazw**  
  
### <a name="the-instancepromotedproperties-view"></a>Widok InstancePromotedProperties  
 Widok InstancePromotedProperties zawiera następujące pola. Aby uzyskać szczegółowe informacje na temat podwyższonych właściwości, zobacz temat [rozszerzalność magazynu](store-extensibility.md) .  
  
1. **Identyfikator wystąpienia**  
  
2. **EncodingOption**  
  
3. **Podwyższanie poziomu**  
  
4. **Wartość #** (zakres pól od **wartość1** do **Value64**).
