---
title: 'Instrukcje: Ładowanie zestawów do domeny aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, loading assemblies
- loading assemblies
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86b66d0a88864188d67aab19de67aaa857a06eaa
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053168"
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a><span data-ttu-id="27445-102">Instrukcje: Ładowanie zestawów do domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="27445-102">How to: Load Assemblies into an Application Domain</span></span>
<span data-ttu-id="27445-103">Istnieje kilka sposobów ładowania zestawu do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="27445-103">There are several ways to load an assembly into an application domain.</span></span> <span data-ttu-id="27445-104">Zalecanym `static` sposobem jest użycie metody (`Shared` w <xref:System.Reflection.Assembly?displayProperty=nameWithType> Visual Basic) <xref:System.Reflection.Assembly.Load%2A> klasy.</span><span class="sxs-lookup"><span data-stu-id="27445-104">The recommended way is to use the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.Load%2A> method of the <xref:System.Reflection.Assembly?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="27445-105">Inne sposoby ładowania zestawów obejmują:</span><span class="sxs-lookup"><span data-stu-id="27445-105">Other ways assemblies can be loaded include:</span></span>  
  
- <span data-ttu-id="27445-106"><xref:System.Reflection.Assembly.LoadFrom%2A> Metoda<xref:System.Reflection.Assembly> klasy ładuje zestaw z uwzględnieniem jego lokalizacji pliku.</span><span class="sxs-lookup"><span data-stu-id="27445-106">The <xref:System.Reflection.Assembly.LoadFrom%2A> method of the <xref:System.Reflection.Assembly> class loads an assembly given its file location.</span></span> <span data-ttu-id="27445-107">Ładowanie zestawów za pomocą tej metody używa innego kontekstu ładowania.</span><span class="sxs-lookup"><span data-stu-id="27445-107">Loading assemblies with this method uses a different load context.</span></span>  
  
- <span data-ttu-id="27445-108">Metody <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> i<xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> ładują zestaw do kontekstu tylko odbicie.</span><span class="sxs-lookup"><span data-stu-id="27445-108">The <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> and <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> methods load an assembly into the reflection-only context.</span></span> <span data-ttu-id="27445-109">Zestawy ładowane do tego kontekstu mogą być badane, ale nie wykonywane, umożliwiając badanie zestawów przeznaczonych dla innych platform.</span><span class="sxs-lookup"><span data-stu-id="27445-109">Assemblies loaded into this context can be examined but not executed, allowing the examination of assemblies that target other platforms.</span></span> <span data-ttu-id="27445-110">Zobacz [How to: Załaduj zestawy do kontekstu](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)tylko odbicie.</span><span class="sxs-lookup"><span data-stu-id="27445-110">See [How to: Load Assemblies into the Reflection-Only Context](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="27445-111">Kontekst tylko odbicia jest nowy w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="27445-111">The reflection-only context is new in the .NET Framework version 2.0.</span></span>  
  
- <span data-ttu-id="27445-112">Metody takie jak <xref:System.AppDomain.CreateInstance%2A> i <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> <xref:System.AppDomain> klasy mogą ładować zestawy do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="27445-112">Methods such as <xref:System.AppDomain.CreateInstance%2A> and <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> of the <xref:System.AppDomain> class can load assemblies into an application domain.</span></span>  
  
- <span data-ttu-id="27445-113"><xref:System.Type.GetType%2A> Metoda<xref:System.Type> klasy może ładować zestawy.</span><span class="sxs-lookup"><span data-stu-id="27445-113">The <xref:System.Type.GetType%2A> method of the <xref:System.Type> class can load assemblies.</span></span>  
  
- <span data-ttu-id="27445-114"><xref:System.AppDomain.Load%2A> Metoda<xref:System.AppDomain?displayProperty=nameWithType> klasy może ładować zestawy, ale jest używana głównie do współdziałania z modelem com.</span><span class="sxs-lookup"><span data-stu-id="27445-114">The <xref:System.AppDomain.Load%2A> method of the <xref:System.AppDomain?displayProperty=nameWithType> class can load assemblies, but is primarily used for COM interoperability.</span></span> <span data-ttu-id="27445-115">Nie należy używać go do ładowania zestawów do domeny aplikacji innej niż domena aplikacji, z której jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="27445-115">It should not be used to load assemblies into an application domain other than the application domain from which it is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="27445-116">Począwszy od .NET Framework w wersji 2,0 środowisko uruchomieniowe nie załaduje zestawu, który został skompilowany przy użyciu wersji .NET Framework, która ma wyższy numer wersji niż aktualnie załadowane środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="27445-116">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="27445-117">Dotyczy to kombinacji głównych i pomocniczych składników numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="27445-117">This applies to the combination of the major and minor components of the version number.</span></span>  
  
 <span data-ttu-id="27445-118">Można określić sposób udostępniania kodu skompilowanego just-in-Time (JIT) z załadowanych zestawów między domenami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="27445-118">You can specify the way the just-in-time (JIT) compiled code from loaded assemblies is shared between application domains.</span></span> <span data-ttu-id="27445-119">Aby uzyskać więcej informacji, zobacz [domeny i zestawy aplikacji](application-domains.md#application-domains-and-assemblies).</span><span class="sxs-lookup"><span data-stu-id="27445-119">For more information, see [Application domains and assemblies](application-domains.md#application-domains-and-assemblies).</span></span>  
  
## <a name="example"></a><span data-ttu-id="27445-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="27445-120">Example</span></span>  
 <span data-ttu-id="27445-121">Poniższy kod ładuje zestaw o nazwie "example. exe" lub "example. dll" do domeny bieżącej aplikacji, pobiera typ nazwany `Example` z zestawu, pobiera metodę bez parametrów o nazwie `MethodA` dla tego typu i wykonuje metodę.</span><span class="sxs-lookup"><span data-stu-id="27445-121">The following code loads an assembly named "example.exe" or "example.dll" into the current application domain, gets a type named `Example` from the assembly, gets a parameterless method named `MethodA` for that type, and executes the method.</span></span> <span data-ttu-id="27445-122">Aby uzyskać pełną dyskusję na temat uzyskiwania informacji z załadowanego zestawu, zobacz [dynamiczne ładowanie i używanie typów](../reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="27445-122">For a complete discussion on obtaining information from a loaded assembly, see [Dynamically Loading and Using Types](../reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="27445-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27445-123">See also</span></span>

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- [<span data-ttu-id="27445-124">Programowanie przy użyciu domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="27445-124">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="27445-125">Odbicie</span><span class="sxs-lookup"><span data-stu-id="27445-125">Reflection</span></span>](../reflection-and-codedom/reflection.md)
- [<span data-ttu-id="27445-126">Używanie domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="27445-126">Using Application Domains</span></span>](use.md)
- [<span data-ttu-id="27445-127">Instrukcje: Ładowanie zestawów do kontekstu tylko odbicie</span><span class="sxs-lookup"><span data-stu-id="27445-127">How to: Load Assemblies into the Reflection-Only Context</span></span>](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)
- [<span data-ttu-id="27445-128">Domeny aplikacji i zestawy</span><span class="sxs-lookup"><span data-stu-id="27445-128">Application domains and assemblies</span></span>](application-domains.md#application-domains-and-assemblies)
