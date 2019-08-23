---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: e67cc316b8747ee785055ceb4f954988fa82a44c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940617"
---
# <a name="usemanagedpresentation"></a>\<useManagedPresentation >
Element powiązania używany do komunikowania się z usługą tokenu zabezpieczającego CardSpace obsługującą profil CardSpace usługi WS-Trust. Ten element nie ma atrybutu i jest obecny jako pusty przełącznik.  
  
 \<system.serviceModel>  
\<> powiązań  
\<customBinding>  
\<> powiązania  
\<useManagedPresentation >  
  
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
|[\<> powiązania](../../../misc/binding.md)|Definiuje wszystkie możliwości powiązań niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element jest używany przez dostawcę tożsamości do wyrażenia w jego zasadom faktu, że obsługuje profil CardSpace usługi WS-Trust. Dostawcy tożsamości, którzy publikują takie potwierdzenie zasad, powinni mieć możliwość wystawiania tokenów opartych na tym profilu programu CardSpace.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
