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
ms.openlocfilehash: a5651e9dc8cf40e737dd523ec5d29e876a9c0765
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130302"
---
# <a name="accessing-custom-attributes"></a><span data-ttu-id="82fdb-102">Uzyskiwanie dostępu do atrybutów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="82fdb-102">Accessing Custom Attributes</span></span>
<span data-ttu-id="82fdb-103">Po skojarzeniu atrybutów z elementami programu odbicie może służyć do wykonywania zapytań o ich istnienie i wartości.</span><span class="sxs-lookup"><span data-stu-id="82fdb-103">After attributes have been associated with program elements, reflection can be used to query their existence and values.</span></span> <span data-ttu-id="82fdb-104">W .NET Framework w wersji 1,0 i 1,1 atrybuty niestandardowe są badane w kontekście wykonania.</span><span class="sxs-lookup"><span data-stu-id="82fdb-104">In the .NET Framework version 1.0 and 1.1, custom attributes are examined in the execution context.</span></span> <span data-ttu-id="82fdb-105">.NET Framework w wersji 2,0 udostępnia nowy kontekst ładowania, kontekst tylko odbicia, który może służyć do badania kodu, którego nie można załadować do wykonania.</span><span class="sxs-lookup"><span data-stu-id="82fdb-105">The .NET Framework version 2.0 provides a new load context, the reflection-only context, which can be used to examine code that cannot be loaded for execution.</span></span>  
  
