---
title: -Resource (C# opcje kompilatora)
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
ms.openlocfilehash: e14bf59f5922a918b627af22c052c8efd9081e84
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602525"
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="051da-102">-Resource (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="051da-102">-resource (C# Compiler Options)</span></span>
<span data-ttu-id="051da-103">Osadza określony zasób w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="051da-103">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="051da-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="051da-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="051da-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="051da-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="051da-106">Plik zasobów .NET Framework, który ma zostać osadzony w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="051da-106">The .NET Framework resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="051da-107">`identifier`obowiązkowe</span><span class="sxs-lookup"><span data-stu-id="051da-107">`identifier` (optional)</span></span>  
 <span data-ttu-id="051da-108">Nazwa logiczna zasobu; Nazwa, która jest używana do ładowania zasobu.</span><span class="sxs-lookup"><span data-stu-id="051da-108">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="051da-109">Wartość domyślna to nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="051da-109">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="051da-110">`accessibility-modifier`obowiązkowe</span><span class="sxs-lookup"><span data-stu-id="051da-110">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="051da-111">Dostępność zasobu: Public lub Private.</span><span class="sxs-lookup"><span data-stu-id="051da-111">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="051da-112">Wartość domyślna to Public.</span><span class="sxs-lookup"><span data-stu-id="051da-112">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="051da-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="051da-113">Remarks</span></span>  
 <span data-ttu-id="051da-114">Użyj polecenia [-linkresource —](./linkresource-compiler-option.md) , aby połączyć zasób z zestawem, a nie dodać pliku zasobów do pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="051da-114">Use [-linkresource](./linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="051da-115">Domyślnie zasoby są publiczne w zestawie, gdy są tworzone przy użyciu C# kompilatora.</span><span class="sxs-lookup"><span data-stu-id="051da-115">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="051da-116">Aby udostępnić zasoby jako prywatne, określ `private` jako modyfikator dostępności.</span><span class="sxs-lookup"><span data-stu-id="051da-116">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="051da-117">Żadna inna dostępność jest inna `public` niż `private` lub niedozwolona.</span><span class="sxs-lookup"><span data-stu-id="051da-117">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="051da-118">Jeśli `filename` jest .NET Framework utworzony plik zasobów, na przykład przez [Resgen. exe](../../../framework/tools/resgen-exe-resource-file-generator.md) lub w środowisku deweloperskim, dostęp do niego można uzyskać <xref:System.Resources> za pomocą elementów członkowskich w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="051da-118">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="051da-119">Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="051da-119">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="051da-120">W przypadku wszystkich innych zasobów Użyj `GetManifestResource` metod <xref:System.Reflection.Assembly> w klasie, aby uzyskać dostęp do zasobu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="051da-120">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="051da-121">**-res** to krótka forma **zasobu**.</span><span class="sxs-lookup"><span data-stu-id="051da-121">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="051da-122">Kolejność zasobów w pliku wyjściowym jest określana na podstawie kolejności określonej w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="051da-122">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="051da-123">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="051da-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="051da-124">Dodaj plik zasobów do projektu.</span><span class="sxs-lookup"><span data-stu-id="051da-124">Add a resource file to your project.</span></span>  
  
2. <span data-ttu-id="051da-125">Wybierz plik, który ma zostać osadzony w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="051da-125">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3. <span data-ttu-id="051da-126">Wybierz pozycję **Akcja kompilacji** dla pliku w oknie **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="051da-126">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4. <span data-ttu-id="051da-127">Ustaw **akcję kompilacji** na **zasób osadzony**.</span><span class="sxs-lookup"><span data-stu-id="051da-127">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="051da-128">Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.FileProperties2.BuildAction%2A>tę opcję kompilatora, zobacz.</span><span class="sxs-lookup"><span data-stu-id="051da-128">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="051da-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="051da-129">Example</span></span>  
 <span data-ttu-id="051da-130">Kompiluj `in.cs` i Dołącz plik `rf.resource`zasobu:</span><span class="sxs-lookup"><span data-stu-id="051da-130">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="051da-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="051da-131">See also</span></span>

- [<span data-ttu-id="051da-132">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="051da-132">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="051da-133">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="051da-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
