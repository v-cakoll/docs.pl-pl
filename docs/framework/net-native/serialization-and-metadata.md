---
title: Serializacja i metadane
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c82d32fe5b1e62a19ff5e2920c5943f1303b2d64
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599487"
---
# <a name="serialization-and-metadata"></a>Serializacja i metadane
Jeśli Twoja aplikacja serializuje i deserializuje obiektów, konieczne może być dodawanie wpisów do Twojej dyrektywy środowiska uruchomieniowego (. rd.xml) plik, aby upewnić się, że metadane potrzebne znajduje się w czasie wykonywania. Istnieją dwie kategorie serializatory, a każdy z nich wymaga innej obsługi w pliku dyrektyw środowiska uruchomieniowego:  
  
- Oparty na odbiciu serializatory innych firm. Te wymagają modyfikacji pliku dyrektyw środowiska uruchomieniowego i zostały omówione w następnej sekcji.  
  
- Odbicie inne niż oparte serializatory znalezione w bibliotece klas programu .NET Framework. Te mogą wymagać modyfikacji pliku dyrektyw środowiska uruchomieniowego, zostały one omówione w [serializatory Microsoft](#Microsoft) sekcji.  
  
<a name="ThirdParty"></a>   
## <a name="third-party-serializers"></a>Serializatory innych firm  
 Serializatory firm trzecich, w tym Newtonsoft.JSON, są zazwyczaj oparty na odbiciu. Biorąc pod uwagę duży obiekt binarny (BLOB) serializowanych danych, pól danych są przypisane do konkretnego typu przez wyszukanie pola typu docelowego według nazwy. Jako minimum, korzystania z tych bibliotek powoduje, że [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) wyjątki dla poszczególnych <xref:System.Type> obiekt, który próbujesz serializacji lub deserializacji w `List<Type>` kolekcji.  
  
 Najprostszym sposobem, aby rozwiązać problemy spowodowane przez Brak metadanych dla tych serializatory ma zbierać typy, które będą używane w serializacji w ramach jednej przestrzeni nazw (takich jak `App.Models`) i Zastosuj `Serialize` dyrektywy metadanych:  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 Aby uzyskać informacje dotyczące składni użytych w tym przykładzie, zobacz [ \<Namespace > Element](../../../docs/framework/net-native/namespace-element-net-native.md).  
  
<a name="Microsoft"></a>   
## <a name="microsoft-serializers"></a>Serializatory firmy Microsoft  
 Mimo że <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, i <xref:System.Xml.Serialization.XmlSerializer> klasy, nie należy polegać na podstawie odbicia, wymagają one generowania kodu na podstawie obiektu serializacji lub deserializacji. Przeciążenia konstruktorów dla każdego elementu serializującego obejmują <xref:System.Type> parametr, który określa typ serializacji lub deserializacji. Jak określić typu w kodzie definiuje akcję, którą należy wykonać, zgodnie z opisem w dwóch następnych sekcjach.  
  
### <a name="typeof-used-in-the-constructor"></a>TypeOf używany w Konstruktorze  
 Możesz wywołać konstruktora klasy te serializacji i obejmują C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) — słowo kluczowe w wywołaniu metody **nie trzeba wykonywać żadnych dodatkowych działań**. Na przykład w każdym z następujących wywołania konstruktora klasy serializacji `typeof` słowo kluczowe jest używane jako część wyrażenia przekazany do konstruktora.  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] Kompilator będzie automatycznie obsługiwać ten kod.  
  
### <a name="typeof-used-outside-the-constructor"></a>TypeOf używany poza konstruktora  
 Możesz wywołać konstruktora klasy te serializacji i używać C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) — słowo kluczowe poza wyrażenie dostarczane do konstruktora <xref:System.Type> parametru, zgodnie z poniższym kodem [!INCLUDE[net_native](../../../includes/net-native-md.md)] kompilatora Nie można rozpoznać typu:  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 W takim przypadku należy określić typ w plik dyrektywy środowiska uruchomieniowego, dodając wpis podobny do tego:  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 Podobnie jeśli takie jak wywołać konstruktora <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> i zapewniają szereg dodatkowych <xref:System.Type> obiekty do serializacji, tak jak w poniższym kodzie [!INCLUDE[net_native](../../../includes/net-native-md.md)] kompilator nie może rozpoznać te typy.  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 Należy dodać wpisy podobny do następującego dla każdego typu pliku dyrektyw środowiska uruchomieniowego:  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 Aby uzyskać informacje dotyczące składni użytych w tym przykładzie, zobacz [ \<typ > Element](../../../docs/framework/net-native/type-element-net-native.md).  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)
- [\<Typ > Element](../../../docs/framework/net-native/type-element-net-native.md)
- [\<Namespace > Element](../../../docs/framework/net-native/namespace-element-net-native.md)
