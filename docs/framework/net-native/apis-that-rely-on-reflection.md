---
title: Interfejsy API, które działają na podstawie odbicia
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 49ac12bcae3fd85744961a6e3b81129178c2c323
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="apis-that-rely-on-reflection"></a>Interfejsy API, które działają na podstawie odbicia
W niektórych przypadkach użycia odbicie w kodzie nie jest widoczne, a więc [!INCLUDE[net_native](../../../includes/net-native-md.md)] łańcucha narzędzi nie przechowują metadane, który jest wymagany w czasie wykonywania. W tym temacie omówiono niektóre typowe interfejsów API lub typowe wzorce programowania, które nie są traktowane jako część odbicia interfejsu API, ale które działają na podstawie odbicia się pomyślnie. Jeśli używasz je w kodzie źródłowym, można dodać informacje dotyczące ich do dyrektyw środowiska uruchomieniowego (. rd.xml) plików w celu wywołania tych interfejsów API nie zgłaszają [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) wyjątku lub innych wyjątek w czasie wykonywania.  
  
## <a name="typemakegenerictype-method"></a>Type.MakeGenericType — metoda  
 Można dynamicznie utworzyć wystąpienia typu ogólnego `AppClass<T>` przez wywołanie metody <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metody przy użyciu kodu w następujący sposób:  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 Dla tego kodu została wykonana pomyślnie w czasie wykonywania wymagane są kilka elementów metadanych. Pierwsza to `Browse` metadanych dla typu ogólnego bez `AppClass<T>`:  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 Dzięki temu <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> wywołanie metody sukcesu i zwracać prawidłowy <xref:System.Type> obiektu.  
  
 Ale nawet wtedy, gdy dodasz metadanych dla typu ogólnego bez wywoływania <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metoda zgłasza [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) wyjątek:  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.AppClass`1<System.Int32>.  
```  
  
 Następujące dyrektywy środowiska wykonawczego można dodać do pliku dyrektyw środowiska uruchomieniowego można dodać `Activate` metadanych dla konkretnego wystąpienia za pośrednictwem `AppClass<T>` z <xref:System.Int32?displayProperty=nameWithType>:  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"   
                   Activate="Required Public" />  
```  
  
 Podczas tworzenia wystąpienia każdej innej za pośrednictwem `AppClass<T>` wymaga oddzielnej dyrektywy, jeśli jest tworzony z <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> — metoda i nie używać statycznie.  
  
## <a name="methodinfomakegenericmethod-method"></a>MethodInfo.MakeGenericMethod — metoda  
 Podana klasa `Class1` metodą rodzajową `GetMethod<T>(T t)`, `GetMethod` może być wywoływany przez odbicie przy użyciu kodu w następujący sposób:  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 Aby pomyślnie uruchomić, ten kod wymaga kilku elementów metadanych:  
  
-   `Browse` metadane dla typu metody, których chcesz się połączyć.  
  
-   `Browse` metadane dla metodę, którą chcesz się połączyć.  Jeśli jest to metoda publiczne, dodawanie publicznego `Browse` metadanych dla typu zawierającego obejmuje metodę za.  
  
-   Dynamiczne metadanych dla metody chcesz się połączyć, tak aby delegat wywołania odbicia nie został usunięty przez [!INCLUDE[net_native](../../../includes/net-native-md.md)] narzędzia łańcucha. Jeśli metadane dynamiczne brakuje metody, następującego wyjątku podczas <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> metoda jest wywoływana:  
  
    ```  
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 Następujące dyrektyw środowiska uruchomieniowego upewnij się, że wszystkie wymagane metadane są dostępne:  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 A `MethodInstantiation` dyrektywa jest wymagana dla każdego innego wystąpienia metody, która jest wywołana dynamicznie, i `Arguments` element jest aktualizowana w celu odzwierciedlenia każdy argument innego wystąpienia.  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a>Metody Array.CreateInstance i Type.MakeTypeArray  
 Następujące przykładowe wywołania <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> i <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metody w typie `Class1`.  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 Jeśli metadanych tablicy nie jest obecny, powoduje następujący błąd:  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 `Browse` metadane dla typu tablicy jest wymagana do dynamicznie utworzyć wystąpienia.  Następujące dyrektyw środowiska uruchomieniowego umożliwia dynamiczne tworzenie wystąpienia `Class1[]`.  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
