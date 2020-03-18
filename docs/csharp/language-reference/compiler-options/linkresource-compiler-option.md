---
title: -linkresource (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /linkresource
helpviewer_keywords:
- /linkresource compiler option [C#]
- linkres compiler option [C#]
- /linkres compiler option [C#]
- -linkres compiler option [C#]
- -linkresource compiler option [C#]
- linkresource compiler option [C#]
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
ms.openlocfilehash: 41af8e0ba8ffebd07d3cb1d2bc5fbc04b8cd595d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173734"
---
# <a name="-linkresource-c-compiler-options"></a><span data-ttu-id="4c7e3-102">-linkresource (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="4c7e3-102">-linkresource (C# Compiler Options)</span></span>
<span data-ttu-id="4c7e3-103">Tworzy łącze do zasobu .NET Framework w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="4c7e3-103">Creates a link to a .NET Framework resource in the output file.</span></span> <span data-ttu-id="4c7e3-104">Plik zasobu nie jest dodawany do pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="4c7e3-104">The resource file is not added to the output file.</span></span> <span data-ttu-id="4c7e3-105">Różni się to od opcji [-resource,](./resource-compiler-option.md) która osadza plik zasobu w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="4c7e3-105">This differs from the [-resource](./resource-compiler-option.md) option which does embed a resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c7e3-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c7e3-106">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4c7e3-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4c7e3-107">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="4c7e3-108">Plik zasobów .NET Framework, do którego chcesz połączyć się z zestawu.</span><span class="sxs-lookup"><span data-stu-id="4c7e3-108">The .NET Framework resource file to which you want to link from the assembly.</span></span>  
  
 <span data-ttu-id="4c7e3-109">`identifier` (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="4c7e3-109">`identifier` (optional)</span></span>  
 <span data-ttu-id="4c7e3-110">Logiczna nazwa zasobu; nazwa, która jest używana do ładowania zasobu.</span><span class="sxs-lookup"><span data-stu-id="4c7e3-110">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="4c7e3-111">Wartością domyślną jest nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="4c7e3-111">The default is the name of the file.</span></span>  
  
 <span data-ttu-id="4c7e3-112">`accessibility-modifier` (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="4c7e3-112">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="4c7e3-113">Dostępność zasobu: publiczna lub prywatna.</span><span class="sxs-lookup"><span data-stu-id="4c7e3-113">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="4c7e3-114">Wartość domyślna jest publiczna.</span><span class="sxs-lookup"><span data-stu-id="4c7e3-114">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c7e3-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4c7e3-115">Remarks</span></span>  
 <span data-ttu-id="4c7e3-116">Domyślnie połączone zasoby są publiczne w zestawie, gdy są tworzone za pomocą kompilatora C#.</span><span class="sxs-lookup"><span data-stu-id="4c7e3-116">By default, linked resources are public in the assembly when they are created with the C# compiler.</span></span> <span data-ttu-id="4c7e3-117">Aby zasoby były `private` prywatne, określ jako modyfikator ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="4c7e3-117">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="4c7e3-118">Żaden inny modyfikator inny niż `public` lub `private` jest dozwolony.</span><span class="sxs-lookup"><span data-stu-id="4c7e3-118">No other modifier other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="4c7e3-119">**-linkresource** wymaga jednej z opcji [-target](./target-compiler-option.md) innych niż **-target:module**.</span><span class="sxs-lookup"><span data-stu-id="4c7e3-119">**-linkresource** requires one of the [-target](./target-compiler-option.md) options other than **-target:module**.</span></span>  
  
 <span data-ttu-id="4c7e3-120">Jeśli `filename` jest plikiem zasobów .NET Framework utworzonym na przykład przez [resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) lub w środowisku <xref:System.Resources> programistycznym, można uzyskać do niego dostęp za pomocą elementów członkowskich w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="4c7e3-120">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="4c7e3-121">Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4c7e3-121">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4c7e3-122">Dla wszystkich innych zasobów `GetManifestResource` należy użyć <xref:System.Reflection.Assembly> metod w klasie, aby uzyskać dostęp do zasobu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4c7e3-122">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="4c7e3-123">Plik określony w `filename` może być dowolny format.</span><span class="sxs-lookup"><span data-stu-id="4c7e3-123">The file specified in `filename` can be any format.</span></span> <span data-ttu-id="4c7e3-124">Na przykład można zrobić natywną część dll zestawu, dzięki czemu można zainstalować w globalnej pamięci podręcznej zestawów i uzyskać dostęp z kodu zarządzanego w zestawie.</span><span class="sxs-lookup"><span data-stu-id="4c7e3-124">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span> <span data-ttu-id="4c7e3-125">Drugi z poniższych przykładów pokazuje, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="4c7e3-125">The second of the following examples shows how to do this.</span></span> <span data-ttu-id="4c7e3-126">To samo można zrobić w konsolidacie zestawu.</span><span class="sxs-lookup"><span data-stu-id="4c7e3-126">You can do the same thing in the Assembly Linker.</span></span> <span data-ttu-id="4c7e3-127">Trzeci z poniższych przykładów pokazuje, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="4c7e3-127">The third of the following examples shows how to do this.</span></span> <span data-ttu-id="4c7e3-128">Aby uzyskać więcej informacji, zobacz [Al.exe (Łączełączenie zestawów)](../../../framework/tools/al-exe-assembly-linker.md) i [praca z zespołami i globalną pamięcią podręczną zestawów](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="4c7e3-128">For more information, see [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) and [Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span></span>  
  
 <span data-ttu-id="4c7e3-129">**-linkres** jest krótką formą **-linkresource**.</span><span class="sxs-lookup"><span data-stu-id="4c7e3-129">**-linkres** is the short form of **-linkresource**.</span></span>  
  
 <span data-ttu-id="4c7e3-130">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można jej zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="4c7e3-130">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c7e3-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="4c7e3-131">Example</span></span>  
 <span data-ttu-id="4c7e3-132">Kompilowanie `in.cs` i tworzenie `rf.resource`łącza do pliku zasobów:</span><span class="sxs-lookup"><span data-stu-id="4c7e3-132">Compile `in.cs` and link to resource file `rf.resource`:</span></span>  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a><span data-ttu-id="4c7e3-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="4c7e3-133">Example</span></span>  
 <span data-ttu-id="4c7e3-134">Skompiluj `A.cs` w dll, łącze do nll macierzystej dll dll i umieścić dane wyjściowe w globalnej pamięci podręcznej zestawów (GAC).</span><span class="sxs-lookup"><span data-stu-id="4c7e3-134">Compile `A.cs` into a DLL, link to a native DLL N.dll, and put the output in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="4c7e3-135">W tym przykładzie zarówno A.dll, jak i N.dll będą dostępne w identyfikatorze GAC.</span><span class="sxs-lookup"><span data-stu-id="4c7e3-135">In this example, both A.dll and N.dll will reside in the GAC.</span></span>  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a><span data-ttu-id="4c7e3-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="4c7e3-136">Example</span></span>  
 <span data-ttu-id="4c7e3-137">W tym przykładzie robi to samo, co poprzedni, ale za pomocą opcji konsolidatora zestawów.</span><span class="sxs-lookup"><span data-stu-id="4c7e3-137">This example does the same thing as the previous one, but by using Assembly Linker options.</span></span>  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll
gacutil -i A.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c7e3-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4c7e3-138">See also</span></span>

- [<span data-ttu-id="4c7e3-139">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="4c7e3-139">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="4c7e3-140">Al.exe (konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="4c7e3-140">Al.exe (Assembly Linker)</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="4c7e3-141">Praca z zestawami i globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="4c7e3-141">Working with Assemblies and the Global Assembly Cache</span></span>](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="4c7e3-142">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="4c7e3-142">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
