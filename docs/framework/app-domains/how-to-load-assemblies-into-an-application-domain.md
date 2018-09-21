---
title: 'Porady: ładowanie zestawów do domeny aplikacji'
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
ms.openlocfilehash: fd6f14f89d143edd03f8b5d028ec84315b2f2e97
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46507577"
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a><span data-ttu-id="9c408-102">Porady: ładowanie zestawów do domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="9c408-102">How to: Load Assemblies into an Application Domain</span></span>
<span data-ttu-id="9c408-103">Istnieje kilka sposobów, aby załadować zestawu do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9c408-103">There are several ways to load an assembly into an application domain.</span></span> <span data-ttu-id="9c408-104">Zalecaną metodą jest użycie `static` (`Shared` w języku Visual Basic) <xref:System.Reflection.Assembly.Load%2A> metody <xref:System.Reflection.Assembly?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="9c408-104">The recommended way is to use the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.Load%2A> method of the <xref:System.Reflection.Assembly?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="9c408-105">Inne sposoby, które zestawy można załadować obejmują:</span><span class="sxs-lookup"><span data-stu-id="9c408-105">Other ways assemblies can be loaded include:</span></span>  
  
-   <span data-ttu-id="9c408-106"><xref:System.Reflection.Assembly.LoadFrom%2A> Metody <xref:System.Reflection.Assembly> klasy ładuje zestaw podanej lokalizacji pliku.</span><span class="sxs-lookup"><span data-stu-id="9c408-106">The <xref:System.Reflection.Assembly.LoadFrom%2A> method of the <xref:System.Reflection.Assembly> class loads an assembly given its file location.</span></span> <span data-ttu-id="9c408-107">Ładowanie zestawów przy użyciu tej metody używa kontekstu różne obciążenia.</span><span class="sxs-lookup"><span data-stu-id="9c408-107">Loading assemblies with this method uses a different load context.</span></span>  
  
-   <span data-ttu-id="9c408-108"><xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> i <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metody ładowania zestawu do kontekstu reflection-only.</span><span class="sxs-lookup"><span data-stu-id="9c408-108">The <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> and <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> methods load an assembly into the reflection-only context.</span></span> <span data-ttu-id="9c408-109">Zestawy ładowane w tym kontekście można zbadać, ale nie jest to wykonywane, dzięki czemu badania zestawów, przeznaczonych dla innych platform.</span><span class="sxs-lookup"><span data-stu-id="9c408-109">Assemblies loaded into this context can be examined but not executed, allowing the examination of assemblies that target other platforms.</span></span> <span data-ttu-id="9c408-110">Zobacz [porady: ładowanie zestawów do kontekstu Reflection-Only](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="9c408-110">See [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c408-111">Kontekstu reflection-only jest nowa w .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="9c408-111">The reflection-only context is new in the .NET Framework version 2.0.</span></span>  
  
-   <span data-ttu-id="9c408-112">Metody takie jak <xref:System.AppDomain.CreateInstance%2A> i <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> z <xref:System.AppDomain> klasy można ładować zestawy do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9c408-112">Methods such as <xref:System.AppDomain.CreateInstance%2A> and <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> of the <xref:System.AppDomain> class can load assemblies into an application domain.</span></span>  
  
-   <span data-ttu-id="9c408-113"><xref:System.Type.GetType%2A> Metody <xref:System.Type> klasy można ładować zestawy.</span><span class="sxs-lookup"><span data-stu-id="9c408-113">The <xref:System.Type.GetType%2A> method of the <xref:System.Type> class can load assemblies.</span></span>  
  
-   <span data-ttu-id="9c408-114"><xref:System.AppDomain.Load%2A> Metody <xref:System.AppDomain?displayProperty=nameWithType> klasy można ładować zestawy, ale jest używany głównie dla współdziałania COM.</span><span class="sxs-lookup"><span data-stu-id="9c408-114">The <xref:System.AppDomain.Load%2A> method of the <xref:System.AppDomain?displayProperty=nameWithType> class can load assemblies, but is primarily used for COM interoperability.</span></span> <span data-ttu-id="9c408-115">Nie można stosować ładować zestawy do domeny aplikacji innej niż ta, z którego jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="9c408-115">It should not be used to load assemblies into an application domain other than the application domain from which it is called.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c408-116">Począwszy od programu .NET Framework w wersji 2.0 środowisko uruchomieniowe nie załaduje zestawu, który został skompilowany przy użyciu wersji programu .NET Framework, który ma wyższy numer wersji niż obecnie załadowanym środowiskiem uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="9c408-116">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="9c408-117">Dotyczy to kombinacja składniki główny i pomocniczy numer wersji.</span><span class="sxs-lookup"><span data-stu-id="9c408-117">This applies to the combination of the major and minor components of the version number.</span></span>  
  
 <span data-ttu-id="9c408-118">Można określić sposób just-in-time (JIT) skompilowany kod z załadowanych zestawów jest współużytkowane między domenami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9c408-118">You can specify the way the just-in-time (JIT) compiled code from loaded assemblies is shared between application domains.</span></span> <span data-ttu-id="9c408-119">Aby uzyskać więcej informacji, zobacz [domeny aplikacji i zestawy](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346).</span><span class="sxs-lookup"><span data-stu-id="9c408-119">For more information, see [Application Domains and Assemblies](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c408-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c408-120">Example</span></span>  
 <span data-ttu-id="9c408-121">Następujące obciążenia kod pobiera zestaw o nazwie "example.exe" lub "example.dll" do bieżącej domeny aplikacji typu o nazwie `Example` z zestawu, pobiera bez parametrów metody o nazwie `MethodA` wpisz i wykonuje metodę.</span><span class="sxs-lookup"><span data-stu-id="9c408-121">The following code loads an assembly named "example.exe" or "example.dll" into the current application domain, gets a type named `Example` from the assembly, gets a parameterless method named `MethodA` for that type, and executes the method.</span></span> <span data-ttu-id="9c408-122">Wyczerpujące omówienie na uzyskiwanie informacji z załadowanego zestawu, zobacz [dynamiczne ładowanie i przy użyciu typów](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="9c408-122">For a complete discussion on obtaining information from a loaded assembly, see [Dynamically Loading and Using Types](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="9c408-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c408-123">See Also</span></span>  
 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>  
 [<span data-ttu-id="9c408-124">Programowanie z domenami aplikacji</span><span class="sxs-lookup"><span data-stu-id="9c408-124">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)  
 [<span data-ttu-id="9c408-125">Odbicie</span><span class="sxs-lookup"><span data-stu-id="9c408-125">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 [<span data-ttu-id="9c408-126">Używanie domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="9c408-126">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)  
 [<span data-ttu-id="9c408-127">Instrukcje: ładowanie zestawów do kontekstu Reflection-Only</span><span class="sxs-lookup"><span data-stu-id="9c408-127">How to: Load Assemblies into the Reflection-Only Context</span></span>](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)  
 [<span data-ttu-id="9c408-128">Domeny aplikacji i zestawy</span><span class="sxs-lookup"><span data-stu-id="9c408-128">Application Domains and Assemblies</span></span>](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)
