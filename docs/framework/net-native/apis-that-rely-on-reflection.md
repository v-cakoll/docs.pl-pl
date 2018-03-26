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
# <a name="apis-that-rely-on-reflection"></a><span data-ttu-id="34050-102">Interfejsy API, które działają na podstawie odbicia</span><span class="sxs-lookup"><span data-stu-id="34050-102">APIs That Rely on Reflection</span></span>
<span data-ttu-id="34050-103">W niektórych przypadkach użycia odbicie w kodzie nie jest widoczne, a więc [!INCLUDE[net_native](../../../includes/net-native-md.md)] łańcucha narzędzi nie przechowują metadane, który jest wymagany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="34050-103">In some cases, the use of reflection in code isn't obvious, and so the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain doesn't preserve metadata that is needed at run time.</span></span> <span data-ttu-id="34050-104">W tym temacie omówiono niektóre typowe interfejsów API lub typowe wzorce programowania, które nie są traktowane jako część odbicia interfejsu API, ale które działają na podstawie odbicia się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="34050-104">This topic covers some common APIs or common programming patterns that aren't considered part of the reflection API but that rely on reflection to execute successfully.</span></span> <span data-ttu-id="34050-105">Jeśli używasz je w kodzie źródłowym, można dodać informacje dotyczące ich do dyrektyw środowiska uruchomieniowego (. rd.xml) plików w celu wywołania tych interfejsów API nie zgłaszają [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) wyjątku lub innych wyjątek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="34050-105">If you use them in your source code, you can add information about them to the runtime directives (.rd.xml) file so that calls to these APIs do not throw a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception or some other exception at run time.</span></span>  
  
## <a name="typemakegenerictype-method"></a><span data-ttu-id="34050-106">Type.MakeGenericType — metoda</span><span class="sxs-lookup"><span data-stu-id="34050-106">Type.MakeGenericType method</span></span>  
 <span data-ttu-id="34050-107">Można dynamicznie utworzyć wystąpienia typu ogólnego `AppClass<T>` przez wywołanie metody <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metody przy użyciu kodu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="34050-107">You can dynamically instantiate a generic type `AppClass<T>` by calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 <span data-ttu-id="34050-108">Dla tego kodu została wykonana pomyślnie w czasie wykonywania wymagane są kilka elementów metadanych.</span><span class="sxs-lookup"><span data-stu-id="34050-108">For this code to succeed at run time, several items of metadata are required.</span></span> <span data-ttu-id="34050-109">Pierwsza to `Browse` metadanych dla typu ogólnego bez `AppClass<T>`:</span><span class="sxs-lookup"><span data-stu-id="34050-109">The first is `Browse` metadata for the uninstantiated generic type, `AppClass<T>`:</span></span>  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="34050-110">Dzięki temu <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> wywołanie metody sukcesu i zwracać prawidłowy <xref:System.Type> obiektu.</span><span class="sxs-lookup"><span data-stu-id="34050-110">This allows the <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> method call to succeed and return a valid <xref:System.Type> object.</span></span>  
  
 <span data-ttu-id="34050-111">Ale nawet wtedy, gdy dodasz metadanych dla typu ogólnego bez wywoływania <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metoda zgłasza [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) wyjątek:</span><span class="sxs-lookup"><span data-stu-id="34050-111">But even when you add metadata for the uninstantiated generic type, calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method throws a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception:</span></span>  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.AppClass`1<System.Int32>.  
```  
  
 <span data-ttu-id="34050-112">Następujące dyrektywy środowiska wykonawczego można dodać do pliku dyrektyw środowiska uruchomieniowego można dodać `Activate` metadanych dla konkretnego wystąpienia za pośrednictwem `AppClass<T>` z <xref:System.Int32?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="34050-112">You can add the following run-time directive to the runtime directives file to add `Activate` metadata for the specific instantiation over `AppClass<T>` of <xref:System.Int32?displayProperty=nameWithType>:</span></span>  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"   
                   Activate="Required Public" />  
