---
title: Interfejsy API, które działają na podstawie odbicia
ms.date: 03/30/2017
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
ms.openlocfilehash: 1d8daceb6b744b984f86b011ad7952d0da583a79
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79181092"
---
# <a name="apis-that-rely-on-reflection"></a>Interfejsy API, które działają na podstawie odbicia
W niektórych przypadkach użycie odbicia w kodzie nie jest oczywiste i dlatego łańcuch narzędzi .NET Native nie zachowuje metadanych wymaganych w czasie wykonywania. W tym temacie opisano niektóre typowe interfejsy API lub typowe wzorce programowania, które nie są uważane za część interfejsu API odbicia, ale które polegają na pomyślnym wykonaniu odbicia. Jeśli używasz ich w kodzie źródłowym, możesz dodać informacje o nich do pliku dyrektywy środowiska uruchomieniowego (. Rd. xml), tak aby wywołania tych interfejsów API nie zgłaszają wyjątku [MissingMetadataException](missingmetadataexception-class-net-native.md) ani innego wyjątku w czasie wykonywania.  
  
## <a name="typemakegenerictype-method"></a>Type. MakeGenericType, Metoda  
 Można dynamicznie utworzyć wystąpienie typu ogólnego `AppClass<T>` , wywołując <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metodę przy użyciu kodu w następujący sposób:  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 Aby ten kod zakończył się pomyślnie w czasie wykonywania, wymagane są kilka elementów metadanych. Pierwszy to `Browse` metadane dla niewystąpienia typu ogólnego, `AppClass<T>` :  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 Dzięki temu <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> wywołanie metody powiodło się i zwróci prawidłowy <xref:System.Type> obiekt.  
  
 Jednak nawet w przypadku dodania metadanych dla typu ogólnego bez wystąpienia, wywołanie <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metody zgłasza wyjątek [MissingMetadataException](missingmetadataexception-class-net-native.md) :  
  
Nie można wykonać tej operacji, ponieważ metadane następującego typu zostały usunięte ze względu na wydajność:  
  
`App1.AppClass`1<system. Int32>".  
  
 Można dodać następującą dyrektywę uruchomieniową do pliku dyrektywy środowiska uruchomieniowego, aby dodać `Activate` metadane dla konkretnego wystąpienia `AppClass<T>` z <xref:System.Int32?displayProperty=nameWithType> :  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"
                   Activate="Required Public" />  
```  
  
 Każde różne wystąpienie `AppClass<T>` tego typu wymaga oddzielnej dyrektywy, jeśli jest tworzona przy użyciu <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metody i nie jest używana statycznie.  
  
## <a name="methodinfomakegenericmethod-method"></a>MethodInfo. MakeGenericMethod — Metoda  
 Dana Klasa `Class1` z metodą generyczną `GetMethod<T>(T t)` `GetMethod` może być wywoływana poprzez odbicie przy użyciu kodu w następujący sposób:  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 Aby pomyślnie uruchomić, ten kod wymaga kilku elementów metadanych:  
  
- `Browse`metadane dla typu, którego Metoda ma zostać wywołana.  
  
- `Browse`metadane dla metody, która ma zostać wywołana.  Jeśli jest to metoda publiczna, Dodawanie publicznych `Browse` metadanych dla typu zawierającego zawiera również metodę.  
  
- Dynamiczne metadane dla metody, która ma zostać wywołana, tak aby delegat wywołania odbicia nie został usunięty przez łańcuch narzędzi .NET Native. Jeśli brakuje metadanych dynamicznych dla metody, następujący wyjątek jest zgłaszany, gdy wywoływana jest <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> Metoda:  
  
    ```output
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 Następujące dyrektywy środowiska uruchomieniowego zapewniają dostępność wszystkich wymaganych metadanych:  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 `MethodInstantiation`Dyrektywa jest wymagana dla każdego innego wystąpienia metody, która jest wywoływana dynamicznie, i `Arguments` jest aktualizowana w celu odzwierciedlenia każdego innego argumentu tworzenia wystąpienia.  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a>Array. CreateInstance i Type. MakeTypeArray, metody  
 Poniższy przykład wywołuje <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metody i dla typu, `Class1` .  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 Jeśli nie ma metadanych tablicy, następujące wyniki błędu:  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 `Browse`metadane dla typu tablicy są wymagane do dynamicznego tworzenia wystąpienia.  Następująca dyrektywa środowiska uruchomieniowego umożliwia dynamiczne tworzenie wystąpień `Class1[]` .  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie](getting-started-with-net-native.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
