---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 123f58ee3d77bf605db21fa0d9537b3196d56468
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919111"
---
# <a name="enablewebscript"></a>\<enableWebScript >
Ten element włącza zachowanie punktu końcowego, który umożliwia korzystanie z usługi z ASP.NET AJAX stron sieci Web.  
  
 \<system.ServiceModel>  
\<> zachowań  
\<endpointBehaviors>  
\<> zachowania  
\<enableWebScript >  
  
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
|[\<> zachowania](behavior-of-endpointbehaviors.md)|Określa zestaw zachowań punktów końcowych.|  
  
## <a name="remarks"></a>Uwagi  
 Tego zachowania należy używać tylko w połączeniu z [ \<](webhttpbinding.md) elementem WebHttpBinding > [ \<](webmessageencoding.md) powiązanie standardowe lub webMessageEncoding > powiązania.  Aby uzyskać więcej informacji na temat tego zachowania <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>, zobacz.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [Obsługa integracji AJAX i notacji JSON](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttp>](webhttp.md)
