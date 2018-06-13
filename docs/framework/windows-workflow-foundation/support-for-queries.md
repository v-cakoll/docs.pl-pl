---
title: Obsługa zapytań
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: 5c46ed5ae2fc2cc2275bfa7251fe5f8fa346c1f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517994"
---
# <a name="support-for-queries"></a>Obsługa zapytań
W magazynie wystąpień przepływu pracy SQL rejestruje zestaw dobrze znanych właściwości w magazynie. Użytkownicy mogą wykonywać kwerendę o wystąpień na podstawie tych właściwości. Poniższa lista zawiera niektóre z tych znanych właściwości:  
  
-   **Nazwa witryny.** Nazwa witryny sieci Web, który zawiera tę usługę.  
  
-   **Ścieżka względna aplikacji.** Ścieżka aplikacji względem witryny sieci Web.  
  
-   **Ścieżka względna usługi.** Ścieżka usługi względem aplikacji.  
  
-   **Nazwa usługi.** Nazwa usługi.  
  
-   **Usługa Namespace.** Nazwa przestrzeni nazw, która korzysta z usługi.  
  
-   **Bieżącego komputera.**  
  
-   **Ostatni maszyny**. Komputer, na którym został uruchomiony podczas ostatniego wystąpienia usługi przepływu pracy.  
  
> [!NOTE]
>  W przypadku scenariuszy hostowania samoobsługowego przy użyciu hosta usługi przepływu pracy są wypełniane tylko cztery ostatnie właściwości. W przypadku scenariuszy aplikacji przepływu pracy jest wypełniana tylko ostatnich właściwości.  
  
 Środowiska uruchomieniowego przepływu pracy, dostarcza wartości dla właściwości pierwsze trzy. Hosta usługi przepływu pracy, dostarcza wartość **zawiesić Przyczyna** właściwości. Samego magazynu wystąpienia przepływu pracy SQL dostarcza wartości dla **ostatnia maszyna zaktualizowane** właściwości.  
  
 Funkcja magazynu wystąpienia przepływu pracy SQL umożliwia także określić, czy właściwości niestandardowe, dla których mają być przechowywane w bazie danych trwałości i wartości mają być używane w zapytaniach. Aby uzyskać więcej informacji o promocjach niestandardowych, zobacz [rozszerzalności magazynu](../../../docs/framework/windows-workflow-foundation/store-extensibility.md).  
  
## <a name="views"></a>Widoki  
 W magazynie wystąpień zawiera następujące widoki. Zobacz [schematu bazy danych trwałości](../../../docs/framework/windows-workflow-foundation/persistence-database-schema.md) uzyskać więcej szczegółowych informacji.  
  
### <a name="the-instances-view"></a>Widok wystąpień  
 Widok wystąpień zawiera następujące pola:  
  
1.  **Id**  
  
2.  **PendingTimer**  
  
3.  **CreationTime**  
  
4.  **LastUpdatedTime**  
  
5.  **ServiceDeploymentId**  
  
6.  **SuspensionExceptionName**  
  
7.  **SuspensionReason**  
  
8.  **ActiveBookmarks**  
  
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
  
1.  **Nazwa witryny**  
  
2.  **RelativeServicePath**  
  
3.  **RelativeApplicationPath**  
  
4.  **ServiceName**  
  
5.  **ServiceNamespace**  
  
### <a name="the-instancepromotedproperties-view"></a>Widok InstancePromotedProperties  
 Widok InstancePromotedProperties zawiera następujące pola. Aby uzyskać więcej informacji na temat awansowanej właściwości, zobacz [rozszerzalności magazynu](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) tematu.  
  
1.  **Identyfikator wystąpienia**  
  
2.  **EncodingOption**  
  
3.  **PromotionName**  
  
4.  **Wartość #** (zakresu pola z **wartość1** do **Value64**).
