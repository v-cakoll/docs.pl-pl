---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 22ef3c3c6d23d6c68c27d6b5d1ed35b7c9910d48
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783438"
---
# <a name="parameter"></a>\<parameter>
Określa parametr generyczny, gdy deklarowany typ jest typem ogólnym.  
  
 \<system.runtime.serialization>  
\<dataContractSerializer>  
\<declaredTypes > Element  
\<Dodaj >, element dla \<declaredTypes >  
\<knownType> Element  
\<parameter> Element  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<parameter index="Integer"
           type="String" />
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
|„0”|Pierwszy parametr w typie ogólnym. Na przykład <xref:System.Collections.Generic.List%601> ma tylko jeden parametr. Jeśli jest używany jako typ zadeklarowany, indeksem będzie miał ustawienie "0".|  
|"1"|Drugi parametr typu ogólnego. Na przykład <xref:System.Collections.Generic.Dictionary%602> zawiera dwa parametry. Jeśli znany typ zwracany przez drugi parametr, należy ustawić atrybutu indeksu "1".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Element knownType >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|Określa znany typ, który może zostać zwrócony przez pole lub właściwość zadeklarowanym typem.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Zobacz [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) na przykład przy użyciu tego elementu.  
  
 Ten element konfiguracji nie może mieć obu atrybutów, w tym samym czasie. Jeśli oba atrybuty są ustawione, <xref:System.Configuration.ConfigurationErrorsException> występuje.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [Znane typy kontraktów danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
