---
title: Interfejsy API, które działają na podstawie odbicia
ms.date: 03/30/2017
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
ms.openlocfilehash: 1d8daceb6b744b984f86b011ad7952d0da583a79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181092"
---
# <a name="apis-that-rely-on-reflection"></a>Interfejsy API, które działają na podstawie odbicia
W niektórych przypadkach użycie odbicia w kodzie nie jest oczywiste, a więc łańcuch narzędzi natywnych platformy .NET nie zachowuje metadanych, które są potrzebne w czasie wykonywania. W tym temacie opisano niektóre typowe interfejsy API lub typowe wzorce programowania, które nie są uważane za część interfejsu API odbicia, ale które opierają się na odbicie, aby wykonać pomyślnie. Jeśli używasz ich w kodzie źródłowym, można dodać informacje o nich do pliku dyrektywy środowiska wykonawczego (.rd.xml), tak aby wywołania tych interfejsów API nie [zgłaszać missingmetadataexception](missingmetadataexception-class-net-native.md) wyjątek lub inny wyjątek w czasie wykonywania.  
  
## <a name="typemakegenerictype-method"></a>Typ.MakeGenericType metoda  
 Można dynamicznie utworzyć wystąpienia typu `AppClass<T>` ogólnego, <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> wywołując metodę przy użyciu kodu w ten sposób:  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 Aby ten kod zakończył się pomyślnie w czasie wykonywania, wymagane jest kilka elementów metadanych. Pierwszym z `Browse` nich są metadane dla nierozpoznanego typu ogólnego, `AppClass<T>`:  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 Dzięki temu <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> wywołanie metody zakończy <xref:System.Type> się pomyślnie i zwraca prawidłowy obiekt.  
  
 Ale nawet po dodaniu metadanych dla nieuznanego <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> typu ogólnego, wywołanie metody zgłasza wyjątek [MissingMetadataException:](missingmetadataexception-class-net-native.md)  
  
Ta operacja nie może być przeprowadzona jako metadane dla następującego typu został usunięty ze względu na wydajność:  
  
`App1.AppClass`1<System.Int32>'.  
  
 Do pliku dyrektyw środowiska wykonawczego można dodać następującą dyrektywę w czasie wykonywania, aby dodać `Activate` metadane dla określonego `AppClass<T>` <xref:System.Int32?displayProperty=nameWithType>wystąpienia:  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"
                   Activate="Required Public" />  
```  
  
 Każde wystąpienie nad `AppClass<T>` wymaga oddzielnej dyrektywy, jeśli <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> jest tworzony za pomocą metody i nie jest używany statycznie.  
  
## <a name="methodinfomakegenericmethod-method"></a>MethodInfo.MakeGenericMetoda metoda  
 Biorąc pod `Class1` uwagę klasę `GetMethod<T>(T t)` `GetMethod` z metodą rodzajową, można wywołać poprzez odbicie przy użyciu kodu w ten sposób:  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 Aby uruchomić pomyślnie, ten kod wymaga kilku elementów metadanych:  
  
- `Browse`metadanych dla typu, którego metodę chcesz wywołać.  
  
- `Browse`metadanych dla metody, którą chcesz wywołać.  Jeśli jest to metoda publiczna, dodawanie publicznych `Browse` metadanych dla typu zawierającego zawiera również metodę.  
  
- Dynamiczne metadane metody, którą chcesz wywołać, aby delegat wywołania odbicia nie został usunięty przez łańcuch narzędzi natywnych dla platformy .NET. Jeśli brakuje metadanych dynamicznych dla metody, następujący <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> wyjątek jest zgłaszany, gdy metoda jest wywoływana:  
  
    ```output
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 Następujące dyrektywy środowiska wykonawczego zapewniają, że wszystkie wymagane metadane są dostępne:  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 Dyrektywa `MethodInstantiation` jest wymagana dla każdego wystąpienia różnych metody, która jest dynamicznie `Arguments` wywoływana, a element jest aktualizowany w celu odzwierciedlenia każdego argumentu wystąpienia.  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a>Metody Array.CreateInstance i Type.MakeTypeArray  
 W poniższym <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> przykładzie wywołuje <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> i `Class1`metody na typ, .  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 Jeśli nie ma metadanych tablicy, wyniki błędu są następujące:  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 `Browse`metadane dla typu tablicy jest wymagane do dynamicznego wystąpienia go.  Poniższa dyrektywa środowiska wykonawczego umożliwia `Class1[]`dynamiczne tworzenie wystąpienia programu .  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie](getting-started-with-net-native.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
