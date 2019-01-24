---
title: '&lt;xmlSerializer&gt; Element'
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: 4b511dc229c9e8321b91fbb0f9395627680e5d12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591958"
---
# <a name="ltxmlserializergt-element"></a>&lt;xmlSerializer&gt; Element
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
