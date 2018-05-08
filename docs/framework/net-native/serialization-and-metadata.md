---
title: Serializacja i metadane
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e4db59da7a17e47b8e3df939ec64f5124e04454
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="serialization-and-metadata"></a>Serializacja i metadane
Jeśli aplikacja serializuje i deserializuje obiektów, może być konieczne dodanie wpisów do Twojej dyrektyw środowiska uruchomieniowego (. rd.xml) pliku, aby upewnić się, że metadane potrzebne jest obecny w czasie wykonywania. Istnieją dwie kategorie serializatorów i każdy z nich wymaga innej obsługi w pliku dyrektyw środowiska uruchomieniowego:  
  
-   Oparty na odbiciu serializatorów innych firm. Są wymagają modyfikacji pliku dyrektyw środowiska uruchomieniowego które opisano w następnej sekcji.  
  
-   Odbicie nie na podstawie serializatorów w bibliotece klas programu .NET Framework. Są mogą wymagać modyfikacji pliku dyrektyw środowiska uruchomieniowego które zostały omówione w [serializatorów Microsoft](#Microsoft) sekcji.  
  
<a name="ThirdParty"></a>   
## <a name="third-party-serializers"></a>Serializatorów innych firm  
 Serializatorów innych części, w tym Newtonsoft.JSON, zazwyczaj są oparty na odbiciu. Podana dużego obiektu binarnego (BLOB) serializowanych danych, pola w danych są przypisane do konkretnego typu według pola Typ docelowy według nazwy. Co najmniej przy użyciu biblioteki powoduje [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) wyjątków dla każdego <xref:System.Type> obiekt, który zostanie podjęta próba serializacji lub deserializacji w `List<Type>` kolekcji.  
  
 Najprostszym sposobem, aby rozwiązać problemy spowodowane przez Brak metadanych dla tych serializatorów jest zbieranie typy, które będą używane w serializacji w jednej przestrzeni nazw (takich jak `App.Models`) i zastosować `Serialize` dyrektywy metadanych:  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 Informacje o składni używanej w tym przykładzie, zobacz [ \<Namespace > elementu](../../../docs/framework/net-native/namespace-element-net-native.md).  
  
<a name="Microsoft"></a>   
## <a name="microsoft-serializers"></a>Microsoft serializatorów  
 Mimo że <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, i <xref:System.Xml.Serialization.XmlSerializer> klas, nie należy polegać na podstawie odbicia, wymagają one będzie generowany kod na podstawie obiektu serializacji lub deserializacji. Przeciążone konstruktory dla każdego serializator obejmują <xref:System.Type> parametr określający typ serializacji lub deserializacji. Sposób określania typu w kodzie definiuje akcji, które należy podjąć, zgodnie z opisem w dwóch następnych sekcjach.  
  
### <a name="typeof-used-in-the-constructor"></a>TypeOf używany w Konstruktorze  
 Jeśli można wywołać konstruktora z tych klas serializacji i obejmują C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) — słowo kluczowe w wywołaniu metody **nie trzeba wykonywać żadnych dodatkowych działań**. Na przykład w każdej z następujących wywołania konstruktora klasy serializacji `typeof` słowo kluczowe jest używane jako część wyrażenia przekazany do konstruktora.  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] Kompilatora będzie automatycznie obsługiwał tego kodu.  
  
### <a name="typeof-used-outside-the-constructor"></a>TypeOf używane poza konstruktora  
 Można wywołać konstruktora z tych klas serializacji i używać języka C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) — słowo kluczowe poza wyrażeniem przekazany do konstruktora <xref:System.Type> parametru zgodnie z poniższym kodem [!INCLUDE[net_native](../../../includes/net-native-md.md)] nie kompilatora Aby usunąć typ:  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 W takim przypadku należy określić typ pliku dyrektyw środowiska uruchomieniowego, dodając wpis następująco:  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 Podobnie jeśli takie jak wywołać konstruktora <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> i podaj tablicę dodatkowe <xref:System.Type> obiekty do serializacji, zgodnie z poniższym kodem [!INCLUDE[net_native](../../../includes/net-native-md.md)] kompilatora nie można rozpoznać typu.  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 Wpisy, takich jak dla każdego typu należy dodać do pliku dyrektyw środowiska uruchomieniowego:  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 Informacje o składni używanej w tym przykładzie, zobacz [ \<typu > elementu](../../../docs/framework/net-native/type-element-net-native.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [\<Typ > — Element](../../../docs/framework/net-native/type-element-net-native.md)  
 [\<Namespace > — Element](../../../docs/framework/net-native/namespace-element-net-native.md)
