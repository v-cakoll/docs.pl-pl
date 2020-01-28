---
title: Ustawienia zasad dyrektyw środowiska uruchomieniowego
ms.date: 03/30/2017
ms.assetid: cb52b1ef-47fd-4609-b69d-0586c818ac9e
ms.openlocfilehash: 7a8933decaec45e8000f3f3d1717847f333deddd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738503"
---
# <a name="runtime-directive-policy-settings"></a>Ustawienia zasad dyrektyw środowiska uruchomieniowego

> [!NOTE]
> Ten temat dotyczy wersji zapoznawczej programu .NET Native Developer, która jest oprogramowaniem w wersji wstępnej. Wersję zapoznawczą można pobrać z [witryny sieci Web Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (wymaga rejestracji).

Ustawienia zasad dyrektywy środowiska uruchomieniowego dla .NET Native określają dostępność metadanych dla typów i elementów członkowskich typu w czasie wykonywania. Bez wymaganych metadanych operacje, które polegają na odbiciu, serializacji i deserializacji lub kierowaniu typów .NET Framework do modelu COM lub środowisko wykonawcze systemu Windows mogą zakończyć się niepowodzeniem i zgłosić wyjątek. Najczęstszymi wyjątkami są [MissingMetadataException](missingmetadataexception-class-net-native.md) i (w przypadku współdziałania) [MissingInteropDataException](missinginteropdataexception-class-net-native.md).

Ustawienia zasad środowiska uruchomieniowego są kontrolowane przez plik dyrektywy środowiska uruchomieniowego (. Rd. xml). Każda dyrektywa środowiska uruchomieniowego definiuje zasady dla określonego elementu programu, takie jak zestaw ( [\<zestawu >](assembly-element-net-native.md) elementu), typ ( [\<typ >](type-element-net-native.md) elementu) lub Metoda ( [\<](method-element-net-native.md) elementu). Dyrektywa zawiera jeden lub więcej atrybutów, które definiują typy zasad odbicia, typy zasad serializacji i typy zasad międzyoperacyjnych omówione w następnej sekcji. Wartość atrybutu definiuje ustawienie zasad.

## <a name="policy-types"></a>Typy zasad

Pliki dyrektyw środowiska uruchomieniowego rozpoznają trzy kategorie typów zasad: odbicie, serializacja i międzyoperacyjność.

- Typy zasad odbicia określają, które metadane są udostępniane w czasie wykonywania dla odbicia:

  - `Activate` kontroluje dostęp środowiska uruchomieniowego do konstruktorów, aby umożliwić aktywację wystąpień.

  - `Browse` kontroluje wykonywanie zapytań dotyczących elementów programu.

  - `Dynamic` kontroluje dostęp środowiska uruchomieniowego do wszystkich typów i elementów członkowskich, aby umożliwić programowanie dynamiczne.

  Poniższa tabela zawiera listę typów zasad odbicia i elementów programu, za pomocą których można ich używać.

  |Element|Aktywacja|Przycisku|Dynamiczne|
  |-------------|--------------|------------|-------------|
  |[\<> aplikacji](application-element-net-native.md)|✔️|✔️|✔️|
  |[\<zestawu >](assembly-element-net-native.md)|✔️|✔️|✔️|
  |[\<AttributeImplies >](attributeimplies-element-net-native.md)|✔️|✔️|✔️|
  |[> zdarzeń \<](event-element-net-native.md)||✔️|✔️|
  |[\<pole >](field-element-net-native.md)||✔️|✔️|
  |[\<GenericParameter >](genericparameter-element-net-native.md)|✔️|✔️|✔️|
  |[\<ImpliesType >](impliestype-element-net-native.md)|✔️|✔️|✔️|
  |[> metody \<](method-element-net-native.md)||✔️|✔️|
  |[\<MethodInstantiation >](methodinstantiation-element-net-native.md)||✔️|✔️|
  |[\<Namespace>](namespace-element-net-native.md)|✔️|✔️|✔️|
  |[\<parametr >](parameter-element-net-native.md)|✔️|✔️|✔️|
  |[\<Właściwość >](property-element-net-native.md)||✔️|✔️|
  |[podtypy \<](subtypes-element-net-native.md)|✔️|✔️|✔️|
  |[\<Type>](type-element-net-native.md)|✔️|✔️|✔️|
  |[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|✔️|✔️|✔️|
  |[\<TypeParameter >](typeparameter-element-net-native.md)|✔️|✔️|✔️|

- Typy zasad serializacji określają, które metadane są udostępniane w czasie wykonywania na potrzeby serializacji i deserializacji:

  - `Serialize` kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie wystąpień typów przez biblioteki innych firm, takie jak serializator JSON Newtonsoft.

  - `DataContractSerializer` kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie wystąpień typów przez klasę <xref:System.Runtime.Serialization.DataContractSerializer>.

  - `DataContractJsonSerializer` kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie wystąpień typów przez klasę <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.

  - `XmlSerializer` kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie wystąpień typów przez klasę <xref:System.Xml.Serialization.XmlSerializer>.

  Poniższa tabela zawiera listę typów zasad serializacji i elementów programu, za pomocą których można ich używać.

  |Element|Potrzeby|DataContractSerializer|DataContractJsonSerializer|XmlSerializer|
  |-------------|---------------|----------------------------|--------------------------------|-------------------|
  |[\<> aplikacji](application-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<zestawu >](assembly-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<AttributeImplies >](attributeimplies-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[> zdarzeń \<](event-element-net-native.md)|||||
  |[\<pole >](field-element-net-native.md)|✔️||||
  |[\<GenericParameter >](genericparameter-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<ImpliesType >](impliestype-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[> metody \<](method-element-net-native.md)|||||
  |[\<MethodInstantiation >](methodinstantiation-element-net-native.md)|||||
  |[\<Namespace>](namespace-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<parametr >](parameter-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Właściwość >](property-element-net-native.md)|✔️||||
  |[podtypy \<](subtypes-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Type>](type-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<TypeParameter >](typeparameter-element-net-native.md)|✔️|✔️|✔️|✔️|

- Typy zasad międzyoperacyjnych określają, które metadane są udostępniane w czasie wykonywania, aby przekazywać typy odwołań, typy wartości i wskaźniki funkcji do modelu COM i środowisko wykonawcze systemu Windows:

  - `MarshalObject` kontroluje natywne kierowanie do modelu COM i środowisko wykonawcze systemu Windows dla typów referencyjnych.

  - `MarshalDelegate` kontroluje natywne kierowanie typów delegatów jako wskaźniki funkcji.

  - `MarshalStructure` kontroluje natywne kierowanie do modelu COM i środowisko wykonawcze systemu Windows dla typów wartości.

  Poniższa tabela zawiera listę typów zasad międzyoperacyjnych i elementów programu, za pomocą których można ich używać.

  |Element|Marshalobject|MarshalDelegate|MarshalStructure|
  |-------------|-------------------|---------------------|----------------------|
  |[\<> aplikacji](application-element-net-native.md)|✔️|✔️|✔️|
  |[\<zestawu >](assembly-element-net-native.md)|✔️|✔️|✔️|
  |[\<AttributeImplies >](attributeimplies-element-net-native.md)|✔️|✔️|✔️|
  |[> zdarzeń \<](event-element-net-native.md)||||
  |[\<pole >](field-element-net-native.md)||||
  |[\<GenericParameter >](genericparameter-element-net-native.md)|✔️|✔️|✔️|
  |[\<ImpliesType >](impliestype-element-net-native.md)|✔️|✔️|✔️|
  |[> metody \<](method-element-net-native.md)||||
  |[\<MethodInstantiation >](methodinstantiation-element-net-native.md)||||
  |[\<Namespace>](namespace-element-net-native.md)|✔️|✔️|✔️|
  |[\<parametr >](parameter-element-net-native.md)|✔️|✔️|✔️|
  |[\<Właściwość >](property-element-net-native.md)||||
  |[podtypy \<](subtypes-element-net-native.md)|✔️|✔️|✔️|
  |[\<Type>](type-element-net-native.md)|✔️|✔️|✔️|
  |[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|✔️|✔️|✔️|
  |[\<TypeParameter >](typeparameter-element-net-native.md)|✔️|✔️|✔️|

## <a name="policy-settings"></a>Ustawienia zasad

Każdy typ zasad może być ustawiony na jedną z wartości wymienionych w poniższej tabeli. Należy zauważyć, że elementy reprezentujące składowe typu obsługują inny zestaw ustawień zasad niż inne elementy.

|Ustawienie zasad|Opis|`Assembly`, `Namespace`, `Type`i elementy `TypeInstantiation`|`Event`, `Field`, `Method`, `MethodInstantiation`i `Property` elementów|
|--------------------|-----------------|-----------------------------------------------------------------------|--------------------------------------------------------------------------------|
|`All`|Włącza zasady dla wszystkich typów i elementów członkowskich, które nie są usuwane przez łańcuch narzędzi .NET Native.|✔️||
|`Auto`|Określa, że zasady domyślne mają być stosowane dla typu zasad dla tego elementu programu. Jest to identyczne z pominięciem zasad dla tego typu zasad. `Auto` jest zwykle używany do wskazania, że zasady są dziedziczone z elementu nadrzędnego.|✔️|✔️|
|`Excluded`|Określa, że zasady są wyłączone dla określonego elementu programu. Na przykład dyrektywa środowiska uruchomieniowego:<br /><br /> `<Type Name="BusinessClasses.Person" Browse="Excluded" Dynamic="Excluded" />`<br /><br /> Określa, że metadane dla klasy `BusinessClasses.Person` nie są dostępne do przeglądania lub dynamicznego tworzenia wystąpień i modyfikowania obiektów `Person`.|✔️|✔️|
|`Included`|Włącza zasady, jeśli są dostępne metadane dla typu nadrzędnego.||✔️|
|`Public`|Włącza zasady dla typów publicznych lub członków, chyba że łańcuch narzędzi określa, że typ lub element członkowski nie są potrzebne, a tym samym go usunie. To ustawienie różni się od `Required Public`, co gwarantuje, że metadane dla typów publicznych i członków są zawsze dostępne nawet wtedy, gdy łańcuch narzędzi ustali, że nie jest to konieczne.|✔️||
|`PublicAndInternal`|Włącza zasady dla typów publicznych i wewnętrznych lub składowych, chyba że łańcuch narzędzi określa, że typ lub element członkowski nie są potrzebne, a tym samym go usunie. To ustawienie różni się od `Required PublicAndInternal`, co zapewnia, że metadane dla typów publicznych i wewnętrznych oraz członków są zawsze dostępne nawet wtedy, gdy łańcuch narzędzi ustali, że nie jest to konieczne.|✔️||
|`Required`|Określa, że zasady dla elementu członkowskiego są włączone i metadane będą dostępne nawet wtedy, gdy element członkowski jest używany.||✔️|
|`Required Public`|Włącza zasady dla typów publicznych lub członków i gwarantuje, że metadane dla typów publicznych i członków są zawsze dostępne. To ustawienie różni się od `Public`, co sprawia, że metadane dla typów publicznych i członków są dostępne tylko wtedy, gdy łańcuch narzędzi określa, że jest to konieczne.|✔️||
|`Required PublicAndInternal`|Włącza zasady dla typów publicznych i wewnętrznych oraz członków, a także zapewnia, że metadane dla typów publicznych i wewnętrznych oraz członków są zawsze dostępne. To ustawienie różni się od `PublicAndInternal`, co sprawia, że metadane dla typów publicznych i wewnętrznych oraz składowe są dostępne tylko wtedy, gdy łańcuch narzędzi określa, że jest to konieczne.|✔️||
|`Required All`|Wymaga łańcucha narzędzi, aby zachować wszystkie typy i członków, niezależnie od tego, czy są one używane, i włącza dla nich zasady.|✔️||

## <a name="see-also"></a>Zobacz także

- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
