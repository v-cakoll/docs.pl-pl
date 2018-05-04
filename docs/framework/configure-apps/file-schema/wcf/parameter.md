---
title: '&lt;Parametr&gt;'
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: b9cccfe37e7658afbf2e49555e6c505497598fbb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltparametergt"></a>&lt;Parametr&gt;
Określa parametr generyczny, gdy deklarowany typ jest typem ogólnym.  
  
 \<System.Runtime.serialization >  
\<dataContractSerializer >  
\<declaredTypes > — Element  
\<Dodaj > elementu \<declaredTypes >  
\<Typ knownType > — Element  
\<Parametr > — Element  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<parameter index="integer"  
                      type=String" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|indeks|Gdy deklarowany typ jest typem ogólnym, określa parametr generyczny, który zwróci typ znany.|  
|— typ|Ciąg opisujący znany typ używany do serializacji i deserializacji.|  
  
## <a name="index-attribute"></a>Indeks atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|„0”|Pierwszy parametr typu ogólnego. Na przykład <xref:System.Collections.Generic.List%601> ma tylko jeden parametr. Jeśli jest on używany jako deklarowanego typu, indeks ustawiał "0".|  
|"1"|Drugi parametr typu ogólnego. Na przykład <xref:System.Collections.Generic.Dictionary%602> zawiera dwa parametry. Jeśli drugi parametr zwracany jest znanym typem, ustaw dla atrybutu indeksu "1".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Typ knownType >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|Określa znanym typem, który może być zwracany przez pole lub właściwość deklarowanego typu.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Zobacz [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) przykład za pomocą tego elementu.  
  
 Ten element konfiguracji nie może mieć obu atrybutów, w tym samym czasie. Jeśli oba atrybuty są ustawione, <xref:System.Configuration.ConfigurationErrorsException> występuje.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [Znane typy kontraktów danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
