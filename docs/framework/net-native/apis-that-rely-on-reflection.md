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
# <a name="apis-that-rely-on-reflection"></a><span data-ttu-id="79d03-102">Interfejsy API, które działają na podstawie odbicia</span><span class="sxs-lookup"><span data-stu-id="79d03-102">APIs That Rely on Reflection</span></span>
<span data-ttu-id="79d03-103">W niektórych przypadkach użycie odbicia w kodzie nie jest oczywiste, a więc łańcuch narzędzi natywnych platformy .NET nie zachowuje metadanych, które są potrzebne w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="79d03-103">In some cases, the use of reflection in code isn't obvious, and so the .NET Native tool chain doesn't preserve metadata that is needed at run time.</span></span> <span data-ttu-id="79d03-104">W tym temacie opisano niektóre typowe interfejsy API lub typowe wzorce programowania, które nie są uważane za część interfejsu API odbicia, ale które opierają się na odbicie, aby wykonać pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="79d03-104">This topic covers some common APIs or common programming patterns that aren't considered part of the reflection API but that rely on reflection to execute successfully.</span></span> <span data-ttu-id="79d03-105">Jeśli używasz ich w kodzie źródłowym, można dodać informacje o nich do pliku dyrektywy środowiska wykonawczego (.rd.xml), tak aby wywołania tych interfejsów API nie [zgłaszać missingmetadataexception](missingmetadataexception-class-net-native.md) wyjątek lub inny wyjątek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="79d03-105">If you use them in your source code, you can add information about them to the runtime directives (.rd.xml) file so that calls to these APIs do not throw a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception or some other exception at run time.</span></span>  
  
## <a name="typemakegenerictype-method"></a><span data-ttu-id="79d03-106">Typ.MakeGenericType metoda</span><span class="sxs-lookup"><span data-stu-id="79d03-106">Type.MakeGenericType method</span></span>  
 <span data-ttu-id="79d03-107">Można dynamicznie utworzyć wystąpienia typu `AppClass<T>` ogólnego, <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> wywołując metodę przy użyciu kodu w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="79d03-107">You can dynamically instantiate a generic type `AppClass<T>` by calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 <span data-ttu-id="79d03-108">Aby ten kod zakończył się pomyślnie w czasie wykonywania, wymagane jest kilka elementów metadanych.</span><span class="sxs-lookup"><span data-stu-id="79d03-108">For this code to succeed at run time, several items of metadata are required.</span></span> <span data-ttu-id="79d03-109">Pierwszym z `Browse` nich są metadane dla nierozpoznanego typu ogólnego, `AppClass<T>`:</span><span class="sxs-lookup"><span data-stu-id="79d03-109">The first is `Browse` metadata for the uninstantiated generic type, `AppClass<T>`:</span></span>  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="79d03-110">Dzięki temu <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> wywołanie metody zakończy <xref:System.Type> się pomyślnie i zwraca prawidłowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="79d03-110">This allows the <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> method call to succeed and return a valid <xref:System.Type> object.</span></span>  
  
 <span data-ttu-id="79d03-111">Ale nawet po dodaniu metadanych dla nieuznanego <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> typu ogólnego, wywołanie metody zgłasza wyjątek [MissingMetadataException:](missingmetadataexception-class-net-native.md)</span><span class="sxs-lookup"><span data-stu-id="79d03-111">But even when you add metadata for the uninstantiated generic type, calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method throws a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception:</span></span>  
  
<span data-ttu-id="79d03-112">Ta operacja nie może być przeprowadzona jako metadane dla następującego typu został usunięty ze względu na wydajność:</span><span class="sxs-lookup"><span data-stu-id="79d03-112">This operation cannot be carried out as metadata for the following type was removed for performance reasons:</span></span>  
  
<span data-ttu-id="79d03-113">`App1.AppClass`1<System.Int32>'.</span><span class="sxs-lookup"><span data-stu-id="79d03-113">`App1.AppClass`1<System.Int32>\`.</span></span>  
  
 <span data-ttu-id="79d03-114">Do pliku dyrektyw środowiska wykonawczego można dodać następującą dyrektywę w czasie wykonywania, aby dodać `Activate` metadane dla określonego `AppClass<T>` <xref:System.Int32?displayProperty=nameWithType>wystąpienia:</span><span class="sxs-lookup"><span data-stu-id="79d03-114">You can add the following run-time directive to the runtime directives file to add `Activate` metadata for the specific instantiation over `AppClass<T>` of <xref:System.Int32?displayProperty=nameWithType>:</span></span>  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"
                   Activate="Required Public" />  
