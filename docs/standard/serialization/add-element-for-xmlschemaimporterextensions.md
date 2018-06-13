---
title: '&lt;Dodaj&gt; elementu &lt;xmlSchemaImporterExtensions&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <xmlSchemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 6e14c478e33c465d2ea3d10158f856dc5ca6c49a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581745"
---
# <a name="ltaddgt-element-for-ltxmlschemaimporterextensionsgt"></a>&lt;Dodaj&gt; elementu &lt;xmlSchemaImporterExtensions&gt;
Dodaje typy używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> do mapowania typów XSD typów programu .NET Framework. Aby uzyskać więcej informacji o plikach konfiguracji, zobacz [schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md).  
  
 \<Konfiguracja >  
\<System.XML.serialization >  
\<XmlSchemaImporterExtensions >  
\<add>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**Nazwa**|Prosta nazwa jest używana do znajdowania wystąpienia.|  
|**Typ**|Wymagana. Określa klasę rozszerzenia schematu do dodania. **Typu** wartość atrybutu musi być w jednym wierszu i zawierać pełni kwalifikowaną nazwę typu. Jeśli zestaw znajduje się w globalnej pamięci podręcznej zestawów (GAC), musi także obejmować wersję, kulturę i token klucza publicznego zestawu podpisem.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|\<xmlSchemaImporterExtensions >|Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter>.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod dodaje typ rozszerzenia, które XmlSchemaImporter można użyć w przypadku mapowania typów.  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSchemaImporterExtensions>  
       <add name="contoso" type="System.Web.Mobile.MobileCapabilities,   
       System.Web.Mobile, Version=2.0.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a" />   
    </xmlSchemaImporterExtensions>  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 [\<system.xml.serialization> Element](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 [\<schemaImporterExtensions > — Element](../../../docs/standard/serialization/schemaimporterextensions-element.md)
