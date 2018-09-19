---
title: Ustawienia zasad dyrektyw środowiska uruchomieniowego
ms.date: 03/30/2017
ms.assetid: cb52b1ef-47fd-4609-b69d-0586c818ac9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac5d80664bbca8cf950eb2e6f37badc485c398d2
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46000991"
---
# <a name="runtime-directive-policy-settings"></a>Ustawienia zasad dyrektyw środowiska uruchomieniowego
> [!NOTE]
>  W tym temacie odnosi się do platformy .NET Native Developer Preview, czyli wstępnej wersji oprogramowania. Możesz pobrać podglądu [witryny sieci Web Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (wymaga rejestracji).  
  
 Ustawienia zasad dyrektyw środowiska uruchomieniowego dla platformy .NET Native ustalić dostępności metadanych dla typów i elementów członkowskich typu w czasie wykonywania. Bez potrzeby metadanych operacje, które zależą od odbicia, serializacji i deserializacji lub szeregowanie typów środowiska .NET Framework do modelu COM lub środowiska wykonawczego Windows może zakończyć się niepowodzeniem i zgłosić wyjątek. Najbardziej powszechne wyjątki są [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) i (w przypadku współdziałania) [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md).  
  
 Środowisko uruchomieniowe ustawienia zasad są kontrolowane przez dyrektywy środowiska uruchomieniowego (. rd.xml) pliku. Każdy dyrektyw środowiska uruchomieniowego definiuje zasady dla elementu określonego programu, taką jak zestaw ( [ \<zestawu >](../../../docs/framework/net-native/assembly-element-net-native.md) element), typu ( [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) element), lub metody ( [ \<metody >](../../../docs/framework/net-native/method-element-net-native.md) elementu). Dyrektywa zawiera jeden lub więcej atrybutów, które definiują typy zasad odbicia, serializacji typów zasad i typów międzyoperacyjnych zasad omówiona w następnej sekcji. Wartość atrybutu definiują ustawienia zasad.  
  
## <a name="policy-types"></a>Typy zasad  
 Dyrektywy środowiska uruchomieniowego pliki rozpoznaje trzy kategorie typów zasad: odbicia, serializacja i współdziałania.  
  
-   Typy zasad odbicia ustalić metadanych, który ma zostać udostępnione w czasie wykonywania odbicia:  
  
    -   `Activate` kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, aby włączyć aktywacji wystąpień.  
  
    -   `Browse` wykonanie zapytania dotyczącego informacji o kontroli programu elementów.  
  
    -   `Dynamic` dostęp do środowiska uruchomieniowego kontroli do wszystkich typów i członków, aby włączyć dynamiczne programowania.  
  
     Poniższa tabela zawiera listę typów zasad odbicia i elementy programu, z którymi mogą być używane.  
  
    |Element|Aktywuj|Przeglądaj|Dynamiczne|  
    |-------------|--------------|------------|-------------|  
    |[\<Aplikacji >](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|  
    |[\<Zestaw >](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|  
    |[\<AttributeImplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|  
    |[\<Zdarzenie >](../../../docs/framework/net-native/event-element-net-native.md)||✓|✓|  
    |[\<pole >](../../../docs/framework/net-native/field-element-net-native.md)||✓|✓|  
    |[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|✓|✓|✓|  
    |[\<ImpliesType >](../../../docs/framework/net-native/impliestype-element-net-native.md)|✓|✓|✓|  
    |[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)||✓|✓|  
    |[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)||✓|✓|  
    |[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|✓|✓|✓|  
    |[\<Parametr >](../../../docs/framework/net-native/parameter-element-net-native.md)|✓|✓|✓|  
    |[\<Właściwość >](../../../docs/framework/net-native/property-element-net-native.md)||✓|✓|  
    |[\<Podtypy >](../../../docs/framework/net-native/subtypes-element-net-native.md)|✓|✓|✓|  
    |[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|✓|✓|✓|  
    |[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|✓|✓|✓|  
    |[\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)|✓|✓|✓|  
  
-   Serializacja typów zasad ustalić metadanych, który ma zostać udostępnione w czasie wykonywania do serializacji i deserializacji:  
  
    -   `Serialize` kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, pola i właściwości, aby umożliwić wystąpień typu przez bibliotek innych firm, takich jak serializator Newtonsoft JSON.  
  
    -   `DataContractSerializer` kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, pola i właściwości, aby umożliwić wystąpień typu przez <xref:System.Runtime.Serialization.DataContractSerializer> klasy.  
  
    -   `DataContractJsonSerializer` kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, pola i właściwości, aby umożliwić wystąpień typu przez <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> klasy.  
  
    -   `XmlSerializer` kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, pola i właściwości, aby umożliwić wystąpień typu przez <xref:System.Xml.Serialization.XmlSerializer> klasy.  
  
     W poniższej tabeli wymieniono serializacji typów zasad i elementy programu, z którymi mogą być używane.  
  
    |Element|Serializacji|DataContractSerializer|Klasa DataContractJsonSerializer|Element XmlSerializer|  
    |-------------|---------------|----------------------------|--------------------------------|-------------------|  
    |[\<Aplikacji >](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Zestaw >](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|✓|  
    |[\<AttributeImplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Zdarzenie >](../../../docs/framework/net-native/event-element-net-native.md)|||||  
    |[\<pole >](../../../docs/framework/net-native/field-element-net-native.md)|✓||||  
    |[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|✓|✓|✓|✓|  
    |[\<ImpliesType >](../../../docs/framework/net-native/impliestype-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)|||||  
    |[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|||||  
    |[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Parametr >](../../../docs/framework/net-native/parameter-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Właściwość >](../../../docs/framework/net-native/property-element-net-native.md)|✓||||  
    |[\<Podtypy >](../../../docs/framework/net-native/subtypes-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|✓|✓|✓|✓|  
    |[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|✓|✓|✓|✓|  
    |[\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)|✓|✓|✓|✓|  
  
-   Typy międzyoperacyjne zasad ustalić metadanych, który ma zostać udostępnione w czasie wykonywania do przekazania do modelu COM i środowiska wykonawczego Windows typy odwołań, typy wartości i wskaźników do funkcji:  
  
    -   `MarshalObject` kontrolki natywne skierowanie do modelu COM i środowiska wykonawczego Windows, dla typów odwołań.  
  
    -   `MarshalDelegate` kontroluje kierowanie natywne typy delegatów jako wskaźniki funkcji.  
  
    -   `MarshalStructure` kontrolki natywne skierowanie do modelu COM i środowiska wykonawczego Windows, dla typów wartości.  
  
     Poniższa tabela zawiera listę typów międzyoperacyjnych zasad i elementy programu, z którymi mogą być używane.  
  
    |Element|MarshalObject|MarshalDelegate|MarshalStructure|  
    |-------------|-------------------|---------------------|----------------------|  
    |[\<Aplikacji >](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|  
    |[\<Zestaw >](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|  
    |[\<AttributeImplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|  
    |[\<Zdarzenie >](../../../docs/framework/net-native/event-element-net-native.md)||||  
    |[\<pole >](../../../docs/framework/net-native/field-element-net-native.md)||||  
    |[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|✓|✓|✓|  
    |[\<ImpliesType >](../../../docs/framework/net-native/impliestype-element-net-native.md)|✓|✓|✓|  
    |[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)||||  
    |[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)||||  
    |[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|✓|✓|✓|  
    |[\<Parametr >](../../../docs/framework/net-native/parameter-element-net-native.md)|✓|✓|✓|  
    |[\<Właściwość >](../../../docs/framework/net-native/property-element-net-native.md)||||  
    |[\<Podtypy >](../../../docs/framework/net-native/subtypes-element-net-native.md)|✓|✓|✓|  
    |[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|✓|✓|✓|  
    |[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|✓|✓|✓|  
    |[\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)|✓|✓|✓|  
  
## <a name="policy-settings"></a>Ustawienia zasad  
 Każdy typ zasad można ustawić na jedną z wartości wymienionych w poniższej tabeli. Należy pamiętać, że elementy, które reprezentują elementy członkowskie typu obsługuje inny zbiór ustawień zasad niż inne elementy.  
  
|Ustawienie zasad|Opis|`Assembly`, `Namespace`, `Type`, i `TypeInstantiation` elementów|`Event`, `Field`, `Method`, `MethodInstantiation`, i `Property` elementów|  
|--------------------|-----------------|-----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|`All`|Włącza zasady dla wszystkich typów i elementów członkowskich, które nie powoduje usunięcia łańcucha narzędzi .NET Native.|✓||  
|`Auto`|Określa, że domyślne zasady powinny być używane dla tego typu zasad dla tego elementu programu. Jest to taka sama jak pomijanie zasad dla tego typu zasad. `Auto` Zazwyczaj służy do wskazywania, czy zasady są dziedziczone z elementu nadrzędnego.|✓|✓|  
|`Excluded`|Określa, że zasady są wyłączone dla elementu określonego programu. Na przykład dyrektyw środowiska uruchomieniowego:<br /><br /> `<Type Name="BusinessClasses.Person" Browse="Excluded" Dynamic="Excluded" />`<br /><br /> Określa, że metadane dla `BusinessClasses.Person` klasy nie jest dostępna, albo do przeglądania lub do dynamicznego utworzenia wystąpienia i zmodyfikować `Person` obiektów.|✓|✓|  
|`Included`|Włącza zasadę, jeśli metadane dla typu nadrzędnego jest dostępna.||✓|  
|`Public`|Włącza zasady dla publiczne typy lub członków, chyba że łańcucha narzędzi Określa typ lub element członkowski nie jest konieczne i w związku z tym powoduje jej usunięcie. To ustawienie różni się od `Required Public`, dzięki któremu tych metadanych dla typów publicznych i elementów członkowskich są zawsze dostępne nawet wtedy, gdy łańcucha narzędzi Określa, że nie jest konieczne.|✓||  
|`PublicAndInternal`|Włącza zasady dla typów publicznych i wewnętrznych lub elementów członkowskich, chyba że łańcucha narzędzi Określa typ lub element członkowski nie jest konieczne i w związku z tym powoduje jej usunięcie. To ustawienie różni się od `Required PublicAndInternal`, dzięki któremu tych metadanych do publicznych i wewnętrznych typów i elementów członkowskich są zawsze dostępne nawet wtedy, gdy łańcucha narzędzi Określa, że nie jest konieczne.|✓||  
|`Required`|Określa, że jest włączona dla elementu członkowskiego, a metadane będą dostępne, nawet wtedy, gdy element członkowski, który pojawia się do użycia.||✓|  
|`Required Public`|Włącza zasady dla publiczne typy lub elementy członkowskie i zapewnia tych metadanych dla typów publicznych i elementy członkowskie są zawsze dostępne. To ustawienie różni się od `Public`, co sprawia, że metadane dotyczące typów publicznych i elementy członkowskie dostępne tylko wtedy, gdy łańcucha narzędzi Określa, że jest to konieczne.|✓||  
|`Required PublicAndInternal`|Umożliwia zasady dla publicznych i wewnętrznych typów ani elementów członkowskich i zapewnia tych metadanych dla publicznych i wewnętrznych typów i elementów członkowskich jest zawsze dostępna. To ustawienie różni się od `PublicAndInternal`, co sprawia, że metadane dotyczące typów publicznych i wewnętrznych i członków dostępne tylko wtedy, gdy łańcucha narzędzi Określa, że jest to konieczne.|✓||  
|`Required All`|Wymaga łańcucha narzędzi, aby zachować wszystkie typy i elementy Członkowskie określa, czy są używane i zasad umożliwia ich.|✓||  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)
