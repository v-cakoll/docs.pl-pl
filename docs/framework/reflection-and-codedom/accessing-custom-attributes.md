---
title: Uzyskiwanie dostępu do atrybutów niestandardowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- custom attributes, accessibility
- attributes [.NET Framework], accessing
- reflection, custom attributes
ms.assetid: 1d8e3398-00d8-47d5-a084-214f9859d3d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8aafd1586068dcd7aaf4a72ef5454e3a2698ccd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="accessing-custom-attributes"></a><span data-ttu-id="f8d4f-102">Uzyskiwanie dostępu do atrybutów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="f8d4f-102">Accessing Custom Attributes</span></span>
<span data-ttu-id="f8d4f-103">Po atrybuty zostały skojarzone z elementów programu, odbicia może służyć do badania ich istnienie i wartości.</span><span class="sxs-lookup"><span data-stu-id="f8d4f-103">After attributes have been associated with program elements, reflection can be used to query their existence and values.</span></span> <span data-ttu-id="f8d4f-104">W programie .NET Framework w wersji 1.0, 1.1 atrybuty niestandardowe są sprawdzane w kontekstu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f8d4f-104">In the .NET Framework version 1.0 and 1.1, custom attributes are examined in the execution context.</span></span> <span data-ttu-id="f8d4f-105">.NET Framework w wersji 2.0 zapewnia nowy kontekst ładowania kontekstu reflection-only, którego można użyć do sprawdzenia kod, który nie może zostać załadowany do wykonania.</span><span class="sxs-lookup"><span data-stu-id="f8d4f-105">The .NET Framework version 2.0 provides a new load context, the reflection-only context, which can be used to examine code that cannot be loaded for execution.</span></span>  
  
## <a name="the-reflection-only-context"></a><span data-ttu-id="f8d4f-106">Kontekstu Reflection-Only</span><span class="sxs-lookup"><span data-stu-id="f8d4f-106">The Reflection-Only Context</span></span>  
 <span data-ttu-id="f8d4f-107">Nie można wykonać kod ładowane do kontekstu reflection-only.</span><span class="sxs-lookup"><span data-stu-id="f8d4f-107">Code loaded into the reflection-only context cannot be executed.</span></span> <span data-ttu-id="f8d4f-108">Oznacza to, że nie można tworzyć wystąpień atrybutów niestandardowych, ponieważ który wymaga wykonywania ich konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="f8d4f-108">This means that instances of custom attributes cannot be created, because that would require executing their constructors.</span></span> <span data-ttu-id="f8d4f-109">Aby załadować i sprawdź, czy atrybuty niestandardowe w kontekstu reflection-only, użyj <xref:System.Reflection.CustomAttributeData> klasy.</span><span class="sxs-lookup"><span data-stu-id="f8d4f-109">To load and examine custom attributes in the reflection-only context, use the <xref:System.Reflection.CustomAttributeData> class.</span></span> <span data-ttu-id="f8d4f-110">Wystąpienia tej klasy można uzyskać za pomocą odpowiedniego przeciążenia statycznych <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="f8d4f-110">You can obtain instances of this class by using the appropriate overload of the static <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f8d4f-111">Zobacz [porady: ładowanie zestawów do kontekstu Reflection-Only](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="f8d4f-111">See [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
## <a name="the-execution-context"></a><span data-ttu-id="f8d4f-112">Kontekst wykonywania</span><span class="sxs-lookup"><span data-stu-id="f8d4f-112">The Execution Context</span></span>  
 <span data-ttu-id="f8d4f-113">Metody main odbicia atrybutów kontekstu wykonywania zapytania są <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> i <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f8d4f-113">The main reflection methods to query attributes in the execution context are <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> and <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="f8d4f-114">Dostępność atrybut niestandardowy jest sprawdzana względem zestawu, w której jest dołączony.</span><span class="sxs-lookup"><span data-stu-id="f8d4f-114">The accessibility of a custom attribute is checked with respect to the assembly in which it is attached.</span></span> <span data-ttu-id="f8d4f-115">Jest to równoważne sprawdzanie, czy metody dla typu w zestawie, w której jest dołączona atrybutu niestandardowego można wywołać konstruktora atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="f8d4f-115">This is equivalent to checking whether a method on a type in the assembly in which the custom attribute is attached can call the constructor of the custom attribute.</span></span>  
  
 <span data-ttu-id="f8d4f-116">Metody, takie jak <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> Sprawdź widoczność i dostępności argumentu typu.</span><span class="sxs-lookup"><span data-stu-id="f8d4f-116">Methods such as <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> check the visibility and accessibility of the type argument.</span></span> <span data-ttu-id="f8d4f-117">Tylko kod w zestawie, którą zawiera typ zdefiniowany przez użytkownika można pobrać atrybutu niestandardowego o tego typu za pomocą **GetCustomAttributes**.</span><span class="sxs-lookup"><span data-stu-id="f8d4f-117">Only code in the assembly that contains the user-defined type can retrieve a custom attribute of that type using **GetCustomAttributes**.</span></span>  
  
 <span data-ttu-id="f8d4f-118">W poniższym przykładzie C# to wzorzec projektowania typowe atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="f8d4f-118">The following C# example is a typical custom attribute design pattern.</span></span> <span data-ttu-id="f8d4f-119">Zastosowano modelu odbicia atrybutu niestandardowego środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="f8d4f-119">It illustrates the runtime custom attribute reflection model.</span></span>  
  
