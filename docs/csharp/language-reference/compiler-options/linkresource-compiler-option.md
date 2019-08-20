---
title: -linkresource — (C# opcje kompilatora)
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
ms.openlocfilehash: 454915454f3faf15933257f3e3e221afec51d0ee
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606752"
---
# <a name="-linkresource-c-compiler-options"></a><span data-ttu-id="74c26-102">-linkresource — (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="74c26-102">-linkresource (C# Compiler Options)</span></span>
<span data-ttu-id="74c26-103">Tworzy łącze do zasobu .NET Framework w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="74c26-103">Creates a link to a .NET Framework resource in the output file.</span></span> <span data-ttu-id="74c26-104">Plik zasobów nie został dodany do pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="74c26-104">The resource file is not added to the output file.</span></span> <span data-ttu-id="74c26-105">Różni się to od opcji [-Resource](./resource-compiler-option.md) , która osadza plik zasobów w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="74c26-105">This differs from the [-resource](./resource-compiler-option.md) option which does embed a resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74c26-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="74c26-106">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="74c26-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="74c26-107">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="74c26-108">Plik zasobów .NET Framework, do którego chcesz utworzyć łącze z zestawu.</span><span class="sxs-lookup"><span data-stu-id="74c26-108">The .NET Framework resource file to which you want to link from the assembly.</span></span>  
  
 <span data-ttu-id="74c26-109">`identifier`obowiązkowe</span><span class="sxs-lookup"><span data-stu-id="74c26-109">`identifier` (optional)</span></span>  
 <span data-ttu-id="74c26-110">Nazwa logiczna zasobu; Nazwa, która jest używana do ładowania zasobu.</span><span class="sxs-lookup"><span data-stu-id="74c26-110">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="74c26-111">Wartość domyślna to nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="74c26-111">The default is the name of the file.</span></span>  
  
 <span data-ttu-id="74c26-112">`accessibility-modifier`obowiązkowe</span><span class="sxs-lookup"><span data-stu-id="74c26-112">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="74c26-113">Dostępność zasobu: Public lub Private.</span><span class="sxs-lookup"><span data-stu-id="74c26-113">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="74c26-114">Wartość domyślna to Public.</span><span class="sxs-lookup"><span data-stu-id="74c26-114">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74c26-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="74c26-115">Remarks</span></span>  
 <span data-ttu-id="74c26-116">Domyślnie połączone zasoby są publiczne w zestawie, gdy są tworzone przy użyciu C# kompilatora.</span><span class="sxs-lookup"><span data-stu-id="74c26-116">By default, linked resources are public in the assembly when they are created with the C# compiler.</span></span> <span data-ttu-id="74c26-117">Aby udostępnić zasoby jako prywatne, określ `private` jako modyfikator dostępności.</span><span class="sxs-lookup"><span data-stu-id="74c26-117">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="74c26-118">Inny modyfikator inny niż `public` lub `private` jest niedozwolony.</span><span class="sxs-lookup"><span data-stu-id="74c26-118">No other modifier other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="74c26-119">**-linkresource —** wymaga jednej z opcji [-Target](./target-compiler-option.md) innych niż **-target: module**.</span><span class="sxs-lookup"><span data-stu-id="74c26-119">**-linkresource** requires one of the [-target](./target-compiler-option.md) options other than **-target:module**.</span></span>  
  
 <span data-ttu-id="74c26-120">Jeśli `filename` jest .NET Framework utworzony plik zasobów, na przykład przez [Resgen. exe](../../../framework/tools/resgen-exe-resource-file-generator.md) lub w środowisku deweloperskim, dostęp do niego można uzyskać <xref:System.Resources> za pomocą elementów członkowskich w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="74c26-120">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="74c26-121">Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="74c26-121">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="74c26-122">W przypadku wszystkich innych zasobów Użyj `GetManifestResource` metod <xref:System.Reflection.Assembly> w klasie, aby uzyskać dostęp do zasobu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="74c26-122">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="74c26-123">Plik określony w `filename` może być dowolnym formatem.</span><span class="sxs-lookup"><span data-stu-id="74c26-123">The file specified in `filename` can be any format.</span></span> <span data-ttu-id="74c26-124">Można na przykład utworzyć natywną bibliotekę DLL zestawu, tak aby można ją było zainstalować w globalnej pamięci podręcznej zestawów i uzyskać do niej dostęp z kodu zarządzanego w zestawie.</span><span class="sxs-lookup"><span data-stu-id="74c26-124">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span> <span data-ttu-id="74c26-125">W drugim z poniższych przykładów pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="74c26-125">The second of the following examples shows how to do this.</span></span> <span data-ttu-id="74c26-126">Tę samą czynność można wykonać w konsolidatorze zestawu.</span><span class="sxs-lookup"><span data-stu-id="74c26-126">You can do the same thing in the Assembly Linker.</span></span> <span data-ttu-id="74c26-127">Trzeci z poniższych przykładów pokazuje, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="74c26-127">The third of the following examples shows how to do this.</span></span> <span data-ttu-id="74c26-128">Aby uzyskać więcej informacji, zobacz [Al. exe (Konsolidator zestawu)](../../../framework/tools/al-exe-assembly-linker.md) i [Praca z zestawami i globalną pamięcią podręczną zestawów](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="74c26-128">For more information, see [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) and [Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span></span>  
  
 <span data-ttu-id="74c26-129">**-linkres** jest krótką formą **-linkresource —** .</span><span class="sxs-lookup"><span data-stu-id="74c26-129">**-linkres** is the short form of **-linkresource**.</span></span>  
  
 <span data-ttu-id="74c26-130">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można jej zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="74c26-130">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74c26-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="74c26-131">Example</span></span>  
 <span data-ttu-id="74c26-132">Kompiluj `in.cs` i Połącz z plikiem `rf.resource`zasobów:</span><span class="sxs-lookup"><span data-stu-id="74c26-132">Compile `in.cs` and link to resource file `rf.resource`:</span></span>  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a><span data-ttu-id="74c26-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="74c26-133">Example</span></span>  
 <span data-ttu-id="74c26-134">Kompiluj `A.cs` do biblioteki DLL, połącz ją z natywną biblioteką DLL N. dll i umieść dane wyjściowe w globalnej pamięci podręcznej zestawów (GAC).</span><span class="sxs-lookup"><span data-stu-id="74c26-134">Compile `A.cs` into a DLL, link to a native DLL N.dll, and put the output in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="74c26-135">W tym przykładzie zarówno plik. dll, jak i N. dll będą znajdować się w pamięci podręcznej GAC.</span><span class="sxs-lookup"><span data-stu-id="74c26-135">In this example, both A.dll and N.dll will reside in the GAC.</span></span>  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a><span data-ttu-id="74c26-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="74c26-136">Example</span></span>  
 <span data-ttu-id="74c26-137">Ten przykład wykonuje te same czynności co w poprzednim, ale przy użyciu opcji konsolidatora zestawu.</span><span class="sxs-lookup"><span data-stu-id="74c26-137">This example does the same thing as the previous one, but by using Assembly Linker options.</span></span>  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll   
gacutil -i A.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="74c26-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="74c26-138">See also</span></span>

- [<span data-ttu-id="74c26-139">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="74c26-139">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="74c26-140">Al.exe (konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="74c26-140">Al.exe (Assembly Linker)</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="74c26-141">Praca z zestawami i globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="74c26-141">Working with Assemblies and the Global Assembly Cache</span></span>](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="74c26-142">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="74c26-142">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
