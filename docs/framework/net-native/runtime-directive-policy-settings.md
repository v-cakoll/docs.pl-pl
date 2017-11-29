---
title: "Ustawienia zasad dyrektyw środowiska uruchomieniowego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb52b1ef-47fd-4609-b69d-0586c818ac9e
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 969b2468b9b627d9b69f02209f30362edbbcce3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="runtime-directive-policy-settings"></a>Ustawienia zasad dyrektyw środowiska uruchomieniowego
> [!NOTE]
>  W tym temacie odnosi się do .NET Native Developer Preview, która jest wersja wstępna oprogramowania. Możesz pobrać podglądu [witryny sieci Web Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=394611) (wymaga rejestracji).  
  
 Ustawienia zasad dyrektyw środowiska uruchomieniowego dla platformy .NET Native ustalić dostępność metadanych typy i elementy członkowskie typu w czasie wykonywania. Bez potrzeby metadanych operacje, które opierają się na odbicia serializacji i deserializacji i przekazywanie typów .NET Framework do modelu COM lub środowiska uruchomieniowego systemu Windows można zakończyć się niepowodzeniem i zgłosić wyjątek. Najbardziej typowe wyjątki są [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) i (w przypadku interop) [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md).  
  
 Środowisko uruchomieniowe ustawienia zasad są kontrolowane przez dyrektyw środowiska uruchomieniowego (. rd.xml) pliku. Każdy dyrektyw środowiska uruchomieniowego definiuje zasady dla elementu określonego programu, takich jak zestaw ( [ \<zestawu >](../../../docs/framework/net-native/assembly-element-net-native.md) element), typ ( [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) element), lub metody ( [ \<metody >](../../../docs/framework/net-native/method-element-net-native.md) elementu). Dyrektywa zawiera jeden lub więcej atrybutów definiujących odbicia typów zasad, serializacji typów zasad i typy międzyoperacyjne zasad omówiona w następnej sekcji. Wartość atrybutu definiują ustawienia zasad.  
  
## <a name="policy-types"></a>Typy zasad  
 Pliki rozpoznaje trzy kategorie typów zasad dyrektyw środowiska uruchomieniowego: odbicia, serializacji i interop.  
  