```  
System.DLL  
public class DescriptionAttribute : Attribute  
{  
}  
  
System.Web.DLL  
internal class MyDescriptionAttribute : DescriptionAttribute  
{  
}  
  
public class LocalizationExtenderProvider  
{  
    [MyDescriptionAttribute(...)]  
    public CultureInfo GetLanguage(...)  
    {  
    }  
}  
```  
  
 <span data-ttu-id="f8d4f-120">Jeśli środowisko wykonawcze próbuje pobrać atrybutów niestandardowych dla typu atrybutu niestandardowego publicznego <xref:System.ComponentModel.DescriptionAttribute> dołączony do **GetLanguage** metoda wykonuje następujące akcje:</span><span class="sxs-lookup"><span data-stu-id="f8d4f-120">If the runtime is attempting to retrieve the custom attributes for the public custom attribute type <xref:System.ComponentModel.DescriptionAttribute> attached to the **GetLanguage** method, it performs the following actions:</span></span>  
  
1.  <span data-ttu-id="f8d4f-121">Środowisko uruchomieniowe sprawdza, czy argument typu **DescriptionAttribute** do **Type.GetCustomAttributes**(typ *typu*) nie jest publiczny i dlatego jest widoczny i jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="f8d4f-121">The runtime checks that the type argument **DescriptionAttribute** to **Type.GetCustomAttributes**(Type *type*) is public, and therefore is visible and accessible.</span></span>  
  
2.  <span data-ttu-id="f8d4f-122">Środowisko uruchomieniowe sprawdza, czy typ zdefiniowany przez użytkownika **MyDescriptionAttribute** która jest pochodną **DescriptionAttribute** jest widoczny i jest dostępny w ramach **System.Web.DLL**zestawu, w której jest podłączony do metody **GetLanguage**().</span><span class="sxs-lookup"><span data-stu-id="f8d4f-122">The runtime checks that the user-defined type **MyDescriptionAttribute** that is derived from **DescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly, where it is attached to the method **GetLanguage**().</span></span>  
  
3.  <span data-ttu-id="f8d4f-123">Środowisko uruchomieniowe sprawdza, czy konstruktora **MyDescriptionAttribute** jest widoczny i jest dostępny w ramach **System.Web.DLL** zestawu.</span><span class="sxs-lookup"><span data-stu-id="f8d4f-123">The runtime checks that the constructor of **MyDescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly.</span></span>  
  
4.  <span data-ttu-id="f8d4f-124">Środowisko uruchomieniowe wywołania konstruktora **MyDescriptionAttribute** z parametrami atrybutu niestandardowego i zwraca nowy obiekt do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f8d4f-124">The runtime calls the constructor of **MyDescriptionAttribute** with the custom attribute parameters and returns the new object to the caller.</span></span>  
  
 <span data-ttu-id="f8d4f-125">Atrybut niestandardowy model odbicia można wyciek wystąpień typów zdefiniowanych przez użytkownika spoza zestawu, w którym jest zdefiniowany typ.</span><span class="sxs-lookup"><span data-stu-id="f8d4f-125">The custom attribute reflection model could leak instances of user-defined types outside the assembly in which the type is defined.</span></span> <span data-ttu-id="f8d4f-126">To nie różni się od elementów członkowskich w Biblioteka środowiska uruchomieniowego systemu, które zwracają wystąpień typów zdefiniowanych przez użytkownika, takie jak <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> tablicę **RuntimeMethodInfo** obiektów.</span><span class="sxs-lookup"><span data-stu-id="f8d4f-126">This is no different from the members in the runtime system library that return instances of user-defined types, such as <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> returning an array of **RuntimeMethodInfo** objects.</span></span> <span data-ttu-id="f8d4f-127">Aby zapobiec klienta z odnajdowania informacji o typie atrybutów niestandardowych zdefiniowanych przez użytkownika, należy zdefiniować elementów członkowskich typu jako niepubliczny.</span><span class="sxs-lookup"><span data-stu-id="f8d4f-127">To prevent a client from discovering information about a user-defined custom attribute type, define the type's members to be nonpublic.</span></span>  
  
 <span data-ttu-id="f8d4f-128">W poniższym przykładzie pokazano podstawową metodą do uzyskania dostępu do atrybutów niestandardowych za pomocą odbicia.</span><span class="sxs-lookup"><span data-stu-id="f8d4f-128">The following example demonstrates the basic way of using reflection to get access to custom attributes.</span></span>  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f8d4f-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8d4f-129">See Also</span></span>  
 <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="f8d4f-130">Wyświetlanie informacji o typie</span><span class="sxs-lookup"><span data-stu-id="f8d4f-130">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)  
 [<span data-ttu-id="f8d4f-131">Zagadnienia dotyczące zabezpieczeń dla odbicia</span><span class="sxs-lookup"><span data-stu-id="f8d4f-131">Security Considerations for Reflection</span></span>](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)