```  
  
 <span data-ttu-id="79d03-115">Każde wystąpienie nad `AppClass<T>` wymaga oddzielnej dyrektywy, jeśli <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> jest tworzony za pomocą metody i nie jest używany statycznie.</span><span class="sxs-lookup"><span data-stu-id="79d03-115">Each different instantiation over `AppClass<T>` requires a separate directive if it is being created with the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method and not used statically.</span></span>  
  
## <a name="methodinfomakegenericmethod-method"></a><span data-ttu-id="79d03-116">MethodInfo.MakeGenericMetoda metoda</span><span class="sxs-lookup"><span data-stu-id="79d03-116">MethodInfo.MakeGenericMethod method</span></span>  
 <span data-ttu-id="79d03-117">Biorąc pod `Class1` uwagę klasę `GetMethod<T>(T t)` `GetMethod` z metodą rodzajową, można wywołać poprzez odbicie przy użyciu kodu w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="79d03-117">Given a class `Class1` with a generic method `GetMethod<T>(T t)`, `GetMethod` can be invoked through reflection by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 <span data-ttu-id="79d03-118">Aby uruchomić pomyślnie, ten kod wymaga kilku elementów metadanych:</span><span class="sxs-lookup"><span data-stu-id="79d03-118">To run successfully, this code requires several items of metadata:</span></span>  
  
- <span data-ttu-id="79d03-119">`Browse`metadanych dla typu, którego metodę chcesz wywołać.</span><span class="sxs-lookup"><span data-stu-id="79d03-119">`Browse` metadata for the type whose method you want to call.</span></span>  
  
- <span data-ttu-id="79d03-120">`Browse`metadanych dla metody, którą chcesz wywołać.</span><span class="sxs-lookup"><span data-stu-id="79d03-120">`Browse` metadata for the method you want to call.</span></span>  <span data-ttu-id="79d03-121">Jeśli jest to metoda publiczna, dodawanie publicznych `Browse` metadanych dla typu zawierającego zawiera również metodę.</span><span class="sxs-lookup"><span data-stu-id="79d03-121">If it is a public method, adding public `Browse` metadata for the containing type includes the method, too.</span></span>  
  
- <span data-ttu-id="79d03-122">Dynamiczne metadane metody, którą chcesz wywołać, aby delegat wywołania odbicia nie został usunięty przez łańcuch narzędzi natywnych dla platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="79d03-122">Dynamic metadata for the method you want to call, so that the reflection invocation delegate is not removed by the .NET Native tool chain.</span></span> <span data-ttu-id="79d03-123">Jeśli brakuje metadanych dynamicznych dla metody, następujący <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> wyjątek jest zgłaszany, gdy metoda jest wywoływana:</span><span class="sxs-lookup"><span data-stu-id="79d03-123">If dynamic metadata is missing for the method, the following exception is thrown when the <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> method is called:</span></span>  
  
    ```output
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 <span data-ttu-id="79d03-124">Następujące dyrektywy środowiska wykonawczego zapewniają, że wszystkie wymagane metadane są dostępne:</span><span class="sxs-lookup"><span data-stu-id="79d03-124">The following runtime directives ensure that all required metadata is available:</span></span>  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 <span data-ttu-id="79d03-125">Dyrektywa `MethodInstantiation` jest wymagana dla każdego wystąpienia różnych metody, która jest dynamicznie `Arguments` wywoływana, a element jest aktualizowany w celu odzwierciedlenia każdego argumentu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="79d03-125">A `MethodInstantiation` directive is required for each different instantiation of the method that is dynamically invoked, and the `Arguments` element is updated to reflect each different instantiation argument.</span></span>  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a><span data-ttu-id="79d03-126">Metody Array.CreateInstance i Type.MakeTypeArray</span><span class="sxs-lookup"><span data-stu-id="79d03-126">Array.CreateInstance and Type.MakeTypeArray methods</span></span>  
 <span data-ttu-id="79d03-127">W poniższym <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> przykładzie wywołuje <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> i `Class1`metody na typ, .</span><span class="sxs-lookup"><span data-stu-id="79d03-127">The following example calls the <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> methods on a type, `Class1`.</span></span>  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 <span data-ttu-id="79d03-128">Jeśli nie ma metadanych tablicy, wyniki błędu są następujące:</span><span class="sxs-lookup"><span data-stu-id="79d03-128">If no array metadata is present, the following error results:</span></span>  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 <span data-ttu-id="79d03-129">`Browse`metadane dla typu tablicy jest wymagane do dynamicznego wystąpienia go.</span><span class="sxs-lookup"><span data-stu-id="79d03-129">`Browse` metadata for the array type is required to dynamically instantiate it.</span></span>  <span data-ttu-id="79d03-130">Poniższa dyrektywa środowiska wykonawczego umożliwia `Class1[]`dynamiczne tworzenie wystąpienia programu .</span><span class="sxs-lookup"><span data-stu-id="79d03-130">The following runtime directive allows dynamic instantiation of `Class1[]`.</span></span>  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="79d03-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="79d03-131">See also</span></span>

- [<span data-ttu-id="79d03-132">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="79d03-132">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="79d03-133">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="79d03-133">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
