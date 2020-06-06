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
# <a name="apis-that-rely-on-reflection"></a><span data-ttu-id="5339f-102">Interfejsy API, które działają na podstawie odbicia</span><span class="sxs-lookup"><span data-stu-id="5339f-102">APIs That Rely on Reflection</span></span>
<span data-ttu-id="5339f-103">W niektórych przypadkach użycie odbicia w kodzie nie jest oczywiste i dlatego łańcuch narzędzi .NET Native nie zachowuje metadanych wymaganych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5339f-103">In some cases, the use of reflection in code isn't obvious, and so the .NET Native tool chain doesn't preserve metadata that is needed at run time.</span></span> <span data-ttu-id="5339f-104">W tym temacie opisano niektóre typowe interfejsy API lub typowe wzorce programowania, które nie są uważane za część interfejsu API odbicia, ale które polegają na pomyślnym wykonaniu odbicia.</span><span class="sxs-lookup"><span data-stu-id="5339f-104">This topic covers some common APIs or common programming patterns that aren't considered part of the reflection API but that rely on reflection to execute successfully.</span></span> <span data-ttu-id="5339f-105">Jeśli używasz ich w kodzie źródłowym, możesz dodać informacje o nich do pliku dyrektywy środowiska uruchomieniowego (. Rd. xml), tak aby wywołania tych interfejsów API nie zgłaszają wyjątku [MissingMetadataException](missingmetadataexception-class-net-native.md) ani innego wyjątku w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5339f-105">If you use them in your source code, you can add information about them to the runtime directives (.rd.xml) file so that calls to these APIs do not throw a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception or some other exception at run time.</span></span>  
  
## <a name="typemakegenerictype-method"></a><span data-ttu-id="5339f-106">Type. MakeGenericType, Metoda</span><span class="sxs-lookup"><span data-stu-id="5339f-106">Type.MakeGenericType method</span></span>  
 <span data-ttu-id="5339f-107">Można dynamicznie utworzyć wystąpienie typu ogólnego `AppClass<T>` , wywołując <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metodę przy użyciu kodu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5339f-107">You can dynamically instantiate a generic type `AppClass<T>` by calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 <span data-ttu-id="5339f-108">Aby ten kod zakończył się pomyślnie w czasie wykonywania, wymagane są kilka elementów metadanych.</span><span class="sxs-lookup"><span data-stu-id="5339f-108">For this code to succeed at run time, several items of metadata are required.</span></span> <span data-ttu-id="5339f-109">Pierwszy to `Browse` metadane dla niewystąpienia typu ogólnego, `AppClass<T>` :</span><span class="sxs-lookup"><span data-stu-id="5339f-109">The first is `Browse` metadata for the uninstantiated generic type, `AppClass<T>`:</span></span>  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="5339f-110">Dzięki temu <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> wywołanie metody powiodło się i zwróci prawidłowy <xref:System.Type> obiekt.</span><span class="sxs-lookup"><span data-stu-id="5339f-110">This allows the <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> method call to succeed and return a valid <xref:System.Type> object.</span></span>  
  
 <span data-ttu-id="5339f-111">Jednak nawet w przypadku dodania metadanych dla typu ogólnego bez wystąpienia, wywołanie <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metody zgłasza wyjątek [MissingMetadataException](missingmetadataexception-class-net-native.md) :</span><span class="sxs-lookup"><span data-stu-id="5339f-111">But even when you add metadata for the uninstantiated generic type, calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method throws a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception:</span></span>  
  
<span data-ttu-id="5339f-112">Nie można wykonać tej operacji, ponieważ metadane następującego typu zostały usunięte ze względu na wydajność:</span><span class="sxs-lookup"><span data-stu-id="5339f-112">This operation cannot be carried out as metadata for the following type was removed for performance reasons:</span></span>  
  
<span data-ttu-id="5339f-113">`App1.AppClass`1<system. Int32>".</span><span class="sxs-lookup"><span data-stu-id="5339f-113">`App1.AppClass`1<System.Int32>\`.</span></span>  
  
 <span data-ttu-id="5339f-114">Można dodać następującą dyrektywę uruchomieniową do pliku dyrektywy środowiska uruchomieniowego, aby dodać `Activate` metadane dla konkretnego wystąpienia `AppClass<T>` z <xref:System.Int32?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="5339f-114">You can add the following run-time directive to the runtime directives file to add `Activate` metadata for the specific instantiation over `AppClass<T>` of <xref:System.Int32?displayProperty=nameWithType>:</span></span>  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"
                   Activate="Required Public" />  
