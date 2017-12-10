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
ms.openlocfilehash: 68a586fd8a8a8fbe6e351efa3e51c5ba1d2ff4d7
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="reflection-c"></a><span data-ttu-id="a2ddc-102">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="a2ddc-102">Reflection (C#)</span></span>
<span data-ttu-id="a2ddc-103">Odbicie udostępnia obiekty (typu <xref:System.Type>) opisują zestawy, moduły i typy.</span><span class="sxs-lookup"><span data-stu-id="a2ddc-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="a2ddc-104">Odbicie umożliwia dynamicznie utworzyć wystąpienia typu, powiązać danego typu do istniejącego obiektu, lub pobranie typu z istniejącego obiektu i wywołanie metody lub dostępu do swoich pól i właściwości.</span><span class="sxs-lookup"><span data-stu-id="a2ddc-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="a2ddc-105">Jeśli używane są atrybuty w kodzie, odbicia umożliwia dostęp do nich.</span><span class="sxs-lookup"><span data-stu-id="a2ddc-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="a2ddc-106">Aby uzyskać więcej informacji, zobacz [atrybutów](../../../../docs/standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="a2ddc-106">For more information, see [Attributes](../../../../docs/standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="a2ddc-107">Poniżej przedstawiono prosty przykład odbicia przy użyciu metody statycznej `GetType` — dziedziczone przez wszystkie typy z `Object` podstawowa klasa — można uzyskać typu zmienną:</span><span class="sxs-lookup"><span data-stu-id="a2ddc-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 <span data-ttu-id="a2ddc-108">Wynik jest:</span><span class="sxs-lookup"><span data-stu-id="a2ddc-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="a2ddc-109">W poniższym przykładzie użyto odbicia, aby uzyskać pełną nazwę załadowanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="a2ddc-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```csharp  
// Using Reflection to get information from an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 <span data-ttu-id="a2ddc-110">Wynik jest:</span><span class="sxs-lookup"><span data-stu-id="a2ddc-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
>  <span data-ttu-id="a2ddc-111">Słowa kluczowe języka C# `protected` i `internal` mają znaczenia w IL i nie są używane w odbicia interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="a2ddc-111">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="a2ddc-112">Odpowiednie warunki IL *rodziny* i *zestawu*.</span><span class="sxs-lookup"><span data-stu-id="a2ddc-112">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="a2ddc-113">Aby zidentyfikować `internal` za pomocą odbicia, użyj metody <xref:System.Reflection.MethodBase.IsAssembly%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a2ddc-113">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="a2ddc-114">Aby zidentyfikować `protected internal` metody, użyj <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2ddc-114">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>  
  
## <a name="reflection-overview"></a><span data-ttu-id="a2ddc-115">Odbicie — omówienie</span><span class="sxs-lookup"><span data-stu-id="a2ddc-115">Reflection Overview</span></span>  
 <span data-ttu-id="a2ddc-116">Odbicie jest przydatne w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="a2ddc-116">Reflection is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="a2ddc-117">Jeśli użytkownik ma dostęp do atrybutów w metadanych programu.</span><span class="sxs-lookup"><span data-stu-id="a2ddc-117">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="a2ddc-118">Aby uzyskać więcej informacji, zobacz [pobierania informacji przechowywanych w atrybutach](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="a2ddc-118">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
-   <span data-ttu-id="a2ddc-119">Badanie i tworzenie wystąpień typów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="a2ddc-119">For examining and instantiating types in an assembly.</span></span>  
  
-   <span data-ttu-id="a2ddc-120">Do tworzenia nowych typów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a2ddc-120">For building new types at runtime.</span></span> <span data-ttu-id="a2ddc-121">Korzystanie z klas w <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="a2ddc-121">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
-   <span data-ttu-id="a2ddc-122">Do wykonania późne wiązanie podczas uzyskiwania dostępu do metody na typach utworzone w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a2ddc-122">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="a2ddc-123">Zobacz temat [dynamiczne ładowanie i przy użyciu typów](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="a2ddc-123">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a2ddc-124">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="a2ddc-124">Related Sections</span></span>  
 <span data-ttu-id="a2ddc-125">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="a2ddc-125">For more information:</span></span>  
  
-   [<span data-ttu-id="a2ddc-126">Odbicie</span><span class="sxs-lookup"><span data-stu-id="a2ddc-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [<span data-ttu-id="a2ddc-127">Wyświetlanie informacji o typie</span><span class="sxs-lookup"><span data-stu-id="a2ddc-127">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [<span data-ttu-id="a2ddc-128">Odbicie i typy ogólne</span><span class="sxs-lookup"><span data-stu-id="a2ddc-128">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [<span data-ttu-id="a2ddc-129">Pobieranie informacji przechowywanych w atrybutach</span><span class="sxs-lookup"><span data-stu-id="a2ddc-129">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="a2ddc-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2ddc-130">See Also</span></span>  
 [<span data-ttu-id="a2ddc-131">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a2ddc-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a2ddc-132">Zestawy w środowisko uruchomieniowe języka wspólnego</span><span class="sxs-lookup"><span data-stu-id="a2ddc-132">Assemblies in the Common Language Runtime</span></span>](../../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
