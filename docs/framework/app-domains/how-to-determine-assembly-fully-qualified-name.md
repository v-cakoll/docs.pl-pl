---
title: "Porady: ustalić zestawu &#39; s w pełni kwalifikowana nazwa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 841bec105f171f3450bfc33ee9052ddb85814a5e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-an-assembly39s-fully-qualified-name"></a><span data-ttu-id="d536f-102">Porady: ustalić zestawu &#39; s w pełni kwalifikowana nazwa</span><span class="sxs-lookup"><span data-stu-id="d536f-102">How to: Determine an Assembly&#39;s Fully Qualified Name</span></span>
<span data-ttu-id="d536f-103">Aby dowiedzieć się, w pełni kwalifikowanej nazwy zestawu w globalnej pamięci podręcznej zestawów, użyj narzędzie globalnej pamięci podręcznej zestawów ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="d536f-103">To discover the fully qualified name of an assembly in the global assembly cache, use the Global Assembly Cache Tool ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)).</span></span> <span data-ttu-id="d536f-104">Zobacz [porady: wyświetlanie zawartości globalnej pamięci podręcznej zestawów](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="d536f-104">See [How to: View the Contents of the Global Assembly Cache](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span></span>  
  
 <span data-ttu-id="d536f-105">Nazwy zestawu w pełni kwalifikowaną dla zestawów, które nie znajdują się w globalnej pamięci podręcznej zestawów, można uzyskać na kilka sposobów: można użyć kodu do danych wyjściowych informacji w konsoli lub do zmiennej lub skorzystać z [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)zbadać metadanych zestawu, który zawiera w pełni kwalifikowana nazwa.</span><span class="sxs-lookup"><span data-stu-id="d536f-105">For assemblies that are not in the global assembly cache, you can get the fully qualified assembly name in a number of ways: can use code to output the information to the console or to a variable, or you can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>  
  
-   <span data-ttu-id="d536f-106">Jeśli zestaw jest już załadowany przez aplikację, możesz pobrać wartość <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> właściwości można uzyskać w pełni kwalifikowanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="d536f-106">If the assembly is already loaded by the application, you can retrieve the value of the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property to get the fully qualified name.</span></span> <span data-ttu-id="d536f-107">Można użyć tej metody, czy zestaw jest w pamięci GAC.</span><span class="sxs-lookup"><span data-stu-id="d536f-107">You can use this approach whether or not the assembly is in the GAC.</span></span> <span data-ttu-id="d536f-108">Przykład stanowi ilustrację.</span><span class="sxs-lookup"><span data-stu-id="d536f-108">The example provides an illustration.</span></span>  
  
-   <span data-ttu-id="d536f-109">Jeśli znasz ścieżki systemu plików zestawu, należy wywołać statycznych (`Shared` w języku Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> metody można pobrać nazwy zestawu w pełni kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="d536f-109">If you know the assembly's file system path, you can call the static (`Shared` in Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method to get the fully qualified assembly name.</span></span> <span data-ttu-id="d536f-110">Poniżej przedstawiono prosty przykład.</span><span class="sxs-lookup"><span data-stu-id="d536f-110">The following is a simple example.</span></span>  
  
     [!code-csharp[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/cs/getassemblyname1.cs#1)]
     [!code-vb[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/vb/getassemblyname1.vb#1)]  
  
-   <span data-ttu-id="d536f-111">Można użyć [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) zbadać metadanych zestawu, który zawiera w pełni kwalifikowana nazwa.</span><span class="sxs-lookup"><span data-stu-id="d536f-111">You can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>  
  
 <span data-ttu-id="d536f-112">Aby uzyskać więcej informacji na temat ustawienia zestawu atrybutów, takich jak wersji, kultury i nazwy zestawu, zobacz [ustawienie atrybutów zestawu](../../../docs/framework/app-domains/set-assembly-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="d536f-112">For more information about setting assembly attributes such as version, culture, and assembly name, see [Setting Assembly Attributes](../../../docs/framework/app-domains/set-assembly-attributes.md).</span></span> <span data-ttu-id="d536f-113">Aby uzyskać więcej informacji na temat nadanie silnej nazwy zestawu, zobacz [tworzenie i zestawy Using Strong-Named](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="d536f-113">For more information about giving an assembly a strong name, see [Creating and Using Strong-Named Assemblies](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d536f-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="d536f-114">Example</span></span>  
 <span data-ttu-id="d536f-115">Poniższy przykładowy kod przedstawia sposób wyświetlania w pełni kwalifikowana nazwa zestawu zawierającego klasę określonej w konsoli.</span><span class="sxs-lookup"><span data-stu-id="d536f-115">The following code example shows how to display the fully qualified name of an assembly containing a specified class to the console.</span></span> <span data-ttu-id="d536f-116">Ponieważ pobiera on nazwę zestawu, który aplikacji został już załadowany, nie ma znaczenia, czy zestaw jest w pamięci GAC.</span><span class="sxs-lookup"><span data-stu-id="d536f-116">Because it retrieves the name of an assembly that the app has already loaded, it does not matter whether the assembly is in the GAC.</span></span>  
  
 [!code-cpp[Assembly.Fullname#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.FullName/CPP/example2.cpp#2)]
 [!code-csharp[Assembly.Fullname#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.FullName/CS/example2.cs#2)]
 [!code-vb[Assembly.Fullname#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.FullName/VB/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d536f-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d536f-117">See Also</span></span>  
 [<span data-ttu-id="d536f-118">Nazwy zestawów</span><span class="sxs-lookup"><span data-stu-id="d536f-118">Assembly Names</span></span>](../../../docs/framework/app-domains/assembly-names.md)  
 [<span data-ttu-id="d536f-119">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="d536f-119">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="d536f-120">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="d536f-120">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [<span data-ttu-id="d536f-121">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="d536f-121">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
 [<span data-ttu-id="d536f-122">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="d536f-122">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="d536f-123">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="d536f-123">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
