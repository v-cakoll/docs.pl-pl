---
title: Serializacja i metadane
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
ms.openlocfilehash: 7c6fe241fbf92f52abfa0eb66c37bff4d227b4e5
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81241922"
---
# <a name="serialization-and-metadata"></a>Serializacja i metadane

Jeśli aplikacja serializuje i deserializes obiektów, może być konieczne dodanie wpisów do pliku dyrektywy środowiska uruchomieniowego (.rd.xml), aby upewnić się, że niezbędne metadane są obecne w czasie wykonywania. Istnieją dwie kategorie serializatorów, a każda z nich wymaga innej obsługi w pliku dyrektyw środowiska wykonawczego:  
  
- Serializatory innych firm oparte na odbiciach. Wymagają one modyfikacji pliku dyrektyw środowiska wykonawczego i zostały omówione w następnej sekcji.  
  
- Serializatory oparte na braku odbicia znalezione w bibliotece klas .NET Framework. Mogą one wymagać modyfikacji pliku dyrektyw środowiska wykonawczego i są omówione w sekcji [serializatory firmy Microsoft.](#Microsoft)  
  
<a name="ThirdParty"></a>
## <a name="third-party-serializers"></a>Serializatory innych firm

 Serializatory trzeciej części, w tym Newtonsoft.JSON, zazwyczaj są oparte na refleksji. Biorąc pod uwagę binarny duży obiekt (BLOB) z serializowanych danych, pola w danych są przypisywane do typu betonowego, wyszukując pola typu docelowego według nazwy. Co najmniej przy użyciu tych bibliotek powoduje [MissingMetadataException](missingmetadataexception-class-net-native.md) wyjątki dla każdego <xref:System.Type> obiektu, który `List<Type>` próbujesz serializować lub deserialize w kolekcji.  
  
 Najprostszym sposobem rozwiązania problemów spowodowanych brakującymi metadanymi dla tych serializatorów jest zbieranie typów, które `App.Models`będą używane `Serialize` w serializacji w ramach pojedynczego obszaru nazw (na przykład) i stosowanie do niej dyrektywy metadanych:  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 Aby uzyskać informacje na temat składni [ \<](namespace-element-net-native.md)używanej w przykładzie, zobacz Obszar nazw> element .  
  
<a name="Microsoft"></a>
## <a name="microsoft-serializers"></a>Serializatory firmy Microsoft

 Chociaż <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>i <xref:System.Xml.Serialization.XmlSerializer> klasy nie opierają się na odbicie, wymagają kodu do wygenerowania na podstawie obiektu, który ma być serializowany lub deserializacji. Przeciążonych konstruktorów dla każdego <xref:System.Type> serializatora zawierają parametr, który określa typ, który ma być serializowany lub deserialized. Sposób określenia tego typu w kodzie definiuje akcję, którą należy podjąć, jak opisano w następnych dwóch sekcjach.  
  
### <a name="typeof-used-in-the-constructor"></a>typeof używane w konstruktorze

 Jeśli wywołasz konstruktor tych klas serializacji i uwzględnisz operator [typu](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) C# w wywołaniu metody, **nie musisz wykonywać żadnej dodatkowej pracy.** Na przykład w każdym z następujących wywołań do konstruktora klasy `typeof` serializacji, słowo kluczowe jest używane jako część wyrażenia przekazywane do konstruktora.  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 Kompilator natywny platformy .NET automatycznie obsłuży ten kod.  
  
### <a name="typeof-used-outside-the-constructor"></a>typeof używane poza konstruktorem

 Jeśli wywołasz konstruktor tych klas serializacji i użyjesz operatora [typu](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) C# <xref:System.Type> poza wyrażeniem dostarczonym do parametru konstruktora, jak w poniższym kodzie, kompilator .NET Native nie może rozwiązać tego typu:  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 W takim przypadku należy określić typ w pliku dyrektyw środowiska wykonawczego, dodając wpis w ten sposób:  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 Podobnie jeśli wywołasz konstruktora, takich jak <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29> <xref:System.Type> i podać tablicę dodatkowych obiektów do serializacji, jak w poniższym kodzie, .NET natywnego kompilatora nie może rozwiązać tych typów.  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 Do pliku dyrektyw środowiska wykonawczego należy dodać wpisy, takie jak następujące:  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 Aby uzyskać informacje na temat składni [ \<](type-element-net-native.md)używanej w przykładzie, zobacz Typ> Element .  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
- [\<Wpisz element>](type-element-net-native.md)
- [\<Element> przestrzeni nazw](namespace-element-net-native.md)
