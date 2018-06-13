---
title: '&lt;workflowUnhandledException&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: d9db6ecc2e95e0d1ec5738f1d2f4a09a89c57f21
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755139"
---
# <a name="ltworkflowunhandledexceptiongt"></a>&lt;workflowUnhandledException&gt;
Zachowanie usługi, który umożliwia określenie Akcja podejmowana po wystąpieniu nieobsługiwanego wyjątku w ramach usługi przepływu pracy.  
  
\<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<workflowUnhandledException >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Akcja|Ciąg, który określa akcję, która ma zostać podjęta po wystąpieniu nieobsługiwanego wyjątku. Ten atrybut nie ma typu<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction>|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie > z \<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Określa zachowanie elementu.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
