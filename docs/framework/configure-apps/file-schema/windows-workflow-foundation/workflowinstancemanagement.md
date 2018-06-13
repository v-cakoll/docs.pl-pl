---
title: '&lt;workflowInstanceManagement&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: d86b0f61c6741fa156e04da75a62853f459324d1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767105"
---
# <a name="ltworkflowinstancemanagementgt"></a>&lt;workflowInstanceManagement&gt;
Zachowanie usługi, które umożliwia określenie ustawień, które kontrolują, jak są uruchamiane wystąpienia przepływu pracy, łącznie z trwałości, nieobsługiwanych wyjątków zachowanie i zachowanie bezczynności.  
  
\<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<workflowInstanceManagement >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|authorizedWindowsGroup||  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie > z \<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Określa zachowanie elementu.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
