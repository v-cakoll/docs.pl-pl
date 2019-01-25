---
title: Interfejsy API, które działają na podstawie odbicia
ms.date: 03/30/2017
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26a198db13e5855d9473cf7780dade9ce95e9298
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610850"
---
# <a name="apis-that-rely-on-reflection"></a><span data-ttu-id="84f9e-102">Interfejsy API, które działają na podstawie odbicia</span><span class="sxs-lookup"><span data-stu-id="84f9e-102">APIs That Rely on Reflection</span></span>
<span data-ttu-id="84f9e-103">W niektórych przypadkach użycie odbicia w kodzie nie jest oczywisty, a więc [!INCLUDE[net_native](../../../includes/net-native-md.md)] łańcucha narzędzi nie przechowują metadane, które są potrzebne w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="84f9e-103">In some cases, the use of reflection in code isn't obvious, and so the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain doesn't preserve metadata that is needed at run time.</span></span> <span data-ttu-id="84f9e-104">W tym temacie omówiono niektóre typowe interfejsów API lub typowe wzorce programowania, które nie są traktowane jako część interfejs API odbicia, ale opierają się na podstawie odbicia, aby zostać pomyślnie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="84f9e-104">This topic covers some common APIs or common programming patterns that aren't considered part of the reflection API but that rely on reflection to execute successfully.</span></span> <span data-ttu-id="84f9e-105">Jeśli będziesz ich używać w kodzie źródłowym, można dodać informacji o nich dyrektyw środowiska uruchomieniowego (. rd.xml) plików nie zgłaszają wywołań do tych interfejsów API [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) wyjątku lub innych wyjątków w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="84f9e-105">If you use them in your source code, you can add information about them to the runtime directives (.rd.xml) file so that calls to these APIs do not throw a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception or some other exception at run time.</span></span>  
  
## <a name="typemakegenerictype-method"></a><span data-ttu-id="84f9e-106">Metoda Type.MakeGenericType</span><span class="sxs-lookup"><span data-stu-id="84f9e-106">Type.MakeGenericType method</span></span>  
 <span data-ttu-id="84f9e-107">Dynamicznie utworzyć wystąpienia typu ogólnego `AppClass<T>` przez wywołanie metody <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metody przy użyciu kodu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="84f9e-107">You can dynamically instantiate a generic type `AppClass<T>` by calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 <span data-ttu-id="84f9e-108">Dla tego kodu zakończyło się sukcesem w czasie wykonywania wymagane są kilka elementów metadanych.</span><span class="sxs-lookup"><span data-stu-id="84f9e-108">For this code to succeed at run time, several items of metadata are required.</span></span> <span data-ttu-id="84f9e-109">Pierwsza to `Browse` metadanych dla typ ogólny bez wystąpień `AppClass<T>`:</span><span class="sxs-lookup"><span data-stu-id="84f9e-109">The first is `Browse` metadata for the uninstantiated generic type, `AppClass<T>`:</span></span>  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="84f9e-110">Dzięki temu <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> wywołanie metody powiodło się i zwraca prawidłową <xref:System.Type> obiektu.</span><span class="sxs-lookup"><span data-stu-id="84f9e-110">This allows the <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> method call to succeed and return a valid <xref:System.Type> object.</span></span>  
  
 <span data-ttu-id="84f9e-111">Ale nawet wtedy, gdy dodasz metadanych dla typ ogólny bez wystąpień, wywołanie <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metoda zgłasza wyjątek [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) wyjątek:</span><span class="sxs-lookup"><span data-stu-id="84f9e-111">But even when you add metadata for the uninstantiated generic type, calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method throws a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception:</span></span>  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.AppClass`1<System.Int32>.  
```  
  
 <span data-ttu-id="84f9e-112">Następująca dyrektywa czasu wykonywania można dodać do pliku dyrektywy środowiska uruchomieniowego, aby dodać `Activate` metadanych dla określonego wystąpienia ciągu `AppClass<T>` z <xref:System.Int32?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="84f9e-112">You can add the following run-time directive to the runtime directives file to add `Activate` metadata for the specific instantiation over `AppClass<T>` of <xref:System.Int32?displayProperty=nameWithType>:</span></span>  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"   
                   Activate="Required Public" />  
