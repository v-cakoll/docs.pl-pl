---
title: Obsługa zapytań
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: 30695fcd791a0d69c31a897068d69838c80c3957
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307954"
---
# <a name="support-for-queries"></a>Obsługa zapytań
Store wystąpienia przepływu pracy SQL rejestruje zestaw właściwości dobrze znane w magazynie. Użytkownicy mogą wyszukiwać wystąpień na podstawie tych właściwości. Poniższa lista zawiera niektóre z tych znanych właściwości:  
  
-   **Nazwa witryny.** Nazwa witryny sieci Web, które zawiera tę usługę.  
  
-   **Ścieżka względna aplikacji.** Ścieżka aplikacji względem witryny sieci Web.  
  
-   **Relative Service Path.** Ścieżka usługi względem aplikacji.  
  
-   **Nazwa usługi.** Nazwa usługi.  
  
-   **Usługa Namespace.** Nazwa przestrzeni nazw, używanymi przez usługę.  
  
-   **Bieżąca maszyna.**  
  
-   **Ostatnie maszyny**. Komputer, na którym został uruchomiony ostatniego wystąpienia usługi przepływu pracy.  
  
> [!NOTE]
>  W przypadku scenariuszy samodzielnie hostowany przy użyciu hosta usługi przepływu pracy są wypełniane tylko cztery ostatnie właściwości. W przypadku scenariuszy aplikacji przepływu pracy jest wypełniana tylko ostatnie właściwości.  
  
 Środowisko wykonawcze przepływów pracy dostarcza wartości dla pierwszych trzech właściwości. Hosta usługi przepływu pracy dostarcza wartość **zawiesić Przyczyna** właściwości. Store wystąpienia przepływu pracy SQL, sama dostarcza wartości dla **ostatnia maszyna zaktualizowane** właściwości.  
  
 Funkcja Store wystąpienia przepływu pracy SQL umożliwia także określić właściwości niestandardowe, dla których mają być przechowywane wartości w bazie danych trwałości i chcesz używać w zapytaniach. Aby uzyskać więcej informacji na temat niestandardowych promocji zobacz [rozszerzalności Store](store-extensibility.md).  
  
## <a name="views"></a>Widoki  
 Magazyn wystąpienie zawiera następujące widoki. Zobacz [schemat bazy danych trwałości](persistence-database-schema.md) więcej szczegółowych informacji.  
  
### <a name="the-instances-view"></a>Wyświetl wystąpienia  
 Widok wystąpień zawiera następujące pola:  
  
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
  
13. **IsSuspended**  
  
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
  
5. **ServiceNamespace**  
  
### <a name="the-instancepromotedproperties-view"></a>Widok InstancePromotedProperties  
 Widok InstancePromotedProperties zawiera następujące pola. Aby uzyskać więcej informacji na temat właściwości o podwyższonym poziomie, zobacz [rozszerzalności Store](store-extensibility.md) tematu.  
  
1. **InstanceId**  
  
2. **EncodingOption**  
  
3. **PromotionName**  
  
4. **Wartość #** (zakres pola z **wartość1** do **Value64**).
