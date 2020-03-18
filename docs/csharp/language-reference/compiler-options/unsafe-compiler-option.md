---
title: -niebezpieczne (opcje kompilatora C#)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 146299fda103567b111c66400c17edf36addd843
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "65877990"
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="ecc2b-102">-niebezpieczne (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="ecc2b-102">-unsafe (C# Compiler Options)</span></span>

<span data-ttu-id="ecc2b-103">**Opcja -unsafe** kompilator umożliwia kod, który używa [niebezpiecznego](../keywords/unsafe.md) słowa kluczowego do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-103">The **-unsafe** compiler option allows code that uses the [unsafe](../keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecc2b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ecc2b-104">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="ecc2b-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ecc2b-105">Remarks</span></span>

<span data-ttu-id="ecc2b-106">Aby uzyskać więcej informacji na temat niebezpiecznego kodu, zobacz [Niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="ecc2b-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ecc2b-107">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ecc2b-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="ecc2b-108">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-108">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="ecc2b-109">Kliknij stronę **Właściwości kompilacji.**</span><span class="sxs-lookup"><span data-stu-id="ecc2b-109">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="ecc2b-110">Zaznacz pole wyboru **Zezwalaj na niebezpieczny kod.**</span><span class="sxs-lookup"><span data-stu-id="ecc2b-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
### <a name="to-add-this-option-in-a-csproj-file"></a><span data-ttu-id="ecc2b-111">Aby dodać tę opcję w pliku csproj</span><span class="sxs-lookup"><span data-stu-id="ecc2b-111">To add this option in a csproj file</span></span>

<span data-ttu-id="ecc2b-112">Otwórz plik csproj dla projektu i dodaj następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="ecc2b-112">Open the .csproj file for a project, and add the following elements:</span></span>

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 <span data-ttu-id="ecc2b-113">Aby uzyskać informacje dotyczące programowego ustawiania tej <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>opcji kompilatora, zobacz .</span><span class="sxs-lookup"><span data-stu-id="ecc2b-113">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecc2b-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="ecc2b-114">Example</span></span>

<span data-ttu-id="ecc2b-115">Skompiluj `in.cs` dla trybu niebezpiecznego:</span><span class="sxs-lookup"><span data-stu-id="ecc2b-115">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="ecc2b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ecc2b-116">See also</span></span>

- [<span data-ttu-id="ecc2b-117">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="ecc2b-117">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="ecc2b-118">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="ecc2b-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
