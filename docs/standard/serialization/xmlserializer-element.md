---
title: <xmlSerializer>, element
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: 2919e8d4c1af858973ff3d2b58b4d3bc4f925527
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55258256"
---
# <a name="xmlserializer-element"></a>\<xmlSerializer> Element
Określa, czy dodatkowe wyboru postęp <xref:System.Xml.Serialization.XmlSerializer> jest wykonywane.  
  
 \<Konfiguracja >  
\<system.xml.serialization>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true"|"false" />  
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
|[\<system.xml.serialization> Element](../../../docs/standard/serialization/system-xml-serialization-element.md)|Zawiera ustawienia konfiguracji dla <xref:System.Xml.Serialization.XmlSerializer> i <xref:System.Xml.Serialization.XmlSchemaImporter> klasy.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie <xref:System.Xml.Serialization.XmlSerializer> zapewnia dodatkową warstwę zabezpieczeń przed potencjalnym atakom typu odmowa usługi podczas deserializacji niezaufanych danych. Robi to za pomocą próby wykrycia podczas deserializacji w pętli nieskończonej. Po wykryciu tych warunków, wyjątek zgłaszany następujący komunikat o błędzie: "Błąd wewnętrzny: Deserializacja nie powiodła się przejść na zasadniczy strumień."  
  
 Odbieranie ten komunikat nie musi oznaczać, że typu "odmowa usługi" jest w toku. W niektórych sytuacjach szczególnych mechanizm wykrywania pętli nieskończonej tworzy fałszywego ostrzeżenia i wyjątku wiarygodnego wiadomości przychodzącej. Jeśli okaże się, że w określonej aplikacji istotnych wiadomości są odrzucane przez ten dodatkową warstwę ochrony, ustaw **checkDeserializeAdvances** atrybutu "false".  
  
## <a name="example"></a>Przykład  
 Poniższy kod ustawia przykład **checkDeserializeAdvances** atrybutu "false".  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Serialization.XmlSerializer>
- [\<system.xml.serialization> Element](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [Serializacja XML i SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)
