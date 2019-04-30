---
title: -resource (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /resource
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
ms.openlocfilehash: ed9f4648ae632786ce860ce2c02637977f709c55
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662442"
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="20e72-102">-resource (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="20e72-102">-resource (C# Compiler Options)</span></span>
<span data-ttu-id="20e72-103">Osadza określony zasób w pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="20e72-103">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20e72-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="20e72-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="20e72-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="20e72-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="20e72-106">Plik zasobu .NET Framework, którą chcesz osadzić w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="20e72-106">The .NET Framework resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="20e72-107">`identifier` (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="20e72-107">`identifier` (optional)</span></span>  
 <span data-ttu-id="20e72-108">Nazwa logiczna zasobu; Nazwa która jest używana do ładowania zasobów.</span><span class="sxs-lookup"><span data-stu-id="20e72-108">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="20e72-109">Wartość domyślna to nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="20e72-109">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="20e72-110">`accessibility-modifier` (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="20e72-110">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="20e72-111">Dostępność zasobów: publicznych lub prywatnych.</span><span class="sxs-lookup"><span data-stu-id="20e72-111">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="20e72-112">Wartość domyślna jest publiczny.</span><span class="sxs-lookup"><span data-stu-id="20e72-112">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20e72-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="20e72-113">Remarks</span></span>  
 <span data-ttu-id="20e72-114">Użyj [- linkresource —](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) łączenie zasobu z zestawem i nie należy dodać plik zasobów do pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="20e72-114">Use [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="20e72-115">Zasoby są domyślnie publiczne w zestawie podczas ich tworzenia za pomocą kompilatora C#.</span><span class="sxs-lookup"><span data-stu-id="20e72-115">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="20e72-116">Zasoby prywatne, ustaw `private` jako modyfikator dostępności metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="20e72-116">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="20e72-117">Nie innych ułatwień dostępu innym niż `public` lub `private` jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="20e72-117">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="20e72-118">Jeśli `filename` jest plikiem zasobów .NET Framework, utworzonym na przykład przez [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) lub w środowisku deweloperskim, jest dostępny za pomocą elementów członkowskich w <xref:System.Resources> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="20e72-118">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="20e72-119">Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="20e72-119">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="20e72-120">W przypadku wszystkich innych zasobów, użyj `GetManifestResource` metody <xref:System.Reflection.Assembly> klasy, aby uzyskać dostęp do zasobu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="20e72-120">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="20e72-121">**-res** jest krótka forma **-resource**.</span><span class="sxs-lookup"><span data-stu-id="20e72-121">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="20e72-122">Kolejność zasobów w pliku danych wyjściowych jest określana na podstawie kolejności określonej w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="20e72-122">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="20e72-123">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="20e72-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="20e72-124">Dodaj plik zasobów do projektu.</span><span class="sxs-lookup"><span data-stu-id="20e72-124">Add a resource file to your project.</span></span>  
  
2. <span data-ttu-id="20e72-125">Wybierz plik, który ma zostać osadzony w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="20e72-125">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3. <span data-ttu-id="20e72-126">Wybierz **Build Action** dla pliku **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="20e72-126">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4. <span data-ttu-id="20e72-127">Ustaw **Akcja kompilacji** do **osadzony zasób**.</span><span class="sxs-lookup"><span data-stu-id="20e72-127">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="20e72-128">Aby dowiedzieć się, jak programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span><span class="sxs-lookup"><span data-stu-id="20e72-128">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20e72-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="20e72-129">Example</span></span>  
 <span data-ttu-id="20e72-130">Skompilować `in.cs` i dołączyć plik zasobów `rf.resource`:</span><span class="sxs-lookup"><span data-stu-id="20e72-130">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="20e72-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20e72-131">See also</span></span>

- [<span data-ttu-id="20e72-132">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="20e72-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="20e72-133">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="20e72-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
