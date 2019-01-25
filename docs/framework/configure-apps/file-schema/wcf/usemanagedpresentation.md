---
title: '&lt;useManagedPresentation&gt;'
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: 96490421addfadd9cef6b65bddaed0aae3370d15
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720278"
---
# <a name="ltusemanagedpresentationgt"></a>&lt;useManagedPresentation&gt;
Element powiązania, używany do komunikacji z usługi tokenów zabezpieczeń CardSpace obsługującego profil CardSpace WS-Trust. Ten element nie ma atrybutu i ma jako pustego przełącznika.  
  
 \<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<useManagedPresentation>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie funkcje powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element jest używany przez dostawcę tożsamości do wyrażenia w zasadach fakt, że obsługuje ona profil CardSpace WS-Trust. Dostawcy tożsamości, których publikowanie asercję zasad powinno być możliwe do tokenów problem, w oparciu o ten profil CardSpace.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