```  
  
 <span data-ttu-id="5339f-115">Każde różne wystąpienie `AppClass<T>` tego typu wymaga oddzielnej dyrektywy, jeśli jest tworzona przy użyciu <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metody i nie jest używana statycznie.</span><span class="sxs-lookup"><span data-stu-id="5339f-115">Each different instantiation over `AppClass<T>` requires a separate directive if it is being created with the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method and not used statically.</span></span>  
  
## <a name="methodinfomakegenericmethod-method"></a><span data-ttu-id="5339f-116">MethodInfo. MakeGenericMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="5339f-116">MethodInfo.MakeGenericMethod method</span></span>  
 <span data-ttu-id="5339f-117">Dana Klasa `Class1` z metodą generyczną `GetMethod<T>(T t)` `GetMethod` może być wywoływana poprzez odbicie przy użyciu kodu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5339f-117">Given a class `Class1` with a generic method `GetMethod<T>(T t)`, `GetMethod` can be invoked through reflection by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 <span data-ttu-id="5339f-118">Aby pomyślnie uruchomić, ten kod wymaga kilku elementów metadanych:</span><span class="sxs-lookup"><span data-stu-id="5339f-118">To run successfully, this code requires several items of metadata:</span></span>  
  
- <span data-ttu-id="5339f-119">`Browse`metadane dla typu, którego Metoda ma zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="5339f-119">`Browse` metadata for the type whose method you want to call.</span></span>  
  
- <span data-ttu-id="5339f-120">`Browse`metadane dla metody, która ma zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="5339f-120">`Browse` metadata for the method you want to call.</span></span>  <span data-ttu-id="5339f-121">Jeśli jest to metoda publiczna, Dodawanie publicznych `Browse` metadanych dla typu zawierającego zawiera również metodę.</span><span class="sxs-lookup"><span data-stu-id="5339f-121">If it is a public method, adding public `Browse` metadata for the containing type includes the method, too.</span></span>  
  
- <span data-ttu-id="5339f-122">Dynamiczne metadane dla metody, która ma zostać wywołana, tak aby delegat wywołania odbicia nie został usunięty przez łańcuch narzędzi .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5339f-122">Dynamic metadata for the method you want to call, so that the reflection invocation delegate is not removed by the .NET Native tool chain.</span></span> <span data-ttu-id="5339f-123">Jeśli brakuje metadanych dynamicznych dla metody, następujący wyjątek jest zgłaszany, gdy wywoływana jest <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> Metoda:</span><span class="sxs-lookup"><span data-stu-id="5339f-123">If dynamic metadata is missing for the method, the following exception is thrown when the <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> method is called:</span></span>  
  
    ```output
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 <span data-ttu-id="5339f-124">Następujące dyrektywy środowiska uruchomieniowego zapewniają dostępność wszystkich wymaganych metadanych:</span><span class="sxs-lookup"><span data-stu-id="5339f-124">The following runtime directives ensure that all required metadata is available:</span></span>  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 <span data-ttu-id="5339f-125">`MethodInstantiation`Dyrektywa jest wymagana dla każdego innego wystąpienia metody, która jest wywoływana dynamicznie, i `Arguments` jest aktualizowana w celu odzwierciedlenia każdego innego argumentu tworzenia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5339f-125">A `MethodInstantiation` directive is required for each different instantiation of the method that is dynamically invoked, and the `Arguments` element is updated to reflect each different instantiation argument.</span></span>  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a><span data-ttu-id="5339f-126">Array. CreateInstance i Type. MakeTypeArray, metody</span><span class="sxs-lookup"><span data-stu-id="5339f-126">Array.CreateInstance and Type.MakeTypeArray methods</span></span>  
 <span data-ttu-id="5339f-127">Poniższy przykład wywołuje <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metody i dla typu, `Class1` .</span><span class="sxs-lookup"><span data-stu-id="5339f-127">The following example calls the <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> methods on a type, `Class1`.</span></span>  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 <span data-ttu-id="5339f-128">Jeśli nie ma metadanych tablicy, następujące wyniki błędu:</span><span class="sxs-lookup"><span data-stu-id="5339f-128">If no array metadata is present, the following error results:</span></span>  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 <span data-ttu-id="5339f-129">`Browse`metadane dla typu tablicy są wymagane do dynamicznego tworzenia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5339f-129">`Browse` metadata for the array type is required to dynamically instantiate it.</span></span>  <span data-ttu-id="5339f-130">Następująca dyrektywa środowiska uruchomieniowego umożliwia dynamiczne tworzenie wystąpień `Class1[]` .</span><span class="sxs-lookup"><span data-stu-id="5339f-130">The following runtime directive allows dynamic instantiation of `Class1[]`.</span></span>  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="5339f-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5339f-131">See also</span></span>

- [<span data-ttu-id="5339f-132">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="5339f-132">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="5339f-133">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="5339f-133">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
