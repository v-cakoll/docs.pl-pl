---
title: Odbicie (C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f567eb47d93fcd95e5895b4b44e1c89fb0b901b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="reflection-c"></a><span data-ttu-id="2c349-102">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="2c349-102">Reflection (C#)</span></span>
<span data-ttu-id="2c349-103">Odbicie udostępnia obiekty (typu <xref:System.Type>) opisują zestawy, moduły i typy.</span><span class="sxs-lookup"><span data-stu-id="2c349-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="2c349-104">Odbicie umożliwia dynamicznie utworzyć wystąpienia typu, powiązać danego typu do istniejącego obiektu, lub pobranie typu z istniejącego obiektu i wywołanie metody lub dostępu do swoich pól i właściwości.</span><span class="sxs-lookup"><span data-stu-id="2c349-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="2c349-105">Jeśli używane są atrybuty w kodzie, odbicia umożliwia dostęp do nich.</span><span class="sxs-lookup"><span data-stu-id="2c349-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="2c349-106">Aby uzyskać więcej informacji, zobacz [atrybutów](https://msdn.microsoft.com/library/5x6cd29c).</span><span class="sxs-lookup"><span data-stu-id="2c349-106">For more information, see [Attributes](https://msdn.microsoft.com/library/5x6cd29c).</span></span>  
  
 <span data-ttu-id="2c349-107">Poniżej przedstawiono prosty przykład odbicia przy użyciu metody statycznej `GetType` — dziedziczone przez wszystkie typy z `Object` podstawowa klasa — można uzyskać typu zmienną:</span><span class="sxs-lookup"><span data-stu-id="2c349-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 <span data-ttu-id="2c349-108">Wynik jest:</span><span class="sxs-lookup"><span data-stu-id="2c349-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="2c349-109">W poniższym przykładzie użyto odbicia, aby uzyskać pełną nazwę załadowanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="2c349-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```csharp  
// Using Reflection to get information from an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 <span data-ttu-id="2c349-110">Wynik jest:</span><span class="sxs-lookup"><span data-stu-id="2c349-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
>  <span data-ttu-id="2c349-111">Słowa kluczowe języka C# `protected` i `internal` mają znaczenia w IL i nie są używane w odbicia interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="2c349-111">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="2c349-112">Odpowiednie warunki IL *rodziny* i *zestawu*.</span><span class="sxs-lookup"><span data-stu-id="2c349-112">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="2c349-113">Aby zidentyfikować `internal` za pomocą odbicia, użyj metody <xref:System.Reflection.MethodBase.IsAssembly%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="2c349-113">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="2c349-114">Aby zidentyfikować `protected internal` metody, użyj <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="2c349-114">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>  
  
## <a name="reflection-overview"></a><span data-ttu-id="2c349-115">Odbicie — omówienie</span><span class="sxs-lookup"><span data-stu-id="2c349-115">Reflection Overview</span></span>  
 <span data-ttu-id="2c349-116">Odbicie jest przydatne w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="2c349-116">Reflection is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="2c349-117">Jeśli użytkownik ma dostęp do atrybutów w metadanych programu.</span><span class="sxs-lookup"><span data-stu-id="2c349-117">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="2c349-118">Aby uzyskać więcej informacji, zobacz [pobierania informacji przechowywanych w atrybutach](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="2c349-118">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
-   <span data-ttu-id="2c349-119">Badanie i tworzenie wystąpień typów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="2c349-119">For examining and instantiating types in an assembly.</span></span>  
  
-   <span data-ttu-id="2c349-120">Do tworzenia nowych typów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2c349-120">For building new types at runtime.</span></span> <span data-ttu-id="2c349-121">Korzystanie z klas w <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="2c349-121">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
-   <span data-ttu-id="2c349-122">Do wykonania późne wiązanie podczas uzyskiwania dostępu do metody na typach utworzone w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2c349-122">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="2c349-123">Zobacz temat [dynamiczne ładowanie i przy użyciu typów](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="2c349-123">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2c349-124">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="2c349-124">Related Sections</span></span>  
 <span data-ttu-id="2c349-125">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="2c349-125">For more information:</span></span>  
  
-   [<span data-ttu-id="2c349-126">Odbicie</span><span class="sxs-lookup"><span data-stu-id="2c349-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [<span data-ttu-id="2c349-127">Wyświetlanie informacji o typie</span><span class="sxs-lookup"><span data-stu-id="2c349-127">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [<span data-ttu-id="2c349-128">Odbicie i typy ogólne</span><span class="sxs-lookup"><span data-stu-id="2c349-128">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [<span data-ttu-id="2c349-129">Pobieranie informacji przechowywanych w atrybutach</span><span class="sxs-lookup"><span data-stu-id="2c349-129">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="2c349-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c349-130">See Also</span></span>  
 [<span data-ttu-id="2c349-131">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2c349-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2c349-132">Zestawy w środowisko uruchomieniowe języka wspólnego</span><span class="sxs-lookup"><span data-stu-id="2c349-132">Assemblies in the Common Language Runtime</span></span>](https://msdn.microsoft.com/library/k3677y81)
