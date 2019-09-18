---
title: Serializacja i metadane
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec8180da9637ec2b2c4e1b432773b4f9f1ac908b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049174"
---
# <a name="serialization-and-metadata"></a>Serializacja i metadane

Jeśli aplikacja serializować i deserializacji obiektów, może być konieczne dodanie wpisów do pliku dyrektywy środowiska uruchomieniowego (. Rd. xml) w celu upewnienia się, że niezbędne metadane są obecne w czasie wykonywania. Istnieją dwie kategorie serializatorów, a każdy z nich wymaga innej obsługi w pliku dyrektywy środowiska uruchomieniowego:  
  
- Serializatory innych firm oparte na odbiciu. Wymagają one modyfikacji pliku dyrektywy środowiska uruchomieniowego i zostały omówione w następnej sekcji.  
  
- W bibliotece klas .NET Framework nie znaleziono serializatorów opartych na nieodbiciach. Mogą one wymagać modyfikacji pliku dyrektywy środowiska uruchomieniowego i zostały omówione w sekcji [serializatory firmy Microsoft](#Microsoft) .  
  
<a name="ThirdParty"></a>
## <a name="third-party-serializers"></a>Serializatory innych firm

 Serializatory innych firm, w tym Newtonsoft. JSON, zazwyczaj są oparte na odbiciach. Przy użyciu binarnego dużego obiektu (BLOB) danych serializowanych pola w danych są przypisywane do konkretnego typu przez wyszukanie pól typu docelowego według nazwy. Co najmniej przy użyciu tych bibliotek powoduje wyjątki [MissingMetadataException](missingmetadataexception-class-net-native.md) dla każdego <xref:System.Type> obiektu, który próbujesz serializować `List<Type>` lub deserializować w kolekcji.  
  
 Najprostszym sposobem rozwiązania problemów spowodowanych brakiem metadanych dla tych serializatorów jest zbieranie typów, które będą używane w serializacji w ramach pojedynczej przestrzeni nazw (na `App.Models`przykład) i `Serialize` zastosowanie dyrektywy Metadata do niej:  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 Aby uzyskać informacje o składni używanej w tym przykładzie, zobacz [ \<Namespace > element](namespace-element-net-native.md).  
  
<a name="Microsoft"></a>
## <a name="microsoft-serializers"></a>Serializatory firmy Microsoft

 Chociaż klasy <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> i<xref:System.Xml.Serialization.XmlSerializer> nie polegają na odbiciu, wymagają generowania kodu na podstawie obiektu do serializacji lub deserializacji. Przeciążone konstruktory dla każdego serializatora <xref:System.Type> obejmują parametr, który określa typ do serializacji lub deserializacji. Sposób określenia tego typu w kodzie definiuje działanie, które należy wykonać, zgodnie z opisem w dwóch następnych sekcjach.  
  
### <a name="typeof-used-in-the-constructor"></a>wartość typeof użyta w konstruktorze

 W przypadku wywołania konstruktora tych klas serializacji i dołączenia C# operatora [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) w wywołaniu metody **nie trzeba wykonywać żadnych dodatkowych czynności**. Na przykład w każdym z następujących wywołań konstruktora `typeof` klasy serializacji słowo kluczowe jest używane jako część wyrażenia przesłanego do konstruktora.  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 Kompilator .NET Native automatycznie obsłuży ten kod.  
  
### <a name="typeof-used-outside-the-constructor"></a>wartość typeof użyta poza konstruktorem

 Jeśli wywołasz konstruktora tych klas serializacji i użyjesz C# operatora [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) poza wyrażeniem dostarczonym do <xref:System.Type> parametru konstruktora, jak w poniższym kodzie, kompilator .NET Native nie może rozpoznać typu:  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 W takim przypadku należy określić typ w pliku dyrektywy środowiska uruchomieniowego, dodając wpis podobny do tego:  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 Podobnie w przypadku wywołania konstruktora, takiego jak <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> i udostępnienia tablicy dodatkowych <xref:System.Type> obiektów do serializacji, jak w poniższym kodzie, kompilator .NET Native nie może rozpoznać tych typów.  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 Należy dodać następujące wpisy dla każdego typu do pliku dyrektywy środowiska uruchomieniowego:  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 Aby uzyskać informacje o składni używanej w tym przykładzie, zobacz [ \<Type > element](type-element-net-native.md).  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
- [\<Typ > element](type-element-net-native.md)
- [\<Przestrzeń nazw > element](namespace-element-net-native.md)