## <a name="the-reflection-only-context"></a><span data-ttu-id="82fdb-106">Kontekst tylko odbicie</span><span class="sxs-lookup"><span data-stu-id="82fdb-106">The Reflection-Only Context</span></span>  
 <span data-ttu-id="82fdb-107">Nie można wykonać kodu załadowanego do kontekstu tylko odbicie.</span><span class="sxs-lookup"><span data-stu-id="82fdb-107">Code loaded into the reflection-only context cannot be executed.</span></span> <span data-ttu-id="82fdb-108">Oznacza to, że nie można utworzyć wystąpień atrybutów niestandardowych, ponieważ wymagałoby to wykonania konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="82fdb-108">This means that instances of custom attributes cannot be created, because that would require executing their constructors.</span></span> <span data-ttu-id="82fdb-109">Aby załadować i przejrzeć atrybuty niestandardowe w kontekście tylko odbicia, użyj klasy <xref:System.Reflection.CustomAttributeData>.</span><span class="sxs-lookup"><span data-stu-id="82fdb-109">To load and examine custom attributes in the reflection-only context, use the <xref:System.Reflection.CustomAttributeData> class.</span></span> <span data-ttu-id="82fdb-110">Wystąpienia tej klasy można uzyskać przy użyciu odpowiedniego przeciążenia statycznej metody <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="82fdb-110">You can obtain instances of this class by using the appropriate overload of the static <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="82fdb-111">Zobacz [instrukcje: ładowanie zestawów do kontekstu tylko odbicie](how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="82fdb-111">See [How to: Load Assemblies into the Reflection-Only Context](how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
## <a name="the-execution-context"></a><span data-ttu-id="82fdb-112">Kontekst wykonywania</span><span class="sxs-lookup"><span data-stu-id="82fdb-112">The Execution Context</span></span>  
 <span data-ttu-id="82fdb-113">Główne metody odbicia, aby zbadać atrybuty w kontekście wykonywania, są <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> i <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="82fdb-113">The main reflection methods to query attributes in the execution context are <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> and <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="82fdb-114">Dostępność atrybutu niestandardowego jest sprawdzana w odniesieniu do zestawu, w którym jest dołączony.</span><span class="sxs-lookup"><span data-stu-id="82fdb-114">The accessibility of a custom attribute is checked with respect to the assembly in which it is attached.</span></span> <span data-ttu-id="82fdb-115">Jest to równoznaczne z sprawdzeniem, czy metoda na typie w zestawie, do którego jest dołączony atrybut niestandardowy, może wywołać konstruktora atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="82fdb-115">This is equivalent to checking whether a method on a type in the assembly in which the custom attribute is attached can call the constructor of the custom attribute.</span></span>  
  
 <span data-ttu-id="82fdb-116">Metody takie jak <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> sprawdzają widoczność i dostępność argumentu typu.</span><span class="sxs-lookup"><span data-stu-id="82fdb-116">Methods such as <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> check the visibility and accessibility of the type argument.</span></span> <span data-ttu-id="82fdb-117">Tylko kod w zestawie, który zawiera typ zdefiniowany przez użytkownika, może pobrać atrybut niestandardowy tego typu za pomocą **GetCustomAttributes —** .</span><span class="sxs-lookup"><span data-stu-id="82fdb-117">Only code in the assembly that contains the user-defined type can retrieve a custom attribute of that type using **GetCustomAttributes**.</span></span>  
  
 <span data-ttu-id="82fdb-118">Poniższy C# przykład jest typowym wzorcem projektowania atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="82fdb-118">The following C# example is a typical custom attribute design pattern.</span></span> <span data-ttu-id="82fdb-119">Ilustruje on model odbicia niestandardowego atrybutu środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="82fdb-119">It illustrates the runtime custom attribute reflection model.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="82fdb-120">Jeśli środowisko uruchomieniowe próbuje pobrać atrybuty niestandardowe dla publicznego typu atrybutu niestandardowego <xref:System.ComponentModel.DescriptionAttribute> dołączone do metody **GetLanguage** , wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="82fdb-120">If the runtime is attempting to retrieve the custom attributes for the public custom attribute type <xref:System.ComponentModel.DescriptionAttribute> attached to the **GetLanguage** method, it performs the following actions:</span></span>  
  
1. <span data-ttu-id="82fdb-121">Środowisko uruchomieniowe sprawdza, czy argument typu **DescriptionAttribute** do **typu. GetCustomAttributes —** ( *Typ typu) jest*publiczny i dlatego jest widoczny i dostępny.</span><span class="sxs-lookup"><span data-stu-id="82fdb-121">The runtime checks that the type argument **DescriptionAttribute** to **Type.GetCustomAttributes**(Type *type*) is public, and therefore is visible and accessible.</span></span>  
  
2. <span data-ttu-id="82fdb-122">Środowisko uruchomieniowe sprawdza, czy zdefiniowany przez użytkownika typ **DescriptionAttribute** pochodzący z **DescriptionAttribute** jest widoczny i dostępny w ramach zestawu **System. Web. dll** , gdzie jest dołączony do metody **GetLanguage** ().</span><span class="sxs-lookup"><span data-stu-id="82fdb-122">The runtime checks that the user-defined type **MyDescriptionAttribute** that is derived from **DescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly, where it is attached to the method **GetLanguage**().</span></span>  
  
3. <span data-ttu-id="82fdb-123">Środowisko uruchomieniowe sprawdza, czy Konstruktor elementu **WebDescriptionAttribute** jest widoczny i dostępny w zestawie **System. Web. dll** .</span><span class="sxs-lookup"><span data-stu-id="82fdb-123">The runtime checks that the constructor of **MyDescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly.</span></span>  
  
4. <span data-ttu-id="82fdb-124">Środowisko uruchomieniowe wywołuje konstruktora elementu **WebDescriptionAttribute** z parametrami atrybutu niestandardowego i zwraca nowy obiekt do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="82fdb-124">The runtime calls the constructor of **MyDescriptionAttribute** with the custom attribute parameters and returns the new object to the caller.</span></span>  
  
 <span data-ttu-id="82fdb-125">Model odbicia atrybutów niestandardowych może wyciekować wystąpienia typów zdefiniowanych przez użytkownika poza zestawem, w którym jest zdefiniowany typ.</span><span class="sxs-lookup"><span data-stu-id="82fdb-125">The custom attribute reflection model could leak instances of user-defined types outside the assembly in which the type is defined.</span></span> <span data-ttu-id="82fdb-126">Nie różni się to od elementów członkowskich w bibliotece systemowej środowiska uruchomieniowego, które zwracają wystąpienia typów zdefiniowanych przez użytkownika, takich jak <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> zwracają tablicę obiektów **RuntimeMethodInfo** .</span><span class="sxs-lookup"><span data-stu-id="82fdb-126">This is no different from the members in the runtime system library that return instances of user-defined types, such as <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> returning an array of **RuntimeMethodInfo** objects.</span></span> <span data-ttu-id="82fdb-127">Aby zapobiec odnajdywaniu przez klienta informacji o typie atrybutu niestandardowego zdefiniowanym przez użytkownika, należy zdefiniować członków typu jako niepubliczny.</span><span class="sxs-lookup"><span data-stu-id="82fdb-127">To prevent a client from discovering information about a user-defined custom attribute type, define the type's members to be nonpublic.</span></span>  
  
 <span data-ttu-id="82fdb-128">Poniższy przykład ilustruje podstawowy sposób używania odbicia w celu uzyskania dostępu do atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="82fdb-128">The following example demonstrates the basic way of using reflection to get access to custom attributes.</span></span>  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="82fdb-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82fdb-129">See also</span></span>

- <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [<span data-ttu-id="82fdb-130">Wyświetlanie informacji o typie</span><span class="sxs-lookup"><span data-stu-id="82fdb-130">Viewing Type Information</span></span>](viewing-type-information.md)
- [<span data-ttu-id="82fdb-131">Zagadnienia dotyczące zabezpieczeń dla odbicia</span><span class="sxs-lookup"><span data-stu-id="82fdb-131">Security Considerations for Reflection</span></span>](security-considerations-for-reflection.md)