```  
  
 <span data-ttu-id="84f9e-113">Każdy różne wystąpienia ciągu `AppClass<T>` wymaga oddzielnej dyrektywy, jeśli jest tworzona przy użyciu <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metody i nie używać statycznie.</span><span class="sxs-lookup"><span data-stu-id="84f9e-113">Each different instantiation over `AppClass<T>` requires a separate directive if it is being created with the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method and not used statically.</span></span>  
  
## <a name="methodinfomakegenericmethod-method"></a><span data-ttu-id="84f9e-114">Metoda MethodInfo.MakeGenericMethod</span><span class="sxs-lookup"><span data-stu-id="84f9e-114">MethodInfo.MakeGenericMethod method</span></span>  
 <span data-ttu-id="84f9e-115">Podana klasa `Class1` przy użyciu metody ogólnej `GetMethod<T>(T t)`, `GetMethod` może być wywoływany przez odbicie, przy użyciu kodu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="84f9e-115">Given a class `Class1` with a generic method `GetMethod<T>(T t)`, `GetMethod` can be invoked through reflection by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 <span data-ttu-id="84f9e-116">Pomyślnie uruchomić ten kod wymaga kilku elementów metadanych:</span><span class="sxs-lookup"><span data-stu-id="84f9e-116">To run successfully, this code requires several items of metadata:</span></span>  
  
-   <span data-ttu-id="84f9e-117">`Browse` metadane dla typu do wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="84f9e-117">`Browse` metadata for the type whose method you want to call.</span></span>  
  
-   <span data-ttu-id="84f9e-118">`Browse` metadane dla metody, którą chcesz się połączyć.</span><span class="sxs-lookup"><span data-stu-id="84f9e-118">`Browse` metadata for the method you want to call.</span></span>  <span data-ttu-id="84f9e-119">Jeśli jest to metoda publiczna, dodając publicznych `Browse` metadane dla typu zawierającego zawierają metody, zbyt.</span><span class="sxs-lookup"><span data-stu-id="84f9e-119">If it is a public method, adding public `Browse` metadata for the containing type includes the method, too.</span></span>  
  
-   <span data-ttu-id="84f9e-120">Dynamiczne metadane dla metody ma zostać wywołana, tak aby delegat wywołania odbicia nie są usuwane przez [!INCLUDE[net_native](../../../includes/net-native-md.md)] łańcucha narzędzi.</span><span class="sxs-lookup"><span data-stu-id="84f9e-120">Dynamic metadata for the method you want to call, so that the reflection invocation delegate is not removed by the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain.</span></span> <span data-ttu-id="84f9e-121">W przypadku brakujących metody dynamiczne metadane następujący wyjątek jest generowany, gdy <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> metoda jest wywoływana:</span><span class="sxs-lookup"><span data-stu-id="84f9e-121">If dynamic metadata is missing for the method, the following exception is thrown when the <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> method is called:</span></span>  
  
    ```  
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 <span data-ttu-id="84f9e-122">Następujące dyrektywy środowiska uruchomieniowego upewnij się, że wszystkie wymagane metadane są dostępne:</span><span class="sxs-lookup"><span data-stu-id="84f9e-122">The following runtime directives ensure that all required metadata is available:</span></span>  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 <span data-ttu-id="84f9e-123">A `MethodInstantiation` dyrektywa jest wymagana dla każdego wystąpienia różne metody, która jest wywołana dynamicznie, a `Arguments` element zostanie zaktualizowany w celu odzwierciedlenia każdy argument różne wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="84f9e-123">A `MethodInstantiation` directive is required for each different instantiation of the method that is dynamically invoked, and the `Arguments` element is updated to reflect each different instantiation argument.</span></span>  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a><span data-ttu-id="84f9e-124">Metody Array.CreateInstance i Type.MakeTypeArray</span><span class="sxs-lookup"><span data-stu-id="84f9e-124">Array.CreateInstance and Type.MakeTypeArray methods</span></span>  
 <span data-ttu-id="84f9e-125">Poniższy przykład wywołuje <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> i <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metod w danym typie `Class1`.</span><span class="sxs-lookup"><span data-stu-id="84f9e-125">The following example calls the <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> methods on a type, `Class1`.</span></span>  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 <span data-ttu-id="84f9e-126">Jeśli ma metadanych tablicy nie powoduje następujący błąd:</span><span class="sxs-lookup"><span data-stu-id="84f9e-126">If no array metadata is present, the following error results:</span></span>  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 <span data-ttu-id="84f9e-127">`Browse` metadane dla typu tablicy jest wymagany do dynamicznego utworzenia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="84f9e-127">`Browse` metadata for the array type is required to dynamically instantiate it.</span></span>  <span data-ttu-id="84f9e-128">Następujące dyrektyw środowiska uruchomieniowego umożliwia dynamiczne wystąpienia `Class1[]`.</span><span class="sxs-lookup"><span data-stu-id="84f9e-128">The following runtime directive allows dynamic instantiation of `Class1[]`.</span></span>  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="84f9e-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84f9e-129">See also</span></span>
- [<span data-ttu-id="84f9e-130">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="84f9e-130">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [<span data-ttu-id="84f9e-131">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="84f9e-131">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
