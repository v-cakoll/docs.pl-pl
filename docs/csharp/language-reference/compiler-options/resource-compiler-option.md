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
ms.openlocfilehash: 726956275436e22723bc32b98b2b8b7c7df5fb12
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="resource-c-compiler-options"></a><span data-ttu-id="896c5-102">/resource (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="896c5-102">/resource (C# Compiler Options)</span></span>
<span data-ttu-id="896c5-103">Osadza określony zasób w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="896c5-103">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="896c5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="896c5-104">Syntax</span></span>  
  
```console  
/resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="896c5-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="896c5-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="896c5-106">Plik zasobu .NET Framework ma być osadzony w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="896c5-106">The .NET Framework resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="896c5-107">`identifier`(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="896c5-107">`identifier` (optional)</span></span>  
 <span data-ttu-id="896c5-108">Nazwa logiczna zasobu; Nazwa, która jest używana do załadowania zasobu.</span><span class="sxs-lookup"><span data-stu-id="896c5-108">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="896c5-109">Wartość domyślna to nazwą pliku.</span><span class="sxs-lookup"><span data-stu-id="896c5-109">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="896c5-110">`accessibility-modifier`(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="896c5-110">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="896c5-111">Dostępność zasobu: publicznych lub prywatnych.</span><span class="sxs-lookup"><span data-stu-id="896c5-111">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="896c5-112">Wartość domyślna jest publiczny.</span><span class="sxs-lookup"><span data-stu-id="896c5-112">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="896c5-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="896c5-113">Remarks</span></span>  
 <span data-ttu-id="896c5-114">Użyj [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) Połącz zasób z zestawem i nie dodać pliku zasobu do pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="896c5-114">Use [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="896c5-115">Domyślnie zasoby są publiczne w zestawie podczas ich tworzenia za pomocą kompilatora C#.</span><span class="sxs-lookup"><span data-stu-id="896c5-115">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="896c5-116">Zasoby prywatny, ustaw `private` jako modyfikator dostępności.</span><span class="sxs-lookup"><span data-stu-id="896c5-116">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="896c5-117">Nie inne dostępności innych niż `public` lub `private` jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="896c5-117">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="896c5-118">Jeśli `filename` to plik zasobu .NET Framework utworzone, na przykład przez [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) lub w środowisku programistycznym, jest dostępny z elementami członkowskimi w <xref:System.Resources> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="896c5-118">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="896c5-119">Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="896c5-119">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="896c5-120">Inne zasoby, można użyć `GetManifestResource` metod w <xref:System.Reflection.Assembly> klasę, aby uzyskać dostęp do zasobu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="896c5-120">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="896c5-121">**/ res** jest krótka forma **/Resource**.</span><span class="sxs-lookup"><span data-stu-id="896c5-121">**/res** is the short form of **/resource**.</span></span>  
  
 <span data-ttu-id="896c5-122">Kolejność zasobów w pliku wyjściowym jest określana w kolejności określonej w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="896c5-122">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="896c5-123">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="896c5-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="896c5-124">Dodawanie pliku zasobu do projektu.</span><span class="sxs-lookup"><span data-stu-id="896c5-124">Add a resource file to your project.</span></span>  
  
2.  <span data-ttu-id="896c5-125">Wybierz plik, który ma zostać osadzony w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="896c5-125">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3.  <span data-ttu-id="896c5-126">Wybierz **Akcja kompilacji** pliku w **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="896c5-126">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4.  <span data-ttu-id="896c5-127">Ustaw **Akcja kompilacji** do **osadzonego zasobu**.</span><span class="sxs-lookup"><span data-stu-id="896c5-127">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="896c5-128">Aby dowiedzieć się, jak ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span><span class="sxs-lookup"><span data-stu-id="896c5-128">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="896c5-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="896c5-129">Example</span></span>  
 <span data-ttu-id="896c5-130">Kompiluj `in.cs` i Dołącz plik zasobu `rf.resource`:</span><span class="sxs-lookup"><span data-stu-id="896c5-130">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc /resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="896c5-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="896c5-131">See Also</span></span>  
 [<span data-ttu-id="896c5-132">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="896c5-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="896c5-133">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="896c5-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
