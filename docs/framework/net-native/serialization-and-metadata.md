---
title: Serializacja i metadane
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
ms.openlocfilehash: cc9adf0e6627ef3190e74fea5d4f0f3afd581811
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "81389219"
---
# <a name="serialization-and-metadata"></a>Serializacja i metadane

Jeśli aplikacja serializować i deserializacji obiektów, może być konieczne dodanie wpisów do pliku dyrektywy środowiska uruchomieniowego (. Rd. xml) w celu upewnienia się, że niezbędne metadane są obecne w czasie wykonywania. Istnieją dwie kategorie serializatorów, a każdy z nich wymaga innej obsługi w pliku dyrektywy środowiska uruchomieniowego:  
  
- Serializatory innych firm oparte na odbiciu. Wymagają one modyfikacji pliku dyrektywy środowiska uruchomieniowego i zostały omówione w następnej sekcji.  
  
- W bibliotece klas .NET Framework nie znaleziono serializatorów opartych na nieodbiciach. Mogą one wymagać modyfikacji pliku dyrektywy środowiska uruchomieniowego i zostały omówione w sekcji [serializatory firmy Microsoft](#Microsoft) .  
  
<a name="ThirdParty"></a>
## <a name="third-party-serializers"></a>Serializatory innych firm

 Serializatory innych firm, w tym Newtonsoft. JSON, zazwyczaj są oparte na odbiciach. Przy użyciu binarnego dużego obiektu (BLOB) danych serializowanych pola w danych są przypisywane do konkretnego typu przez wyszukanie pól typu docelowego według nazwy. Co najmniej przy użyciu tych bibliotek powoduje wyjątki [MissingMetadataException](missingmetadataexception-class-net-native.md) dla każdego <xref:System.Type> obiektu, który próbujesz serializować lub deserializować w `List<Type>` kolekcji.  
  
 Najprostszym sposobem rozwiązania problemów spowodowanych brakiem metadanych dla tych serializatorów jest zbieranie typów, które będą używane w serializacji w ramach pojedynczej przestrzeni nazw (na przykład `App.Models` ) i zastosowanie `Serialize` dyrektywy Metadata do niej:  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 Aby uzyskać informacje o składni używanej w przykładzie, zobacz [ \<Namespace> element](namespace-element-net-native.md).  
  
<a name="Microsoft"></a>
## <a name="microsoft-serializers"></a>Serializatory firmy Microsoft

 Chociaż <xref:System.Runtime.Serialization.DataContractSerializer> klasy, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> i nie <xref:System.Xml.Serialization.XmlSerializer> polegają na odbiciu, wymagają generowania kodu na podstawie obiektu do serializacji lub deserializacji. Przeciążone konstruktory dla każdego serializatora obejmują <xref:System.Type> parametr, który określa typ do serializacji lub deserializacji. Sposób określenia tego typu w kodzie definiuje działanie, które należy wykonać, zgodnie z opisem w dwóch następnych sekcjach.  
  
### <a name="typeof-used-in-the-constructor"></a>wartość typeof użyta w konstruktorze

 W przypadku wywołania konstruktora tych klas serializacji i uwzględnienia operatora C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) w wywołaniu metody **nie trzeba wykonywać żadnych dodatkowych czynności**. Na przykład w każdym z następujących wywołań konstruktora klasy serializacji `typeof` słowo kluczowe jest używane jako część wyrażenia przesłanego do konstruktora.  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 Kompilator .NET Native automatycznie obsłuży ten kod.  
  
### <a name="typeof-used-outside-the-constructor"></a>wartość typeof użyta poza konstruktorem

 W przypadku wywołania konstruktora tych klas serializacji i [użycia operatora języka](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) C#, poza wyrażeniem dostarczonym do <xref:System.Type> parametru konstruktora, jak w poniższym kodzie, kompilator .NET Native nie może rozpoznać typu:  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 W takim przypadku należy określić typ w pliku dyrektywy środowiska uruchomieniowego, dodając wpis podobny do tego:  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 Podobnie w przypadku wywołania konstruktora, takiego jak <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29> i udostępnienia tablicy dodatkowych <xref:System.Type> obiektów do serializacji, jak w poniższym kodzie, kompilator .NET Native nie może rozpoznać tych typów.  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
Dodaj wpisy, takie jak następujące dla każdego typu do pliku dyrektywy środowiska uruchomieniowego:  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
Aby uzyskać informacje o składni używanej w przykładzie, zobacz [ \<Type> element](type-element-net-native.md).  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
- [\<Type>Postaci](type-element-net-native.md)
- [\<Namespace>Postaci](namespace-element-net-native.md)
