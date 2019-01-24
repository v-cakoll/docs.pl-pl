---
title: '&lt;enableWebScript&gt;'
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 1115b598776ca7d28698815974e06f3de57be598
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600105"
---
# <a name="ltenablewebscriptgt"></a>&lt;enableWebScript&gt;
Ten element włącza zachowanie punktu końcowego, który pozwala na korzystanie z usługi z ASP.NET AJAX stron sieci web.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<endpointBehaviors>  
\<zachowanie >  
\<enableWebScript>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zestaw zachowań punktu końcowego.|  
  
## <a name="remarks"></a>Uwagi  
 To zachowanie należy używać tylko w połączeniu z oboma [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) Powiązanie standardowe lub [ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) element powiązania.  Aby uzyskać więcej informacji na temat tego zachowania, zobacz <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [Obsługa integracji AJAX i notacji JSON](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttp>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
