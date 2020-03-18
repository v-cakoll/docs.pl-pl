---
title: -resource (Opcje kompilatora C#)
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602525"
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="87067-102">-resource (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="87067-102">-resource (C# Compiler Options)</span></span>
<span data-ttu-id="87067-103">Osadza określony zasób w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="87067-103">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87067-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="87067-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="87067-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="87067-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="87067-106">Plik zasobów .NET Framework, który chcesz osadzić w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="87067-106">The .NET Framework resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="87067-107">`identifier` (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="87067-107">`identifier` (optional)</span></span>  
 <span data-ttu-id="87067-108">Logiczna nazwa zasobu; nazwa, która jest używana do ładowania zasobu.</span><span class="sxs-lookup"><span data-stu-id="87067-108">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="87067-109">Wartością domyślną jest nazwa nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="87067-109">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="87067-110">`accessibility-modifier` (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="87067-110">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="87067-111">Dostępność zasobu: publiczna lub prywatna.</span><span class="sxs-lookup"><span data-stu-id="87067-111">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="87067-112">Wartość domyślna jest publiczna.</span><span class="sxs-lookup"><span data-stu-id="87067-112">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87067-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87067-113">Remarks</span></span>  
 <span data-ttu-id="87067-114">Użyj [-linkresource,](./linkresource-compiler-option.md) aby połączyć zasób z zestawem i nie dodawać pliku zasobu do pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="87067-114">Use [-linkresource](./linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="87067-115">Domyślnie zasoby są publiczne w zestawie, gdy są tworzone przy użyciu kompilatora C#.</span><span class="sxs-lookup"><span data-stu-id="87067-115">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="87067-116">Aby zasoby były `private` prywatne, określ jako modyfikator ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="87067-116">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="87067-117">Żadna inna `public` dostępność `private` nie jest lub jest dozwolona.</span><span class="sxs-lookup"><span data-stu-id="87067-117">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="87067-118">Jeśli `filename` jest plikiem zasobów .NET Framework utworzonym na przykład przez [resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) lub w środowisku <xref:System.Resources> programistycznym, można uzyskać do niego dostęp za pomocą elementów członkowskich w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="87067-118">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="87067-119">Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="87067-119">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="87067-120">Dla wszystkich innych zasobów `GetManifestResource` należy użyć <xref:System.Reflection.Assembly> metod w klasie, aby uzyskać dostęp do zasobu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="87067-120">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="87067-121">**-res** jest krótką formą **-resource**.</span><span class="sxs-lookup"><span data-stu-id="87067-121">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="87067-122">Kolejność zasobów w pliku wyjściowym jest określana na podstawie kolejności określonej w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="87067-122">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="87067-123">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="87067-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="87067-124">Dodaj plik zasobów do projektu.</span><span class="sxs-lookup"><span data-stu-id="87067-124">Add a resource file to your project.</span></span>  
  
2. <span data-ttu-id="87067-125">Wybierz plik, który chcesz osadzić w **Eksploratorze rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="87067-125">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3. <span data-ttu-id="87067-126">Wybierz **akcję kompilacji** dla pliku w oknie **Właściwości.**</span><span class="sxs-lookup"><span data-stu-id="87067-126">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4. <span data-ttu-id="87067-127">Ustaw **akcję kompilacji** na **osadzony zasób**.</span><span class="sxs-lookup"><span data-stu-id="87067-127">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="87067-128">Aby uzyskać informacje dotyczące programowego ustawiania tej <xref:VSLangProj80.FileProperties2.BuildAction%2A>opcji kompilatora, zobacz .</span><span class="sxs-lookup"><span data-stu-id="87067-128">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87067-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="87067-129">Example</span></span>  
 <span data-ttu-id="87067-130">Kompilowanie `in.cs` i dołączanie pliku `rf.resource`zasobów:</span><span class="sxs-lookup"><span data-stu-id="87067-130">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="87067-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87067-131">See also</span></span>

- [<span data-ttu-id="87067-132">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="87067-132">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="87067-133">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="87067-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
