---
title: -unsafe (opcje kompilatora C#)
ms.date: 04/25/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 35868923ed2f34587c66f04395324489e8b36538
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="1916d-102">-unsafe (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="1916d-102">-unsafe (C# Compiler Options)</span></span>
<span data-ttu-id="1916d-103">**-Unsafe** — opcja kompilatora umożliwia kodu korzystającego z [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) — słowo kluczowe do skompilowania.</span><span class="sxs-lookup"><span data-stu-id="1916d-103">The **-unsafe** compiler option allows code that uses the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1916d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1916d-104">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="1916d-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1916d-105">Remarks</span></span>  
 <span data-ttu-id="1916d-106">Aby uzyskać więcej informacji na temat niebezpieczny kod, zobacz [niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="1916d-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="1916d-107">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1916d-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="1916d-108">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="1916d-108">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="1916d-109">Kliknij przycisk **kompilacji** strony właściwości.</span><span class="sxs-lookup"><span data-stu-id="1916d-109">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="1916d-110">Wybierz **Zezwalaj niebezpieczny kod** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="1916d-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
### <a name="to-add-this-option-in-a-csproj-file"></a><span data-ttu-id="1916d-111">Aby dodać tę opcję w plik csproj</span><span class="sxs-lookup"><span data-stu-id="1916d-111">To add this option in a csproj file</span></span>

<span data-ttu-id="1916d-112">Otwórz pliku .csproj dla projektu i dodaj następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="1916d-112">Open the .csproj file for a project, and add the following elements:</span></span>

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 <span data-ttu-id="1916d-113">Aby dowiedzieć się, jak ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span><span class="sxs-lookup"><span data-stu-id="1916d-113">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1916d-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="1916d-114">Example</span></span>  
 <span data-ttu-id="1916d-115">Kompiluj `in.cs` dla trybu niebezpiecznego:</span><span class="sxs-lookup"><span data-stu-id="1916d-115">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="1916d-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1916d-116">See Also</span></span>  
 [<span data-ttu-id="1916d-117">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="1916d-117">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="1916d-118">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="1916d-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
