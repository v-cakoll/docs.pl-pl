---
title: -unsafe (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.assetid: fdb77ed9-da03-45bd-bb7f-250704da1bcc
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 146977522b400418a26f6a83e1a0ccdca8675bf9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="unsafe-c-compiler-options"></a><span data-ttu-id="4b80a-102">/unsafe (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="4b80a-102">/unsafe (C# Compiler Options)</span></span>
<span data-ttu-id="4b80a-103">**/ Unsafe** — opcja kompilatora umożliwia kodu korzystającego z [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) — słowo kluczowe do skompilowania.</span><span class="sxs-lookup"><span data-stu-id="4b80a-103">The **/unsafe** compiler option allows code that uses the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b80a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b80a-104">Syntax</span></span>  
  
```console  
/unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="4b80a-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4b80a-105">Remarks</span></span>  
 <span data-ttu-id="4b80a-106">Aby uzyskać więcej informacji na temat niebezpieczny kod, zobacz [niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="4b80a-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="4b80a-107">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4b80a-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="4b80a-108">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="4b80a-108">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="4b80a-109">Kliknij przycisk **kompilacji** strony właściwości.</span><span class="sxs-lookup"><span data-stu-id="4b80a-109">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="4b80a-110">Wybierz **Zezwalaj niebezpieczny kod** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="4b80a-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
 <span data-ttu-id="4b80a-111">Aby dowiedzieć się, jak ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span><span class="sxs-lookup"><span data-stu-id="4b80a-111">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b80a-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b80a-112">Example</span></span>  
 <span data-ttu-id="4b80a-113">Kompiluj `in.cs` dla trybu niebezpiecznego:</span><span class="sxs-lookup"><span data-stu-id="4b80a-113">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc /unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b80a-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b80a-114">See Also</span></span>  
 [<span data-ttu-id="4b80a-115">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="4b80a-115">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="4b80a-116">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="4b80a-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
