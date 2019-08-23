---
title: Ustawienia zasad dyrektyw środowiska uruchomieniowego
ms.date: 03/30/2017
ms.assetid: cb52b1ef-47fd-4609-b69d-0586c818ac9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe78e2bd9c31bfb122e90b97977117adfc0235d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967889"
---
# <a name="runtime-directive-policy-settings"></a>Ustawienia zasad dyrektyw środowiska uruchomieniowego

> [!NOTE]
> Ten temat dotyczy wersji zapoznawczej programu .NET Native Developer, która jest oprogramowaniem w wersji wstępnej. Wersję zapoznawczą można pobrać z [witryny sieci Web Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (wymaga rejestracji).

Ustawienia zasad dyrektywy środowiska uruchomieniowego dla .NET Native określają dostępność metadanych dla typów i elementów członkowskich typu w czasie wykonywania. Bez wymaganych metadanych operacje, które polegają na odbiciu, serializacji i deserializacji lub kierowaniu typów .NET Framework do modelu COM lub środowisko wykonawcze systemu Windows mogą zakończyć się niepowodzeniem i zgłosić wyjątek. Najczęstszymi wyjątkami są [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) i (w przypadku współdziałania) [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md).

Ustawienia zasad środowiska uruchomieniowego są kontrolowane przez plik dyrektywy środowiska uruchomieniowego (. Rd. xml). Każda dyrektywa środowiska uruchomieniowego definiuje zasady dla określonego elementu programu, takie jak zestaw ( [ \<element > zestawu](../../../docs/framework/net-native/assembly-element-net-native.md) ), typ ( [ \<element >](../../../docs/framework/net-native/type-element-net-native.md) ) lub metodę ( [ \<Metoda >](../../../docs/framework/net-native/method-element-net-native.md) element). Dyrektywa zawiera jeden lub więcej atrybutów, które definiują typy zasad odbicia, typy zasad serializacji i typy zasad międzyoperacyjnych omówione w następnej sekcji. Wartość atrybutu definiuje ustawienie zasad.

## <a name="policy-types"></a>Typy zasad

Pliki dyrektyw środowiska uruchomieniowego rozpoznają trzy kategorie typów zasad: odbicie, serializacja i międzyoperacyjność.

- Typy zasad odbicia określają, które metadane są udostępniane w czasie wykonywania dla odbicia:

  - `Activate`kontroluje dostęp środowiska uruchomieniowego do konstruktorów, aby umożliwić aktywację wystąpień.

  - `Browse`steruje wykonywaniem zapytań dotyczących informacji o elementach programu.

  - `Dynamic`kontroluje dostęp środowiska uruchomieniowego do wszystkich typów i elementów członkowskich, aby umożliwić programowanie dynamiczne.

  Poniższa tabela zawiera listę typów zasad odbicia i elementów programu, za pomocą których można ich używać.

  |Element|Zdezaktywować|Przycisku|Dynamiczne|
  |-------------|--------------|------------|-------------|
  |[\<> Aplikacji](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|
  |[\<> Zestawu](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|
  |[\<AttributeImplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|
  |[\<> Zdarzeń](../../../docs/framework/net-native/event-element-net-native.md)||✓|✓|
  |[\<> Pola](../../../docs/framework/net-native/field-element-net-native.md)||✓|✓|
  |[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|✓|✓|✓|
  |[\<ImpliesType >](../../../docs/framework/net-native/impliestype-element-net-native.md)|✓|✓|✓|
  |[\<> Metody](../../../docs/framework/net-native/method-element-net-native.md)||✓|✓|
  |[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)||✓|✓|
  |[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|✓|✓|✓|
  |[\<> Parametru](../../../docs/framework/net-native/parameter-element-net-native.md)|✓|✓|✓|
  |[\<> Właściwości](../../../docs/framework/net-native/property-element-net-native.md)||✓|✓|
  |[\<Podtypy >](../../../docs/framework/net-native/subtypes-element-net-native.md)|✓|✓|✓|
  |[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|✓|✓|✓|
  |[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|✓|✓|✓|
  |[\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)|✓|✓|✓|

- Typy zasad serializacji określają, które metadane są udostępniane w czasie wykonywania na potrzeby serializacji i deserializacji:

  - `Serialize`kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie wystąpień typu za pomocą bibliotek innych firm, takich jak serializator JSON Newtonsoft.

  - `DataContractSerializer`kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie wystąpień typów przez <xref:System.Runtime.Serialization.DataContractSerializer> klasę.

  - `DataContractJsonSerializer`kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie wystąpień typów przez <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> klasę.

  - `XmlSerializer`kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie wystąpień typów przez <xref:System.Xml.Serialization.XmlSerializer> klasę.

  Poniższa tabela zawiera listę typów zasad serializacji i elementów programu, za pomocą których można ich używać.

  |Element|Potrzeby|DataContractSerializer|DataContractJsonSerializer|XmlSerializer|
  |-------------|---------------|----------------------------|--------------------------------|-------------------|
  |[\<> Aplikacji](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|✓|
  |[\<> Zestawu](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|✓|
  |[\<AttributeImplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|✓|
  |[\<> Zdarzeń](../../../docs/framework/net-native/event-element-net-native.md)|||||
  |[\<> Pola](../../../docs/framework/net-native/field-element-net-native.md)|✓||||
  |[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|✓|✓|✓|✓|
  |[\<ImpliesType >](../../../docs/framework/net-native/impliestype-element-net-native.md)|✓|✓|✓|✓|
  |[\<> Metody](../../../docs/framework/net-native/method-element-net-native.md)|||||
  |[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|||||
  |[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|✓|✓|✓|✓|
  |[\<> Parametru](../../../docs/framework/net-native/parameter-element-net-native.md)|✓|✓|✓|✓|
  |[\<> Właściwości](../../../docs/framework/net-native/property-element-net-native.md)|✓||||
  |[\<Podtypy >](../../../docs/framework/net-native/subtypes-element-net-native.md)|✓|✓|✓|✓|
  |[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|✓|✓|✓|✓|
  |[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|✓|✓|✓|✓|
  |[\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)|✓|✓|✓|✓|

- Typy zasad międzyoperacyjnych określają, które metadane są udostępniane w czasie wykonywania, aby przekazywać typy odwołań, typy wartości i wskaźniki funkcji do modelu COM i środowisko wykonawcze systemu Windows:

  - `MarshalObject`steruje natywnym kierowaniem do modelu COM i środowisko wykonawcze systemu Windows dla typów referencyjnych.

  - `MarshalDelegate`steruje natywnym kierowaniem typów delegatów jako wskaźników funkcji.

  - `MarshalStructure`steruje natywnym kierowaniem do modelu COM i środowisko wykonawcze systemu Windows dla typów wartości.

  Poniższa tabela zawiera listę typów zasad międzyoperacyjnych i elementów programu, za pomocą których można ich używać.

  |Element|Marshalobject|MarshalDelegate|MarshalStructure|
  |-------------|-------------------|---------------------|----------------------|
  |[\<> Aplikacji](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|
  |[\<> Zestawu](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|
  |[\<AttributeImplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|
  |[\<> Zdarzeń](../../../docs/framework/net-native/event-element-net-native.md)||||
  |[\<> Pola](../../../docs/framework/net-native/field-element-net-native.md)||||
  |[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|✓|✓|✓|
  |[\<ImpliesType >](../../../docs/framework/net-native/impliestype-element-net-native.md)|✓|✓|✓|
  |[\<> Metody](../../../docs/framework/net-native/method-element-net-native.md)||||
  |[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)||||
  |[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|✓|✓|✓|
  |[\<> Parametru](../../../docs/framework/net-native/parameter-element-net-native.md)|✓|✓|✓|
  |[\<> Właściwości](../../../docs/framework/net-native/property-element-net-native.md)||||
  |[\<Podtypy >](../../../docs/framework/net-native/subtypes-element-net-native.md)|✓|✓|✓|
  |[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|✓|✓|✓|
  |[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|✓|✓|✓|
  |[\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)|✓|✓|✓|

## <a name="policy-settings"></a>Ustawienia zasad

Każdy typ zasad może być ustawiony na jedną z wartości wymienionych w poniższej tabeli. Należy zauważyć, że elementy reprezentujące składowe typu obsługują inny zestaw ustawień zasad niż inne elementy.

|Ustawienie zasad|Opis|`Assembly`, `Namespace`, `Type`i elementy`TypeInstantiation`|`Event`, `Field`, `Method`, i`MethodInstantiation`elementy `Property`|
|--------------------|-----------------|-----------------------------------------------------------------------|--------------------------------------------------------------------------------|
|`All`|Włącza zasady dla wszystkich typów i elementów członkowskich, które nie są usuwane przez łańcuch narzędzi .NET Native.|✓||
|`Auto`|Określa, że zasady domyślne mają być stosowane dla typu zasad dla tego elementu programu. Jest to identyczne z pominięciem zasad dla tego typu zasad. `Auto`jest zazwyczaj używany do wskazania, że zasady są dziedziczone z elementu nadrzędnego.|✓|✓|
|`Excluded`|Określa, że zasady są wyłączone dla określonego elementu programu. Na przykład dyrektywa środowiska uruchomieniowego:<br /><br /> `<Type Name="BusinessClasses.Person" Browse="Excluded" Dynamic="Excluded" />`<br /><br /> Określa, że metadane `BusinessClasses.Person` klasy nie są dostępne do przeglądania lub dynamicznego tworzenia wystąpień i modyfikowania `Person` obiektów.|✓|✓|
|`Included`|Włącza zasady, jeśli są dostępne metadane dla typu nadrzędnego.||✓|
|`Public`|Włącza zasady dla typów publicznych lub członków, chyba że łańcuch narzędzi określa, że typ lub element członkowski nie są potrzebne, a tym samym go usunie. To ustawienie różni się `Required Public`od, co gwarantuje, że metadane dla typów publicznych i członków są zawsze dostępne nawet wtedy, gdy łańcuch narzędzi ustali, że nie jest to konieczne.|✓||
|`PublicAndInternal`|Włącza zasady dla typów publicznych i wewnętrznych lub składowych, chyba że łańcuch narzędzi określa, że typ lub element członkowski nie są potrzebne, a tym samym go usunie. To ustawienie różni się `Required PublicAndInternal`od, co gwarantuje, że metadane dla typów publicznych i wewnętrznych oraz członków są zawsze dostępne nawet wtedy, gdy łańcuch narzędzi ustali, że nie jest to konieczne.|✓||
|`Required`|Określa, że zasady dla elementu członkowskiego są włączone i metadane będą dostępne nawet wtedy, gdy element członkowski jest używany.||✓|
|`Required Public`|Włącza zasady dla typów publicznych lub członków i gwarantuje, że metadane dla typów publicznych i członków są zawsze dostępne. To ustawienie różni się `Public`od, co sprawia, że metadane dla typów publicznych i członków są dostępne tylko wtedy, gdy łańcuch narzędzi określa, że jest to konieczne.|✓||
|`Required PublicAndInternal`|Włącza zasady dla typów publicznych i wewnętrznych oraz członków, a także zapewnia, że metadane dla typów publicznych i wewnętrznych oraz członków są zawsze dostępne. To ustawienie różni się `PublicAndInternal`od, co sprawia, że metadane dla typów publicznych i wewnętrznych oraz składowe są dostępne tylko wtedy, gdy łańcuch narzędzi określa, że jest to konieczne.|✓||
|`Required All`|Wymaga łańcucha narzędzi, aby zachować wszystkie typy i członków, niezależnie od tego, czy są one używane, i włącza dla nich zasady.|✓||

## <a name="see-also"></a>Zobacz także

- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)
