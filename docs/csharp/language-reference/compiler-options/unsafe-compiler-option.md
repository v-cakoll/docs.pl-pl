---
title: -unsafe (opcje kompilatora C#)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 4a8f7d099b2cd3c1b4331c87f853b617fef505ae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726536"
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="04b2a-102">-unsafe (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="04b2a-102">-unsafe (C# Compiler Options)</span></span>
<span data-ttu-id="04b2a-103">**-Unsafe** — opcja kompilatora umożliwia kod, który używa [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) — słowo kluczowe, aby skompilować.</span><span class="sxs-lookup"><span data-stu-id="04b2a-103">The **-unsafe** compiler option allows code that uses the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04b2a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="04b2a-104">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="04b2a-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="04b2a-105">Remarks</span></span>  
 <span data-ttu-id="04b2a-106">Aby uzyskać więcej informacji na temat niebezpieczny kod, zobacz [niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="04b2a-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="04b2a-107">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="04b2a-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="04b2a-108">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="04b2a-108">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="04b2a-109">Kliknij przycisk **kompilacji** stronę właściwości.</span><span class="sxs-lookup"><span data-stu-id="04b2a-109">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="04b2a-110">Wybierz **Zezwalaj na niebezpieczny kod** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="04b2a-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
### <a name="to-add-this-option-in-a-csproj-file"></a><span data-ttu-id="04b2a-111">Aby dodać tę opcję w pliku csproj</span><span class="sxs-lookup"><span data-stu-id="04b2a-111">To add this option in a csproj file</span></span>

<span data-ttu-id="04b2a-112">Otwórz plik csproj projektu i dodaj następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="04b2a-112">Open the .csproj file for a project, and add the following elements:</span></span>

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 <span data-ttu-id="04b2a-113">Aby dowiedzieć się, jak programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span><span class="sxs-lookup"><span data-stu-id="04b2a-113">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04b2a-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="04b2a-114">Example</span></span>  
 <span data-ttu-id="04b2a-115">Skompilować `in.cs` dla trybu niebezpiecznego:</span><span class="sxs-lookup"><span data-stu-id="04b2a-115">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="04b2a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04b2a-116">See also</span></span>

- [<span data-ttu-id="04b2a-117">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="04b2a-117">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="04b2a-118">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="04b2a-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
