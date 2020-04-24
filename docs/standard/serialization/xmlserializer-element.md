---
title: <xmlSerializer>, element
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: b83ecda30bba8af1f3175eb6ad08593b07a80e6c
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249542"
---
# <a name="xmlserializer-element"></a>\<Element XmlSerializer>
Określa, czy dodatkowe wyboru postęp <xref:System.Xml.Serialization.XmlSerializer> jest wykonywane.  
  
 \<> konfiguracji  
\<> system. XML. Serialization  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**checkDeserializeAdvances**|Określa, czy postęp <xref:System.Xml.Serialization.XmlSerializer> jest zaznaczone. Atrybut "prawda" lub "false". Wartość domyślna to "true".|  
|**useLegacySerializationGeneration**|Określa, czy <xref:System.Xml.Serialization.XmlSerializer> używa Generowanie starszego serializacji, generująca zestawy zapis do PLiku kodu C# i zestawiania do zestawu. Wartość domyślna to **false**.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Element> system. XML. Serialization](../../../docs/standard/serialization/system-xml-serialization-element.md)|Zawiera ustawienia konfiguracji dla <xref:System.Xml.Serialization.XmlSerializer> i <xref:System.Xml.Serialization.XmlSchemaImporter> klasy.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie <xref:System.Xml.Serialization.XmlSerializer> zapewnia dodatkową warstwę zabezpieczeń przed potencjalnym atakom typu odmowa usługi podczas deserializacji niezaufanych danych. Robi to za pomocą próby wykrycia podczas deserializacji w pętli nieskończonej. W przypadku wykrycia takiego warunku zostanie zgłoszony wyjątek z następującym komunikatem: "błąd wewnętrzny: deserializacja nie powiodła się przed strumieniem bazowym".  
  
 Odbieranie ten komunikat nie musi oznaczać, że typu "odmowa usługi" jest w toku. W niektórych sytuacjach szczególnych mechanizm wykrywania pętli nieskończonej tworzy fałszywego ostrzeżenia i wyjątku wiarygodnego wiadomości przychodzącej. Jeśli okaże się, że w konkretnej aplikacji legalne komunikaty są odrzucane przez tę dodatkową warstwę ochrony, ustaw atrybut **checkDeserializeAdvances** na wartość "false".  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu ustawia atrybut **checkDeserializeAdvances** na wartość "false".  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Serialization.XmlSerializer>
- [\<Element> system. XML. Serialization](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [Serializacja XML i SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)