-   Typy zasad odbicia określają, które metadane są udostępniane w czasie wykonywania w celu odbicia:  
  
    -   `Activate`Służy do sterowania dostępem środowiska uruchomieniowego konstruktorów, aby włączyć aktywacji wystąpień.  
  
    -   `Browse`Formanty wykonywania zapytania dotyczącego informacji o programie elementów.  
  
    -   `Dynamic`Formanty środowiska uruchomieniowego dostęp do wszystkich typów i członków, aby włączyć dynamiczne programowania.  
  
     W poniższej tabeli wymieniono odbicia typów zasad i elementów programu, które mogą być używane.  
  
    |Element|Aktywuj|Przeglądaj|dynamiczne|  
    |-------------|--------------|------------|-------------|  
    |[\<Aplikacji >](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|  
    |[\<Zestaw >](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|  
    |[\<AttributeImplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|  
    |[\<Zdarzenie >](../../../docs/framework/net-native/event-element-net-native.md)||✓|✓|  
    |[\<Pole >](../../../docs/framework/net-native/field-element-net-native.md)||✓|✓|  
    |[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|✓|✓|✓|  
    |[\<ImpliesType >](../../../docs/framework/net-native/impliestype-element-net-native.md)|✓|✓|✓|  
    |[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)||✓|✓|  
    |[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)||✓|✓|  
    |[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|✓|✓|✓|  
    |[\<Parametr >](../../../docs/framework/net-native/parameter-element-net-native.md)|✓|✓|✓|  
    |[\<Właściwość >](../../../docs/framework/net-native/property-element-net-native.md)||✓|✓|  
    |[\<Subtypes >](../../../docs/framework/net-native/subtypes-element-net-native.md)|✓|✓|✓|  
    |[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|✓|✓|✓|  
    |[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|✓|✓|✓|  
    |[\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)|✓|✓|✓|  
  
-   Typy zasad serializacji określają, które metadane są udostępniane w czasie wykonywania do serializacji i deserializacji:  
  
    -   `Serialize`Służy do sterowania dostępem środowiska uruchomieniowego konstruktorów, pól i właściwości, aby umożliwić wystąpień typów można było serializować przez biblioteki innych firm, takich jak serializator Newtonsoft JSON.  
  
    -   `DataContractSerializer`Służy do sterowania dostępem środowiska uruchomieniowego konstruktorów, pól i właściwości, aby umożliwić wystąpień typów przez <xref:System.Runtime.Serialization.DataContractSerializer> klasy.  
  
    -   `DataContractJsonSerializer`Służy do sterowania dostępem środowiska uruchomieniowego konstruktorów, pól i właściwości, aby umożliwić wystąpień typów przez <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> klasy.  
  
    -   `XmlSerializer`Służy do sterowania dostępem środowiska uruchomieniowego konstruktorów, pól i właściwości, aby umożliwić wystąpień typów przez <xref:System.Xml.Serialization.XmlSerializer> klasy.  
  
     W poniższej tabeli wymieniono serializacji typów zasad i elementów programu, które mogą być używane.  
  
    |Element|serializacji|DataContractSerializer|Klasa DataContractJsonSerializer|Element XmlSerializer|  
    |-------------|---------------|----------------------------|--------------------------------|-------------------|  
    |[\<Aplikacji >](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Zestaw >](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|✓|  
    |[\<AttributeImplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Zdarzenie >](../../../docs/framework/net-native/event-element-net-native.md)|||||  
    |[\<Pole >](../../../docs/framework/net-native/field-element-net-native.md)|✓||||  
    |[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|✓|✓|✓|✓|  
    |[\<ImpliesType >](../../../docs/framework/net-native/impliestype-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)|||||  
    |[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|||||  
    |[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Parametr >](../../../docs/framework/net-native/parameter-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Właściwość >](../../../docs/framework/net-native/property-element-net-native.md)|✓||||  
    |[\<Subtypes >](../../../docs/framework/net-native/subtypes-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|✓|✓|✓|✓|  
    |[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|✓|✓|✓|✓|  
    |[\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)|✓|✓|✓|✓|  
  
-   Typy międzyoperacyjne zasad należy ustalić metadanych, które ma zostać udostępnione w czasie wykonywania do przekazania typy odwołań, typy wartości i wskaźniki funkcji COM i środowiska wykonawczego systemu Windows:  
  
    -   `MarshalObject`Steruje natywnym, organizowanie COM i środowiska wykonawczego systemu Windows dla typów odwołań.  
  
    -   `MarshalDelegate`Steruje natywnym, przekazywanie typów delegatów jako wskaźników funkcji.  
  
    -   `MarshalStructure`Steruje natywnym, organizowanie COM i środowiska wykonawczego systemu Windows dla typów wartości.  
  
     W poniższej tabeli wymieniono typy międzyoperacyjne zasad i elementów programu, które mogą być używane.  
  
    |Element|MarshalObject|MarshalDelegate|MarshalStructure|  
    |-------------|-------------------|---------------------|----------------------|  
    |[\<Aplikacji >](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|  
    |[\<Zestaw >](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|  
    |[\<AttributeImplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|  
    |[\<Zdarzenie >](../../../docs/framework/net-native/event-element-net-native.md)||||  
    |[\<Pole >](../../../docs/framework/net-native/field-element-net-native.md)||||  
    |[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|✓|✓|✓|  
    |[\<ImpliesType >](../../../docs/framework/net-native/impliestype-element-net-native.md)|✓|✓|✓|  
    |[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)||||  
    |[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)||||  
    |[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|✓|✓|✓|  
    |[\<Parametr >](../../../docs/framework/net-native/parameter-element-net-native.md)|✓|✓|✓|  
    |[\<Właściwość >](../../../docs/framework/net-native/property-element-net-native.md)||||  
    |[\<Subtypes >](../../../docs/framework/net-native/subtypes-element-net-native.md)|✓|✓|✓|  
    |[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|✓|✓|✓|  
    |[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|✓|✓|✓|  
    |[\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)|✓|✓|✓|  
  
## <a name="policy-settings"></a>Ustawienia zasad  
 Każdego typu zasad może należeć do jednej z wartości wymienionych w poniższej tabeli. Należy zauważyć, że elementy, które reprezentują elementy członkowskie typu obsługuje inny zestaw ustawień zasad niż inne elementy.  
  
|Ustawienie zasad|Opis|`Assembly`, `Namespace`, `Type`, i `TypeInstantiation` elementów|`Event`, `Field`, `Method`, `MethodInstantiation`, i `Property` elementów|  
|--------------------|-----------------|-----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|`All`|Włącza zasady dla wszystkich typów i elementów członkowskich, które nie będą usuwane łańcucha narzędzi dla platformy .NET Native.|✓||  
|`Auto`|Określa, że zasada domyślna ma być używany dla tego typu zasad dla tego elementu programu. To jest identyczny z pominięciem zasad dla tego typu zasad. `Auto`zwykle służy do wskazywania, czy zasady są dziedziczone z elementu nadrzędnego.|✓|✓|  
|`Excluded`|Określa, czy zasady są wyłączone dla elementu określonego programu. Na przykład dyrektyw środowiska uruchomieniowego:<br /><br /> `<Type Name="BusinessClasses.Person" Browse="Excluded" Dynamic="Excluded" />`<br /><br /> Określa, że metadane dla `BusinessClasses.Person` klasy nie jest dostępna, albo do przeglądania lub do dynamicznie utworzyć wystąpienia i modyfikowania `Person` obiektów.|✓|✓|  
|`Included`|Włącza zasadę, jeśli metadane dla typu nadrzędnego jest dostępna.||✓|  
|`Public`|Włącza zasady dla typy publiczne lub elementy członkowskie, chyba że łańcucha narzędzi Określa typ lub element członkowski nie jest konieczne i w związku z tym spowoduje usunięcie jej. To ustawienie różni się od `Required Public`, co zapewnia, że metadane typy publiczne i elementów członkowskich są zawsze dostępne, nawet jeśli łańcucha narzędzi Określa, że nie jest konieczne.|✓||  
|`PublicAndInternal`|Włącza zasady dla publicznych i wewnętrznych typów albo elementów członkowskich, chyba że łańcucha narzędzi Określa typ lub element członkowski nie jest konieczne i w związku z tym spowoduje usunięcie jej. To ustawienie różni się od `Required PublicAndInternal`, co zapewnia, że metadane dla publicznych i wewnętrznych typów i członków jest zawsze dostępny nawet wtedy, gdy łańcucha narzędzi Określa, że nie jest konieczne.|✓||  
|`Required`|Określa, że jest włączona dla elementu członkowskiego i metadane będą dostępne, nawet jeśli element członkowski wydaje się być używane.||✓|  
|`Required Public`|Włącza zasady dla typy publiczne lub elementy członkowskie i zapewnia, że metadane typy publiczne i elementów członkowskich są zawsze dostępne. To ustawienie różni się od `Public`, co czyni metadanych dla publicznych typów i członków dostępne tylko wtedy, gdy łańcucha narzędzi Określa, że jest to konieczne.|✓||  
|`Required PublicAndInternal`|Włącza zasady dla publicznych i wewnętrznych typów albo elementów członkowskich i zapewnia, że metadane publicznych oraz wewnętrznych typy i składniki są zawsze dostępne. To ustawienie różni się od `PublicAndInternal`, co czyni metadanych dla publicznych i wewnętrznych typów i członków dostępne tylko wtedy, gdy łańcucha narzędzi Określa, że jest to konieczne.|✓||  
|`Required All`|Wymaga łańcucha narzędzi, aby zachować wszystkie elementy członkowskie i typy czy są używane i umożliwia zasad dla nich.|✓||  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do pliku konfiguracji dyrektyw (rd.xml) środowiska wykonawczego](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)
