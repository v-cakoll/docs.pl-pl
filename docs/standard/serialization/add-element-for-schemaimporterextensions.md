---
title: <add> — Element do <schemaImporterExtensions>
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 89196b094d5631c9e243a51a718e53f9c06db20d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270566"
---
# <a name="add-element-for-schemaimporterextensions"></a>\<add> Element for \<schemaImporterExtensions>
Dodaje typy używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> do mapowania typów XSD typów programu .NET Framework. Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md).  
  
 \<Konfiguracja >  
\<system.xml.serialization>  
\<schemaImporterExtensions>  
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
|**type**|Wymagana. Określa klasę rozszerzenia schematu do dodania. **Typu** wartość atrybutu musi być w jednym wierszu i zawierać w pełni kwalifikowana nazwa typu. Gdy zestawu znajduje się w globalnej pamięci podręcznej zestawów (GAC), to również obejmować wersji, kulturę i token klucza publicznego zestawu podpisem.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|\<schemaImporterExtensions>|Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter>.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu dodaje typ rozszerzenia, które XmlSchemaImporter można używać podczas mapowania typów.  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <schemaImporterExtensions>  
       <add name="contoso" type="System.Web.Mobile.MobileCapabilities,   
       System.Web.Mobile, Version=2.0.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a" />   
    </schemaImporterExtensions>  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [\<system.xml.serialization> Element](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [\<schemaImporterExtensions> Element](../../../docs/standard/serialization/schemaimporterextensions-element.md)
