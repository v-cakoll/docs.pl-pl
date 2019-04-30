---
title: 'Instrukcje: Określanie w pełni kwalifikowanej nazwy zestawu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60a4ef1f5bde121d5773925437307b2749aa7282
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674977"
---
# <a name="how-to-determine-an-assemblys-fully-qualified-name"></a><span data-ttu-id="55540-102">Instrukcje: Określanie w pełni kwalifikowanej nazwy zestawu</span><span class="sxs-lookup"><span data-stu-id="55540-102">How to: Determine an Assembly's Fully Qualified Name</span></span>
<span data-ttu-id="55540-103">Aby dowiedzieć się, w pełni kwalifikowana nazwa zestawu w globalnej pamięci podręcznej, użyj Global Assembly Cache Tool ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="55540-103">To discover the fully qualified name of an assembly in the global assembly cache, use the Global Assembly Cache Tool ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)).</span></span> <span data-ttu-id="55540-104">Zobacz [jak: Wyświetlanie zawartości globalnej pamięci podręcznej](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="55540-104">See [How to: View the Contents of the Global Assembly Cache](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span></span>  
  
 <span data-ttu-id="55540-105">Dla zestawów, które nie znajdują się w globalnej pamięci podręcznej, można uzyskać w pełni kwalifikowanej nazwy zestawu na kilka sposobów: można użyć kod służący do wypełniania wyjściowego informacji konsoli lub do zmiennej lub można użyć [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)zbadać metadanych zestawu, który zawiera w pełni kwalifikowana nazwa.</span><span class="sxs-lookup"><span data-stu-id="55540-105">For assemblies that are not in the global assembly cache, you can get the fully qualified assembly name in a number of ways: can use code to output the information to the console or to a variable, or you can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>  
  
- <span data-ttu-id="55540-106">Jeśli zestaw jest już załadowany przez aplikację, możesz pobrać wartość <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> właściwości do pobrania w pełni kwalifikowana nazwa.</span><span class="sxs-lookup"><span data-stu-id="55540-106">If the assembly is already loaded by the application, you can retrieve the value of the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property to get the fully qualified name.</span></span> <span data-ttu-id="55540-107">Czy zestaw znajduje się w pamięci podręcznej GAC, można użyć tej metody.</span><span class="sxs-lookup"><span data-stu-id="55540-107">You can use this approach whether or not the assembly is in the GAC.</span></span> <span data-ttu-id="55540-108">Przykład stanowi ilustrację.</span><span class="sxs-lookup"><span data-stu-id="55540-108">The example provides an illustration.</span></span>  
  
- <span data-ttu-id="55540-109">Jeśli znasz ścieżka systemu plików zestawu, można wywołać statyczną (`Shared` w języku Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> metodę, aby uzyskać w pełni kwalifikowanej nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="55540-109">If you know the assembly's file system path, you can call the static (`Shared` in Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method to get the fully qualified assembly name.</span></span> <span data-ttu-id="55540-110">Poniżej przedstawiono prosty przykład.</span><span class="sxs-lookup"><span data-stu-id="55540-110">The following is a simple example.</span></span>  
  
     [!code-csharp[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/cs/getassemblyname1.cs#1)]
     [!code-vb[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/vb/getassemblyname1.vb#1)]  
  
- <span data-ttu-id="55540-111">Możesz użyć [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) zbadać metadanych zestawu, który zawiera w pełni kwalifikowana nazwa.</span><span class="sxs-lookup"><span data-stu-id="55540-111">You can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>  
  
 <span data-ttu-id="55540-112">Aby uzyskać więcej informacji na temat ustawienia zestawu atrybutów, takich jak wersji, kultury i nazwy zestawu, zobacz [Konfigurowanie atrybutów zestawu](../../../docs/framework/app-domains/set-assembly-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="55540-112">For more information about setting assembly attributes such as version, culture, and assembly name, see [Setting Assembly Attributes](../../../docs/framework/app-domains/set-assembly-attributes.md).</span></span> <span data-ttu-id="55540-113">Aby uzyskać więcej informacji na temat zapewniając zestawu z silną nazwą, zobacz [tworzenie i zestawy Using Strong-Named](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="55540-113">For more information about giving an assembly a strong name, see [Creating and Using Strong-Named Assemblies](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="55540-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="55540-114">Example</span></span>  
 <span data-ttu-id="55540-115">Poniższy przykład kodu pokazuje sposób wyświetlania w pełni kwalifikowana nazwa zestawu zawierającego określonej klasy do konsoli.</span><span class="sxs-lookup"><span data-stu-id="55540-115">The following code example shows how to display the fully qualified name of an assembly containing a specified class to the console.</span></span> <span data-ttu-id="55540-116">Ponieważ pobiera nazwę zestawu, który aplikacji został już załadowany, nie ma znaczenia, czy zestaw znajduje się w pamięci podręcznej GAC.</span><span class="sxs-lookup"><span data-stu-id="55540-116">Because it retrieves the name of an assembly that the app has already loaded, it does not matter whether the assembly is in the GAC.</span></span>  
  
 [!code-cpp[Assembly.Fullname#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.FullName/CPP/example2.cpp#2)]
 [!code-csharp[Assembly.Fullname#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.FullName/CS/example2.cs#2)]
 [!code-vb[Assembly.Fullname#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.FullName/VB/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="55540-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55540-117">See also</span></span>

- [<span data-ttu-id="55540-118">Nazwy zestawów</span><span class="sxs-lookup"><span data-stu-id="55540-118">Assembly Names</span></span>](../../../docs/framework/app-domains/assembly-names.md)
- [<span data-ttu-id="55540-119">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="55540-119">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)
- [<span data-ttu-id="55540-120">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="55540-120">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [<span data-ttu-id="55540-121">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="55540-121">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)
- [<span data-ttu-id="55540-122">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="55540-122">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="55540-123">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="55540-123">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