```  
  
 <span data-ttu-id="34050-113">Podczas tworzenia wystąpienia każdej innej za pośrednictwem `AppClass<T>` wymaga oddzielnej dyrektywy, jeśli jest tworzony z <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> — metoda i nie używać statycznie.</span><span class="sxs-lookup"><span data-stu-id="34050-113">Each different instantiation over `AppClass<T>` requires a separate directive if it is being created with the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method and not used statically.</span></span>  
  
## <a name="methodinfomakegenericmethod-method"></a><span data-ttu-id="34050-114">MethodInfo.MakeGenericMethod — metoda</span><span class="sxs-lookup"><span data-stu-id="34050-114">MethodInfo.MakeGenericMethod method</span></span>  
 <span data-ttu-id="34050-115">Podana klasa `Class1` metodą rodzajową `GetMethod<T>(T t)`, `GetMethod` może być wywoływany przez odbicie przy użyciu kodu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="34050-115">Given a class `Class1` with a generic method `GetMethod<T>(T t)`, `GetMethod` can be invoked through reflection by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 <span data-ttu-id="34050-116">Aby pomyślnie uruchomić, ten kod wymaga kilku elementów metadanych:</span><span class="sxs-lookup"><span data-stu-id="34050-116">To run successfully, this code requires several items of metadata:</span></span>  
  
-   <span data-ttu-id="34050-117">`Browse` metadane dla typu metody, których chcesz się połączyć.</span><span class="sxs-lookup"><span data-stu-id="34050-117">`Browse` metadata for the type whose method you want to call.</span></span>  
  
-   <span data-ttu-id="34050-118">`Browse` metadane dla metodę, którą chcesz się połączyć.</span><span class="sxs-lookup"><span data-stu-id="34050-118">`Browse` metadata for the method you want to call.</span></span>  <span data-ttu-id="34050-119">Jeśli jest to metoda publiczne, dodawanie publicznego `Browse` metadanych dla typu zawierającego obejmuje metodę za.</span><span class="sxs-lookup"><span data-stu-id="34050-119">If it is a public method, adding public `Browse` metadata for the containing type includes the method, too.</span></span>  
  
-   <span data-ttu-id="34050-120">Dynamiczne metadanych dla metody chcesz się połączyć, tak aby delegat wywołania odbicia nie został usunięty przez [!INCLUDE[net_native](../../../includes/net-native-md.md)] narzędzia łańcucha.</span><span class="sxs-lookup"><span data-stu-id="34050-120">Dynamic metadata for the method you want to call, so that the reflection invocation delegate is not removed by the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain.</span></span> <span data-ttu-id="34050-121">Jeśli metadane dynamiczne brakuje metody, następującego wyjątku podczas <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> metoda jest wywoływana:</span><span class="sxs-lookup"><span data-stu-id="34050-121">If dynamic metadata is missing for the method, the following exception is thrown when the <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> method is called:</span></span>  
  
    ```  
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 <span data-ttu-id="34050-122">Następujące dyrektyw środowiska uruchomieniowego upewnij się, że wszystkie wymagane metadane są dostępne:</span><span class="sxs-lookup"><span data-stu-id="34050-122">The following runtime directives ensure that all required metadata is available:</span></span>  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 <span data-ttu-id="34050-123">A `MethodInstantiation` dyrektywa jest wymagana dla każdego innego wystąpienia metody, która jest wywołana dynamicznie, i `Arguments` element jest aktualizowana w celu odzwierciedlenia każdy argument innego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="34050-123">A `MethodInstantiation` directive is required for each different instantiation of the method that is dynamically invoked, and the `Arguments` element is updated to reflect each different instantiation argument.</span></span>  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a><span data-ttu-id="34050-124">Metody Array.CreateInstance i Type.MakeTypeArray</span><span class="sxs-lookup"><span data-stu-id="34050-124">Array.CreateInstance and Type.MakeTypeArray methods</span></span>  
 <span data-ttu-id="34050-125">Następujące przykładowe wywołania <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> i <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metody w typie `Class1`.</span><span class="sxs-lookup"><span data-stu-id="34050-125">The following example calls the <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> methods on a type, `Class1`.</span></span>  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 <span data-ttu-id="34050-126">Jeśli metadanych tablicy nie jest obecny, powoduje następujący błąd:</span><span class="sxs-lookup"><span data-stu-id="34050-126">If no array metadata is present, the following error results:</span></span>  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 <span data-ttu-id="34050-127">`Browse` metadane dla typu tablicy jest wymagana do dynamicznie utworzyć wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="34050-127">`Browse` metadata for the array type is required to dynamically instantiate it.</span></span>  <span data-ttu-id="34050-128">Następujące dyrektyw środowiska uruchomieniowego umożliwia dynamiczne tworzenie wystąpienia `Class1[]`.</span><span class="sxs-lookup"><span data-stu-id="34050-128">The following runtime directive allows dynamic instantiation of `Class1[]`.</span></span>  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="34050-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34050-129">See Also</span></span>  
 [<span data-ttu-id="34050-130">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="34050-130">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [<span data-ttu-id="34050-131">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="34050-131">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
