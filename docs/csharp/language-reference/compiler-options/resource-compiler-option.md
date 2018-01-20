---
title: -resource (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /resource
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c20de499ae0fd5f8869c9b6e78a308fde9787ef9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="a93c6-102">-resource (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="a93c6-102">-resource (C# Compiler Options)</span></span>
<span data-ttu-id="a93c6-103">Osadza określony zasób w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="a93c6-103">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a93c6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a93c6-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a93c6-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a93c6-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="a93c6-106">Plik zasobu .NET Framework ma być osadzony w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="a93c6-106">The .NET Framework resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="a93c6-107">`identifier`(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="a93c6-107">`identifier` (optional)</span></span>  
 <span data-ttu-id="a93c6-108">Nazwa logiczna zasobu; Nazwa, która jest używana do załadowania zasobu.</span><span class="sxs-lookup"><span data-stu-id="a93c6-108">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="a93c6-109">Wartość domyślna to nazwą pliku.</span><span class="sxs-lookup"><span data-stu-id="a93c6-109">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="a93c6-110">`accessibility-modifier`(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="a93c6-110">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="a93c6-111">Dostępność zasobu: publicznych lub prywatnych.</span><span class="sxs-lookup"><span data-stu-id="a93c6-111">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="a93c6-112">Wartość domyślna jest publiczny.</span><span class="sxs-lookup"><span data-stu-id="a93c6-112">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a93c6-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a93c6-113">Remarks</span></span>  
 <span data-ttu-id="a93c6-114">Użyj [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) Połącz zasób z zestawem i nie dodać pliku zasobu do pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="a93c6-114">Use [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="a93c6-115">Domyślnie zasoby są publiczne w zestawie podczas ich tworzenia za pomocą kompilatora C#.</span><span class="sxs-lookup"><span data-stu-id="a93c6-115">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="a93c6-116">Zasoby prywatny, ustaw `private` jako modyfikator dostępności.</span><span class="sxs-lookup"><span data-stu-id="a93c6-116">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="a93c6-117">Nie inne dostępności innych niż `public` lub `private` jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="a93c6-117">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="a93c6-118">Jeśli `filename` to plik zasobu .NET Framework utworzone, na przykład przez [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) lub w środowisku programistycznym, jest dostępny z elementami członkowskimi w <xref:System.Resources> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a93c6-118">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="a93c6-119">Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a93c6-119">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a93c6-120">Inne zasoby, można użyć `GetManifestResource` metod w <xref:System.Reflection.Assembly> klasę, aby uzyskać dostęp do zasobu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a93c6-120">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="a93c6-121">**-res** jest krótka forma **-zasobów**.</span><span class="sxs-lookup"><span data-stu-id="a93c6-121">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="a93c6-122">Kolejność zasobów w pliku wyjściowym jest określana w kolejności określonej w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="a93c6-122">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="a93c6-123">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a93c6-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="a93c6-124">Dodawanie pliku zasobu do projektu.</span><span class="sxs-lookup"><span data-stu-id="a93c6-124">Add a resource file to your project.</span></span>  
  
2.  <span data-ttu-id="a93c6-125">Wybierz plik, który ma zostać osadzony w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="a93c6-125">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3.  <span data-ttu-id="a93c6-126">Wybierz **Akcja kompilacji** pliku w **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="a93c6-126">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4.  <span data-ttu-id="a93c6-127">Ustaw **Akcja kompilacji** do **osadzonego zasobu**.</span><span class="sxs-lookup"><span data-stu-id="a93c6-127">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="a93c6-128">Aby dowiedzieć się, jak ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span><span class="sxs-lookup"><span data-stu-id="a93c6-128">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a93c6-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="a93c6-129">Example</span></span>  
 <span data-ttu-id="a93c6-130">Kompiluj `in.cs` i Dołącz plik zasobu `rf.resource`:</span><span class="sxs-lookup"><span data-stu-id="a93c6-130">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="a93c6-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a93c6-131">See Also</span></span>  
 [<span data-ttu-id="a93c6-132">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="a93c6-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="a93c6-133">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="a93c6-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
