---
title: 'Instrukcje: Ładowanie zestawów do domeny aplikacji'
description: Dowiedz się, jak ładować zestawy do domeny aplikacji w programie .NET. Zalecanym sposobem jest użycie metody ładowania static (lub Shared) w System. odbicie. Assembly.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, loading assemblies
- loading assemblies
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
ms.openlocfilehash: c91c70625b79002e9297755dfdfac8aa6e283208
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104756"
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a><span data-ttu-id="41b4b-104">Instrukcje: Ładowanie zestawów do domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="41b4b-104">How to: Load Assemblies into an Application Domain</span></span>
<span data-ttu-id="41b4b-105">Istnieje kilka sposobów ładowania zestawu do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41b4b-105">There are several ways to load an assembly into an application domain.</span></span> <span data-ttu-id="41b4b-106">Zalecanym sposobem jest użycie `static` `Shared` metody (w Visual Basic) <xref:System.Reflection.Assembly.Load%2A> <xref:System.Reflection.Assembly?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="41b4b-106">The recommended way is to use the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.Load%2A> method of the <xref:System.Reflection.Assembly?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="41b4b-107">Inne sposoby ładowania zestawów obejmują:</span><span class="sxs-lookup"><span data-stu-id="41b4b-107">Other ways assemblies can be loaded include:</span></span>  
  
- <span data-ttu-id="41b4b-108"><xref:System.Reflection.Assembly.LoadFrom%2A>Metoda <xref:System.Reflection.Assembly> klasy ładuje zestaw z uwzględnieniem jego lokalizacji pliku.</span><span class="sxs-lookup"><span data-stu-id="41b4b-108">The <xref:System.Reflection.Assembly.LoadFrom%2A> method of the <xref:System.Reflection.Assembly> class loads an assembly given its file location.</span></span> <span data-ttu-id="41b4b-109">Ładowanie zestawów za pomocą tej metody używa innego kontekstu ładowania.</span><span class="sxs-lookup"><span data-stu-id="41b4b-109">Loading assemblies with this method uses a different load context.</span></span>  
  
- <span data-ttu-id="41b4b-110"><xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>Metody i <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> ładują zestaw do kontekstu tylko odbicie.</span><span class="sxs-lookup"><span data-stu-id="41b4b-110">The <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> and <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> methods load an assembly into the reflection-only context.</span></span> <span data-ttu-id="41b4b-111">Zestawy ładowane do tego kontekstu mogą być badane, ale nie wykonywane, umożliwiając badanie zestawów przeznaczonych dla innych platform.</span><span class="sxs-lookup"><span data-stu-id="41b4b-111">Assemblies loaded into this context can be examined but not executed, allowing the examination of assemblies that target other platforms.</span></span> <span data-ttu-id="41b4b-112">Zobacz [instrukcje: ładowanie zestawów do kontekstu tylko odbicie](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="41b4b-112">See [How to: Load Assemblies into the Reflection-Only Context](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="41b4b-113">Kontekst tylko odbicia jest nowy w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="41b4b-113">The reflection-only context is new in the .NET Framework version 2.0.</span></span>  
  
- <span data-ttu-id="41b4b-114">Metody takie jak <xref:System.AppDomain.CreateInstance%2A> i <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> <xref:System.AppDomain> klasy mogą ładować zestawy do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41b4b-114">Methods such as <xref:System.AppDomain.CreateInstance%2A> and <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> of the <xref:System.AppDomain> class can load assemblies into an application domain.</span></span>  
  
- <span data-ttu-id="41b4b-115"><xref:System.Type.GetType%2A>Metoda <xref:System.Type> klasy może ładować zestawy.</span><span class="sxs-lookup"><span data-stu-id="41b4b-115">The <xref:System.Type.GetType%2A> method of the <xref:System.Type> class can load assemblies.</span></span>  
  
- <span data-ttu-id="41b4b-116"><xref:System.AppDomain.Load%2A>Metoda <xref:System.AppDomain?displayProperty=nameWithType> klasy może ładować zestawy, ale jest używana głównie do współdziałania z modelem com.</span><span class="sxs-lookup"><span data-stu-id="41b4b-116">The <xref:System.AppDomain.Load%2A> method of the <xref:System.AppDomain?displayProperty=nameWithType> class can load assemblies, but is primarily used for COM interoperability.</span></span> <span data-ttu-id="41b4b-117">Nie należy używać go do ładowania zestawów do domeny aplikacji innej niż domena aplikacji, z której jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="41b4b-117">It should not be used to load assemblies into an application domain other than the application domain from which it is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="41b4b-118">Począwszy od .NET Framework w wersji 2,0 środowisko uruchomieniowe nie załaduje zestawu, który został skompilowany przy użyciu wersji .NET Framework, która ma wyższy numer wersji niż aktualnie załadowane środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="41b4b-118">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="41b4b-119">Dotyczy to kombinacji głównych i pomocniczych składników numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="41b4b-119">This applies to the combination of the major and minor components of the version number.</span></span>  
  
 <span data-ttu-id="41b4b-120">Można określić sposób udostępniania kodu skompilowanego just-in-Time (JIT) z załadowanych zestawów między domenami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41b4b-120">You can specify the way the just-in-time (JIT) compiled code from loaded assemblies is shared between application domains.</span></span> <span data-ttu-id="41b4b-121">Aby uzyskać więcej informacji, zobacz [domeny i zestawy aplikacji](application-domains.md#application-domains-and-assemblies).</span><span class="sxs-lookup"><span data-stu-id="41b4b-121">For more information, see [Application domains and assemblies](application-domains.md#application-domains-and-assemblies).</span></span>  
  
## <a name="example"></a><span data-ttu-id="41b4b-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="41b4b-122">Example</span></span>  
 <span data-ttu-id="41b4b-123">Poniższy kod ładuje zestaw o nazwie "example.exe" lub "example.dll" do domeny bieżącej aplikacji, pobiera typ o nazwie `Example` z zestawu, pobiera metodę bez parametrów o nazwie `MethodA` dla tego typu i wykonuje metodę.</span><span class="sxs-lookup"><span data-stu-id="41b4b-123">The following code loads an assembly named "example.exe" or "example.dll" into the current application domain, gets a type named `Example` from the assembly, gets a parameterless method named `MethodA` for that type, and executes the method.</span></span> <span data-ttu-id="41b4b-124">Aby uzyskać pełną dyskusję na temat uzyskiwania informacji z załadowanego zestawu, zobacz [dynamiczne ładowanie i używanie typów](../reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="41b4b-124">For a complete discussion on obtaining information from a loaded assembly, see [Dynamically Loading and Using Types](../reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="41b4b-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41b4b-125">See also</span></span>

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- [<span data-ttu-id="41b4b-126">Programowanie przy użyciu domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="41b4b-126">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="41b4b-127">Odbicie</span><span class="sxs-lookup"><span data-stu-id="41b4b-127">Reflection</span></span>](../reflection-and-codedom/reflection.md)
- [<span data-ttu-id="41b4b-128">Używanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="41b4b-128">Using Application Domains</span></span>](use.md)
- [<span data-ttu-id="41b4b-129">Instrukcje: Ładowanie zestawów do kontekstu Reflection-Only</span><span class="sxs-lookup"><span data-stu-id="41b4b-129">How to: Load Assemblies into the Reflection-Only Context</span></span>](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)
- [<span data-ttu-id="41b4b-130">Domeny aplikacji i zestawy</span><span class="sxs-lookup"><span data-stu-id="41b4b-130">Application domains and assemblies</span></span>](application-domains.md#application-domains-and-assemblies)
